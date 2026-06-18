# 生命周期管理
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

ANI引用、`ani_env`和VM相关资源都有明确的生命周期边界。native侧保存ArkTS对象、从系统回调线程调用ANI，或在长期运行线程中循环创建对象时，最容易遇到局部引用泄漏、跨线程误用和悬空指针。

## References生命周期

所有在C++ native侧创建的对象都是局部引用（_local references_）。这意味着：
- 它们的生命周期仅在当前调用上下文中有效；
- 一旦退出当前native调用，它们可能会被垃圾回收器回收；
- 即使你将这些引用存储到全局C++对象中，也不能保证其在下次使用时仍然有效。
**以下示例展示了将局部引用（_local reference_）错误地保存到全局变量中可能导致的问题：**

```cpp
ani_object g_obj;
void NativeFuncImpl(ani_env* env, ani_object param) {
    ani_object newObj {};
    if (env->Object_New(cls, ctor, &newObj) != ANI_OK) {
        std::cerr << "Failed to create object" << std::endl;
        return;
    }
    g_obj = newObj; // Local reference leakage, will cause UB
}
```
如果你需要创建在多次native函数调用之间持久存在的全局引用，可以使用`GlobalReference_Create`将局部引用提升为全局引用：

```cpp
ani_ref g_obj;
void OnEnterImpl(ani_env *env, ani_object param) {
    ani_object newObj {};
    if (env->Object_New(cls, ctor, &newObj) != ANI_OK) {
        std::cerr << "Failed to create object" << std::endl;
        return;
    }
    if (env->GlobalReference_Create(newObj, &g_obj) != ANI_OK) {
        std::cerr << "Failed to create global reference" << std::endl;
    }
}
void OnExitImpl(ani_env *env) {
    env->GlobalReference_Delete(g_obj);
}
```

> **注意：**
>
> - `GlobalReference_Create`返回的`ani_ref`被认为与原先的object相同。
> - 当`global reference`不再被使用时，必须使用`GlobalReference_Delete`删除。避免内存耗尽。

## Native线程回调中的引用管理

在纯native线程（非Virtual Machine（VM）调用的线程，例如定时器、传感器回调、网络线程）中触发回调时，没有VM自动管理的栈帧（Stack Frame）。

这意味着：
+ 没有自动回收：在该线程中创建的任何局部引用（Local Reference），在函数返回后不会自动释放。
+ 引用表溢出风险：如果不手动释放，这些引用会一直累积，直到线程销毁或达到引用表上限（导致Crash）。

**以下常见操作会产生局部引用：**
+ 创建新对象（`Object_New`）
+ 创建字符串（`String_NewUTF8`）
+ 创建数组（`Array_New`）
+ 获取类对象（`FindClass`）
+ ...

**错误示范：**

以下代码模拟了一个传感器数据回调。虽然逻辑看似简单，但由于未释放ani_object data，每次回调都会泄漏一个引用，运行一段时间后必然崩溃。

```cpp
// 假设这是一个通过pthread或std::thread运行的后台工作函数
void BackgroundWorkerThread(ani_vm* vm) {
    // 1. 线程挂载：Env的生命周期从此开始
    ani_env *env {nullptr};
    ani_option interopEnabled {"--interop=disable", nullptr};
    ani_options aniArgs {1, &interopEnabled};
    auto status = vm->AttachCurrentThread(&aniArgs, ANI_VERSION_1, &env);
    if (status != ANI_OK) return;

    // 模拟一个长期的任务循环（例如：监听网络、传感器、渲染循环）
    while (g_isRunning) {
        // 危险操作：在此函数内新建了对象，但以为函数返回就会自动释放
        // 实际上，因为线程没有Detach，这些对象一直堆积在env的引用表中
        HandleOneDataPacket(env); 
        std::this_thread::sleep_for(std::chrono::milliseconds(100));
    }
    
    // 2. 线程卸载：只有到了这里，引用才会被释放
    vm->DetachCurrentThread();
}

// 具体的处理函数
void HandleOneDataPacket(ani_env* env) {
    // 创建一个新的局部引用 (Object_New)
    ani_object data;
    if (env->Object_New(cls, ctor, &data) != ANI_OK) return;

    // 回调ArkTS层
    env->Object_CallMethod_Void(callback, method, data);

    // 【错误】：没有手动Delete。
    // 当前场景为native->native回调没有手动Delete是错误的，而在ArkTS->native场景下，这里不需要delete。
    // 但在BackgroundWorkerThread中，这个data对象会一直存活！
}
```
**正确示范：** 

