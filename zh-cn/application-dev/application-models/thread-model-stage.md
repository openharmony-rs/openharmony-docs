# 线程模型

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->


线程是操作系统进行运算调度的基本单位，是进程中的执行流，共享进程的资源。一个进程可以包含多个线程。

## 线程类型
Stage模型下的线程主要有如下三类：
- 主线程
  - 执行UI绘制。
  - 管理主线程的ArkTS引擎实例，使多个UIAbility组件能够运行在其之上。
  - 管理其他线程的ArkTS引擎实例，例如使用TaskPool（任务池）创建任务或取消任务、启动和终止Worker线程。
  - 分发交互事件。
  - 处理应用代码的回调，包括事件处理和生命周期管理。
  - 接收TaskPool以及Worker线程发送的消息。
- TaskPool线程（@ohos.taskpool）
  - 用于执行耗时操作，支持设置调度优先级、负载均衡等功能，推荐使用。
- Worker线程（@ohos.worker）
  - 用于执行耗时操作，支持线程间通信。

    TaskPool与Worker的运作机制、通信手段和使用方法可以参考TaskPool和Worker的对比。

    ![thread-model-stage](figures/thread-model-stage.png)

> **说明：**
>
> - TaskPool自行管理线程数量，其生命周期由TaskPool统一管理。Worker线程的生命周期由开发者自行维护。
> - 同一线程中存在多个组件，例如UIAbility组件和UI组件都存在于主线程中。在Stage模型中目前主要使用EventHub进行数据通信。
> - 执行`hdc shell`命令，进入设备的shell命令行。在shell命令行中，执行`ps -p <pid> -T`命令，可以查看指定应用进程的线程信息。其中，`<pid>`为需要指定的应用进程的进程ID。



## 使用EventHub进行线程内通信

EventHub提供了线程内发送和处理事件的能力，包括对事件订阅、取消订阅、触发事件等。以UIAbility组件与UI之间的数据同步为例，具体使用方法可以参考UIAbility组件与UI的数据同步。
