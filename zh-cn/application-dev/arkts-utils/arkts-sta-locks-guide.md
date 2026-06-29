# 锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta对象默认可以在线程间共享。多个线程同时修改同一份可变数据，或一个线程读取、另一个线程修改同一份数据时，需要使用同步机制保护临界区。ArkTS-Sta提供[Mutex (互斥锁)](../reference/apis-arkts/arkts-sta-mutex.md)、[RWLock (读写锁)](../reference/apis-arkts/arkts-sta-rwlock.md)和[AsyncLock (异步锁)](../reference/apis-arkts/arkts-sta-asynclock.md)，分别适用于同步临界区、读多写少和异步流程。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 锁能力选择

| 能力 | 适用场景 | 使用要点 |
| -------- | -------- | -------- |
| Mutex | 多线程同步访问同一份可变数据。 | lock和unlock成对出现，建议使用try-finally确保释放锁。 |
| RWLock | 读多写少的数据访问。 | 多个读操作可并发，写操作需要独占访问。 |
| AsyncLock | 异步流程中保护共享资源。 | 使用lockAsync并await返回的Promise；可通过AsyncLockMode指定共享或独占模式。 |

## 使用Mutex保护同步临界区

Mutex适合保护短小的同步临界区。下面示例中，两个TaskPool任务同时更新同一个计数器，通过Mutex保证递增操作互斥执行。

```ts
// ArkTS-Sta示例
class MutexCounter {
  private value: int = 0;
  private lock: Mutex = new Mutex();

  increase(): void {
    this.lock.lock();
    try {
      this.value++;
    } finally {
      this.lock.unlock();
    }
  }

  current(): int {
    this.lock.lock();
    try {
      return this.value;
    } finally {
      this.lock.unlock();
    }
  }
}

function increaseMutexGuideCounter(counter: MutexCounter): void {
  counter.increase();
}

async function runMutexTask(): Promise<void> {
  let counter: MutexCounter = new MutexCounter();

  await Promise.all<Any>([
    taskpool.execute(increaseMutexGuideCounter, counter),
    taskpool.execute(increaseMutexGuideCounter, counter)
  ]);

  console.info("mutex counter: " + counter.current()); // mutex counter: 2
}
```

使用Mutex时，应避免在持有锁期间执行长时间阻塞操作，否则会影响其他线程进入临界区。

## 使用RWLock保护读多写少数据

RWLock适合读操作明显多于写操作的场景。读锁允许多个读线程同时进入，写锁需要独占访问。

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

读锁和写锁都需要在finally中释放。不要在持有读锁时再尝试获取写锁，避免锁升级带来的等待问题。

## 使用AsyncLock保护异步更新

AsyncLock适合异步代码中的共享状态保护。下面示例通过同名AsyncLock串行化两个存款任务，避免并发更新余额。

```ts
// ArkTS-Sta示例
class AsyncAccount {
  balance: int = 0;
}

async function depositLockGuideAccount(account: AsyncAccount, amount: int, lockName: string): Promise<void> {
  let lock: AsyncLock = AsyncLock.request(lockName);
  await lock.lockAsync<void>(() => {
    account.balance += amount;
  }, AsyncLockMode.EXCLUSIVE);
}

async function runAsyncLockTask(): Promise<void> {
  let account: AsyncAccount = new AsyncAccount();
  let lockName: string = "accountLock";

  await Promise.all<Any>([
    taskpool.execute(depositLockGuideAccount, account, 10, lockName),
    taskpool.execute(depositLockGuideAccount, account, 20, lockName)
  ]);

  console.info("account balance: " + account.balance); // account balance: 30
}
```

AsyncLock.request使用锁名称获取锁对象。需要保护同一份共享资源时，应确保不同任务使用同一个锁名称。

## 使用建议

- 优先缩小临界区范围，只把必须互斥的读写操作放入锁内。
- Mutex和RWLock的lock、unlock应成对出现，建议使用try-finally释放锁。
- 异步流程优先使用AsyncLock，不要在持有同步锁时等待耗时异步操作。
- 单个计数器或状态标志优先考虑[原子类型使用指导 (ArkTS-Sta)](arkts-sta-atomics-guide.md)。
- 集合类高频并发读写优先考虑ConcurrentHashMap、ConcurrentSet、ConcurrentQueue等并发容器。

相关API说明请参见[Mutex (互斥锁)](../reference/apis-arkts/arkts-sta-mutex.md)、[RWLock (读写锁)](../reference/apis-arkts/arkts-sta-rwlock.md)和[AsyncLock (异步锁)](../reference/apis-arkts/arkts-sta-asynclock.md)。