使用LocalScope管理作用域。为了避免手动管理每个对象的麻烦，并确保安全，推荐在循环体内部或处理函数的入口/出口使用CreateLocalScope和DestroyLocalScope。

```cpp
void BackgroundWorkerThread(ani_vm* vm) {
    ani_env *env {nullptr};
    ani_option interopEnabled {"--interop=disable", nullptr};
    ani_options aniArgs {1, &interopEnabled};
    auto status = vm->AttachCurrentThread(&aniArgs, ANI_VERSION_1, &env);
    if (status != ANI_OK) return;

    while (g_isRunning) {
        // 最佳实践：在循环的每一次迭代中建立独立的引用作用域
        // 这样可以确保每次循环结束，产生的所有引用（无论多少）都会被清空
        env->CreateLocalScope(16); 

        // 执行具体的业务逻辑（里面可能创建了object, string, array等）
        HandleOneDataPacket(env);

        // 弹栈：一次性销毁本次循环中创建的所有局部引用
        env->DestroyLocalScope();
        
        std::this_thread::sleep_for(std::chrono::milliseconds(100));
    }
    
    vm->DetachCurrentThread();
}
```

## VM 和 env 生命周期
- `ani_vm`在应用启动时创建，其生命周期与应用相同。
- 每个`ani_env`与协程一一对应。在native函数调用期间，可以保证`ani_env`是有效的。

**`ani_env`只能在其创建的线程中使用。**
当协程结束时，`ani_env`会被销毁，成为悬空指针。

**解决方案：** 使用`AttachCurrentThread`

从`env`获取`vm`：
```cpp
ani_vm *vm = nullptr;
env->GetVM(&vm);
```

在另一个线程中：
1. `AttachCurrentThread`（使用后必须分离）：

   ```cpp
   ani_env *env = nullptr;
   ani_options aniArgs {0, nullptr};
   auto status = vm->AttachCurrentThread(&aniArgs, ANI_VERSION_1, &env);
   // env可正常使用，用于native调用ArkTS对象
   ```

2. 若线程已附加到VM，则使用`GetEnv`：

   ```cpp
   ani_env *env;
   auto status = vm->GetEnv(ANI_VERSION_1, &env);
   ```

3. 线程结束时主动分离：

   ```cpp
   vm->DetachCurrentThread();
   ```

> **注意：**
>
> 1. 只有通过`AttachCurrentThread`绑定的线程才可以调用`DetachCurrentThread`。
> 2. 使用`AttachCurrentThread`绑定的线程通常没有稳定的ArkTS类加载上下文，因此不建议在该线程中直接调用`FindClass`、`FindModule`、`FindNamespace`、`FindEnum`等依赖上下文查找的接口。ArkTS运行时会优先根据当前ArkTS栈帧所属类的类加载上下文执行查找，而通过`AttachCurrentThread`附加的native线程通常没有ArkTS栈帧，因此往往缺少应用代码对应的类加载上下文。
>    
>    ArkTS运行时中的类加载上下文主要包括以下两类：
>    - `boot context`：对应boot panda files中的类型，主要包括系统启动阶段已加载的ETS标准库和运行时基础类型，例如`std.core.String`、`std.core.Object`等。对于子线程，这部分内容通常可见，因此查找系统库类型通常可以成功。
>    - 应用侧`ClassLinkerContext`：用于加载HAP/ABC中的应用自定义代码，例如业务类、模块、命名空间和枚举。native线程仅通过`AttachCurrentThread`附加时，由于没有ArkTS调用栈，通常无法自动定位到这部分上下文，因此查找应用自定义类、枚举、模块或命名空间时通常会失败。
>
>    如果子线程需要使用这些对象，建议在已有ArkTS调用栈的线程中先完成查找，并通过`GlobalReference`将所需的`class`、`module`、`namespace`、`enum`或实例对象传递给子线程复用，而不是在子线程中重新执行上下文相关查找。

### ani_options参数

`ANI_CreateVM`和`AttachCurrentThread`的入参`ani_options`本质上是一个`ani_option { option, extra }`数组：

