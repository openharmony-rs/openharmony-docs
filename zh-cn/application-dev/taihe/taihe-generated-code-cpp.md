# 深入解析Taihe生成的代码（ABI层与C++层）

本文档旨在帮助用户深入理解Taihe在ABI层和C++层生成的代码结构和调用链。通过对生成代码的分析，用户可以更好地掌握Taihe的工作原理，并在实际开发中有效利用这些自动生成的接口。

以下我们将以一个简单的API为例，展示Taihe如何在发布方和消费方之间生成ABI层和C++层的代码，以及数据如何跨越这两个层次进行传递。

## 原始Taihe IDL文件内容

```rust
// File: example/idl/my.package.ohidl
struct Data {
    a: i32;
    b: String;
}
union Result {
    ok: i32;
    err: String;
}
interface IFoo {
    init(): void;
}
interface IBar: IFoo {
    process(data: Data): Result;
}
function processWithBar(bar: IBar, data: Data): Result;
```

## 生成的代码结构

当Taihe工具链处理`my.package.ohidl`这个文件后，会在指定的输出目录生成一系列文件。这些文件可以被清晰地划分为ABI层和C++层。

以下是生成文件的结构树及其功能简介：
```
generated/
├── include/
│   ├── my.package.Data.abi.{0,1,2}.h      // ABI层：结构体Data的分阶段定义
│   ├── my.package.Result.abi.{0,1,2}.h    // ABI层：联合体Result的分阶段定义
│   ├── my.package.IFoo.abi.{0,1,2}.h      // ABI层：接口IFoo的分阶段定义
│   ├── my.package.IBar.abi.{0,1,2}.h      // ABI层：接口IBar的分阶段定义
│   ├── my.package.abi.h                   // ABI层：聚合头文件
│   ├── my.package.Data.proj.{0,1,2}.hpp   // C++层：结构体Data的C++投影
│   ├── my.package.Result.proj.{0,1,2}.hpp // C++层：联合体Result的C++投影
│   ├── my.package.IFoo.proj.{0,1,2}.hpp   // C++层：接口IFoo的C++投影
│   ├── my.package.IBar.proj.{0,1,2}.hpp   // C++层：接口IBar的C++投影
│   ├── my.package.proj.hpp                // C++层：聚合通用头文件（供接口实现方和用户使用）
│   ├── my.package.user.hpp                // C++层：供接口【消费方】使用的头文件
│   └── my.package.impl.hpp                // C++层：供接口【发布方】使用的头文件
├── src/
│   └── my.package.abi.c                   // ABI层：接口IID等符号的定义
└── temp/
    └── my.package.impl.cpp                // C++层：为发布方提供的实现模板
```

- **ABI层 (`.abi.h`, `.abi.c`)**：定义了所有类型的C语言内存布局、函数签名和接口ID。这是所有上层代码（包括C++和其他语言）的共同基础。
- **C++层 (`.hpp`, `.cpp`)**：
    - `proj.hpp`文件：包含了所有公开类型（结构体、接口等）的C++封装，是接口实现方和使用方都需要引用的基础文件。
    - `user.hpp`文件：除了`proj.hpp`的内容外，还包含了全局函数的C++包装，专供接口的【消费方】调用。
    - `impl.hpp`文件：提供了导出全局函数的宏，专供接口的【发布方】使用。
    - `impl.cpp`文件：一个自动生成的实现骨架，帮助开发者快速开始编写接口的实现代码。

值得注意的是，头文件被拆分为`*.{0,1,2}.h/hpp`的形式，这是用于解决C/C++中类型间循环依赖问题。
- `*.0.h/hpp`：包含类型的前向声明，`*.proj.0.hpp`中还会包含`taihe::as_abi`模板的特化，用于表示ABI类型和C++类型之间的映射关系。
- `*.1.h/hpp`：包含类型本身的完整定义，以及接口间的动态、静态转换方法等。但不包含接口成员方法的声明和定义。
- `*.2.h/hpp`：包含了接口的所有成员方法，并且会递归地包含该类型所依赖的其他类型（如结构体和联合体中成员的类型、接口成员方法的参数和返回值的类型等）的全部成员方法。

## 运行时调用链示例

理解运行时调用链是掌握Taihe工作原理的关键。

### 场景一：创建对象并调用方法

