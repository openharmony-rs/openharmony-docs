# 并发常见问题 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta并发能力基于共享内存模型实现，[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)任务函数、[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)任务函数、普通对象和ArrayBuffer默认可以跨线程共享。与动态ArkTS相比，ArkTS-Sta不需要@Concurrent、@Sendable、Worker线程文件或Structured Clone，但需要开发者关注共享可变对象的同步、EAWorker生命周期和TaskPool任务编排。

本文整理ArkTS-Sta并发开发中的常见问题及排查方向。涉及TaskPool运行日志时，不同版本的日志字段可能存在差异，应以设备实际Hilog和Trace为准。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## TaskPool任务不执行如何定位

TaskPool任务未按预期执行时，可以按以下顺序排查。

1. 确认taskpool.execute、SequenceRunner.execute或AsyncRunner.execute是否实际调用。

   在调用前后打印业务日志，并给任务的Promise注册then和catch。如果调用前日志已打印，但没有进入then或catch，需要继续结合Hilog或Trace确认任务是否进入TaskPool队列。

   ```ts
   function add(left: int, right: int): int {
     return left + right;
   }

   async function runTask(): Promise<void> {
     console.info("before execute task"); // before execute task
     let task: taskpool.Task = new taskpool.Task("addTask", add, 1, 2);
     try {
       let result: int = (await taskpool.execute(task)) as int;
       console.info("task result: " + result); // task result: 3
     } catch (error) {
       console.error("task failed: " + (error as Error).message); // task failed: xxx（任务执行异常时）
     }
   }
   ```

2. 确认任务对象是否被重复执行。

   普通Task、串行队列任务、异步队列任务、延时任务、周期任务和LongTask都有各自的执行约束。已经执行过的任务再次执行时，可能抛出taskpool:: task has been executed等异常。需要重复执行同一段逻辑时，应重新创建taskpool.Task对象。

3. 确认任务是否被加入不支持的执行器。

   SequenceRunner不能执行任务组任务、已执行任务、依赖任务和周期任务；AsyncRunner不能执行任务组任务、已执行任务、依赖任务、周期任务和串行队列任务。对应异常信息可参考[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)接口文档。

4. 确认任务是否被取消或等待队列丢弃。

   等待中的任务被taskpool.cancel取消后不会执行。使用AsyncRunner且设置了waitingCapacity时，如果等待队列已满，新任务进入队尾，队头等待任务会被取消，对应Promise进入catch分支。

5. 查看TaskPool运行日志或Trace。

   可结合taskpool::、Task Allocation、Task Perform、Task Perform End等关键词搜索设备日志，判断任务是否完成分配、开始执行和结束执行。日志格式与字段名称可能随版本调整，定位时应以实际日志为准。

## TaskPool任务执行慢如何排查

TaskPool任务从提交到执行耗时较长时，常见原因如下。

- 任务优先级较低。高优先级任务会优先调度，如果短时间内提交大量高优先级或默认优先级任务，低优先级任务可能延后执行。
- TaskPool工作线程被长耗时任务占满。检查前序任务是否存在同步等待、无限循环、阻塞I/O或未按预期退出的长时任务。
- 使用了SequenceRunner。串行队列会按提交顺序执行，后续任务必须等待前序任务完成。
- 使用了AsyncRunner。runningCapacity限制同一Runner内同时运行的任务数量，超过并发度的任务需要排队等待。
- 任务粒度过小或提交过密。大量细粒度任务会增加调度开销，可考虑合并批次或使用TaskGroup集中提交。

如果无法仅通过应用日志判断，应结合Trace查看任务提交、线程调度和业务函数执行耗时。

以下示例使用SequenceRunner保证同类任务按顺序执行。如果发现任务执行慢，应优先检查队列前面的任务是否耗时过长。

```ts
// ArkTS-Sta示例
function writeRecord(recordId: int): int {
  return recordId;
}

async function runInSequence(): Promise<void> {
  let runner: taskpool.SequenceRunner = new taskpool.SequenceRunner("recordWriter");
  let task1: taskpool.Task = new taskpool.Task("write-1", writeRecord, 1);
  let task2: taskpool.Task = new taskpool.Task("write-2", writeRecord, 2);

  await runner.execute(task1);
  await runner.execute(task2);
}
```

## TaskPool任务取消后为什么还在运行

taskpool.cancel不会强制中断已经运行的任务。等待中的任务被取消后不会继续执行；已经开始执行的任务需要在任务函数中主动检查取消状态并退出。

