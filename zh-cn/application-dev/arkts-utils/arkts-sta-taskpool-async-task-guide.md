# TaskPool指定任务并发度场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

对于相机预览帧处理、传感器数据处理、批量上传等高频耗时任务，如果提交速度高于处理速度，直接使用taskpool.execute提交所有任务可能导致任务堆积。ArkTS-Sta可以使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)提供的AsyncRunner限制同类任务的并发度，并通过等待队列容量控制等待任务数量。

动态ArkTS示例中通常需要从@kit.ArkTS导入taskpool并使用@Concurrent装饰任务函数。ArkTS-Sta中taskpool为静态并发能力，普通函数可以直接作为TaskPool任务函数，不需要@Concurrent。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 定义耗时任务

以下示例使用计算循环模拟帧数据处理。实际业务中，可以将图像转换、特征提取、数据压缩等耗时逻辑放入TaskPool任务函数。

```ts
// ArkTS-Sta示例
// FrameTask.ets
export class FrameResult {
  frameId: int = 0;
  checksum: int = 0;

  constructor(frameId: int, checksum: int) {
    this.frameId = frameId;
    this.checksum = checksum;
  }
}

export function processFrame(frameId: int, seed: int): FrameResult {
  let checksum: int = 0;

  for (let index: int = 0; index < 2000000; index++) {
    checksum = (checksum + frameId + seed + index) % 100000;

    if (index % 50000 == 0 && taskpool.Task.isCanceled()) {
      return new FrameResult(frameId, -1);
    }
  }

  return new FrameResult(frameId, checksum);
}
```

## 创建AsyncRunner限制并发度

AsyncRunner的runningCapacity表示允许同时执行的最大任务数量，waitingCapacity表示等待队列容量。waitingCapacity大于0时，如果等待队列已满，新任务进入队尾，队头等待任务会被丢弃，对应任务的Promise会被拒绝。该模式适合“只关心较新数据”的高频采集场景。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import hilog from '@ohos.hilog'
import { FrameResult, processFrame } from './FrameTask'

@Entry
@Component
struct Index {
  @State message: string = "ready";
  @State submittedCount: int = 0;
  @State completedCount: int = 0;
  @State failedCount: int = 0;

  private runner: taskpool.AsyncRunner = new taskpool.AsyncRunner("frameRunner", 3, 2);

  private submitFrame(frameId: int): void {
    let task: taskpool.Task = new taskpool.Task("frame-" + frameId, processFrame, frameId, frameId * 13);
    this.submittedCount++;
    this.message = "submitted: " + this.submittedCount;

    this.runner.execute(task).then((result: Any) => {
      let frameResult: FrameResult = result as FrameResult;
      this.completedCount++;
      this.message = "done frame: " + frameResult.frameId + ", checksum: " + frameResult.checksum;
      hilog.info(0x0000, "testTag", "done frame: " + frameResult.frameId);
    }).catch((error: Error) => {
      this.failedCount++;
      this.message = "failed: " + this.failedCount;
      hilog.error(0x0000, "testTag", "execute frame failed: " + error.message);
    });
  }

  build() {
    Column(undefined) {
      Text(this.message).fontSize(20)
      Text("submitted: " + this.submittedCount).fontSize(20)
      Text("completed: " + this.completedCount).fontSize(20)
      Text("failed: " + this.failedCount).fontSize(20)

      Button("submit frames")
        .onClick((e: ClickEvent) => {
          for (let index: int = 0; index < 20; index++) {
            this.submitFrame(index);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

上述示例创建了名为frameRunner的异步队列，并将并发度设置为3、等待队列容量设置为2。高频提交20个帧处理任务时，最多同时运行3个任务，最多等待2个任务；当等待队列已满时，较早进入等待队列但尚未开始运行的任务会被丢弃。

## 使用匿名AsyncRunner

如果不需要跨模块复用同一个异步队列，可以创建匿名AsyncRunner。不传入waitingCapacity或传入0时，等待队列容量不受限制，任务不会因为等待队列满而被丢弃。

```ts
// ArkTS-Sta示例
function upload(index: int): int {
  return index;
}

async function runUploadTasks(): Promise<void> {
  let runner: taskpool.AsyncRunner = new taskpool.AsyncRunner(2);
  let task1: taskpool.Task = new taskpool.Task(upload, 1);
  let task2: taskpool.Task = new taskpool.Task(upload, 2);
  let task3: taskpool.Task = new taskpool.Task(upload, 3);

  let promise1: Promise<Any> = runner.execute(task1);
  let promise2: Promise<Any> = runner.execute(task2);
  let promise3: Promise<Any> = runner.execute(task3);

  let result1: int = (await promise1) as int;
  let result2: int = (await promise2) as int;
  let result3: int = (await promise3) as int;

  console.info("result: " + result1 + ", " + result2 + ", " + result3); // result: 1, 2, 3
}
```

## 使用建议

- runningCapacity应根据任务类型、CPU核数、I/O压力和业务实时性设置。CPU密集型任务不宜设置过高，避免后台任务争抢CPU影响UI响应。
- waitingCapacity为0或不传入时，等待队列不限制容量，适合所有任务都必须处理的场景；大于0时，等待队列满后丢弃队头任务，适合只关心新数据的场景。
- 使用同名AsyncRunner时，会复用首次创建的队列实例；后续使用相同名称创建时，不会更新并发度和等待队列容量。
- 每次提交到AsyncRunner的任务都应是新的taskpool.Task实例。AsyncRunner不支持执行已执行过的任务、任务组任务、依赖任务、周期任务、延迟任务和串行队列任务。
- AsyncRunner只限制该Runner实例内任务的并发数量，不表示指定任务运行在哪个具体线程。需要固定线程或常驻事件循环时，使用EAWorker。
- 多个任务访问同一份可变共享数据时，仍需要使用锁、原子类型或并发容器保护。并发度控制不能替代数据同步。