**代码**:
```cpp
using namespace my::package;

// 创建对象
IBar bar = taihe::make_holder<BarImpl, IBar>();
// 调用方法
bar->process(data);
```

**调用链**:
1.  **对象创建 (`make_holder`)**：（需结合`runtime/include/taihe/object.hpp`）
    1. `taihe::make_holder<BarImpl, IBar>()`会调用`taihe::impl_holder<BarImpl, IBar>`的静态工厂方法`make()`。这会使得在编译期生成一个`rtti`编译期常量，其中包含了`BarImpl`的类型信息，如版本信息、析构函数、Interface ID Map（从所有实现的接口ID到相应虚表指针的映射关系）等。
    2. 接下来，`make()`方法会在堆上申请内存，创建一个`taihe::data_block<BarImpl>`对象，该对象内部同时包含`DataBlockHead`数据和`BarImpl`的实例。`BarImpl`的构造函数会被调用。
    3. 接下来会调用`tobj_init`函数来初始化`DataBlockHead`，这会将对象的引用计数设置为1，并将`rtti`的地址存入`DataBlockHead`的`rtti_ptr`中。
    4. `taihe::impl_holder<BarImpl, IBar>`会持有指向该`taihe::data_block<BarImpl>`对象的指针（`data_ptr`）。
    5. 最后，`taihe::impl_holder<BarImpl, IBar>`被隐式转换为`IBar`，这会根据前者的编译期信息，找到`BarImpl`对应于`IBar`接口的虚表指针（`vtbl_ptr`），并和`data_ptr`一起构成一个`IBar`对象。转换后的对象只能调用`IBar`接口上定义的方法，而丢失了`BarImpl`类本身的具体实现细节。

2.  **方法调用 (`bar->process`)**：
    1. C++代码`bar->process(data)`会调用`weak::IBar::virtual_type`中定义的`process`方法。
    2. 这个C++包装方法通过`into_abi`将C++类型的`data`转换为ABI类型，然后调用ABI层的辅助函数`my_package_IBar_process_f`。
    3. `my_package_IBar_process_f`通过`bar`的`vtbl_ptr`取得`ftbl_ptr_0`（`IBar`的函数表），并调用其中的`process`函数指针。
    4. 这个函数指针指向`weak::IBar::methods_impl<BarImpl>::process`这个静态模板方法，该模板方法是之前在创建`taihe::impl_holder<BarImpl, IBar>`时自动实例化出来，并注册到虚函数表中的。
    5. `methods_impl<BarImpl>::process`是连接ABI和C++实现的最后一环。它接收ABI类型的参数并通过`taihe::from_abi`转换回C++类型，使用`taihe::cast_data_ptr<BarImpl>`将通用的`data_ptr`安全地转回`BarImpl*`类型，然后调用用户在`BarImpl`类中真正实现的`process`方法。
    6. 返回值沿着相反的路径，从`BarImpl::process`返回的C++ `Result`对象，通过`into_abi`转换回ABI `my_package_Result_t`，最终通过`from_abi`转换回调用方的C++ `Result`对象。

3. **析构对象**：
    1. 当`bar`的所有引用都被销毁时，其引用计数会减少到0，然后通过`DataBlockHead`类型的`data_ptr`拿到其`rtti_ptr`，从中获取到`BarImpl`的析构函数并调用。

### 场景二：静态转换（子接口到父接口）

**代码**:
```cpp
using namespace my::package;

IBar bar = ...;
weak::IFoo foo = bar; // 静态转换
```
**调用链**:
1.  该赋值操作触发了`IBar`中定义的到`IFoo`的转换运算符。
2.  此运算符内部调用了ABI层的`my_package_IBar_1_static`辅助函数。
3.  `_static`函数的实现极其高效：它直接对`IBar`的虚表指针`vtbl_ptr`进行指针运算，加上一个编译时已知的偏移量，直接定位到`IBar`虚表中内嵌的`IFoo`虚表部分的起始地址。
4.  这个过程完全在编译期确定，无需任何运行时查找，因此称为“静态转换”。

### 场景三：动态转换（任意接口间）

