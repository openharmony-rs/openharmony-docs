# 多线程并发概述 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

多线程并发是指在一个应用中使用多个线程并行或交替执行任务，以提升CPU利用率，避免耗时操作阻塞当前线程。ArkTS-Sta多线程并发基于任务调度能力实现，运行时将[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)任务调度到工作线程执行，也支持通过[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)创建独占工作线程。

ArkTS-Sta提供TaskPool和EAWorker两类多线程并发能力。TaskPool面向短时、可拆分、可批量调度的后台任务，工作线程由运行时统一管理；EAWorker面向独占线程、长期驻留或固定线程语义的场景，开发者需要显式启动和退出EAWorker。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - ArkTS-Sta采用共享内存模型，跨线程传递对象时不需要Structured Clone，也不需要使用Sendable对象表达共享语义。

## 多线程并发模型

ArkTS-Sta与ArkTS-Dyn的多线程模型存在差异。ArkTS-Dyn的TaskPool和Worker通常基于Actor模型描述，不同线程间通过序列化、转移或共享对象进行通信。ArkTS-Sta中，多个工作线程共享同一个运行时上下文，对象、函数、ArrayBuffer和容器等数据可以直接跨线程共享。

共享内存模型降低了跨线程传递成本，也要求开发者处理并发访问安全。只读数据可以直接共享；多个线程同时读写同一份可变数据时，应使用锁、原子类型或并发容器。

## 能力选择

| 场景 | 推荐能力 | 说明 |
| -------- | -------- | -------- |
| 短时后台任务 | TaskPool | 由运行时管理任务队列和工作线程，适合CPU密集型计算、批量数据处理等任务。 |
| 可拆分并行任务 | TaskPool TaskGroup | 将一组任务提交到TaskPool并发执行，通过Promise获取结果数组。 |
| 有序执行任务 | TaskPool SequenceRunner | 按提交顺序串行执行任务，适合需要严格顺序的后台逻辑。 |
| 限制同类任务并发度 | TaskPool AsyncRunner | 控制任务并发数量和等待队列容量，适合流量削峰。 |
| 固定线程或长期驻留 | EAWorker | 创建独占工作线程，适合长期运行、独立事件循环或固定线程上下文。 |
| 主线程与独占线程协同 | EAWorker和MessageHandler | 通过run、postToMain或消息机制在线程间协作。 |

## TaskPool

TaskPool用于将函数或Task对象提交到运行时管理的任务池执行。任务完成后，调用方通过Promise获取执行结果。TaskPool适合以下场景：

- CPU密集型计算，例如图片处理、数据压缩、加解密、算法计算。
- 可以拆分为多个独立子任务的批量处理。
- 不需要固定线程，只需要将任务调度到后台执行。
- 需要任务优先级、任务组、取消、延迟执行、周期执行、串行队列或并发度控制。

ArkTS-Sta中使用TaskPool时不需要从@kit.ArkTS导入taskpool，普通函数可以作为任务函数，不需要@Concurrent装饰。

```ts
// ArkTS-Sta示例
function calculate(value: int): int {
  return value * value;
}

async function runInTaskPool(): Promise<void> {
  let result: Any = await taskpool.execute(calculate, 10);
  console.info("result: " + result); // result: 100
}
```

TaskPool不保证任务运行在固定工作线程上。需要固定线程、长期驻留或独立事件循环时，应使用EAWorker。

更多TaskPool用法请参见[TaskPool简介 (ArkTS-Sta)](arkts-sta-taskpool-introduction.md)。

## EAWorker

EAWorker用于创建独占工作线程，并在该线程上执行任务。EAWorker适合以下场景：

- 任务需要固定线程上下文。
- 任务需要长期驻留或维护独立事件循环。
- 需要显式管理线程生命周期。
- 需要创建支持ArkTS-Dyn互操作的独占线程。

