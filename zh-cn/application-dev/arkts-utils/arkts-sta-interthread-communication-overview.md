# 线程间通信概述 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

线程间通信指的是多个并发线程之间的数据交换、任务通知和状态同步。ArkTS-Sta采用共享内存模型，函数、对象或ArrayBuffer等数据默认可以跨线程共享，不再以ArkTS-Dyn中的Actor内存隔离、Structured Clone、Sendable对象或SharedArrayBuffer作为主要通信方式。

ArkTS-Sta线程间通信通常由以下几类能力组成：

- 通过共享对象直接传递数据。
- 通过[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)提交任务并获取返回结果，或使用Task.sendData向提交线程发送中间数据。
- 通过[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)的run、postToMain、MessageHandler和Message在指定线程间投递任务或消息。
- 通过并发容器、锁、原子操作和WorkerLocal管理共享状态和线程本地状态。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - ArkTS-Sta中taskpool、EAWorker、AsyncLock等并发能力为静态标准库能力，不需要从@kit.ArkTS导入。
> - ArkTS-Sta对象默认可共享，但“可共享”不等于“并发读写安全”。多个线程同时读写同一对象时，开发者需要使用同步机制保证数据一致性。

## 与ArkTS-Dyn通信模型的差异

ArkTS-Dyn基于Actor内存隔离模型，TaskPool和Worker跨线程传递普通对象时通常需要序列化和反序列化；ArrayBuffer、SharedArrayBuffer和Sendable对象分别对应转移、共享和引用传递等不同语义。

ArkTS-Sta采用共享内存模型，主要差异如下：

| 对比项 | ArkTS-Dyn | ArkTS-Sta |
| -------- | -------- | -------- |
| 内存模型 | 并发实例之间内存隔离。 | 多线程共享同一静态运行时内存模型，对象默认可跨线程共享。 |
| 普通对象传递 | 通常通过Structured Clone进行序列化和反序列化。 | 默认共享对象引用，不需要Structured Clone。 |
| Sendable | 需要使用Sendable表达可共享对象。 | 不需要@Sendable装饰器，也不需要实现Sendable相关接口。 |
| 并发函数 | TaskPool任务函数需要@Concurrent。 | 普通函数可作为TaskPool任务函数，不需要@Concurrent。 |
| ArrayBuffer | 可涉及转移、克隆或SharedArrayBuffer共享。 | ArrayBuffer默认共享，不需要setTransferList、setCloneList或SharedArrayBuffer。 |
| Worker | 使用Worker API和消息通信。 | 使用EAWorker作为独占线程任务执行器；线程间既可共享对象，也可使用消息机制。 |

## 共享对象通信

ArkTS-Sta中，跨线程传递对象时默认共享对象本身。任务函数可以直接接收对象参数并读取其内容。

```ts
// ArkTS-Sta示例
class Config {
  name: string = "default";
  version: int = 1;
}

function readConfig(config: Config): string {
  return config.name + ":" + config.version;
}

async function shareObject(): Promise<void> {
  let config: Config = new Config();
  let result: Any = await taskpool.execute(readConfig, config);
  console.info("config: " + result); // config: default:1
}
```

如果多个线程会修改同一个共享对象，需要使用同步机制。下面示例使用[AsyncLock (异步锁)](../reference/apis-arkts/arkts-sta-asynclock.md)保护共享计数器。

```ts
// ArkTS-Sta示例
class Counter {
  value: int = 0;
}

async function increase(counter: Counter, lockName: string): Promise<void> {
  let lock: AsyncLock = AsyncLock.request(lockName);
  await lock.lockAsync<void>(() => {
    counter.value++;
  });
}

async function updateCounter(): Promise<void> {
  let counter: Counter = new Counter();
  let lockName: string = "counterLock";

  let promise1: Promise<Any> = taskpool.execute(increase, counter, lockName);
  let promise2: Promise<Any> = taskpool.execute(increase, counter, lockName);
  await Promise.all<Any>([promise1, promise2]);
  console.info("counter: " + counter.value); // counter: 2
}
```

除AsyncLock外，也可以根据场景使用[Mutex (互斥锁)](../reference/apis-arkts/arkts-sta-mutex.md)、[RWLock (读写锁)](../reference/apis-arkts/arkts-sta-rwlock.md)、[Atomics模块描述](../reference/apis-arkts/arkts-sta-atomics-overview.md)或并发容器。

## TaskPool通信

TaskPool用于提交独立任务并异步获取执行结果。任务返回值会通过Promise返回给提交方。

```ts
// ArkTS-Sta示例
function calculate(value: int): int {
  return value * 2;
}

async function taskpoolResult(): Promise<void> {
  let result: Any = await taskpool.execute(calculate, 21);
  console.info("result: " + result); // result: 42
}
```