**代码**:
```cpp
using namespace my::package;

IFoo foo = ...;
auto bar = weak::IBar(foo); // 尝试动态转换为IBar
if (!bar.is_error()) {
    // 转换成功
}
```
**调用链**:
1.  该构造调用了`weak::IBar`的`explicit IBar(::taihe::data_view other)`构造函数。
2.  此构造函数内部调用了ABI层的`my_package_IBar_dynamic`辅助函数。
3.  `_dynamic`函数执行以下运行时操作：
    1. 通过`foo`对象的`data_ptr`找到`DataBlockHead`。
    2. 通过`DataBlockHead`上的`rtti_ptr`找到`typeinfo`结构。
    3. 遍历`typeinfo`中的`idmap`数组。
    4. 将`idmap`中每个条目的`id`与目标接口的IID（`my_package_IBar_i`）进行比较。
    5. 如果找到匹配项，则返回该条目对应的`vtbl_ptr`。
    6. 如果遍历完仍未找到，返回`NULL`。
4.  C++层的构造函数接收到返回的`vtbl_ptr`。如果为`NULL`，则`bar.is_error()`将返回`true`，表示转换失败。

## 附录：生成文件的完整内容

以`my.package`为例，以下是生成的文件内容，按生成的后端排列。

### `abi-header`

