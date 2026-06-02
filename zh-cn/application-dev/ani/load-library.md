# `loadLibrary`的使用
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

ArkTS侧通过`loadLibrary`加载native库后，运行时会进入native库的`ANI_Constructor`，由它完成函数或方法绑定。这个流程用于把ArkTS声明的`native function`/`native method`连接到C++实现。

## Native绑定

**什么是Native方法？**

在ArkTS-Sta的开发中`native function/method`是连接应用层业务逻辑与系统底层能力的桥梁。
```ts
native function add(a: int, b: int): int;
class calc {
    native sub(a: int, b: int): int;
}
```
> Native function：定义在ArkTS的模块（Module）顶层或命名空间（Namespace）内，但具体实现在C/C++代码中完成的函数。
>
> Native method：定义在ArkTS类（Class）内部， 但具体实现在C/C++中完成的方法。

**为什么要使用它们？**
1. 极致性能：对于图像处理、复杂数学运算、物理引擎等计算密集型任务，C++的执行效率远高于脚本语言。
2. 复用既有库：可以直接调用已有的C/C++三方库（如OpenCV、FFmpeg等），无需用ArkTS重写。
3. 访问系统底层：某些底层硬件接口或操作系统特定的API只能通过C/C++访问。

**它们是如何工作的？**
1. 声明：在ArkTS中通过native关键字告诉编译器：“这个函数我先写在这，但它的代码在别处。”
2. 加载：通过loadLibrary加载编译好的.so动态链接库。
3. 绑定（Binding）：这是最关键的一步，程序运行期间需要将ArkTS的函数名与C++中的函数指针进行一一对应。ANI提供的`Bind`系列API执行这种“映射”操作。
4. 执行：当在ArkTS中调用该函数时，虚拟机（VM）会暂停当前的脚本执行，跳转到对应的C++代码中运行，完成后再带回结果。

**绑定native函数的过程涉及几个关键步骤：**
1. 在`.ets`文件中声明native函数和方法。
2. 在托管代码中调用`loadLibrary("libraryName")`：
    - 可以在静态块或任何别的入口点（例如`main`函数）中完成，确保native library在调用任何native函数之前被加载，并将所有`native function/method`绑定到其实现。
    - `libraryName`是原生库的名称，例如对于库`libexample.z.so`，名称为`example.z`。
3. 在native library中实现入口函数`ani_status ANI_Constructor(ani_vm* vm, uint32_t* result)`。
    - 函数必须以默认可见性声明（即`__attribute__((visibility("default")))`）。
    - 当通过`loadLibrary`加载native library时，会自动调用此函数。
