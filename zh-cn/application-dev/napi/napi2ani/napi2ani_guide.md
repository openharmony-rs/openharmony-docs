# Node-API到ANI迁移指南

## 背景知识
在之前的章节中，我们已经初步了解了Node-API（Node-API）与ANI的基本概念和设计理念的差别，并体验了如何将一个简单的Node-API模块迁移成ANI（ArkTS Native Interface）模块。

本文接下来将详细介绍如何将Node-API功能迁移到ANI功能，帮助开发者快速完成迁移。

## 详细迁移指导
### 声明文件迁移
在 ArkTS 中，您通常会有一个.d.ts（声明文件）来描述Node-API模块的接口。这个文件本身也是其他ets文件使用这个Node-API模块接口的类型声明文件，是您编写ANI类声明的参考。此文件还提供了其他ets文件使用这个Node-API模块接口的类型声明。开发者可以参考它编写ANI类声明。
如下是一个典型的.d.ts（声明文件）包含的内容
```typescript
export interface BundlePackInfo {
    readonly packages: Array<PackageConfig>;
    readonly summary: PackageSummary;
}
```
ArkTS-Dyn与ArkTS-Sta都支持声明文件，语法上有些不一样，具体请参考[ArkTS语法迁移规则](../../quick-start/arkts-dyn-to-sta-syntax-rules.md)；如果不涉及上面的语法差别，可以直接复用ArkTS-Dyn的声明文件；涉及语法差异时，需要进行小部分调整；如将number改成int等基础类型变更。

### 模块注册
**ArkTS-Dyn Node-API模块注册流程**

在ArkTS-Dyn中，通过`import`语句加载Node-API模块时，系统会按照标准化流程完成模块初始化。

1. 动态库加载阶段
运行时环境自动调用 `dlopen` 加载与模块名称对应的so文件。

2. 构造函数触发阶段
动态库加载时，系统会自动执行库中声明的构造函数。

3. 模块注册完成阶段
在构造函数中完成模块注册，即可建立ArkTS-Dyn与 native代码的绑定关系。

典型代码实现
```cpp
// 模块导出函数声明
static napi_value ExampleMethod(napi_env env, napi_callback_info info) {
    // 方法实现
}

// 模块描述结构体
static napi_module exampleModule = {
    .nm_version = 1,
    .nm_flags = 0,
    .nm_filename = nullptr,
    .nm_register_func = [](napi_env env, napi_value exports) {
        napi_property_descriptor desc[] = {
            {"exampleMethod", nullptr, ExampleMethod, nullptr, nullptr, nullptr, napi_default, nullptr}
        };
        napi_define_properties(env, exports, sizeof(desc)/sizeof(desc[0]), desc);
        return exports;
    },
    .nm_modname = "example",
    .nm_priv = nullptr,
};

// 自动注册函数
__attribute__((constructor)) static void RegisterModule() {
    napi_module_register(&exampleModule);
}
```

关键技术说明
* 自动注册特性
使用 __attribute__((constructor)) 修饰的注册函数会在so加载时自动执行，无需显式调用注册逻辑。

* 模块描述规范
napi_module 结构体定义了模块元信息，nm_register_func 是核心回调函数，负责导出 native 方法。

**ArkTS-Sta ANI注册流程**

在ArkTS-Sta环境中，优化了模块注册机制，采用显式加载方式：

1. 动态库显式加载
在ets类中使用`System.loadLibrary()`加载so库：

```typescript
// 在静态初始化块中加载
static {
    System.loadLibrary("example.z");
}
```
在静态块、构造函数或main函数等入口点调用，确保在调用任何native方法前完成加载。
注意：库名规则，对于libexample.z.so，只需指定example.z。

2. so库入口实现
在so库中实现ANI标准入口函数，以确保模块初始化和native函数的绑定。
```c
__attribute__((visibility("default")))
ani_status ANI_Constructor(ani_vm* vm, uint32_t* result) {
    // 模块初始化逻辑
    // 绑定native函数，

    *result = 0; // 返回初始化状态
    return ANI_OK;
}
```
使用 `__attribute__((visibility("default")))` 声明 `ANI_Constructor` 函数。上层通过 `loadLibrary` 加载时会自动调用此函数。

3. 方法绑定
在 ANI_Constructor 中，使用以下 API 进行方法绑定：
  * Class_BindNativeMethods绑定类方法
  * Namespace_BindNativeFunctions绑定命名空间函数
  * Module_BindNativeFunctions绑定模块级函数
### 复杂类型定义
在完成模块定义以后，接下来需要完成声明文件中定义的各种复杂类型，复杂类型指的是你通过interface，class等自己定义的类型。

- Node-API类型系统特点：
  - 统一类型模型：Node-API使用统一的napi_value作为ArkTS-Dyn与Native代码之间传递数据的通用载体。
  - 动态类型特性：保留了JavaScript的动态类型机制，类型检查在运行时进行，并支持在运行过程中动态创建类型。

ANI类型系统特点：
  - 静态类型映射：ANI类型与C/C++类型之间存在更加明确的映射关系，例如对象统一使用ani_object表示，arraybuffer对应的ani_arraybuffer 。
  - 显式类型声明：不支持动态创建类型，所有自定义类型必须在ets文件中进行明确定义。

因此，在Node-API与ANI中声明interface和class类型时，其实现方式与上述机制有显著差异。

**Node-API类型定义代码示例**