```c
// File: example/generated/include/my.package.Data.abi.0.h
#pragma once
#include "taihe/common.h"
// 阶段0：结构体my_package_Data_t的前向声明，用于解决头文件间的循环依赖。
struct my_package_Data_t;

// File: example/generated/include/my.package.Data.abi.1.h
#pragma once
#include "my.package.Data.abi.0.h"
#include "taihe/string.abi.h"
// 阶段1：结构体my_package_Data_t的完整C语言定义，描述了其在内存中的布局。
struct my_package_Data_t {
    int32_t a;
    struct TString b;
};

// File: example/generated/include/my.package.Data.abi.2.h
#pragma once
#include "my.package.Data.abi.1.h"
// 阶段2：为my.package.Data保留，用于包含其成员依赖类型的阶段2头文件。

// File: example/generated/include/my.package.Result.abi.0.h
#pragma once
#include "taihe/common.h"
// 阶段0：联合体my_package_Result_t的前向声明。
struct my_package_Result_t;

// File: example/generated/include/my.package.Result.abi.1.h
#pragma once
#include "my.package.Result.abi.0.h"
#include "taihe/string.abi.h"
// 联合体my_package_Result_union的C语言内存布局。
union my_package_Result_union {
    int32_t ok;
    struct TString err;
};
// 阶段1：联合体my_package_Result_t的完整C语言定义。
// 它包含一个标签(m_tag)用于区分当前激活的成员，以及一个存储数据的联合体(m_data)。
struct my_package_Result_t {
    int m_tag;
    union my_package_Result_union m_data;
};

// File: example/generated/include/my.package.Result.abi.2.h
#pragma once
#include "my.package.Result.abi.1.h"
// 阶段2：为my.package.Result保留。

// File: example/generated/include/my.package.IFoo.abi.0.h
#pragma once
#include "taihe/object.abi.h"
// 阶段0：接口my_package_IFoo_t的前向声明。
struct my_package_IFoo_t;

// File: example/generated/include/my.package.IFoo.abi.1.h
#pragma once
#include "my.package.IFoo.abi.0.h"
// IFoo接口的函数表(function table)前向声明。
struct my_package_IFoo_ftable;
// IFoo接口的虚函数表(virtual table)，包含指向函数表的指针。
struct my_package_IFoo_vtable {
    struct my_package_IFoo_ftable const* ftbl_ptr_0;
};
// 导出的IFoo接口的唯一标识符(Interface ID, IID)。
TH_EXPORT void const* const my_package_IFoo_i;
// IFoo接口在ABI层的表示，它是一个胖指针，包含一个虚表指针(vtbl_ptr)和一个数据指针(data_ptr)。
struct my_package_IFoo_t {
    struct my_package_IFoo_vtable const* vtbl_ptr;
    struct DataBlockHead* data_ptr;
};
// 动态转换辅助函数：在运行时通过RTTI查找目标接口(IFoo)的虚表。
TH_INLINE struct my_package_IFoo_vtable const* my_package_IFoo_dynamic(struct TypeInfo const* rtti_ptr) {
    for (size_t i = 0; i < rtti_ptr->len; i++) {
        if (rtti_ptr->idmap[i].id == my_package_IFoo_i) {
            return (struct my_package_IFoo_vtable const*)rtti_ptr->idmap[i].vtbl_ptr;
        }
    }
    return NULL;
}

// File: example/generated/include/my.package.IFoo.abi.2.h
#pragma once
#include "my.package.IFoo.abi.1.h"
// IFoo函数表的完整定义，包含其所有方法的函数指针。
struct my_package_IFoo_ftable {
    void (*init)(struct my_package_IFoo_t tobj);
};
// 调用init方法的内联辅助函数。它通过虚表指针找到并调用实际的函数实现。
TH_INLINE void my_package_IFoo_init_f(struct my_package_IFoo_t tobj) {
    return tobj.vtbl_ptr->ftbl_ptr_0->init(tobj);
}

// File: example/generated/include/my.package.IBar.abi.0.h
#pragma once
#include "taihe/object.abi.h"
// 阶段0：接口my_package_IBar_t的前向声明。
struct my_package_IBar_t;

// File: example/generated/include/my.package.IBar.abi.1.h
#pragma once
#include "my.package.IBar.abi.0.h"
#include "my.package.IFoo.abi.1.h"
struct my_package_IBar_ftable;
// IBar的虚表定义。因为它继承自IFoo，所以其虚表包含自身的函数表指针(ftbl_ptr_0)。
// 和父接口IFoo的函数表指针(ftbl_ptr_1)。
struct my_package_IBar_vtable {
    struct my_package_IBar_ftable const* ftbl_ptr_0;
    struct my_package_IFoo_ftable const* ftbl_ptr_1;
};
TH_EXPORT void const* const my_package_IBar_i;
struct my_package_IBar_t {
    struct my_package_IBar_vtable const* vtbl_ptr;
    struct DataBlockHead* data_ptr;
};
// 静态转换辅助函数：通过编译时已知的偏移量，从IBar的虚表指针直接计算出父接口IFoo的虚表指针。
TH_INLINE struct my_package_IFoo_vtable const* my_package_IBar_1_static(struct my_package_IBar_vtable const* vtbl_ptr) {
    return vtbl_ptr ? (struct my_package_IFoo_vtable const*)((void* const*)vtbl_ptr + 1) : NULL;
}
// 动态转换辅助函数：在运行时通过RTTI查找目标接口(IBar)的虚表。
TH_INLINE struct my_package_IBar_vtable const* my_package_IBar_dynamic(struct TypeInfo const* rtti_ptr) {
    for (size_t i = 0; i < rtti_ptr->len; i++) {
        if (rtti_ptr->idmap[i].id == my_package_IBar_i) {
            return (struct my_package_IBar_vtable const*)rtti_ptr->idmap[i].vtbl_ptr;
        }
    }
    return NULL;
}

// File: example/generated/include/my.package.IBar.abi.2.h
#pragma once
#include "my.package.IBar.abi.1.h"
#include "my.package.Data.abi.1.h"
#include "my.package.Result.abi.1.h"
#include "my.package.IFoo.abi.2.h"
#include "my.package.Data.abi.2.h"
#include "my.package.Result.abi.2.h"
// IBar函数表的完整定义。
struct my_package_IBar_ftable {
    struct my_package_Result_t (*process)(struct my_package_IBar_t tobj, struct my_package_Data_t const* data);
};
// 调用process方法的内联辅助函数。
TH_INLINE struct my_package_Result_t my_package_IBar_process_f(struct my_package_IBar_t tobj, struct my_package_Data_t const* data) {
    return tobj.vtbl_ptr->ftbl_ptr_0->process(tobj, data);
}

// File: example/generated/include/my.package.abi.h
#pragma once
#include "my.package.Data.abi.2.h"
#include "my.package.Result.abi.2.h"
#include "my.package.IFoo.abi.2.h"
#include "my.package.IBar.abi.2.h"
#include "taihe/common.h"
// ABI层的聚合头文件，包含此包中所有类型的ABI定义以及全局函数的声明。
TH_EXPORT struct my_package_Result_t my_package_processWithBar_f(struct my_package_IBar_t bar, struct my_package_Data_t const* data);
```

### `abi-source`

```c
// File: example/generated/src/my.package.abi.c
#include "my.package.IFoo.abi.1.h"
#include "my.package.IBar.abi.1.h"
// ABI层的源文件，为各个接口的IID符号提供实际的定义和存储。
void const* const my_package_IFoo_i = &my_package_IFoo_i;
void const* const my_package_IBar_i = &my_package_IBar_i;
```

