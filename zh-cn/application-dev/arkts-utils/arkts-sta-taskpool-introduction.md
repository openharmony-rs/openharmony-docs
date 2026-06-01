# TaskPool简介 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)为ArkTS-Sta应用提供多线程任务执行能力。开发者可以将函数或任务对象提交到TaskPool内部任务队列，由运行时调度到工作线程执行，并通过Promise获取执行结果。TaskPool负责管理工作线程生命周期，开发者无需自行创建、复用或销毁线程。

TaskPool适用于CPU密集型计算、可并行拆分的业务逻辑、后台数据处理等场景。对于需要固定线程、独立事件循环或长期驻留的场景，可结合[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)使用。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - TaskPool接口的完整说明请参见[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)。

## TaskPool运作机制

TaskPool支持开发者在当前线程提交任务到任务队列，运行时根据任务优先级和工作线程状态选择合适的工作线程执行任务。任务执行完成后，TaskPool通过Promise将结果返回给提交方。

TaskPool内部维护不同优先级的任务队列，支持USER_INTERACTION、DEADLINE_REQUEST、HIGH、MEDIUM、LOW和IDLE优先级。其中MEDIUM为默认优先级。运行时会优先调度高优先级任务，USER_INTERACTION和DEADLINE_REQUEST当前按高优先级队列处理。IDLE优先级适合后台低优先级任务。

工作线程由TaskPool内部管理。任务提交后，TaskPool会根据队列负载、空闲工作线程数量和运行时限制进行调度。工作线程空闲时可复用；任务负载变化时，运行时可按需管理工作线程数量。开发者不应依赖固定工作线程数量或指定某个任务必须运行在某个线程上。

## TaskPool注意事项

