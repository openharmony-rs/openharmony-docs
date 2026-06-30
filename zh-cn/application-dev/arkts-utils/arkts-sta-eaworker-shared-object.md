# EAWorker间共享对象通信 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta采用共享内存模型。普通ArkTS-Sta对象作为[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)任务入参传递时，宿主线程和EAWorker线程访问的是同一对象引用。EAWorker修改对象状态后，宿主线程可以读取到同一对象上的最新数据。

该方式适合在固定线程中维护业务状态、复用上下文对象，或在多个EAWorker之间传递任务对象。需要注意的是，共享对象不等于线程安全对象；如果多个线程会同时读写同一份可变数据，需要使用锁、原子类型或并发容器保护共享状态。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 定义共享对象

以下示例使用AtomicInt保存计数值。AtomicInt适合保护单个数值状态，多个线程读写该值时不需要额外加锁。

```ts
// ArkTS-Sta示例
// SharedCounter.ets
export class SharedCounter {
  private value: AtomicInt = new AtomicInt(0);

  public increase(): int {
    return this.value.fetchAdd(1) + 1;
  }

  public current(): int {
    return this.value.load();
  }
}
```

## 在EAWorker中修改共享对象

EAWorker任务函数接收SharedCounter实例并修改计数值。该对象不会被复制，任务函数修改的是宿主线程传入的同一个对象。

```ts
// ArkTS-Sta示例
// SharedCounterTask.ets
import { SharedCounter } from './SharedCounter'

export function increaseInWorker(counter: SharedCounter, times: int): int {
  let latest: int = counter.current();
  for (let index: int = 0; index < times; index++) {
    latest = counter.increase();
  }
  return latest;
}
```

## 在宿主线程读取修改结果

宿主线程创建SharedCounter并传入EAWorker。EAWorker任务返回后，宿主线程读取counter.current()，可以看到EAWorker对同一对象的修改结果。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { SharedCounter } from './SharedCounter'
import { increaseInWorker } from './SharedCounterTask'

@Entry
@Component
struct Index {
  @State message: string = "ready";
  private counter: SharedCounter = new SharedCounter();
  private worker: EAWorker | undefined = undefined;

  aboutToAppear(): void {
    this.worker = new EAWorker("sharedCounterWorker");
    this.worker!.start();
  }

  aboutToDisappear(): void {
    if (this.worker !== undefined) {
      this.worker!.quit();
      this.worker = undefined;
    }
  }

  private runWorkerTask(): void {
    if (this.worker === undefined) {
      this.message = "worker is not started";
      console.info("worker is not started"); // worker is not started
      return;
    }

    let job = this.worker!.run<int>(increaseInWorker, this.counter, 3) as Job<int>;
    let workerValue: int = job.Await();
    let mainValue: int = this.counter.current();
    this.message = "worker value: " + workerValue + ", main value: " + mainValue;
    console.info(this.message); // worker value: 3, main value: 3
  }

  build() {
    Column(undefined) {
      Text(this.message).fontSize(20)
      Button("run")
        .onClick((e: ClickEvent) => {
          this.runWorkerTask();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- ArkTS-Sta对象传入EAWorker时默认按共享引用传递。不要按ArkTS-Dyn普通对象的结构化克隆语义理解。
- 只读对象可以直接在多个EAWorker间共享。
- 一个线程写入、其他线程在消息顺序或任务完成后读取时，可以通过业务流程保证访问顺序。
- 多个EAWorker同时写入同一对象时，应使用AtomicInt、AtomicBoolean、Mutex、RWLock或并发容器保护共享状态。
- ArkUI状态对象不建议直接传入EAWorker中修改。后台线程应修改普通数据对象，再由宿主线程更新ArkUI状态。