### `cpp-common`

```cpp
// File: example/generated/include/my.package.Data.proj.0.hpp
#pragma once
#include "taihe/common.hpp"
#include "my.package.Data.abi.0.h"
namespace my::package {
// C++层Data结构体的前向声明。
struct Data;
}
namespace taihe {
// as_abi模板特化，用于建立C++类型::my::package::Data和其对应的ABI类型my_package_Data_t之间的映射关系。
template<>
struct as_abi<::my::package::Data> {
    using type = struct my_package_Data_t;
};
template<>
struct as_abi<::my::package::Data const&> {
    using type = struct my_package_Data_t const*;
};
template<>
struct as_param<::my::package::Data> {
    using type = ::my::package::Data const&;
};
}

// File: example/generated/include/my.package.Data.proj.1.hpp
#pragma once
#include "my.package.Data.proj.0.hpp"
#include "my.package.Data.abi.1.h"
#include "taihe/string.hpp"
namespace my::package {
// C++层Data结构体的完整定义，提供了更符合C++习惯的类型（例如::taihe::string）。
struct Data {
    int32_t a;
    ::taihe::string b;
};
}
namespace my::package {
// 为C++结构体自动生成operator==。
inline bool operator==(::my::package::Data const& lhs, ::my::package::Data const& rhs) {
    return true && lhs.a == rhs.a && lhs.b == rhs.b;
}
}
// 为C++结构体自动生成std::hash的特化版本。
template<> struct ::std::hash<::my::package::Data> {
    size_t operator()(::my::package::Data const& val) const {
        ::std::size_t seed = 0;
        seed ^= ::std::hash<int32_t>()(val.a) + 0x9e3779b9 + (seed << 6) + (seed >> 2);
        seed ^= ::std::hash<::taihe::string>()(val.b) + 0x9e3779b9 + (seed << 6) + (seed >> 2);
        return seed;
    }
};

// File: example/generated/include/my.package.Data.proj.2.hpp
#pragma once
#include "my.package.Data.proj.1.hpp"
#include "my.package.Data.abi.2.h"

// File: example/generated/include/my.package.Result.proj.0.hpp
#pragma once
#include "taihe/common.hpp"
#include "my.package.Result.abi.0.h"
namespace my::package {
struct Result;
}
namespace taihe {
// as_abi模板特化，建立C++联合体类型和ABI联合体类型之间的映射。
template<>
struct as_abi<::my::package::Result> {
    using type = struct my_package_Result_t;
};
template<>
struct as_abi<::my::package::Result const&> {
    using type = struct my_package_Result_t const*;
};
template<>
struct as_param<::my::package::Result> {
    using type = ::my::package::Result const&;
};
}

// File: example/generated/include/my.package.Result.proj.1.hpp
#pragma once
#include "my.package.Result.proj.0.hpp"
#include "my.package.Result.abi.1.h"
#include "taihe/string.hpp"
namespace my::package {
// C++层Result联合体的定义。
struct Result {
    public:
    // 内部枚举，用于表示当前联合体持有的变体类型。
    enum class tag_t : int {
        ok,
        err,
    };
    // 内部联合体，用于存储各个变体的数据。
    union storage_t {
        storage_t() {}
        ~storage_t() {}
        int32_t ok;
        ::taihe::string err;
    };
    // 实现“五法则”(Rule of Five)，确保在拷贝、移动和析构时对联合体成员进行正确的资源管理。
    Result(Result const& other) : m_tag(other.m_tag) {
        // ...
    }
    Result(Result&& other) : m_tag(other.m_tag) {
        // ...
    }
    Result& operator=(Result const& other) {
        // ...
        return *this;
    }
    Result& operator=(Result&& other) {
        // ...
        return *this;
    }
    ~Result() {
        // ...
    }
    // 提供类型安全的方式来创建、修改、检查和访问联合体的成员。
    template<typename... Args>
    Result(::taihe::static_tag_t<tag_t::ok>, Args&&... args) : m_tag(tag_t::ok) {
        new (&m_data.ok) decltype(m_data.ok)(::std::forward<Args>(args)...);
    }
    template<typename... Args>
    Result(::taihe::static_tag_t<tag_t::err>, Args&&... args) : m_tag(tag_t::err) {
        new (&m_data.err) decltype(m_data.err)(::std::forward<Args>(args)...);
    }
    // ... (make, emplace, get_tag, holds, get_ref, get_ptr)
    
    // 提供访问者模式(Visitor Pattern)相关方法，用于优雅地处理不同的变体。
    template<typename Visitor>
    decltype(auto) match_function(Visitor&& visitor) {
        // ...
    }
    // ... (match, make_ok, make_err, etc.)
    private:
    tag_t m_tag;
    storage_t m_data;
};
}
// ... (operator== and std::hash for Result)

// File: example/generated/include/my.package.Result.proj.2.hpp
#pragma once
#include "my.package.Result.proj.1.hpp"
#include "my.package.Result.abi.2.h"

// File: example/generated/include/my.package.IFoo.proj.0.hpp
#pragma once
#include "taihe/object.hpp"
#include "my.package.IFoo.abi.0.h"
namespace my::package::weak {
// 弱引用版本接口的前向声明。
struct IFoo;
}
namespace my::package {
// 强引用版本接口的前向声明。
struct IFoo;
}
namespace taihe {
// as_abi模板特化，将强弱引用的C++接口类型都映射到同一个ABI类型。
template<>
struct as_abi<::my::package::IFoo> {
    using type = struct my_package_IFoo_t;
};
template<>
struct as_abi<::my::package::weak::IFoo> {
    using type = struct my_package_IFoo_t;
};
template<>
struct as_param<::my::package::IFoo> {
    using type = ::my::package::weak::IFoo;
};
}

// File: example/generated/include/my.package.IFoo.proj.1.hpp
#pragma once
#include "my.package.IFoo.proj.0.hpp"
#include "my.package.IFoo.abi.1.h"
namespace my::package::weak {
// IFoo的弱引用视图(view)，不持有对象所有权，行为类似于std::weak_ptr。
struct IFoo {
    static constexpr bool is_holder = false;
    struct my_package_IFoo_t m_handle;
    explicit IFoo(struct my_package_IFoo_t handle) : m_handle(handle) {}
    // ... (conversion operators to data_view, data_holder)
    // 动态转换构造函数，内部调用ABI层的_dynamic函数。
    explicit IFoo(::taihe::data_view other) : IFoo({
        my_package_IFoo_dynamic(other.data_ptr->rtti_ptr),
        other.data_ptr,
    }) {}
    // 编译期元编程：用于在编译期构建虚表和RTTI信息的模板结构。
    struct virtual_type;
    template<typename Impl>
    struct methods_impl;
    template<typename Impl>
    static const my_package_IFoo_ftable ftbl_impl;
    template<typename Impl>
    static constexpr my_package_IFoo_vtable vtbl_impl = {
        .ftbl_ptr_0 = &::my::package::weak::IFoo::template ftbl_impl<Impl>,
    };
    template<typename Impl>
    static constexpr struct IdMapItem idmap_impl[1] = {
        {&my_package_IFoo_i, &vtbl_impl<Impl>.ftbl_ptr_0},
    };
    // ...
    // 检查接口对象是否有效（例如动态转换失败后，vtbl_ptr为nullptr）。
    bool is_error() const& {
        return m_handle.vtbl_ptr == nullptr;
    }
    // 重载->和*操作符，使其能像普通指针一样调用方法。
    virtual_type const& operator*() const& {
        return *reinterpret_cast<virtual_type const*>(&m_handle);
    }
    virtual_type const* operator->() const& {
        return reinterpret_cast<virtual_type const*>(&m_handle);
    }
};
}
namespace my::package {
// IFoo的强引用持有者(holder)，通过引用计数管理对象生命周期，行为类似于std::shared_ptr。
struct IFoo : public ::my::package::weak::IFoo {
    static constexpr bool is_holder = true;
    explicit IFoo(struct my_package_IFoo_t handle) : ::my::package::weak::IFoo(handle) {}
    IFoo& operator=(::my::package::IFoo other) {
        ::std::swap(this->m_handle, other.m_handle);
        return *this;
    }
    // 析构时会减少对象的引用计数。
    ~IFoo() {
        tobj_drop(this->m_handle.data_ptr);
    }
    // ... (conversion operators)
    // 支持从弱引用、强引用（拷贝/移动）进行构造。
    explicit IFoo(::taihe::data_holder other) : IFoo({
        my_package_IFoo_dynamic(other.data_ptr->rtti_ptr),
        std::exchange(other.data_ptr, nullptr),
    }) {}
    IFoo(::my::package::weak::IFoo const& other) : IFoo({
        other.m_handle.vtbl_ptr,
        tobj_dup(other.m_handle.data_ptr),
    }) {}
    // ... (copy and move constructors)
};
}
// ... (operator== and std::hash for IFoo)

// File: example/generated/include/my.package.IFoo.proj.2.hpp
#pragma once
#include "my.package.IFoo.proj.1.hpp"
#include "my.package.IFoo.abi.2.h"
// 定义C++层的方法(virtual_type)，这些方法是对ABI层调用的一层封装。
struct ::my::package::weak::IFoo::virtual_type {
    void init() const& {
        // 内部调用ABI层的辅助函数my_package_IFoo_init_f，完成到C实现的最终调用。
        return my_package_IFoo_init_f(*reinterpret_cast<my_package_IFoo_t const*>(this));
    }
};
// 静态模板methods_impl，作为从ABI层回调到C++实现类的桥梁。
template<typename Impl>
struct ::my::package::weak::IFoo::methods_impl {
    static void init(struct my_package_IFoo_t tobj) {
        // 它将ABI类型的参数转换为C++类型，然后调用用户实现类(Impl)的方法。
        return ::taihe::cast_data_ptr<Impl>(tobj.data_ptr)->init();
    }
};
template<typename Impl>
constexpr my_package_IFoo_ftable my::package::weak::IFoo::ftbl_impl = {
    .init = &methods_impl<Impl>::init,
};

// File: example/generated/include/my.package.IBar.proj.0.hpp
// ... (similar to IFoo.proj.0.hpp)

// File: example/generated/include/my.package.IBar.proj.1.hpp
#pragma once
#include "my.package.IBar.proj.0.hpp"
#include "my.package.IBar.abi.1.h"
#include "my.package.IFoo.proj.1.hpp"
namespace my::package::weak {
struct IBar {
    // ... (similar to weak::IFoo)
    // 提供了到父接口IFoo的静态转换运算符，内部调用ABI层的_static辅助函数。
    operator ::my::package::weak::IFoo() const& {
        return ::my::package::weak::IFoo({
            my_package_IBar_1_static(this->m_handle.vtbl_ptr),
            this->m_handle.data_ptr,
        });
    }
    operator ::my::package::IFoo() const& {
        return ::my::package::IFoo({
            my_package_IBar_1_static(this->m_handle.vtbl_ptr),
            tobj_dup(this->m_handle.data_ptr),
        });
    }
    // ...
};
}
namespace my::package {
struct IBar : public ::my::package::weak::IBar {
    // ... (similar to strong IFoo, with added conversions to parent IFoo)
};
}
// ... (operator== and std::hash for IBar)

// File: example/generated/include/my.package.IBar.proj.2.hpp
#pragma once
#include "my.package.IBar.proj.1.hpp"
#include "my.package.IBar.abi.2.h"
// 包含IBar依赖的所有类型的完整定义。
#include "my.package.Data.proj.1.hpp"
#include "my.package.Result.proj.1.hpp"
#include "my.package.IFoo.proj.2.hpp"
#include "my.package.Data.proj.2.hpp"
#include "my.package.Result.proj.2.hpp"
// 定义IBar的C++层方法process。
struct ::my::package::weak::IBar::virtual_type {
    ::my::package::Result process(::my::package::Data const& data) const& {
        // 1. 将C++参数data通过into_abi转换为ABI类型。
        // 2. 调用ABI辅助函数my_package_IBar_process_f。
        // 3. 将ABI返回值通过from_abi转换为C++类型Result。
        return ::taihe::from_abi<::my::package::Result>(my_package_IBar_process_f(*reinterpret_cast<my_package_IBar_t const*>(this), ::taihe::into_abi<::my::package::Data const&>(data)));
    }
};
// methods_impl模板，实现从ABI到C++实现类的调用桥接。
template<typename Impl>
struct ::my::package::weak::IBar::methods_impl {
    static struct my_package_Result_t process(struct my_package_IBar_t tobj, struct my_package_Data_t const* data) {
        // 1. 将ABI参数data通过from_abi转换为C++类型。
        // 2. 调用用户实现类Impl的process方法。
        // 3. 将C++返回值通过into_abi转换为ABI类型。
        return ::taihe::into_abi<::my::package::Result>(::taihe::cast_data_ptr<Impl>(tobj.data_ptr)->process(::taihe::from_abi<::my::package::Data const&>(data)));
    }
};
template<typename Impl>
constexpr my_package_IBar_ftable my::package::weak::IBar::ftbl_impl = {
    .process = &methods_impl<Impl>::process,
};

// File: example/generated/include/my.package.proj.hpp
#pragma once
#include "my.package.Data.proj.2.hpp"
#include "my.package.Result.proj.2.hpp"
#include "my.package.IFoo.proj.2.hpp"
#include "my.package.IBar.proj.2.hpp"
// C++层的通用聚合头文件，供接口实现方和消费方共同使用。它包含了包内所有类型的C++投影。
```

