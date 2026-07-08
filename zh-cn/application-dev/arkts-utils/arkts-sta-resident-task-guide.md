# 常驻任务开发指导（EAWorker） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

常驻任务是指需要跟随业务生命周期长期存在、持续接收消息或维护线程内状态的任务。ArkTS-Sta中推荐使用[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)实现常驻任务。

EAWorker对应独占工作线程，开发者需要显式调用start启动，并在不再需要时调用join或quit释放线程资源。与ArkTS-Dyn Worker不同，ArkTS-Sta不使用Worker线程文件，也不使用postMessage接口；常驻任务可通过run、MessageHandler和Message进行控制。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 创建常驻EAWorker

以下示例使用MessageHandler向EAWorker发送start和stop消息。EAWorker收到start后开始周期性上报状态，收到stop后停止任务。

示例重点展示常驻任务的启动、停止和消息通信方式。实际业务中，start和stop通常由页面生命周期、用户操作或业务事件触发。

```ts
// ArkTS-Sta示例
const MSG_START: int = 1;
const MSG_STOP: int = 2;
const MSG_REPORT: int = 3;

class ResidentState {
  running: AtomicBoolean = new AtomicBoolean(false);
}

function performTask(state: ResidentState, mainHandler: concurrency.MessageHandler): void {
  if (!state.running.load()) {
    return;
  }

  let report = new concurrency.Message(MSG_REPORT, "EAWorker is performing a task", mainHandler);
  report.sendToTarget();
}

async function runResidentTask(): Promise<void> {
  let worker: EAWorker = new EAWorker("residentWorker");
  worker.start();

  let state: ResidentState = new ResidentState();

  let mainHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
    if (msg.getWhat() == MSG_REPORT) {
      console.info(msg.getObject() as string); // EAWorker is performing a task; EAWorker stopped
    }
  }, EAWorker.main());

  let workerHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
    if (msg.getWhat() == MSG_START) {
      state.running.store(true);
      performTask(state, mainHandler);
    } else if (msg.getWhat() == MSG_STOP) {
      state.running.store(false);
      let report = new concurrency.Message(MSG_REPORT, "EAWorker stopped", mainHandler);
      report.sendToTarget();
    }
  }, worker);

  try {
    new concurrency.Message(MSG_START, workerHandler).sendToTarget();

    // 示例中直接发送停止消息。实际业务可在页面销毁、任务完成或用户操作时发送停止消息。
    new concurrency.Message(MSG_STOP, workerHandler).sendToTarget();
  } finally {
    await worker.join();
  }
}
```

## 使用run提交常驻任务逻辑

如果常驻任务不需要复杂消息分发，也可以通过run提交长期运行逻辑，并使用共享状态控制退出。

```ts
// ArkTS-Sta示例
function residentLoop(state: ResidentState): void {
  state.running.store(true);
  while (state.running.load()) {
    // 执行常驻任务逻辑。
    state.running.store(false);
  }
}

async function runResidentLoop(): Promise<void> {
  let state: ResidentState = new ResidentState();
  let worker: EAWorker = new EAWorker("residentLoopWorker");
  worker.start();

  try {
    await worker.run<void>(residentLoop, state);
  } finally {
    await worker.join();
  }
}
```

## 使用建议

- 需要长期保留线程上下文、事件循环或状态对象时，使用EAWorker。
- 常驻任务退出条件应由业务显式控制，例如共享原子标志、消息或任务状态。
- 不再需要EAWorker时，应调用join或quit释放线程资源。
- EAWorker间传递对象默认共享引用。多个线程读写同一可变对象时，需要使用同步机制。
- 如果任务只是短时独立执行，优先使用TaskPool，避免手动管理线程生命周期。
