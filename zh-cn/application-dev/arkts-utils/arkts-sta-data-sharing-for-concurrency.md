# ArkTS静态并发数据共享
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta采用共享内存模型，线程间可以直接共享对象数据。与ArkTS-Dyn不同，ArkTS-Sta跨线程传递普通对象时不需要Structured Clone，也不需要使用Sendable对象表达共享语义。

共享数据提升了线程间通信效率，但也要求开发者明确并发访问规则。只读共享不需要同步；多个线程同时写入，或一个线程写入、另一个线程读取同一份可变数据时，需要使用锁、原子操作或并发容器保证数据一致性。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - 本文聚焦线程间数据共享。线程间任务通知和消息分发请参见[静态线程间通信概述](arkts-sta-interthread-communication-overview.md)。

## 数据共享方式选择

不同数据共享方式适合不同场景，建议按以下原则选择：

| 场景 | 推荐方式 | 说明 |
| -------- | -------- | -------- |
| 多线程只读数据 | 直接共享对象 | 不修改对象时，同一对象可被多个线程直接读取。 |
| 多线程修改普通对象 | 锁保护 | [Mutex](../reference/apis-arkts/arkts-sta-mutex.md)或[RWLock](../reference/apis-arkts/arkts-sta-rwlock.md)保护临界区。 |
| 单个共享值计数或状态标记 | 原子类型 | 使用[AtomicInt](../reference/apis-arkts/arkts-sta-atomics.md#atomicint)、AtomicBoolean等实例化原子类型。 |
| 多线程读写Map、Set、Queue | 并发容器 | 使用[ConcurrentHashMap](../reference/apis-arkts/arkts-sta-concurrenthashmap.md)、[ConcurrentSet](../reference/apis-arkts/arkts-sta-concurrentset.md)或[BlockingQueue]。 |
| 任务需要独立快照 | 显式拷贝 | 直接复制原始对象，避免任务修改原始对象。 |
| 每个线程维护独立副本 | WorkerLocal | 使用[WorkerLocal](../reference/apis-arkts/arkts-sta-workerlocal.md) 实现数据在线程间隔离，类似其他语言的thread local。 |

注1： [AsyncLock](../reference/apis-arkts/arkts-sta-asynclock.md) 主要用于处理从ArkTS-Dyn迁移过来的代码，可以参考ArkTS-Dyn相关介绍

## 直接共享只读数据

只读数据可以直接作为TaskPool任务或EAWorker任务的入参共享。

```ts
class UserProfile {
  name: string;
  level: int;

  constructor(name: string, level: int) {
    this.name = name;
    this.level = level;
  }
}

function formatProfile(profile: UserProfile): string {
  return profile.name + ":" + profile.level;
}

async function readSharedObject(): Promise<void> {
  let profile = new UserProfile("Tom", 3);
  let result: Any = await taskpool.execute(formatProfile, profile);
  console.info("profile: " + result); // profile: Tom:3
}
```

只读共享的前提是共享对象在任务执行期间不会被其他线程修改。如果对象可能被修改，应使用锁、并发容器或拷贝策略。

## 使用Mutex保护共享对象

共享对象存在多线程写入时，可以使用Mutex保护临界区。

```ts
class SharedCounter {
  value: int = 0;
  name: string = "";
}

let cntMutex = new Mutex();

function increaseSharedCounterWithAsyncLock(counter: SharedCounter) {
    cntMutex.lock();
    counter.value++;
    cntMutex.unlock();
}

async function updateWithAsyncLock(): Promise<void> {
  let counter = new SharedCounter();
  let lockName: string = "sharedCounterLock";

  let p1: Promise<Any> = taskpool.execute(increaseSharedCounterWithAsyncLock, counter);
  let p2: Promise<Any> = taskpool.execute(increaseSharedCounterWithAsyncLock, counter);
  await Promise.all<Any>([p1, p2]);

  console.info("counter: " + counter.value); // counter: 2
}
```
一般情况下，使用Mutex可以满足大部分需求。在多读少写的场景考虑尝试使用[RWLock](../reference/apis-arkts/arkts-sta-rwlock.md)，看看是否可以获得更佳的性能。


## 使用RWLock保护读多写少数据

RWLock适合读操作明显多于写操作的场景（尤其是单写多读，而且写占比很低的场景）。<br>
如果场景不适合，RWLock性能可能还不如Mutex。<br>
读锁允许多个读线程同时进入，写锁需要独占访问。


```ts
// ArkTS-Sta示例
class ConfigStore {
  private version: int = 0;
  private lock: RWLock = new RWLock();

  readVersion(): int {
    let readLock = this.lock.readLock();
    readLock.lock();
    try {
      return this.version;
    } finally {
      readLock.unlock();
    }
  }

  updateVersion(version: int): void {
    let writeLock = this.lock.writeLock();
    writeLock.lock();
    try {
      this.version = version;
    } finally {
      writeLock.unlock();
    }
  }
}

function writeLockGuideConfig(store: ConfigStore, version: int): void {
  store.updateVersion(version);
}

function readLockGuideConfig(store: ConfigStore): int {
  return store.readVersion();
}

async function runRWLockTask(): Promise<void> {
  let store: ConfigStore = new ConfigStore();

  await taskpool.execute(writeLockGuideConfig, store, 3);
  let version = (await taskpool.execute(readLockGuideConfig, store)) as int;

  console.info("config version: " + version); // config version: 3
}
```

读锁和写锁都需要在finally中释放。不要在持有读锁时再尝试获取写锁，可能导致更多的等待和性能下降。


## 使用原子类型共享单值状态

当共享状态是单个计数器、标志位或引用时，原子类型通常比使用Mutex， RWLock性能更好。

```ts
function addCount(counter: AtomicInt, times: int): void {
  for (let i = 0; i < times; i++) {
    counter.fetchAdd(1);
  }
}

async function updateWithAtomic(): Promise<void> {
  let counter = new AtomicInt(0);

  let p1: Promise<Any> = taskpool.execute(addCount, counter, 100);
  let p2: Promise<Any> = taskpool.execute(addCount, counter, 100);
  await Promise.all<Any>([p1, p2]);

  console.info("counter: " + counter.load()); // counter: 200
}
```
实例化原子类型适合单值操作。需要维护多个字段之间的一致性时，应使用锁保护一组操作，或重新设计为并发容器。

## 使用并发哈希表共享键值数据

普通Map默认可跨线程访问，但并不保证多线程并发读写安全。多线程读写键值数据时，建议使用ConcurrentHashMap。

```ts
function putCache(cache: containers.ConcurrentHashMap<int, string>, key: int, value: string): void {
  cache.set(key, value);
}

async function updateConcurrentMap(): Promise<void> {
  let cache = new containers.ConcurrentHashMap<int, string>();

  let p1: Promise<Any> = taskpool.execute(putCache, cache, 1, "one");
  let p2: Promise<Any> = taskpool.execute(putCache, cache, 2, "two");
  await Promise.all<Any>([p1, p2]);

  let value = cache.get(1);
  console.info("value: " + value); // value: one
}
```

ConcurrentHashMap的key和value不能为null或undefined。如果需要维护唯一元素集合，可使用ConcurrentSet。

```ts
function addVisited(visited: containers.ConcurrentSet<int>, value: int): void {
  visited.add(value);
}

async function updateConcurrentSet(): Promise<void> {
  let visited = new containers.ConcurrentSet<int>();

  await Promise.all<Any>([
    taskpool.execute(addVisited, visited, 1),
    taskpool.execute(addVisited, visited, 2)
  ]);

  console.info("has value: " + visited.has(1)); // has value: true
}
```

## 使用BlockingQueue传递数据

BlockingQueue适合生产者/消费者、任务队列和流量控制场景。队列为空时，pop会异步等待；队列满时，push会异步等待。

```ts
async function produce(queue: containers.stackless.ConcurrentQueue<int>): Promise<void> {
  for (let i = 0; i < 3; i++) {
    await queue.push(i);
  }
}

async function consume(queue: containers.stackless.ConcurrentQueue<int>): Promise<int> {
  let sum: int = 0;
  for (let i = 0; i < 3; i++) {
    let value: int = await queue.pop();
    sum += value;
  }
  return sum;
}

async function useConcurrentQueue(): Promise<void> {
  let queue: containers.stackless.ConcurrentQueue<int> =
    new containers.stackless.LinkedConcurrentQueue<int>(3);

  let producer: Promise<Any> = taskpool.execute(produce, queue);
  let consumer: Promise<Any> = taskpool.execute(consume, queue);
  await producer;

  let sum = (await consumer) as int;
  console.info("sum: " + sum); // sum: 3
}
```

ConcurrentQueue的泛型参数需为非空类型，不能将null或undefined作为队列元素。

## 使用拷贝避免共享修改

如果任务只需要数据快照，且任务内会修改数据，可以显式拷贝后再传入任务，避免修改原始对象。

```ts
function sortSnapshot(values: Array<int>): Array<int> {
  return values.sort();
}

async function useSnapshot(): Promise<void> {
  let source: Array<int> = [3, 1, 2];
  let snapshot: Array<int> = Array.from(source);

  let sorted = (await taskpool.execute(sortSnapshot, snapshot)) as Array<int>;
  console.info("sorted length: " + sorted.length); // sorted length: 3
  console.info("source first: " + source[0]); // source first: 3
}
```

ArkTS-Sta不需要使用ArkTS-Dyn TaskPool的setCloneList和setTransferList接口。需要拷贝语义时，由开发者可以直接创建副本。


## 使用WorkerLocal保存线程本地数据

如果每个工作线程都需要独立状态，例如缓存、统计上下文或临时缓冲区，可以使用WorkerLocal。

```ts

let localCounter = new WorkerLocal<int>(() => 0);

function updateLocalCounter(): int {
  let current: int = localCounter.get();
  localCounter.set(current + 1);
  return localCounter.get();
}

async function useWorkerLocal(): Promise<void> {
  let result1: Any = await taskpool.execute(updateLocalCounter);
  let result2: Any = await taskpool.execute(updateLocalCounter);

  console.info("result1: " + result1); // result1: 1（示例输出，具体值取决于TaskPool工作线程复用情况）
  console.info("result2: " + result2); // result2: 1（示例输出，具体值取决于TaskPool工作线程复用情况）
}
```

WorkerLocal中的值按线程隔离。不同工作线程首次调用get时，会通过初始化函数得到各自的初始值。

## 使用建议

- 共享对象前先判断数据是否会被修改。只读数据可直接共享，可变数据需要同步策略。
- 单个数值或标志位优先使用原子类型；多个字段需要保持一致时优先使用锁。
- 多线程频繁读写集合类数据时，优先使用并发容器。
- 生产者/消费者模型优先使用ConcurrentQueue。
- 使用锁时确保加锁和释放范围清晰，避免在持有同步锁时执行长时间阻塞操作。
- 需要独立数据快照时显式拷贝即可
- 线程私有状态使用WorkerLocal, 可以线程间隔离数据