- `option`用来填写参数本身，例如`--verify:ani`，或者`--ext:log-level=info`等。
- `extra`用来给少数特殊参数补充额外数据；如果该参数不需要额外数据，就传`nullptr`。

**`ANI_CreateVM`参数**

对`ANI_CreateVM`而言，`ani_options`是VM初始化的统一配置入口。

`ANI_CreateVM`可直接识别的参数如下：

| 参数 | `extra` | 含义 |
| --------------- | ------------------------------------- | --------------- |
| `--logger`      | 必须为日志回调函数地址，不能为`nullptr` | 注册ANI日志回调 |
| `--verify:ani`  | `nullptr` | 开启ANI verify模式。发现开发者误用ANI API时，按verify规则做校验和上报；并且走`FATAL`级别报错直接终止当前调用。 |
| `--verify:ani:workround:`<br>`no_crash_if_invalid_usage` | `nullptr` | 开启ANI verify模式。开发者误用ANI API时，如果release实现中有对应错误码则按`ERROR`级别上报；不直接`FATAL`，而是继续走底层release实现。 |
| `--ext:interop` | `extra`可为外部`napi_env`，也可为`nullptr` | 创建VM时初始化interop上下文 |

如果使用`--logger`，需要先定义一个日志回调函数，再把该函数地址通过`extra`传入。例如：

```cpp
void MyLogger(FILE *stream, int logLevel, const char *component, const char *message)
{
    fprintf(stream, "[%s] level=%d %s\n", component, logLevel, message);
}
```

```cpp
ani_option loggerOpt {"--logger", reinterpret_cast<void *>(MyLogger)};
```

除了上表这些特殊参数，`ANI_CreateVM`还可以传其他`--ext:*`扩展参数。它们会在去掉`--ext:`前缀后，继续交给logger / runtime / compiler选项解析器处理。常见示例：

- `--ext:boot-panda-files=/path/to/etsstdlib.abc`：指定VM启动时加载的boot panda files，例如ETS标准库abc文件。
- `--ext:gc-type=g1-gc`：指定垃圾回收器类型。

使用示例：

```cpp
std::array vmOptions {
    ani_option {"--ext:boot-panda-files=/path/to/etsstdlib.abc", nullptr},
    ani_option {"--verify:ani", nullptr},
    ani_option {"--ext:log-level=info", nullptr},
};

ani_options createVmArgs {vmOptions.size(), vmOptions.data()};
ani_vm *vm = nullptr;
ani_status status = ANI_CreateVM(&createVmArgs, ANI_VERSION_1, &vm);
```

**`AttachCurrentThread`参数**

对`AttachCurrentThread`而言，`ani_options`用于描述当前线程如何附加到VM。

当前只支持以下线程附加参数决定是否启用interop：

| 参数 | `extra` | 含义 |
| ------------------- | ---------------------------------- | ------------------------ |
| `--interop=enable`  | 可为外部`napi_env`，也可为`nullptr` | 为当前附加线程启用interop |
| `--interop=disable` | 通常为`nullptr`                    | 显式关闭interop           |

使用示例：

```cpp
ani_env *env {nullptr};
ani_option interopEnabled {"--interop=enable", nullptr};
ani_options aniArgs {1, &interopEnabled};
auto status = vm->AttachCurrentThread(&aniArgs, ANI_VERSION_1, &env);
// env可用于JS ↔ ArkTS互操作的线程
```

如果调用方已经提前创建了外部JS Env，也可以通过`extra`传入：

```cpp
ani_env *env {nullptr};
void *externalJsEnv = GetExternalJsEnv();
ani_option interopEnabled {"--interop=enable", externalJsEnv};
ani_options aniArgs {1, &interopEnabled};
auto status = vm->AttachCurrentThread(&aniArgs, ANI_VERSION_1, &env);
```

- 普通native线程调用`AttachCurrentThread`时`ani_options`通常直接传`nullptr`即可，默认不启用interop。

> **注意：**
>
> 1. `ANI_CreateVM`的初始化选项，不应直接复用到`AttachCurrentThread`。不建议向`AttachCurrentThread`传`--logger`、`--verify:ani`、`--ext:interop`或其他`--ext:*`选项。
> 2. `ANI_CreateVM`中启用interop初始化使用的是`--ext:interop`，而`AttachCurrentThread`中使用的是`--interop=enable` / `--interop=disable`。两者名称相近，但作用阶段不同，不能混用。

