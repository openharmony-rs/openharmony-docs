# 多级EAWorker间高性能消息通信 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

多级[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)通信是指一个EAWorker创建或管理其他EAWorker，并在多个EAWorker之间分发任务、回收结果。这里的“多级”描述的是任务分发链路，不表示线程之间存在父子从属关系；参与通信的EAWorker本质上都是独立工作线程。ArkTS-Sta采用共享内存模型，对象跨EAWorker传递时默认共享对象引用。

多级EAWorker适合任务需要长期驻留、按固定线程分组处理，或需要由一个调度EAWorker统一管理多个处理EAWorker的场景。使用时需要注意生命周期管理：退出调度EAWorker前，应先让处理EAWorker完成任务并退出。

下面以调度EAWorker向两个处理EAWorker分发文件处理任务为例说明。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 定义任务数据

```ts
// ArkTS-Sta示例
class CopyEntry {
  type: string;
  filePath: string;
  status: string = "pending";

  constructor(type: string, filePath: string) {
    this.type = type;
    this.filePath = filePath;
  }
}
```

示例中的CopyEntry对象会在主线程、调度EAWorker和处理EAWorker之间传递。ArkTS-Sta中传递的是同一对象引用，处理EAWorker修改status字段后，调度EAWorker和主线程可以读取到同一对象上的最新状态。该方式适合任务对象由一个线程负责写入、其他线程按消息顺序读取的场景；如果多个EAWorker会同时写入同一对象，需要使用锁、原子类型或并发容器保护。

## 实现调度EAWorker任务

调度EAWorker创建两个处理EAWorker，并通过MessageHandler向处理EAWorker发送任务。处理EAWorker完成任务后，将结果发送回调度EAWorker；调度EAWorker统计所有任务完成后通知主线程。

```ts
// ArkTS-Sta示例
const COPY_1: string = "copy1";
const COPY_2: string = "copy2";
const MSG_COPY: int = 1;
const MSG_DONE: int = 2;
const MSG_ALL_DONE: int = 3;

function startDispatchWorker(tasks: Array<CopyEntry>, mainHandler: concurrency.MessageHandler): void {
  let dispatcher = EAWorker.current();
  if (dispatcher === undefined) {
    return;
  }

  if (tasks.length == 0) {
    let doneMessage = new concurrency.Message(MSG_ALL_DONE, "all tasks done", mainHandler);
    doneMessage.sendToTarget();
    return;
  }

  let processingWorker1: EAWorker = new EAWorker("copyWorker1");
  let processingWorker2: EAWorker = new EAWorker("copyWorker2");
  processingWorker1.start();
  processingWorker2.start();

  let totalRemaining = new AtomicInt(tasks.length);
  let worker1Remaining = new AtomicInt(0);
  let worker2Remaining = new AtomicInt(0);

  for (let task of tasks) {
    if (task.type == COPY_1) {
      worker1Remaining.fetchAdd(1);
    } else if (task.type == COPY_2) {
      worker2Remaining.fetchAdd(1);
    }
  }

  let dispatcherHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
    let entry = msg.getObject() as CopyEntry;
    console.info("dispatcher receive done: " + entry.filePath); // dispatcher receive done: file://copy1-a.txt（示例输出，具体顺序以实际调度为准）

    if (entry.type == COPY_1 && worker1Remaining.fetchSub(1) == 1) {
      processingWorker1.quit();
    }
    if (entry.type == COPY_2 && worker2Remaining.fetchSub(1) == 1) {
      processingWorker2.quit();
    }
    if (totalRemaining.fetchSub(1) == 1) {
      let doneMessage = new concurrency.Message(MSG_ALL_DONE, "all tasks done", mainHandler);
      doneMessage.sendToTarget();
    }
  }, dispatcher);

  let workerHandler1 = new concurrency.MessageHandler((msg: concurrency.Message) => {
    let entry = msg.getObject() as CopyEntry;
    entry.status = "done";
    let doneMessage = new concurrency.Message(MSG_DONE, entry, dispatcherHandler);
    doneMessage.sendToTarget();
  }, processingWorker1);

  let workerHandler2 = new concurrency.MessageHandler((msg: concurrency.Message) => {
    let entry = msg.getObject() as CopyEntry;
    entry.status = "done";
    let doneMessage = new concurrency.Message(MSG_DONE, entry, dispatcherHandler);
    doneMessage.sendToTarget();
  }, processingWorker2);

  if (worker1Remaining.load() == 0) {
    processingWorker1.quit();
  }
  if (worker2Remaining.load() == 0) {
    processingWorker2.quit();
  }

  for (let task of tasks) {
    if (task.type == COPY_1) {
      new concurrency.Message(MSG_COPY, task, workerHandler1).sendToTarget();
    } else if (task.type == COPY_2) {
      new concurrency.Message(MSG_COPY, task, workerHandler2).sendToTarget();
    }
  }
}
```

## 在主线程启动调度EAWorker

主线程创建调度EAWorker，准备任务数据，并通过run启动调度EAWorker中的任务分发逻辑。调度EAWorker处理完成后，通过主线程的MessageHandler通知完成。

```ts
// ArkTS-Sta示例
async function runMultiLevelWorkers(): Promise<void> {
  let dispatchWorker: EAWorker = new EAWorker("copyDispatcher");
  dispatchWorker.start();

  let tasks: Array<CopyEntry> = [
    new CopyEntry(COPY_1, "file://copy1-a.txt"),
    new CopyEntry(COPY_2, "file://copy2-a.txt"),
    new CopyEntry(COPY_1, "file://copy1-b.txt"),
    new CopyEntry(COPY_2, "file://copy2-b.txt")
  ];

  let finished: Promise<undefined> = new Promise<undefined>((resolve, reject) => {
    let mainHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
      if (msg.getWhat() == MSG_ALL_DONE) {
        console.info(msg.getObject() as string); // all tasks done
        resolve(undefined);
      }
    }, EAWorker.main());

    try {
      dispatchWorker.run<void>(startDispatchWorker, tasks, mainHandler);
    } catch (error) {
      reject(error as Error);
    }
  });

  try {
    await finished;
  } finally {
    await dispatchWorker.join();
  }
}
```

## 使用建议

- ArkTS-Sta对象在EAWorker间默认共享。示例中的CopyEntry对象在主线程、调度EAWorker和处理EAWorker之间传递的是同一对象引用。
- 多级EAWorker需要开发者自行管理生命周期。调度EAWorker退出前，应确保处理EAWorker已完成任务并调用join或quit。
- 如果多个EAWorker会同时修改同一个对象或集合，需要使用锁、原子类型或并发容器保证并发安全。
- 如果只是分发短时独立任务，优先使用TaskPool或TaskGroup；只有需要独占线程或长期驻留时才使用多级EAWorker。
