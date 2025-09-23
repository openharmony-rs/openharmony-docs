# AKI到Taihe迁移指南

## 概述

本文档指导开发者将基于鸿蒙AKI（Alpha Kernel Interacting）框架的Node-API Native模块迁移至Taihe ANI模块，实现Native模块升级。

### AKI框架简介

AKI（Alpha Kernel Interacting）是鸿蒙生态中面向边界编程场景的ArkTS FFI开发框架，为Native模块开发提供完整的JavaScript与C/C++跨语言互调解决方案。该框架采用极简语法设计，基于Node-API接口实现，通过一行代码即可完成JS与C++的无障碍互调，实现"所见即所得"的开发体验。

AKI屏蔽了Node-API的对象绑定和参数解析等FFI复杂操作，开发者只需编写纯C++结构和对象即可实现跨语言接口。对于复杂场景，AKI还提供了便捷的Node-API对象转换机制，确保框架的灵活性。

### Taihe框架简介

Taihe（Toolkit for Advanced Interfaces in OpenHarmony Ecosystem）是鸿蒙生态的高性能接口工具集，专注于自动化生成跨语言桥接代码。开发者通过编写Taihe IDL接口描述文件和C++实现代码，工具链自动生成完整的跨语言桥接代码，极大简化API的跨语言支持工作。

本文档提供详细的迁移指导，帮助开发者将基于AKI的FFI接口代码迁移到Taihe平台。未来，Taihe将持续扩展对鸿蒙主流语言的支持，支持Node-API，并为跨平台开发提供统一的接口定义标准。

---

## 第一章 迁移准备

### 1.1 开发环境配置

**AKI环境要求**

AKI作为开发库使用，需将AKI库集成至开发工程中。通过包含aki头文件，即可使用各类AKI方法和宏。

**Taihe环境要求**

Taihe是完整的开发工具链，需要安装鸿蒙NDK。鸿蒙NDK包含Taihec可执行程序，输入 Taihe IDL文件即可生成相应的代码。此外，Taihe工具链提供配套的头文件，开发时只需引入相应的头文件即可。

## 第二章 基础映射关系

### 2.1 模块注册机制改造

**AKI注册机制**
```cpp
#include <aki/jsbind.h>
#include <string>

// 注册AKI插件：插件名对应编译生成的*.so名称
JSBIND_ADDON(hello-world, HelloWorld)
```

**Taihe等效实现**
Taihe为每个IDL文件生成ANIRegister(env)注册函数，需要在自定义cpp文件中调用该入口函数：

```cpp
ANI_EXPORT ani_status ANI_Constructor(ani_vm *vm, uint32_t *result) {
    ani_env *env;
    if (ANI_OK != vm->GetEnv(ANI_VERSION_1, &env)) {
        return ANI_ERROR;
    }
    if (ANI_OK != hello::ANIRegister(env)) {
        std::cerr << "hello模块注册失败！" << std::endl;
        return ANI_ERROR;
    }
    *result = ANI_VERSION_1;
    return ANI_OK;
}
```

通过自定义注册文件，开发者可以灵活决定多个IDL文件合并到一个so库中。此外，Taihe会为每个IDL文件生成对应的ets文件，API消费者可以直接导入并使用。

### 2.2 函数绑定实现

1. 同步函数绑定

**AKI声明机制**
```cpp
#include <aki/jsbind.h>

std::string SayHello(std::string msg) {
    return msg + " too.";
}

JSBIND_GLOBAL() {
    JSBIND_FUNCTION(SayHello);
}

JSBIND_ADDON(hello);
```

在ArkTS侧声明全局函数SayHello。

**Taihe等效实现**

需创建Taihe IDL文件hello.ohidl：
```
function SayHello(msg: string): string;
```

编写配套C++实现：
```cpp
#include "taihe/string.hpp"

taihe::string SayHello(taihe::string_view msg) {
    string result = "";
    // 业务逻辑实现
    return result;
}
TH_EXPORT_CPP_API_SayHello(SayHello);
```

2. 异步函数绑定

