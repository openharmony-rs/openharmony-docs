# 多线程
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

ANI场景下的多线程协作通常有两种方式：自行创建native线程并附加到ArkTS虚拟机，或在ArkTS侧使用语言层并发API（如`taskpool`）调度native调用。选择哪种方式取决于线程模型由谁管理：已有C++线程、系统回调或长期后台任务更适合第一种；只是希望把耗时native计算放到后台执行时，优先使用第二种。

## 自行创建native线程

native侧自行创建线程时，线程默认不具备可用的ANI调用上下文。线程内如果需要调用ANI接口，应先通过`AttachCurrentThread`附加到ArkTS虚拟机，获取当前线程自己的`ani_env`，并在线程退出前调用`DetachCurrentThread`。

1. 在已有的native调用中，通过`GetVM`获取`ani_vm`。
2. 创建native线程时，只捕获`ani_vm`以及必要的全局引用，不要捕获`ani_env`或局部引用。
3. 在线程入口调用`AttachCurrentThread`，获取该线程自己的`ani_env`。
4. 使用该线程获取到的`ani_env`调用ANI接口。
5. 线程退出前调用`DetachCurrentThread`。

示例：

```cpp
void StartWorker(ani_env *env)
{
    ani_vm *vm = nullptr;
    env->GetVM(&vm);

    std::thread([vm]() {
        ani_env *threadEnv = nullptr;
        ani_options args {0, nullptr};
        if (vm->AttachCurrentThread(&args, ANI_VERSION_1, &threadEnv) != ANI_OK) {
            return;
        }

        // 在该线程中只能使用threadEnv调用ANI接口。
        // 不要使用创建线程时所在调用栈中的env。

        vm->DetachCurrentThread();
    }).detach();
}
```

## 使用语言层API

如果只是希望native方法在后台线程执行，建议在ArkTS侧使用`taskpool`等语言层API编排。此时native方法仍按同步函数实现，线程调度、结果回到调用侧以及Promise状态管理都放在ArkTS侧完成，native层不需要自行创建线程。

这种方式更适合短到中等耗时的计算任务，代码结构也更简单。相关异步封装方式可参考[异步编程](ani-asynchronous-programming.md)。

## 注意事项

- `ani_env`与线程绑定，不要保存到全局变量，也不要在`std::thread`、lambda或线程池任务中跨线程捕获或使用；定义在其他线程上执行的lambda表达式时，应捕获`ani_vm`，并通过`AttachCurrentThread`获取当前线程自己的`ani_env`。

更细节的跨线程引用、局部引用释放和`AttachCurrentThread`参数说明可参考[生命周期管理](ani-lifecycle-management.md)。