```ts
// ArkTS-Sta示例
function countUntilCanceled(max: int): int {
  let count: int = 0;
  for (let index: int = 0; index < max; index++) {
    if (index % 10000 == 0 && taskpool.Task.isCanceled()) {
      return count;
    }
    count++;
  }
  return count;
}

let runningTask: taskpool.Task | undefined = undefined;

function startTask(): void {
  let task: taskpool.Task = new taskpool.Task("count", countUntilCanceled, 100000000);
  runningTask = task;
  taskpool.execute(task).catch((error: Error) => {
    console.error("task failed: " + error.message); // task failed: xxx（任务开始前被取消或执行异常）
  });
}

function cancelTask(): void {
  if (runningTask !== undefined) {
    taskpool.cancel(runningTask!);
  }
}
```

如果任务函数从不调用taskpool.Task.isCanceled()或taskpool.Task.checkCancellation()，取消运行中任务后，任务仍会执行到函数自然结束。

## 为什么共享对象在线程间读写结果异常

ArkTS-Sta中对象默认可以跨线程共享，不会像动态ArkTS普通对象那样通过结构化克隆形成副本。因此，多个TaskPool任务或EAWorker同时读写同一份可变对象时，可能出现竞态、丢失更新或读取到中间状态。

处理方式如下：

- 只读数据：提交任务后不再修改输入对象。
- 快照语义：提交任务前显式复制数组、对象或ArrayBuffer。
- 共享可变数据：使用AsyncLock、Mutex、RWLock、原子类型或并发容器保护访问。
- UI状态对象：不要直接传入TaskPool任务中修改。后台任务返回普通数据，宿主线程再更新ArkUI状态。

以下示例使用Mutex保护共享计数器，避免多个任务同时修改同一字段。

```ts
// ArkTS-Sta示例
class SharedCounter {
  value: int = 0;
}

function increase(counter: SharedCounter, mutex: Mutex): void {
  mutex.lock();
  try {
    counter.value++;
  } finally {
    mutex.unlock();
  }
}

async function updateCounter(): Promise<void> {
  let counter: SharedCounter = new SharedCounter();
  let mutex: Mutex = new Mutex();
  await taskpool.execute(increase, counter, mutex);
  await taskpool.execute(increase, counter, mutex);
  console.info("counter: " + counter.value); // counter: 2
}
```

更多说明请参考[并发数据共享 (ArkTS-Sta)](arkts-sta-data-sharing-for-concurrency.md)和[ArkUI数据更新场景 (ArkTS-Sta)](arkts-sta-arkui-data-update.md)。

## Task.sendData没有回调或抛出异常怎么办

Task.sendData只能在TaskPool任务线程中调用，并且需要在提交线程先通过onReceiveData注册回调。

常见问题如下：

- 在普通函数、EAWorker任务或宿主线程中调用Task.sendData，会抛出异常。
- 未注册onReceiveData就调用Task.sendData，会抛出异常。
- 同一个Task多次调用onReceiveData时，后注册的回调会覆盖之前的回调。
- sendData发送的对象在ArkTS-Sta中按共享引用传递。如果发送可变对象，发送方和接收方需要自行保证并发访问安全。

```ts
// ArkTS-Sta示例
function loadWithProgress(total: int): int {
  for (let index: int = 0; index < total; index++) {
    if (index % 10 == 0) {
      taskpool.Task.sendData(index);
    }
  }
  return total;
}

async function receiveProgress(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task("loadWithProgress", loadWithProgress, 100);
  task.onReceiveData((progress: int): void => {
    console.info("progress: " + progress); // progress: 0（首次回调，后续递增10）
  });
  await taskpool.execute(task);
}
```

可参考[TaskPool任务与宿主线程通信 (ArkTS-Sta)](arkts-sta-taskpool-communicates-with-mainthread.md)。

## EAWorker提示未启动或已退出怎么办

EAWorker需要先创建实例并调用start，之后才能通过run、postTask或MessageHandler提交任务。常见异常包括：

- EAWorker:: Cannot run task when worker is not started：调用run前未调用start，或目标EAWorker已经退出。
- EAWorker:: Worker already started or quit：同一个EAWorker实例重复启动，或退出后再次启动。
- EAWorker:: Cannot stop worker before start：启动前调用join或quit。

EAWorker实例使用完毕后，应调用join或quit释放线程资源。quit会等待待处理任务结束后退出，如果当前EAWorker内有长期阻塞任务，quit也会等待较长时间。页面生命周期中释放EAWorker时，应确保任务有明确退出条件。

```ts
// ArkTS-Sta示例
function calculate(value: int): int {
  return value * 2;
}

async function runWithEAWorker(): Promise<void> {
  let worker: EAWorker = new EAWorker("calculateWorker");
  worker.start();
  try {
    let result = await worker.run<int>(calculate, 21);
    console.info("worker result: " + result.Await()); // worker result: 42
  } finally {
    await worker.join();
  }
}
```