假设存在一个异步接口调用，开发者可以发起请求，等待响应结果。
```typescript
import Addon from 'libasync_tasks.so'

Addon.AsyncTaskReturnInt().then(res => {
  console.log('[AKI] AsyncTaskReturnInt: ' + res)
});
```

**AKI声明机制**

通过同步函数自动返回Promise：
```cpp
std::string SayHello(std::string msg) {
    return msg + " too.";
}

// 绑定SayHello函数到上层的SayHello promise函数
JSBIND_GLOBAL() {
    JSBIND_PFUNCTION(SayHello);
}

// 定义一个模块
JSBIND_ADDON(async_tasks);
```

**Taihe等效实现**

只需编写同步函数并添加相应注解：
```
@static_overload("SayHello")
@async function SayHelloWithAsync(msg: string): string;

@static_overload("SayHello")
@promise function SayHelloWithPromise(msg: string): string;
```

C++侧通过宏重新声明：
```cpp
TH_EXPORT_CPP_API_SayHelloWithAsync(SayHelloWithAsync);
TH_EXPORT_CPP_API_SayHelloWithPromise(SayHelloWithPromise);
```

### 2.3 类绑定机制

1. 类方法绑定

**AKI机制**

AKI通过`JSBIND_CLASS`绑定C++类/结构体，支持构造函数、成员函数和成员属性的绑定：

```cpp
class TestObject {
public:
    TestObject();
    explicit TestObject(double) { /* ... */ }

    static double MultiplyObject(double obj1, double obj2) {
        return obj1 * obj2;
    }

    double Multiply(double mult) {
        value_ *= mult;
        return value_;
    }

    ~TestObject() = default;
private:
    double value_;
};

JSBIND_CLASS(TestObject) {
    JSBIND_CONSTRUCTOR<>();
    JSBIND_CONSTRUCTOR<double>();
    JSBIND_METHOD(MultiplyObject);
    JSBIND_METHOD(Multiply);
}
JSBIND_ADDON(hello);
```

**Taihe等效实现**

在Taihe IDL文件中声明类接口：
```
@class
interface TestObject {
    Multiply(mult: double): double;
}

@static("TestObject")
function MultiplyObject(num1: double, num2: double): double;

@ctor("TestObject")
function NewTestObject(): TestObject;

@ctor("TestObject")
function NewTestObject(obj: double): TestObject;
```

在Taihe中，@class声明interface为类（具有构造函数，可在高级语言层实例化）。静态方法和构造函数通过全局function实现，在C++侧投影为无this指针的普通函数，通过@static和@ctor注解指示所属类名。

2. 成员属性绑定

**AKI机制**

- 通过JSBIND_PROPERTY直接绑定C++数据成员：
```cpp
class TestObject {
public:
    explicit TestObject(double) { /* ... */ }
    ~TestObject() = default;
private:
    double value_;
};

JSBIND_CLASS(TestObject) {
    JSBIND_CONSTRUCTOR<double>();
    JSBIND_PROPERTY(value);
}
```

- 通过JSBIND_FIELD绑定getter/setter：
```cpp
class TestObject {
public:
    explicit TestObject(double) { /* ... */ }
    ~TestObject() = default;

    double GetValue() const { return value_; }
    void SetValue(double value) { value_ = value; }

private:
    double value_;
};

JSBIND_CLASS(TestObject) {
    JSBIND_CONSTRUCTOR<double>();
    JSBIND_FIELD("value", GetValue, SetValue);
}
```

**Taihe等效实现**

Taihe对Native侧数据存储的属性统一采用getter/setter方式实现：
```
@class
interface TestObject {
    @get("value") getValue(): double;
    @set("value") setValue(d: double): void;
}
```

C++侧实现对应类方法：
```cpp
class Foo {
    double val__;
public:
    double getValue() { return val__; }
    void setValue(double val) { val__ = val; }
};
```

### 2.4 枚举类型绑定

**AKI机制**