如果任务执行过程中需要向提交线程发送中间数据，可以使用[Task.sendData](../reference/apis-arkts/arkts-sta-taskpool.md#senddata)和[onReceiveData](../reference/apis-arkts/arkts-sta-taskpool.md#onreceivedata)。

```ts
// ArkTS-Sta示例
function doWork(value: int): int {
  taskpool.Task.sendData("start");
  let result = value * 2;
  taskpool.Task.sendData("finish");
  return result;
}

async function taskpoolProgress(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task(doWork, 10);
  task.onReceiveData((message: string) => {
    console.info("progress: " + message); // progress: start（第一次回调）；progress: finish（第二次回调）
  });

  let result: Any = await taskpool.execute(task);
  console.info("result: " + result); // result: 20
}
```

EAWorker用于创建独占线程。开发者需要显式调用start启动线程，并在使用完毕后调用join或quit释放资源。

可以通过[run](../reference/apis-arkts/eaworker_managed.md#run)向指定EAWorker提交任务，并通过返回的Promise获取结果。

```ts
// ArkTS-Sta示例
function work(value: int): int {
  return value + 1;
}

async function eaworkerRun(): Promise<void> {
  let worker: EAWorker = new EAWorker("worker");
  worker.start();

  try {
    let result = await worker.run<int>(work, 1) as Job<int>;
    console.info("worker result: " + result.Await()); // worker result: 2
  } finally {
    await worker.join();
  }
}
```

EAWorker内部任务需要回到主线程执行逻辑时，可以使用[EAWorker.postToMain](../reference/apis-arkts/eaworker_managed.md#posttomain)。

```ts
// ArkTS-Sta示例
function runOnWorker(): void {
  let promise = EAWorker.postToMain<int>((left: int, right: int): int => {
    return left + right;
  }, 1, 2);
  
  console.info("main result: " + result.Await()); // main result: 3

}

async function postToMain(): Promise<void> {
  let worker: EAWorker = new EAWorker("postToMainWorker");
  worker.start();

  try {
    await worker.run<void>(runOnWorker);
  } finally {
    await worker.join();
  }
}
```

## EAWorker消息机制

对于需要按消息类型分发、查询或移除待处理消息的场景，可以使用[MessageHandler](../reference/apis-arkts/message_handler.md)和[Message](../reference/apis-arkts/message.md)。MessageHandler定义消息处理逻辑，Message携带消息标识符、数据对象或回调函数。

```ts
// ArkTS-Sta示例
async function sendMessageToWorker(): Promise<void> {
  let worker: EAWorker = new EAWorker("messageWorker");
  worker.start();

  try {
    let handler = new concurrency.MessageHandler((msg: concurrency.Message) => {
      let message = msg.getObject() as string;
      console.info("receive: " + message); // receive: hello
    }, worker);

    let msg = new concurrency.Message(1, "hello", handler);
    let sent: boolean = handler.sendMessage(msg);
    if (!sent) {
      console.error("send message failed"); // send message failed
    }

    await worker.run<void>(() => {});
  } finally {
    await worker.join();
  }
}
```

使用消息机制时需要注意：

- MessageHandler需要关联一个已启动的EAWorker。目标EAWorker未启动或已停止时，发送消息会失败。
- 同一个Message只能发送一次，重复调用sendToTarget会抛出异常。
- hasMessages、hasCallbacks、removeMessages和removeCallbacks用于查询或移除尚未执行的消息。
- Message携带的对象在ArkTS-Sta中仍是共享对象，消息传递本身不会自动提供并发读写保护。

## 并发容器和同步能力

ArkTS-Sta提供多种能力用于在线程间安全共享状态：

- [ConcurrentQueue](../reference/apis-arkts/arkts-sta-concurrentqueue.md)：线程安全队列，适合生产者/消费者、任务队列和流量控制场景。
- [线程安全容器使用指导 (ArkTS-Sta)](arkts-sta-concurrent-containers-guide.md)：适合多线程并发读写键值数据和维护唯一元素集合。
- [锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)](arkts-sta-locks-guide.md)：适合保护同步临界区、读多写少状态或异步共享资源。
- [原子类型使用指导 (ArkTS-Sta)](arkts-sta-atomics-guide.md)：适合对单个共享值或对象引用执行原子操作。
- [WorkerLocal线程本地状态使用指导 (ArkTS-Sta)](arkts-sta-workerlocal-guide.md)：适合维护每个工作线程独立的数据副本，避免共享状态带来的同步成本。

## 使用建议

- 只读数据或不可变数据可以直接共享。
- 需要跨线程修改共享对象时，应明确同步策略，避免数据竞争。
- 任务结果返回优先使用TaskPool或EAWorker的异步返回值。
- TaskPool任务执行过程中需要发送进度时，使用Task.sendData和onReceiveData。
- EAWorker之间需要基于事件或消息类型通信时，使用MessageHandler和Message。
- 需要高频数据传递或生产者/消费者模型时，优先考虑ConcurrentQueue。
- 需要每个线程持有独立状态时，使用WorkerLocal，而不是共享全局变量。

## 线程间通信场景

- [使用TaskPool执行独立的耗时任务 (ArkTS-Sta)](arkts-sta-independent-time-consuming-task.md)
- [TaskPool任务与宿主线程通信 (ArkTS-Sta)](arkts-sta-taskpool-communicates-with-mainthread.md)
- [EAWorker和宿主线程的即时消息通信 (ArkTS-Sta)](arkts-sta-worker-communicates-with-mainthread.md)
- [EAWorker同步调用宿主线程的接口 (ArkTS-Sta)](arkts-sta-worker-invoke-mainthread-interface.md)
- [EAWorker间共享对象通信 (ArkTS-Sta)](arkts-sta-eaworker-shared-object.md)
- [多级EAWorker间高性能消息通信 (ArkTS-Sta)](arkts-sta-multi-level-eaworker-communication.md)