在 Node-API 中，通常通过在 C++ 代码中调用 Node-API 接口来创建类或对象，常见的创建接口和类对象的方法包括：
1. 使用 `napi_create_object` 创建对象，然后通过设置属性来构建接口对象或类实例。
```cpp
// NAPI_CALL_RETURN_VOID是定义的一个用来检查返回值的宏
napi_value nWindow;
// 先创建一个对象
NAPI_CALL_RETURN_VOID(env, napi_create_object(env, &nWindow));

// 设置window这个对象的一个名字叫"designWidth"的属性
napi_value nDesignWidth;
NAPI_CALL_RETURN_VOID(env, napi_create_uint32(env, 12, &nDesignWidth));
NAPI_CALL_RETURN_VOID(env, napi_set_named_property(env, nWindow, "designWidth", nDesignWidth));
napi_value nAutoDesignWidth;
NAPI_CALL_RETURN_VOID(env, napi_get_boolean(env, TRUE, &nAutoDesignWidth));
NAPI_CALL_RETURN_VOID(env, napi_set_named_property(env, nWindow, "autoDesignWidth", nAutoDesignWidth));
```
2. 使用 `napi_define_class` 定义类，然后通过 `napi_new_instance` 创建该类的实例对象。
```cpp
napi_property_descriptor properties[] = {
    {"value", 0, 0, GetValue, SetValue, 0, napi_default, 0},
    {"plusOne", nullptr, PlusOne, nullptr, nullptr, nullptr, napi_default, nullptr}
};

napi_value cons;
napi_define_class(env, "MyObject", NAPI_AUTO_LENGTH, New, nullptr, 2, properties, &cons);

// ...
napi_value nWindow;
napi_new_instance(env, constructor, 0, nullptr, &napi_value nWindow);
```
**ANI类型定义代码示例**

在ANI中，接口类型必须在ets文件中声明，无法直接通过ANI接口定义。因此，迁移至ArkTS-Sta时，需将原有桥接层拆分为ets和C++两部分实现，具体步骤如下：
1. 首先，新建一个ets文件，声明接口、类等类型。例如，可以先定义 `windows.ets` 文件，在其中编写相应的类型声明。
```cpp
// 定义window类型，对应上面定义的第一个类
class window {
    designWidth: number; // 在ArkTS-Dyn中类型number在ArkTS-Sta中可能是int，long，double等各种数据类型
    autoDesignWidth: boolean;
}
// 定义MyObject类中，napi侧定义了两个方法，在ArkTS-Sta中定义的方法也需要用native标记，表明这两个方法在C++侧定义
class MyObject {
    native get value: number; // 声明一个在native侧实现的get/set
    native plugOne(a: number): number; // 声明这是一个在native侧实现的方法，采用number类型保持与ArkTS-Dyn一致
}
```
在ArkTS-Sta中，Native库的加载机制有所变化：`import`语句仅用于声明需要导入的类，实际加载的SO库需通过显式调用`System.loadLibrary`来加载。上面的代码修改如下：
```cpp
// 定义window类型，对应上面定义的第一个类
class window {
    designWidth: number; // 在ArkTS-Dyn中类型number在ArkTS-Sta中可能是int，long，double等各种数据类型
    autoDesignWidth: boolean;
}
// 定义MyObject类中，napi侧定义了两个方法，在ArkTS-Sta中定义的方法也需要用native标记，表明这两个方法在C++侧定义
class MyObject {
    static {
        System.loadLibrary("myobject"); // 使用静态语句块static {}，可以使得动态库加载在类加载的最初阶段完成
    }
    native get value: number; // 声明一个在native侧实现的get/set属性
    native plugOne(a: number): number; // 声明这是一个在native侧实现的方法，采用number类型保持与ArkTS-Dyn一致
}
```

2. 在ets中声明后，还需要在C++侧的ANI_Constructor中调用ANI接口，完成方法的显式绑定。
```cpp
static ani_int nativePlugOne(ani_env* env, ani_int a) {
    return a + 1; // 示例实现
}

ani_status ANI_Constructor(ani_vm* vm, uint32_t* result) {
    ani_env* env = vm->GetEnv(); // 需要获取 env
    ani_class cls{};

    env->FindClass("C{MyObject}", &cls);

    std::array<ani_native_function, 1> methods = {{
        {"plugOne", "d:d", reinterpret_cast<void*>(nativePlugOne)}
    }};

    // 绑定nativePlugOne函数到MyObject的plugOne方法上
    env->Class_BindNativeMethods(cls, methods.data(), methods.size());

    return ANI_OK; // 需要返回状态
}
```

## 参考链接
1. [ArkTS-Sta用户指导](../../quick-start/arkts-sta-user-guide.md)
2. [ArkTS-Sta语法迁移规则](../../quick-start/arkts-dyn-to-sta-syntax-rules.md)
3. [ArkTS-Sta并发迁移规则](../../quick-start/arkts-dyn-to-sta-concurrency-rules.md)
4. [ArkTS-Sta EAWorker迁移指导](../../quick-start/arkts-dyn-to-sta-worker-migration-guide.md)
5. [ArkTS-Sta builtin迁移规则](../../quick-start/arkts-dyn-to-sta-builtin-rules.md)
6. [ArkTS-Sta SDK迁移规则](../../quick-start/arkts-dyn-to-sta-sdk-rules.md)
7. [ArkTS-Sta与ArkTS-Dyn互操作迁移规则](../../quick-start/arkts-dyn-to-sta-interop-rules.md)
