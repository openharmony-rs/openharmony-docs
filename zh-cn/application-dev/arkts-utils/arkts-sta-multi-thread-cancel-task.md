# 多线程取消TaskPool任务场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)支持通过taskpool.cancel取消已提交的任务。取消等待中或延时未触发的任务时，任务不会继续执行；取消已经运行的任务时，运行时不会强制中断线程，任务函数需要通过taskpool.Task.isCanceled()或taskpool.Task.checkCancellation()感知取消状态并主动返回。

动态ArkTS文档通常使用@Sendable对象跨线程保存任务ID，并在子线程中调用taskpool.cancel(taskId)。ArkTS-Sta不需要使用@Sendable表达共享对象，也不需要从@kit.ArkTS导入taskpool。静态场景可以直接持有taskpool.Task对象，并调用taskpool.cancel(task)取消任务。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 定义任务函数

delayedTask模拟延时执行的业务任务。

```ts
// ArkTS-Sta示例
// CancelTask.ets
export function delayedTask(): string {
  return "delayed task executed";
}
```

## 取消延时任务

页面中先提交一个延时任务，再通过taskpool.cancel(task)取消该延时任务。由于延时任务尚未开始执行，取消成功后，延时任务对应的Promise进入catch分支。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { delayedTask } from './CancelTask'

@Entry
@Component
struct Index {
  @State message: string = "ready";
  @State cancelResult: string = "";

  private startAndCancel(): void {
    let task: taskpool.Task = new taskpool.Task("delayedTask", delayedTask);

    taskpool.executeDelayed(3000, task).then((result: Any) => {
      this.message = "task result: " + result;
    }).catch((error: Error) => {
      this.message = "delayed task canceled";
      console.info("delayed task canceled: " + error.message); // delayed task canceled: xxx
    });

    try {
      taskpool.cancel(task);
      this.cancelResult = "cancel success";
    } catch (error) {
      this.cancelResult = "cancel failed";
      console.info("cancel failed: " + error); // cancel failed: xxx
    }
  }

  build() {
    Column(undefined) {
      Text(this.message).fontSize(20)
      Text(this.cancelResult).fontSize(20)

      Button("start and cancel")
        .onClick((e: ClickEvent) => {
          this.startAndCancel();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 取消正在执行的任务

取消已经开始执行的TaskPool任务时，任务不会被强制停止。taskpool.cancel()只会设置取消状态，任务函数应在循环、分阶段计算或可中断处理点主动检查取消状态，并尽快返回。任务函数主动返回时，任务对应的Promise会正常兑现，不会进入catch分支。

```ts
// ArkTS-Sta示例
// RunningTask.ets
export function countUntilCanceled(limit: int): int {
  let result: int = 0;

  for (let index: int = 0; index < limit; index++) {
    if (index % 10000 == 0 && taskpool.Task.isCanceled()) {
      return result;
    }
    result++;
  }

  return result;
}
```

```ts
// ArkTS-Sta示例
import { countUntilCanceled } from './RunningTask'

async function cancelRunningTask(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task("countUntilCanceled", countUntilCanceled, 100000000);
  let promise: Promise<Any> = taskpool.execute(task);

  setTimeout(() => {
    try {
      taskpool.cancel(task.taskId);
    } catch (error) {
      console.info("cancel failed: " + error); // cancel failed: xxx（任务已完成或已取消等场景）
    }
  }, 10);

  try {
    let result: int = (await promise) as int;
    console.info("running task stopped at: " + result); // running task stopped at: xxx（任务开始执行后主动检查取消状态并返回）
  } catch (error) {
    console.info("running task canceled before start: " + error); // running task canceled before start: xxx（任务开始前被取消）
  }
}
```

上述示例用于说明“运行中任务的协作式取消”。taskpool.cancel(task.taskId)只是设置取消状态；countUntilCanceled通过taskpool.Task.isCanceled()感知取消，并把已经完成的计数作为返回值返回。因此，任务已经开始执行后，日志通常是running task stopped at: xxx，而不是进入catch分支。如果取消发生在任务开始执行前，任务对应的Promise才会进入catch分支；如果任务函数从不检查取消状态，任务会继续执行到函数自然结束。

## 使用建议

- ArkTS-Sta中不需要使用@Concurrent标记TaskPool任务函数，也不需要使用@Sendable封装任务ID。
- 取消延时未触发的任务时，建议保留taskpool.Task对象并调用taskpool.cancel(task)。延时任务触发前尚未进入普通任务队列，使用taskId取消可能查找不到目标任务。
- 取消已经提交到TaskPool调度队列的普通任务时，可以使用taskId调用taskpool.cancel(taskId)。如果取消方已经持有taskpool.Task对象，也可以调用taskpool.cancel(task)。
- 取消等待中、延时未触发或周期任务时，取消操作可以阻止后续执行；取消运行中任务时，需要任务函数主动检查taskpool.Task.isCanceled()或调用taskpool.Task.checkCancellation()。
- 取消未提交、已完成或已取消的任务可能抛出异常。无法保证任务状态时，应捕获异常并按业务需要处理。
- 不要在TaskPool任务中访问ArkUI组件、路由对象或@State状态变量。取消任务可以在后台线程执行，UI状态更新应回到宿主线程处理。