EAWorker创建后需要调用start启动，使用完成后需要调用join或quit退出并释放线程资源。

```ts
// ArkTS-Sta示例
function work(value: int): int {
  return value + 1;
}

async function runInEAWorker(): Promise<void> {
  let worker = new EAWorker("background");
  worker.start();

  let result = await worker.run<int>(work, 1) as Job<int>;
  console.info("result: " + result.Await()); // result: 2

  worker.join();
}
```

更多EAWorker用法请参见[EAWorker简介 (ArkTS-Sta)](eaworker-introduction.md)。

## 线程间通信和数据共享

ArkTS-Sta多线程之间可以直接共享对象。以下示例使用ConcurrentQueue实现生产者消费者模型。生产者和消费者都由TaskPool调度到后台线程执行，队列负责线程安全的数据传递。

```ts
// ArkTS-Sta示例
async function produce(queue: containers.stackless.ConcurrentQueue<int>): Promise<void> {
  for (let i = 0; i < 5; i++) {
    await queue.push(i);
  }
}

async function consume(queue: containers.stackless.ConcurrentQueue<int>): Promise<int> {
  let sum: int = 0;
  for (let i = 0; i < 5; i++) {
    let value: int = await queue.pop();
    sum += value;
  }
  return sum;
}

async function runProducerConsumer(): Promise<void> {
  let queue: containers.stackless.ConcurrentQueue<int> =
    new containers.stackless.LinkedConcurrentQueue<int>(5);

  let producer: Promise<Any> = taskpool.execute(produce, queue);
  let consumer: Promise<Any> = taskpool.execute(consume, queue);

  await producer;
  let result: int = (await consumer) as int;
  console.info("sum: " + result); // sum: 10
}
```

如果多个线程访问普通对象或普通容器，需要根据访问模式选择同步策略：

- 只读共享数据通常可以直接跨线程读取。
- 共享可变对象需要使用AsyncLock、Mutex或RWLock保护临界区。
- 单个共享状态可使用AtomicInt、AtomicBoolean等原子类型。
- 多线程读写Map、Set、Queue时，优先使用ConcurrentHashMap、ConcurrentSet、ConcurrentQueue等并发容器。
- 每个线程需要独立状态时，可使用WorkerLocal。

更多说明请参见[线程间通信概述 (ArkTS-Sta)](arkts-sta-interthread-communication-overview.md)和[并发数据共享 (ArkTS-Sta)](arkts-sta-data-sharing-for-concurrency.md)。

## 与ArkTS-Dyn多线程并发的主要差异

| 差异点 | ArkTS-Sta |
| -------- | -------- |
| 并发模型 | 基于任务调度能力和共享内存模型，多个任务可调度到多个工作线程执行。 |
| TaskPool任务函数 | 普通函数可作为任务函数，不需要@Concurrent装饰。 |
| 跨线程对象 | ArkTS-Sta对象默认可跨线程共享，不需要@Sendable装饰。 |
| 数据传递 | 不提供TaskPool的setCloneList和setTransferList接口，需要拷贝语义时应显式创建副本。 |
| Worker能力 | 使用EAWorker表示独占工作线程，不使用ArkTS-Dyn Worker文件路径式创建方式。 |
| 同步责任 | 共享可变数据需要开发者自行使用同步原语或并发容器保证线程安全。 |

## 使用建议

- 只需要后台执行短时任务时，优先使用TaskPool。
- 任务需要固定线程、长期运行或独立事件循环时，使用EAWorker。
- 不要在TaskPool任务中执行无限期阻塞逻辑，以免长期占用工作线程。
- 共享可变数据前先明确同步策略，不要把共享内存等同于线程安全。
- 可以拆分的批量任务优先使用TaskGroup；需要顺序的任务使用SequenceRunner；需要限制并发数量的任务使用AsyncRunner。
- 使用EAWorker后应在不再需要时调用join或quit释放线程资源。