通过JSBIND_ENUM宏导出C++ enum类型：
```cpp
enum TypeFlags {
    NONE,
    NUM,
    STRING,
    BUTT = -1
};

JSBIND_ENUM(TypeFlags) {
    JSBIND_ENUM_VALUE(NONE);
    JSBIND_ENUM_VALUE(NUM);
    JSBIND_ENUM_VALUE(STRING);
}
```

**Taihe等效实现**

在Taihe IDL文件中直接声明枚举类型：
```
enum Weekday: i32 {
    SUNDAY = 0,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
}

function nextEnumWeekday(day: Weekday): Weekday;
function getValueOfEnumWeekday(day: Weekday): i32;
function fromValueToEnumWeekday(str: i32): Weekday;
```

在C++中使用投影类型：
```cpp
::Weekday NextEnumWeekday(::Weekday day) {
    return (::Weekday::key_t)(((int)day.get_key() + 1) % WEEKDAY_COUNT);
}
```

### 2.5 类型系统映射

| **JavaScript类型** | **AKI C++类型** | **Taihe IDL类型** |
|-------------------|-----------------|-------------------|
| Boolean           | bool            | bool              |
| Number            | 各类数值类型      | i8, u8, i16, u16, i32, u32, i64, u64, float, double |
| String            | const char*, std::string | String          |
| Array             | std::vector, std::array | Array<>         |
| Function          | std::function, aki::Callback | 函数        |
| Class Object      | class           | struct, interface  |
| JsonObject        | std::map        | @record Map<k, v> |
| ArrayBuffer,TypedArray | aki::ArrayBuffer | @arraybuffer Array<> |
| Promise           | JSBIND_PFUNCTION, JSBIND_PMETHOD | @async注解      |
| any               | aki::Value, napi_value | Opaque          |

## 第三章 关键特性对比

### 3.1 内存管理机制

**AKI与Taihe对象生命周期对比**：

| **操作类型**     | **AKI实现方案**          | **Taihe等效方案**       |
|------------------|-------------------------|------------------------|
| 对象创建         | `aki::Object::New()`    | `make_holder<>`        |
| 全局引用管理     | 自动引用管理            | 自动垃圾回收机制          |
| 资源释放         | 析构函数自动处理        | GC自动回收              |

### 3.2 异常处理机制

**AKI错误处理模式**：
```cpp
aki::Result result = func();
if (result.IsErr()) {
    AKI_LOG(ERROR) << result.GetMsg();
}
```

**Taihe错误处理模式**：
```cpp
// Taihe提供抛error，businesserror两种类型的运行时接口
// 抛出error异常
taihe::set_error("throw a error");

// 抛出bussiness error
int errorcode = 5;
taihe::set_business_error(errorcode, "error in noReturnBusinessError");

```

### 3.3 线程安全机制

**AKI线程处理模式**

使用AKI的线程安全特性，绑定JavaScript业务函数后，Native可直接调用：

- **线程安全**：使用AKI线程安全绑定的JavaScript函数具有线程安全性，可在非JS线程直接调用，由框架调度至JS线程执行。
- **阻塞式调用**：C++触发JavaScript函数调用为阻塞式，当在非JS线程调用时，框架进行阻塞式跨线程任务调度，C++线程等待JavaScript函数执行完成。

**Taihe线程处理模式**

ANI开发场景中，虚拟机支持进程全局共享，无单线程限制。当前Taihe从C++触发调用ArkTS函数时不进行线程切换，直接在当前线程attach执行函数功能。

---

## 总结与展望

本迁移指南简单展示了从AKI到ANI转换过程中的架构差异和兼容性问题，开发者应重点关注以下方面：

1. **类型系统严格映射**：确保类型转换的准确性和一致性
2. **内存管理模型升级**：适应从自动引用管理到自动垃圾回收机制的转变
3. **线程安全机制重构**：理解新的线程模型和并发处理方式
4. **性能关键路径优化**：针对新框架特性进行性能调优

建议采用渐进式迁移策略，先确保核心功能正确，再逐步优化性能。对于复杂业务模块，引入适配层以实现平滑过渡，降低迁移风险。