4. 在`ANI_Constructor`中，根据绑定位置使用以下ANI API：`Class_BindStaticNativeMethods`、`Class_BindNativeMethods`、`Namespace_BindNativeFunctions`或`Module_BindNativeFunctions`将ArkTS侧定义的`native function/method`与C++定义实现绑定。参考[类方法的绑定](#绑定类中的方法)。
5. 在native函数定义中，根据函数作用域提供正确的额外参数：

    | 绑定位置 | 绑定函数 | 必需参数 | 描述 |
    | ----------- | ------------------------------- | ----------------------- | ------------------- |
    | 类（非静态） | `Class_BindNativeMethods`       | `ani_env`, `ani_object` | 对类的实例进行操作。 |
    | 类（静态）   | `Class_BindStaticNativeMethods` | `ani_env`, `ani_class` | 对类本身进行操作。   |
    | 命名空间    | `Namespace_BindNativeFunctions`  | `ani_env`              | 无需对象引用。       |
    | 模块        | `Module_BindNativeFunctions`    | `ani_env`               | 无需对象引用。       |

    > **注意：**
    >
    > C++中的native函数签名必须将这些参数作为前导参数：

    ```cpp
    // 实例方法绑定
    void nativeInstanceMethod(ani_env* env, ani_object obj, ...);
    // 静态方法绑定
    void nativeStaticMethod(ani_env* env, ani_class cls, ...);
    // 命名空间或模块绑定
    void nativeNamespaceFunction(ani_env* env, ...);
    ```
**重要注意事项：**
- 传递给native函数的参数的生命周期与native函数绑定。**不要**在参数作用域之外存储native函数参数，底层内存将被释放。请参阅[生命周期管理](ani-lifecycle-management.md)。
- `ani_env`: 通过native函数接收的参数，仅在当前native调用中有效。**不要**在native函数调用作用域之外存储`ani_env`或者传递给新线程使用。
- native函数不能在`interface`块内声明。

---
### 类名、标识符和符号查找
使用`ark_disasm`工具检查`.abc`文件，以确定类名和符号名。请参考[反汇编ABC文件](#反汇编abc文件)获取`ark_disasm`工具。

反汇编结果示例：

```ts
.record example.Foo <ets.extends=std.core.Object, access.record=public>
```
在签名中对应的类名是`C{example.Foo}`，用于`FindClass`的类名是`example.Foo`。

---
### 绑定类中的方法

下面的代码展示如何将ArkTS中声明的native method与对应的C++实现绑定。为了保证在使用`Class_BindNativeMethods`的时候有正确的函数签名，可以先对ABC文件进行反汇编。

**ArkTS代码**：
```ts
class PasteData {
    static { loadLibrary("libraryName") }
    native getRecordCount(a: int): int;
    static native getRecordCount(a: int): int;
}
```
**反汇编的ABC代码**：
```ts
.function i32 example.PasteData.getRecordCount(example.PasteData a0, i32 a1) <native, access.function=public>
.function i32 example.PasteData.getRecordCount(example.PasteData a0, i32 a1) <native, static, access.function=public>
```

**C++实现**：
```cpp
static ani_int getRecordCount(ani_env* env, ani_object object, ani_int a);
static ani_int getRecordCountStatic(ani_env* env, ani_class object, ani_int a);
```

**绑定代码**：
```cpp
// 实例方法绑定
std::array methods = {
    ani_native_function {
        "getRecordCount",
        "i:i",
        reinterpret_cast<void*>(getRecordCount)
    },
};
env->Class_BindNativeMethods(cls, methods.data(), methods.size());

// 静态方法绑定
std::array staticMethods = {
    ani_native_function {
        "getRecordCount",
        "i:i",
        reinterpret_cast<void*>(getRecordCountStatic)
    },
};
env->Class_BindStaticNativeMethods(cls, staticMethods.data(), staticMethods.size());
```

> 使用`reinterpret_cast<void*>`消除C++函数的类型。
---

### 绑定命名空间中的函数
**ArkTS代码**：
```ts
namespace PasteData {
    loadLibrary("libraryName")
    native function getRecordCount(a: int): int;
}
```
**反汇编的ABC代码**：
```ts
.function i32 example.PasteData.getRecordCount(i32 a0) <native, static, access.function=public>
```
**C++实现**：
```cpp
static ani_int getRecordCount(ani_env* env, ani_int a);
```
**绑定代码**：
```cpp
std::array functions = {
    ani_native_function {
        "getRecordCount",
        "i:i",
        reinterpret_cast<void*>(getRecordCount)
    },
};
env->Namespace_BindNativeFunctions(ns, functions.data(), functions.size());
```
> **重要提示**：namespace和modules中声明的native function，对应的C++实现只需要一个额外的`ani_env*`, 不要添加额外的`ani_object`或者`ani_class`。

---
### 绑定模块中的函数
**ArkTS代码**：
```ts
loadLibrary("libraryName")

enum COLORINT { REDINT = 5 }
native function processEnumInt(color: COLORINT): void;
```
**反汇编的ABC代码**：
```ts
.function void example.ETSGLOBAL.processEnumInt(example.COLORINT a0) <native, static, access.function=public>
```

**C++实现**：
```cpp
static void processEnumInt(ani_env* env, ani_enum_item enumItem);
```

**绑定代码**：
```cpp
ani_module module;
env->FindModule("example", &module);

std::array functions = {
    ani_native_function {
        "processEnumInt",
        "E{example.COLORINT}:",
        reinterpret_cast<void*>(processEnumInt)
    },
};
env->Module_BindNativeFunctions(module, functions.data(), functions.size());
```

> **重要提示**：通过`FindModule`只能找到对应的module，必须使用`Module_BindNativeFunctions`绑定模块函数。

---

### 函数绑定中的特殊场景

- **重载函数**：如果存在重载的native函数，必须显式绑定每个变体：

    ```ts
    native function foo(): void;
    native function foo(arg: string): void;
    ```

    这需要绑定两个函数：
    ```cpp
    std::array functions = {
        ani_native_function {
            "foo",
            ":",
            reinterpret_cast<void*>(foo)
        },
        ani_native_function {
            "foo",
            "C{std.core.String}:",
            reinterpret_cast<void*>(fooString)
        },
    };
    ```
- 可选参数**不会**创建重载。

    ```ts
    function foo(a: int, b: int = 3): void
    ```

    在字节码中仅包含一个函数

    ```ts
    .function void example.foo(i32 a0, std.core.Int a1)
    ```

---
### 反汇编ABC文件
要反汇编`.abc`文件，请使用`ark_disasm`二进制文件，它在以下仓库的常规项目构建过程中生成：
- [`arkcompiler_runtime_core`](https://gitcode.com/openharmony/arkcompiler_runtime_core)

- [`arkcompiler_ets_frontend`](https://gitcode.com/openharmony/arkcompiler_ets_frontend)

**反汇编工具构建说明**：[遵循本指南](https://gitcode.com/openharmony/arkcompiler_runtime_core/blob/master/README_zh.md)

**用法**：

```bash
./out/bin/ark_disasm yourabcfile.abc dumpfile.txt
```

> 如果反汇编失败，请检查工具和编译器之间的版本是否匹配。

## 类加载失败诊断

`FindClass`失败时可能会返回错误码`ANI_PENDING_ERROR`，意味着在加载对应class的时候抛出了error。这种情况通常是由于使用了损坏的或不兼容的ABC文件所导致：
* 使用了旧版本的ABC文件与较新的etsstdlib.abc不兼容。
* 运行时新版本包含了不兼容的改动，需要重新编译托管代码。

通常会抛出`LinkerUnresolvedClassError`异常，在托管代码的堆栈跟踪中可见：
```ts
at std.core.LinkerUnresolvedClassError.<ctor> (<unknown>:36)
```

类加载过程中可能抛出的全部错误，可以参考：

[RuntimeLinkerErrors.ets](https://gitcode.com/openharmony/arkcompiler_runtime_core/blob/master/static_core/plugins/ets/stdlib/std/core/RuntimeLinkerErrors.ets).


---
### `loadLibrary`用法

ArkTS 1.2使用模块和类的延迟初始化。在实践中，这意味着静态块和top级语句仅在第一次访问作为类或模块一部分定义的实体之前执行。考虑以下示例：

```ts
loadLibrary("libraryName")
// 模块中唯一导出的实体
export function foo(): void {
    fooImpl(12)
}
native function fooImpl(arg: int): void
```
这里`loadLibrary`作为top级语句添加，因此它将在第一次调用`foo`或`fooImpl`之前执行。

### 设备缺少ABC加载

1. 检查程序的进程，以确定在执行期间是否加载了ABC模块。如果没有，请继续检查所需的ABC模块：

   ```bash
   cat /proc/pid/maps | grep abc
   ```

2. 检查所需的ABC模块是否存在于`/system/framework`路径下。

3. 检查所需的ABC模块加载路径是否存在于`/system/framework/bootpath.json`中。如果不存在，请添加路径：

   ```bash
   hdc file recv /system/framework/bootpath.json ./
   hdc file send bootpath.json /system/framework/bootpath.json
   ```

   > **注意：**<br>
   > 修改此文件需要重启设备！

4. 如果`bootpath.json`缺少ABC模块加载路径，可能是由于模块打包期间缺少配置。在`generate_abc`下的`build.gn`中添加`is_boot_abc="True"`。

----