### `cpp-user`

```cpp
#pragma once
#include "my.package.proj.hpp"
#include "taihe/common.hpp"
#include "my.package.abi.h"
#include "my.package.IBar.proj.2.hpp"
#include "my.package.Data.proj.2.hpp"
#include "my.package.Result.proj.2.hpp"
// 供接口【消费方】使用的头文件。
namespace my::package {
// 提供了对全局函数processWithBar的C++封装，使其可以像普通C++函数一样被调用。
inline ::my::package::Result processWithBar(::my::package::weak::IBar bar, ::my::package::Data const& data) {
    // 内部实现同样是通过into_abi和from_abi进行类型转换，并调用ABI层的函数。
    return ::taihe::from_abi<::my::package::Result>(my_package_processWithBar_f(::taihe::into_abi<::my::package::weak::IBar>(bar), ::taihe::into_abi<::my::package::Data const&>(data)));
}
}
```

### `cpp-author`

```cpp
// File: example/generated/include/my.package.impl.hpp
#pragma once
#include "taihe/common.hpp"
#include "my.package.abi.h"
#include "my.package.IBar.proj.2.hpp"
#include "my.package.Data.proj.2.hpp"
#include "my.package.Result.proj.2.hpp"
// 供接口【发布方】使用的头文件。
// 定义了TH_EXPORT_CPP_API_processWithBar宏，用于将C++实现的函数导出为ABI层可见的符号。
#define TH_EXPORT_CPP_API_processWithBar(CPP_FUNC_IMPL) \
    struct my_package_Result_t my_package_processWithBar_f(struct my_package_IBar_t bar, struct my_package_Data_t const* data) { \
        return ::taihe::into_abi<::my::package::Result>(CPP_FUNC_IMPL(::taihe::from_abi<::my::package::weak::IBar>(bar), ::taihe::from_abi<::my::package::Data const&>(data))); \
    }
```