- ArkTS-Sta中taskpool为内置能力，不需要从@kit.ArkTS导入。
- ArkTS-Sta函数和对象支持共享，不需要使用@Concurrent装饰任务函数，也不需要使用@Sendable装饰跨线程共享对象。
- ArkTS-Sta内存默认共享，不需要通过setTransferList或setCloneList设置ArrayBuffer的跨线程传递方式。
- TaskPool任务在工作线程中执行。任务函数访问共享对象时，开发者需要自行保证并发读写安全，可使用异步锁、并发容器或原子操作。
- TaskPool不支持指定任务运行在哪个工作线程。需要独占线程或固定事件循环时，建议使用[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)。
- 不建议在任务函数中执行无限期阻塞操作。长时间阻塞会占用工作线程，影响其他任务调度。
- 普通Task、TaskGroup、延时任务、周期任务、串行队列任务和异步队列任务存在不同的执行限制，具体请参见[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)。
- LongTask在ArkTS-Sta中由运行时调度执行，任务结束后资源自动回收。[terminateTask](../reference/apis-arkts/arkts-sta-taskpool.md#taskpoolterminatetask)为空实现，仅保留兼容性，通常不需要调用。

## 基本使用

可以直接将函数提交给taskpool.execute，也可以先构造taskpool.Task对象再提交执行。taskpool.execute返回Promise，异步返回任务函数的执行结果。

```ts
// ArkTS-Sta示例
function add(left: int, right: int): int {
  return left + right;
}

async function executeTask(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task(add, 1, 2);
  let result: Any = await taskpool.execute(task);
  console.info("task result: ", result); // task result: 3

  let directResult: Any = await taskpool.execute(add, 3, 4);
  console.info("direct result: ", directResult); // direct result: 7
}
```

提交任务时可以指定优先级。

```ts
// ArkTS-Sta示例
function printArgs(args: string): string {
  return args;
}

async function executeWithPriority(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task(printArgs, "high priority task");
  let result: Any = await taskpool.execute(task, taskpool.Priority.HIGH);
  console.info("result: " + result); // result: high priority task
}
```

任务函数可以返回普通值，也可以返回Promise。任务函数返回Promise时，TaskPool会等待该Promise完成后再返回最终结果。

```ts
// ArkTS-Sta示例
function asyncAdd(left: int, right: int): Promise<int> {
  return new Promise<int>((resolve) => {
    setTimeout(() => {
      resolve(left + right);
    }, 1000);
  });
}

async function executeAsyncTask(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task(asyncAdd, 1, 2);
  let result: Any = await taskpool.execute(task);
  console.info("async result: " + result); // async result: 3
}
```

## 任务组

TaskGroup用于组织一组任务。提交TaskGroup后，组内任务会被加入TaskPool执行，所有任务执行完成后，通过返回的Promise获取结果数组。

```ts
// ArkTS-Sta示例
function multiply(value: int): int {
  return value * 2;
}

async function executeTaskGroup(): Promise<void> {
  let group: taskpool.TaskGroup = new taskpool.TaskGroup();
  group.addTask(multiply, 1);
  group.addTask(multiply, 2);
  group.addTask(multiply, 3);

  let results: Array<Any> = await taskpool.execute(group);
  console.info("group result count: " + results.length); // group result count: 3
}
```

TaskGroup不支持添加LongTask、已执行任务、周期任务、串行队列任务或存在依赖关系的任务。任务组本身也不支持重复执行。

## 任务取消

TaskPool支持取消等待中或执行中的任务。等待中的任务被取消后不会继续执行；已经开始执行的任务不会被强制中断，任务函数可以通过taskpool.Task.isCanceled()或taskpool.Task.checkCancellation()感知取消状态并自行结束。

```ts
// ArkTS-Sta示例
function calculate(value: int): int {
  for (let i = 0; i < 1000000; i++) {
    if (taskpool.Task.isCanceled()) {
      return -1;
    }
  }
  return value;
}

function cancelTask(): void {
  let task: taskpool.Task = new taskpool.Task(calculate, 100);
  taskpool.execute(task).then((result: Any) => {
    console.info("result: " + result); // result: 100（未被取消时）；result: -1（被取消时）
  }).catch((error: Error) => {
    console.error("task failed: " + error.message); // task failed: xxx（任务执行异常或取消异常）
  });

  taskpool.cancel(task);
}
```

取消执行中的任务不会直接抛出用于获取任务结果的cancel error。开发者应通过then获取正常返回值，通过catch获取异常，并在任务函数中主动检查取消状态。

## 延时任务和周期任务

executeDelayed用于延时执行任务，延时时间单位为ms。延时任务不能是任务组任务、串行队列任务、周期任务或已执行任务。

```ts
// ArkTS-Sta示例
function delayedWork(): string {
  return "done";
}

function executeDelayedTask(): void {
  let task: taskpool.Task = new taskpool.Task(delayedWork);
  taskpool.executeDelayed(1000, task).then((result: Any) => {
    console.info("delayed result: " + result); // delayed result: done
  });
}
```

executePeriodically用于周期执行任务。周期任务不能拥有依赖关系，不能是任务组任务、串行队列任务或已执行任务。周期任务可通过taskpool.cancel取消。

```ts
// ArkTS-Sta示例
function report(): void {
  taskpool.Task.sendData("tick");
}

function executePeriodTask(): void {
  let task: taskpool.Task = new taskpool.Task(report);
  task.onReceiveData((message: string) => {
    console.info("receive: " + message); // receive: tick
  });
  taskpool.executePeriodically(1000, task);
}
```

## 串行队列和异步队列

SequenceRunner用于按提交顺序串行执行任务。适用于多个任务需要严格保持执行顺序的场景。

```ts
// ArkTS-Sta示例
function work(value: int): int {
  return value;
}

async function executeInSequence(): Promise<void> {
  let runner: taskpool.SequenceRunner = new taskpool.SequenceRunner();
  let task1: taskpool.Task = new taskpool.Task(work, 1);
  let task2: taskpool.Task = new taskpool.Task(work, 2);

  await runner.execute(task1);
  await runner.execute(task2);
}
```

AsyncRunner用于限制同一类任务的并发度，并可配置等待队列容量。适用于需要控制并发数量或做流量削峰的场景。

```ts
// ArkTS-Sta示例
function request(index: int): int {
  return index;
}

async function executeWithAsyncRunner(): Promise<void> {
  let runner: taskpool.AsyncRunner = new taskpool.AsyncRunner(2, 10);
  let task1: taskpool.Task = new taskpool.Task(request, 1);
  let task2: taskpool.Task = new taskpool.Task(request, 2);
  let task3: taskpool.Task = new taskpool.Task(request, 3);

  let promise1: Promise<Any> = runner.execute(task1);
  let promise2: Promise<Any> = runner.execute(task2);
  let promise3: Promise<Any> = runner.execute(task3);
  let results: Array<Any> = await Promise.all<Any>([promise1, promise2, promise3]);
  console.info("result count: " + results.length); // result count: 3
}
```

通过名称创建的SequenceRunner或AsyncRunner会复用同名Runner实例。SequenceRunner同名实例不允许更改优先级；AsyncRunner同名实例会复用首次创建时的运行容量和等待容量。

## 与ArkTS-Dyn TaskPool的主要差异

ArkTS-Sta TaskPool与ArkTS-Dyn TaskPool在核心使用方式上类似，均通过TaskPool提交任务并通过Promise获取结果。但ArkTS-Sta采用共享内存模型，使用时需要关注以下差异：

- 不需要@Concurrent装饰器，普通函数可作为TaskPool任务函数。
- 不需要@Sendable装饰器，共享对象无需实现Sendable相关接口。
- 不需要从@kit.ArkTS导入taskpool。
- 不提供setCloneList和setTransferList接口，ArrayBuffer等对象默认共享。
- Task的函数属性名为taskFunction，不是function。
- 不提供GenericsTask，需要时直接使用taskpool.Task。
- LongTask不需要调用terminateTask终止。
