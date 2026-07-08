# EAWorker常驻线程通过TaskPool进行多任务并发处理 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

在ArkTS-Sta中，可以实现“EAWorker常驻线程通过TaskPool进行多任务并发处理”场景，但实现模型与动态ArkTS不同。动态ArkTS通常通过Worker线程文件创建ThreadWorker，并在Worker内部使用TaskPool；ArkTS-Sta常驻线程应使用[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)，并将并行子任务提交给[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)，通过run、postToMain、MessageHandler和Message等接口进行线程协同。

EAWorker负责保存长期状态、接收调度请求和汇总结果；可拆分、互不依赖的耗时子任务交给TaskPool并发执行。该方式适用于图片批处理、批量数据计算、后台索引构建等需要“固定调度线程 + 多个并行子任务”的场景。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 实现思路

1. 宿主线程创建并启动一个EAWorker，使其作为常驻调度线程。
2. 宿主线程通过EAWorker.run向EAWorker提交一次批处理请求。
3. EAWorker将批处理请求拆分为多个独立子任务，并提交到TaskPool并发执行。
4. EAWorker等待子任务完成后汇总结果，并通过EAWorker.run返回的Job通知宿主线程。
5. 页面退出或业务结束时，调用quit释放EAWorker线程资源。

## 定义任务数据

以下示例定义子任务输入和输出对象。ArkTS-Sta对象默认按共享引用在线程间传递，示例中的WorkItem在提交后不再修改，因此无需额外加锁。

```ts
// ArkTS-Sta示例
// WorkerTaskModel.ets
export class WorkItem {
  id: int = 0;
  weight: int = 0;

  constructor(id: int, weight: int) {
    this.id = id;
    this.weight = weight;
  }
}

export class WorkResult {
  id: int = 0;
  value: int = 0;

  constructor(id: int, value: int) {
    this.id = id;
    this.value = value;
  }
}
```

## 定义TaskPool子任务

TaskPool子任务是普通函数，不需要使用@Concurrent装饰，也不需要从@kit.ArkTS导入taskpool。

```ts
// ArkTS-Sta示例
// WorkerTaskPoolTask.ets
import { WorkItem, WorkResult } from './WorkerTaskModel'

export function computeSubTask(item: WorkItem): WorkResult {
  let value: int = 0;
  for (let index: int = 0; index < item.weight * 10000; index++) {
    value += (index + item.id) % 7;
  }
  return new WorkResult(item.id, value);
}
```

## 在EAWorker中调度TaskPool任务

EAWorker中的调度函数将批处理请求拆分为多个TaskPool任务。以下示例在EAWorker线程中调用awaitSync等待TaskPool子任务完成，阻塞的是EAWorker调度线程，不会阻塞宿主线程。

```ts
// ArkTS-Sta示例
// WorkerTaskPoolScheduler.ets
import { WorkItem, WorkResult } from './WorkerTaskModel'
import { computeSubTask } from './WorkerTaskPoolTask'

function buildItems(seed: int, count: int): Array<WorkItem> {
  let items: Array<WorkItem> = [];
  for (let index: int = 0; index < count; index++) {
    items.push(new WorkItem(index, seed + index));
  }
  return items;
}

export function dispatchTaskPoolTasks(seed: int, count: int): Array<WorkResult> {
  let items: Array<WorkItem> = buildItems(seed, count);
  let promises: Array<Promise<Any>> = [];

  for (let index: int = 0; index < items.length; index++) {
    let item: WorkItem = items[index];
    let task: taskpool.Task = new taskpool.Task("calculate-" + item.id, computeSubTask, item);
    promises.push(taskpool.execute(task));
  }

  let results: Array<WorkResult> = [];
  for (let index: int = 0; index < promises.length; index++) {
    results.push(promises[index].awaitSync() as WorkResult);
  }
  return results;
}
```

## 宿主线程创建常驻EAWorker

以下示例在页面创建时启动EAWorker，在按钮点击时向EAWorker提交调度任务。EAWorker返回Job后，宿主线程通过Await()获取结果并更新ArkUI状态。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { WorkResult } from './WorkerTaskModel'
import { dispatchTaskPoolTasks } from './WorkerTaskPoolScheduler'

@Entry
@Component
struct Index {
  @State status: string = 'ready';
  @State resultText: string = '';
  private worker: EAWorker | undefined = undefined;

  aboutToAppear(): void {
    this.worker = new EAWorker("resident-dispatcher");
    this.worker!.start();
  }

  aboutToDisappear(): void {
    if (this.worker !== undefined) {
      this.worker!.quit();
      this.worker = undefined;
    }
  }

  private startWork(): void {
    if (this.worker === undefined) {
      this.status = 'worker is not started';
      return;
    }

    this.status = 'running';
    this.resultText = '';
    try {
      let job = this.worker!.run<Array<WorkResult>>(dispatchTaskPoolTasks, 10, 4) as Job<Array<WorkResult>>;
      let results: Array<WorkResult> = job.Await();
      this.status = 'finished';
      this.resultText = this.summarize(results);
    } catch (error) {
      this.status = 'failed';
      this.resultText = 'worker task failed';
      console.info('worker task failed'); // worker task failed
    }
  }

  private summarize(results: Array<WorkResult>): string {
    let total: int = 0;
    for (let index: int = 0; index < results.length; index++) {
      total += results[index].value;
    }
    return 'task count: ' + results.length + ', total: ' + total;
  }

  build() {
    Column(undefined) {
      Text('EAWorker + TaskPool').fontSize(20)
      Text(this.status).fontSize(16)
      Button('Start')
        .onClick((event: ClickEvent) => {
          console.info('start work'); // start work
          this.startWork();
        })
      Text(this.resultText).fontSize(16)
    }
  }
}
```

## 开发建议

- EAWorker适合保存常驻状态和进行调度，不建议把所有计算都放在EAWorker单线程中执行；可拆分的CPU密集型或批量任务应交给TaskPool。
- TaskPool任务函数不要调用EAWorker.current()。静态源码中TaskPool线程调用该接口会抛出异常。
- awaitSync会阻塞当前EAWorker线程，适合调度线程等待一批子任务完成后统一返回结果。不要在宿主线程中使用awaitSync等待耗时任务。
- 多个TaskPool子任务共享同一份可变对象时，需要使用锁、原子类型或并发容器保护；如果子任务只读取输入数据，建议提交后不再修改输入对象。
- 如果业务需要持续多次消息交互，可在EAWorker上创建concurrency.MessageHandler，用消息触发调度函数；如果只是一次请求和一次结果返回，EAWorker.run更直接。