### `cpp-author-template`

```cpp
// File: example/generated/temp/my.package.impl.cpp
#include "my.package.proj.hpp"
#include "my.package.impl.hpp"
#include "taihe/runtime.hpp"
#include "stdexcept"

// 这是一个为发布方提供的实现模板骨架文件。
// 它包含了所有需要实现的接口和函数的空/默认实现，帮助开发者快速开始。
namespace {
// IFoo接口的示例实现类。
class IFooImpl {
    public:
    IFooImpl() {
        // Don't forget to implement the constructor.
    }

    // 默认实现会抛出异常，提示开发者需要在此处编写自己的逻辑。
    void init() {
        TH_THROW(std::runtime_error, "init not implemented");
    }
};

// IBar接口的示例实现类。
class IBarImpl {
    public:
    IBarImpl() {
        // Don't forget to implement the constructor.
    }

    ::my::package::Result process(::my::package::Data const& data) {
        TH_THROW(std::runtime_error, "process not implemented");
    }

    // IBar继承了IFoo，所以也需要实现init方法。
    void init() {
        TH_THROW(std::runtime_error, "init not implemented");
    }
};

// 全局函数processWithBar的示例实现。
::my::package::Result processWithBar(::my::package::weak::IBar bar, ::my::package::Data const& data) {
    TH_THROW(std::runtime_error, "processWithBar not implemented");
}
}  // namespace

// Since these macros are auto-generate, lint will cause false positive.
// NOLINTBEGIN
// 使用宏将C++实现的processWithBar函数导出。
TH_EXPORT_CPP_API_processWithBar(processWithBar);
// NOLINTEND
```
