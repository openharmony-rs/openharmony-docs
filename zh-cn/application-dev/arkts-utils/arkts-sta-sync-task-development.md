# 同步任务开发指导（TaskPool和EAWorker） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

同步任务是指多个任务之间需要按照一定顺序或规则执行的任务，例如依次执行多个步骤、保护共享状态、或在同一个线程上下文中操作同一个句柄。ArkTS-Sta中可使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)或[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)编排这类任务。

ArkTS-Sta中，相互独立的同步任务可使用TaskPool和SequenceRunner；需要固定线程上下文或长期复用同一对象状态时，使用EAWorker。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 使用TaskPool处理独立同步任务

如果每个任务之间只存在结果依赖，可以在宿主线程使用await按顺序等待TaskPool任务完成。

```ts
// ArkTS-Sta示例
async function taskpoolFunc(num: int): Promise<int> {
  return num + 100;
}

async function runSyncTasksInTaskPool(): Promise<void> {
  let task1: taskpool.Task = new taskpool.Task(taskpoolFunc, 1);
  let res1: int = (await taskpool.execute(task1)) as int;

  let task2: taskpool.Task = new taskpool.Task(taskpoolFunc, res1);
  let res2: int = (await taskpool.execute(task2)) as int;

  console.info("taskpool res1: " + res1); // taskpool res1: 101
  console.info("taskpool res2: " + res2); // taskpool res2: 201
}
```

如果一组任务需要严格按提交顺序执行，可以使用SequenceRunner。

```ts
// ArkTS-Sta示例
function syncStep(value: int): int {
  return value + 1;
}

async function runWithSequenceRunner(): Promise<void> {
  let runner: taskpool.SequenceRunner = new taskpool.SequenceRunner();

  let result1: Any = await runner.execute(new taskpool.Task(syncStep, 1));
  let result2: Any = await runner.execute(new taskpool.Task(syncStep, result1 as int));

  console.info("sequence result: " + result2); // sequence result: 3
}
```

## 使用EAWorker处理关联同步任务

当一系列任务需要使用同一个句柄、缓存或类对象，并且希望这些操作始终在同一个线程中执行时，建议使用EAWorker。

```ts
// ArkTS-Sta示例
class Handle {
  private id: int = 0;

  syncGet(): int {
    return this.id;
  }

  syncSet(num: int): boolean {
    this.id = num;
    return true;
  }
}

function setHandle(handle: Handle, value: int): boolean {
  return handle.syncSet(value);
}

function getHandle(handle: Handle): int {
  return handle.syncGet();
}

async function runAssociatedSyncTasks(): Promise<void> {
  let handle: Handle = new Handle();
  let worker: EAWorker = new EAWorker("syncWorker");
  worker.start();

  try {
    let setResult = await worker.run<boolean>(setHandle, handle, 10);
    let getResult = await worker.run<int>(getHandle, handle);

    console.info("set result: " + setResult.Await()); // set result: true
    console.info("get result: " + getResult.Await()); // get result: 10
  } finally {
    await worker.join();
  }
}
```

## 保护共享状态

如果多个TaskPool任务会并发访问同一个可变对象，需要使用同步能力保护临界区。

```ts
// ArkTS-Sta示例
class Counter {
  value: int = 0;
}

async function increase(counter: Counter, lock: AsyncLock): Promise<void> {
  await lock.lockAsync<void>(() => {
    counter.value++;
  });
}

async function runWithLock(): Promise<void> {
  let counter: Counter = new Counter();
  let lock: AsyncLock = new AsyncLock();

  await Promise.all<Any>([
    taskpool.execute(increase, counter, lock),
    taskpool.execute(increase, counter, lock)
  ]);

  console.info("counter: " + counter.value); // counter: 2
}
```

## 使用建议

- 任务只是存在先后依赖时，可以使用await串行等待TaskPool执行结果。
- 多个任务需要严格按提交顺序执行时，使用SequenceRunner。
- 任务需要固定线程上下文或复用同一对象状态时，使用EAWorker。
- 多线程并发访问共享可变对象时，使用AsyncLock、Mutex、RWLock、原子类型或并发容器。
- ArkTS-Sta对象默认共享，不需要通过共享模块或Sendable表达共享语义。
