# WorkerLocal线程本地状态使用指导 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[WorkerLocal (工作线程本地存储)](../reference/apis-arkts/arkts-sta-workerlocal.md)用于为每个工作线程维护独立的数据副本。不同线程访问同一个WorkerLocal实例时，读取和写入的是当前线程自己的本地值，适合保存线程级缓存、统计上下文、临时缓冲区等不需要跨线程共享的状态。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 适用场景

WorkerLocal适用于以下场景：

- 每个工作线程需要独立状态，状态之间不需要同步。
- 任务需要复用线程本地缓存或临时缓冲区，减少重复创建对象。
- 需要避免使用全局共享变量带来的锁竞争。

WorkerLocal不适合保存需要跨线程汇总的最终结果。如果多个线程需要共同更新同一份数据，应使用[锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)](arkts-sta-locks-guide.md)、[原子类型使用指导 (ArkTS-Sta)](arkts-sta-atomics-guide.md)或并发容器。

## 为工作线程维护独立计数

下面示例使用WorkerLocal保存当前工作线程的本地计数。不同工作线程首次调用get时，会通过初始化函数得到各自的初始值。

```ts
// ArkTS-Sta示例
let localCounter: WorkerLocal<int> = new WorkerLocal<int>(() => 0);

function recordOnCurrentWorker(): int {
  let current: int = localCounter.get();
  localCounter.set(current + 1);
  return localCounter.get();
}

async function runWorkerLocalTask(): Promise<void> {
  let result1: Any = await taskpool.execute(recordOnCurrentWorker);
  let result2: Any = await taskpool.execute(recordOnCurrentWorker);

  console.info("worker local result1: " + result1); // worker local result1: 1（示例输出，具体值取决于TaskPool工作线程复用情况）
  console.info("worker local result2: " + result2); // worker local result2: 1（示例输出，具体值取决于TaskPool工作线程复用情况）
}
```

TaskPool任务由运行时调度到不同工作线程执行。示例输出可能受到线程复用影响：如果两个任务在同一个工作线程中执行，第二次读取到的本地计数可能为2；如果在不同工作线程中执行，则各自从1开始。

## 在线程中复用临时缓冲区

对于需要频繁创建临时数组的任务，可以把缓冲区保存在WorkerLocal中。任务结束时根据业务需要清空或删除当前线程的本地值。

```ts
// ArkTS-Sta示例
let localBuffer: WorkerLocal<Array<int>> = new WorkerLocal<Array<int>>(() => new Array<int>());

function appendToLocalBuffer(value: int): int {
  let buffer: Array<int> = localBuffer.get();
  buffer.push(value);

  let size: int = buffer.length;
  buffer.splice(0, size);
  return size;
}

async function useLocalBuffer(): Promise<void> {
  let result: Any = await taskpool.execute(appendToLocalBuffer, 10);
  console.info("buffer size: " + result); // buffer size: 1
}
```

如果当前线程后续不再需要该本地值，可以调用delete删除当前线程的WorkerLocal值。未提供初始化函数且删除后再次调用get时，会抛出初始化异常；如果提供了初始化函数，删除后再次get会重新初始化当前线程的本地值。

```ts
// ArkTS-Sta示例
let localText: WorkerLocal<string> = new WorkerLocal<string>(() => "init");

function resetLocalText(): string {
  localText.set("worker");
  localText.delete();
  return localText.get();
}

async function clearWorkerLocal(): Promise<void> {
  let result: Any = await taskpool.execute(resetLocalText);
  console.info("local text: " + result); // local text: init
}
```

## 与共享对象的区别

| 能力 | 数据可见性 | 适用场景 |
| -------- | -------- | -------- |
| 普通共享对象 | 多个线程访问同一对象。 | 只读共享，或配合锁、原子类型、并发容器进行并发读写。 |
| WorkerLocal | 每个线程访问自己的本地值。 | 线程级缓存、临时对象、上下文信息等不需要跨线程共享的数据。 |

## 使用建议

- WorkerLocal中的值只在当前线程可见，不应用于跨线程结果汇总。
- 初始化函数应保持轻量，避免在首次get时执行耗时操作。
- 长生命周期工作线程中保存大对象时，建议在不再使用时调用delete释放当前线程的本地值。
- 需要多个线程共同修改同一份数据时，应使用[锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)](arkts-sta-locks-guide.md)、[原子类型使用指导 (ArkTS-Sta)](arkts-sta-atomics-guide.md)或并发容器。

WorkerLocal的接口说明请参见[WorkerLocal (工作线程本地存储)](../reference/apis-arkts/arkts-sta-workerlocal.md)。
