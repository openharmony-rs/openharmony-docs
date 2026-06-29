# TaskPool和EAWorker的对比 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)和[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)都为ArkTS-Sta应用提供多线程并发能力，用于将耗时计算、后台数据处理等逻辑放到非当前线程执行，避免阻塞当前线程。

TaskPool偏向任务维度，开发者提交函数、Task或TaskGroup后，由运行时选择合适的工作线程执行，线程生命周期由TaskPool管理。EAWorker偏向线程维度，开发者创建独占线程，显式启动、提交任务并释放线程资源。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - ArkTS-Sta不再使用ArkTS-Dyn中的Worker API。需要独占线程时，使用[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)。
> - TaskPool接口说明请参见[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)，EAWorker接口说明请参见[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)。

## 实现特点对比

**表1** TaskPool和EAWorker的实现特点对比

| 实现 | TaskPool | EAWorker |
| -------- | -------- | -------- |
| 并发模型 | 任务池模型。开发者提交任务，由运行时调度到TaskPool工作线程执行。 | 独占线程模型。开发者创建EAWorker实例，该实例绑定一个独占工作线程。 |
| 内存模型 | ArkTS-Sta共享内存模型，对象可跨线程共享。 | ArkTS-Sta共享内存模型，对象可跨线程共享。创建支持interop的EAWorker时，会为ArkTS-Dyn互操作创建对应运行环境。 |
| 参数传递 | 直接向任务函数传参，无需使用结构化克隆或TransferList。 | 通过run、postTask、postToMain或消息机制提交任务和参数。静态对象默认共享，使用interop能力时会涉及ArkTS-Dyn互操作处理。 |
| 方法调用 | 直接将普通函数传给taskpool.execute，或封装为taskpool.Task后执行。ArkTS-Sta不需要@Concurrent装饰器。 | 创建EAWorker实例并调用start后，通过run或postTask向该EAWorker提交任务，也可通过[MessageHandler](../reference/apis-arkts/message_handler.md)和[Message](../reference/apis-arkts/message.md)进行消息通信。 |
| 返回值 | taskpool.execute、executeDelayed、TaskGroup、SequenceRunner、AsyncRunner等接口通过Promise异步返回执行结果。 | run返回异步任务结果，postTask只提交无返回任务；需要跨线程返回复杂交互结果时，可结合消息机制或异步结果处理。 |
| 生命周期 | TaskPool自行管理工作线程生命周期，开发者无需创建和释放线程。 | 开发者需要显式调用start启动EAWorker，使用完毕后调用join或quit释放线程资源。 |
| 线程复用 | 支持。TaskPool内部复用工作线程。 | 支持。同一个EAWorker实例启动后，可复用其独占线程执行多个任务。 |
| 指定执行线程 | 不支持。任务会由TaskPool调度到合适的工作线程。 | 支持。提交到同一个EAWorker实例的任务会在该实例绑定的独占线程中执行。 |
| 优先级 | 支持任务优先级，默认优先级为taskpool.Priority.MEDIUM。 | 支持线程优先级，默认优先级为WorkerPriority.PRIORITY_HIGH。 |
| 任务取消 | 支持取消等待中或执行中的任务。执行中的任务不会被强制中断，任务函数可通过taskpool.Task.isCanceled()或taskpool.Task.checkCancellation()感知取消状态。 | 不提供与TaskPool等价的任务取消接口。开发者通常通过自定义共享状态、消息或业务协议控制任务退出。 |
| 延时任务 | 支持executeDelayed。 | 不提供TaskPool式延时执行接口。可在EAWorker任务中使用定时器或业务调度逻辑实现。 |
| 周期任务 | 支持executePeriodically。 | 不提供TaskPool式周期任务接口。可在EAWorker事件循环或任务逻辑中自行调度。 |
| 任务依赖 | 支持Task.addDependency和removeDependency。 | 不提供TaskPool式任务依赖接口。需要开发者自行编排任务顺序。 |
| 任务组 | 支持TaskGroup。 | 不提供TaskGroup。 |
| 串行队列 | 支持SequenceRunner。 | 同一个EAWorker可通过业务代码按顺序提交和处理任务，但不提供TaskPool的SequenceRunner接口。 |
| 并发度控制 | 支持AsyncRunner限制同类任务并发度和等待队列容量。 | 不提供AsyncRunner。一个EAWorker实例对应一个独占线程；需要多个独占线程时需创建多个EAWorker实例并自行调度。 |
| 长时间任务 | 支持LongTask。ArkTS-Sta中LongTask由运行时调度执行，任务结束后资源自动回收，terminateTask为空实现。 | 适合需要长期保留线程上下文、持续处理任务或事件循环的场景。开发者负责释放线程资源。 |
| 异常处理 | 任务执行异常会通过返回的Promise进入失败分支，也可注册任务执行失败监听。 | 支持设置未捕获异常处理器，也可通过异步结果或业务消息处理异常。 |