## MessageHandler消息没有收到如何排查

MessageHandler需要关联一个已启动且存活的EAWorker。消息没有收到时，可检查以下内容：

- 创建MessageHandler时传入的目标EAWorker是否正确。
- 目标EAWorker是否已调用start，且未执行join或quit。
- concurrency.Message对象是否被重复发送。已发送的Message不能再次发送。
- 消息what标识与处理分支是否一致。
- 回调内是否抛出异常。建议在回调中捕获异常并打印错误日志。

如果需要从EAWorker回到主线程执行函数，可使用EAWorker.postToMain；如果需要面向指定EAWorker发送消息，使用MessageHandler和Message。

```ts
// ArkTS-Sta示例
const REQUEST_WORK: int = 1;
const RESPONSE_DONE: int = 2;

async function sendMessageToWorker(): Promise<void> {
  let worker: EAWorker = new EAWorker("messageWorker");
  worker.start();

  let done = new Promise<void>((resolve, reject) => {
    let mainHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
      if (msg.getWhat() == RESPONSE_DONE) {
        console.info("main receive: " + (msg.getObject() as string)); // main receive: done: hello
        resolve(undefined);
      }
    }, EAWorker.main());

    let workerHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {
      if (msg.getWhat() == REQUEST_WORK) {
        let data = msg.getObject() as string;
        let response = new concurrency.Message(RESPONSE_DONE, "done: " + data, mainHandler);
        response.sendToTarget();
      }
    }, worker);

    let message = new concurrency.Message(REQUEST_WORK, "hello", workerHandler);
    if (!workerHandler.sendMessage(message)) {
      reject(new Error("send message failed"));
    }
  });

  try {
    await done;
  } finally {
    worker.quit();
  }
}
```

## TaskPool任务中能否调用EAWorker.current

不能。静态源码中EAWorker.current()如果在TaskPool线程内调用，会抛出EAWorker:: Cannot get current worker in taskpool异常。

TaskPool任务不绑定固定EAWorker线程，运行时会将任务调度到任务池工作线程。需要固定线程上下文、长期保存线程内状态或获取当前EAWorker时，应使用EAWorker，而不是TaskPool。

```ts
// ArkTS-Sta示例
function taskpoolWork(value: int): int {
  // TaskPool任务不依赖固定EAWorker线程。
  return value * 2;
}

async function runWithoutCurrentWorker(): Promise<void> {
  let result: int = (await taskpool.execute(taskpoolWork, 10)) as int;
  console.info("taskpool result: " + result); // taskpool result: 20
}
```

## 动态ArkTS的Sendable和Transferable写法能否直接迁移

不能直接迁移。ArkTS-Sta不需要@Sendable表达共享对象，也不通过Transferable转移ArrayBuffer所有权。静态场景中应根据业务语义选择以下方式：

- 需要共享：直接传递对象引用，并用锁、原子类型或并发容器保护可变状态。
- 需要互不影响：显式复制对象、数组或ArrayBuffer。
- 需要Native共享对象：使用ANI绑定Native句柄，并在C++侧使用互斥锁等同步机制保护共享资源。
- 需要表达所有权移交：通过业务协议约定移交后原线程不再访问，而不是依赖运行时自动转移所有权。

以下示例通过显式拷贝表达快照语义，避免后台任务修改宿主线程仍在使用的数组。

```ts
// ArkTS-Sta示例
function sum(values: Array<int>): int {
  let total: int = 0;
  for (let index: int = 0; index < values.length; index++) {
    total += values[index];
  }
  return total;
}

async function submitSnapshot(): Promise<void> {
  let source: Array<int> = [1, 2, 3];
  let snapshot: Array<int> = Array.from(source);
  let result: int = (await taskpool.execute(sum, snapshot)) as int;
  console.info("sum: " + result); // sum: 6
}
```

相关实践可参考[Native资源显式移交场景 (ArkTS-Sta)](arkts-sta-native-resource-transfer.md)和[Native共享资源多线程操作场景 (ArkTS-Sta)](arkts-sta-native-shared-resource.md)。

## 静态并发问题排查建议

- 所有taskpool.execute、EAWorker.run、SequenceRunner.execute和AsyncRunner.execute调用都建议注册catch或使用try/catch处理异常。
- 对有时序要求的任务，记录提交时间、开始执行时间、结束时间和任务ID，方便结合日志定位。
- 对共享可变对象，先判断业务需要共享、快照还是所有权移交，再选择同步机制或复制策略。
- 对EAWorker常驻任务，明确启动、退出和异常处理路径，避免线程泄漏。
- 对Native并发问题，优先结合实际设备日志、崩溃栈和Trace定位，文档中的日志关键词只能作为初始搜索线索。