## 适用场景对比

TaskPool和EAWorker均适用于多线程并发开发，但推荐优先根据任务与线程生命周期关系选择。

TaskPool适合任务相对独立、数量较多、执行点分散、需要由运行时统一调度的场景。开发者只需要描述任务本身，不需要关心工作线程创建、复用和回收。

EAWorker适合需要独占线程语义的场景，例如需要长期保留线程上下文、需要固定线程执行一组关联逻辑、需要显式管理线程生命周期、需要和ArkTS-Dyn互操作运行环境配合，或需要基于事件循环持续处理消息的场景。

常见开发场景及适用说明如下：

- 大量独立计算任务：例如批量图片处理、批量数据计算、多个业务模块并发初始化等，推荐使用TaskPool。
- 需要任务优先级、任务取消、任务依赖、任务组、延时任务、周期任务、串行队列或并发度控制：推荐使用TaskPool。
- 需要固定线程上下文：例如线程内创建了需要复用的上下文对象或句柄，后续任务必须在同一线程中访问，推荐使用EAWorker。
- 需要长期运行或事件循环：例如一个后台线程持续接收消息、处理状态并按业务协议返回结果，推荐使用EAWorker。
- 需要和ArkTS-Dyn代码互操作：可创建支持interop的EAWorker，在独占线程中执行相关互操作逻辑。
- 不希望手动管理线程生命周期：推荐使用TaskPool。EAWorker必须在使用完毕后调用join或quit释放资源。

## TaskPool使用示例

TaskPool可以直接执行普通函数，也可以执行封装后的Task。

```ts
// ArkTS-Sta示例
function calculate(value: int): int {
  return value * 2;
}

async function runInTaskPool(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task(calculate, 21);
  let result: Any = await taskpool.execute(task, taskpool.Priority.HIGH);
  console.info("taskpool result: " + result); // taskpool result: 42
}
```

需要同时执行多个任务时，可以使用TaskGroup。

```ts
// ArkTS-Sta示例
function parseItem(value: int): int {
  return value + 1;
}

async function runTaskGroup(): Promise<void> {
  let group: taskpool.TaskGroup = new taskpool.TaskGroup();
  group.addTask(parseItem, 1);
  group.addTask(parseItem, 2);
  group.addTask(parseItem, 3);

  let results: Array<Any> = await taskpool.execute(group);
  console.info("result count: " + results.length); // result count: 3
}
```

## EAWorker使用示例

EAWorker需要先创建实例并调用start启动，之后通过run提交任务。使用完成后，需要调用join或quit释放线程资源。

```ts
// ArkTS-Sta示例
function calculate(value: int): int {
  return value * 2;
}

async function runInEAWorker(): Promise<void> {
  let worker: EAWorker = new EAWorker("calculateWorker");
  worker.start();

  try {
    let result = await worker.run<int>(calculate, 21) as Job<int> ;
    console.info("EAWorker result: " + result.Await()); // EAWorker result: 42
  } finally {
    await worker.join();
  }
}
```

需要向主线程提交任务时，可以使用EAWorker.postToMain。

```ts
// ArkTS-Sta示例
function runWorkerTask(): void {
  let job = EAWorker.postToMain<int>((left: int, right: int): int => {
    return left + right;
  }, 1, 2);

  let result = job.Await();
  console.info("Result: ", result); // Result: 3
}

async function postToMainFromEAWorker(): Promise<void> {
  let worker: EAWorker = new EAWorker("postWorker");
  worker.start();

  try {
    await worker.run<void>(runWorkerTask);
  } finally {
    await worker.join();
  }
}
```

## 选择建议

- 优先使用TaskPool处理独立、短时、数量多、需要统一调度的任务。
- 需要取消、延时、周期、任务组、依赖、串行队列或并发度控制时，使用TaskPool。
- 需要固定线程、长期运行、保留线程上下文或处理事件循环时，使用EAWorker。
- 使用EAWorker时，应明确线程释放时机，并在任务完成后调用join或quit。
- TaskPool和EAWorker都处于ArkTS-Sta共享内存模型下。跨线程读写共享对象时，应使用锁、并发容器或原子操作保证并发安全。
