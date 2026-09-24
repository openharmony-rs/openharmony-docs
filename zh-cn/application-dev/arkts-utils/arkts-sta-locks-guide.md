# 锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

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

## 锁使用规则

- 同一份共享状态应始终使用同一个锁保护。
- Mutex和RWLock的lock()与unlock()应在同一控制流程中成对出现，并通过try-finally保证释放；不要依赖其他任务代为解锁。
- 尽量缩小临界区，不要在持有Mutex或RWLock时执行文件访问、网络请求、用户回调或异步等待等耗时操作。
- 获取多个锁时，所有任务应按照统一顺序加锁，并按照相反顺序释放。
- Mutex和RWLock均不支持在锁尚未释放时重复获取同一个锁，应避免持锁函数再次获取同一Mutex或RWLock。
- RWLock从读转为写时，应先释放读锁，再获取写锁，并重新校验更新条件。
- 使用AsyncLock.request(name)保护同一资源时，应使用相同且稳定的名称；必要时通过AsyncLockOptions配置超时或取消信号。

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

## 分析锁等待和可能的死锁

排查时可以先向目标进程发送SIGQUIT信号，获取当前进程的整体等待信息。当应用已经卡住、无法再执行主动诊断代码时，运行时接收SIGQUIT后会将Mutex和RWLock的等待原因、请求模式、RWLock数量快照和任务调用栈写入运行时日志。在有权限的调试环境中，可以执行以下命令：

```shell
# Linux环境
kill -3 <pid>

# 设备调试环境
hdc shell kill -3 <pid>
```

如果应用仍能执行调试代码，或需要更精细地控制采集时机、重复采集以及按字段筛选结果，可以使用[静态并发状态信息检测](../reference/apis-arkts/arkts-sta-concurrency-state-detection.md)提供的dumpCoroutineInfo()接口。建议从未参与阻塞链路、仍可以运行的任务或调试入口调用该接口。

下面的辅助函数只输出正在等待Mutex或RWLock的任务：

```ts
function printLockWaitSnapshot(): void {
  let states: CoroutineDumpInfo[] = CoroutineDump.dumpCoroutineInfo();
  for (let i = 0; i < states.length; i++) {
    let state = states[i];
    if (state.status != 'BLOCKED' || state.waitReason == 'NONE') {
      continue;
    }

    console.info('Task: ' + state.coroutineName);
    console.info('WaitReason: ' + state.waitReason);
    console.info('WaitMode: ' + state.lockMode);
    if (state.waitReason == 'RWLOCK_READ' || state.waitReason == 'RWLOCK_WRITE') {
      console.info('Readers: ' + state.readerCount);
      console.info('Writers: ' + state.writerCount);
    }
    console.info('CallStack:\n' + state.callStack);
  }
}
```

状态快照只表示采集时刻观察到的等待状态，不会自动判断是否存在死锁。当前快照也不包含锁对象标识和锁持有者信息，因此需要通过调用栈找到加锁代码，再检查相关代码路径的持锁和等待关系。对于偶发问题，可以间隔采集多次；如果相同任务长期停留在同一加锁栈帧，并且相关业务没有进展，再进一步检查锁顺序和释放路径。

### 案例一：多个Mutex的加锁顺序相反

以下为错误示例。两个任务以相反顺序获取`accountLock`和`cacheLock`。两个原子标志用于确保每个任务都已经获取第一把锁，再继续申请第二把锁，从而稳定构造相互等待。示例会使两个TaskPool任务一直处于等待状态，仅用于独立调试进程，输出快照后需要结束进程，请勿在业务代码中使用。

```ts
let accountLock = new Mutex();
let cacheLock = new Mutex();
let accountLockHeld = new AtomicBoolean(false);
let cacheLockHeld = new AtomicBoolean(false);

function updateAccountThenCache(): void {
  accountLock.lock();
  try {
    accountLockHeld.store(true);
    while (!cacheLockHeld.load()) {
    }
    // cacheLock已被另一个任务持有，此处进入等待。
    cacheLock.lock();
    try {
      // 同时更新账户和缓存。
    } finally {
      cacheLock.unlock();
    }
  } finally {
    accountLock.unlock();
  }
}

function updateCacheThenAccount(): void {
  cacheLock.lock();
  try {
    cacheLockHeld.store(true);
    while (!accountLockHeld.load()) {
    }
    // accountLock已被另一个任务持有，此处进入等待。
    accountLock.lock();
    try {
      // 同时更新缓存和账户。
    } finally {
      accountLock.unlock();
    }
  } finally {
    cacheLock.unlock();
  }
}

function reproduceAndDumpMutexDeadlock(): void {
  taskpool.execute(updateAccountThenCache);
  taskpool.execute(updateCacheThenAccount);

  // 等待两个任务都进入Mutex等待队列。
  let mutexWaiterCount = 0;
  while (mutexWaiterCount < 2) {
    mutexWaiterCount = 0;
    let states: CoroutineDumpInfo[] = CoroutineDump.dumpCoroutineInfo();
    for (let i = 0; i < states.length; i++) {
      if (states[i].status == 'BLOCKED' && states[i].waitReason == 'MUTEX_LOCK') {
        mutexWaiterCount++;
      }
    }
  }

  // 调用前文辅助函数，再采集并打印当前锁等待快照。
  printLockWaitSnapshot();
}

reproduceAndDumpMutexDeadlock();
```

发生上述相互等待时，状态快照可能包含以下关键内容，实际任务名称和调用栈地址以运行结果为准：

```text
Task: updateAccountThenCache
WaitReason: MUTEX_LOCK
WaitMode: MUTEX
CallStack:
Panda call stack:
   0: 0x7e41acfc0080 in std.core.Mutex::lock (managed)
   1: 0x7e41acfc0000 in lock_guide.ETSGLOBAL::updateAccountThenCache (managed)
----------

Task: updateCacheThenAccount
WaitReason: MUTEX_LOCK
WaitMode: MUTEX
CallStack:
Panda call stack:
   0: 0x7e41acfc0180 in std.core.Mutex::lock (managed)
   1: 0x7e41acfc0100 in lock_guide.ETSGLOBAL::updateCacheThenAccount (managed)
----------
```

两条记录只能说明两个任务都在等待Mutex，不能仅凭该快照确定它们等待的是哪一个锁。需要根据调用栈定位到两个函数，检查其加锁顺序。修复时应统一顺序，例如两个函数都先获取`accountLock`，再获取`cacheLock`，并按照相反顺序释放。

### 案例二：持有RWLock读锁时申请写锁

以下为错误示例。任务持有读锁后，在读锁尚未释放时申请同一个RWLock的写锁。写锁需要等待所有读锁释放，但当前任务只有在获得写锁后才能继续执行到`finally`释放读锁，因而可能一直等待。示例会使TaskPool任务一直处于等待状态，仅用于独立调试进程，输出快照后需要结束进程，请勿在业务代码中使用。

```ts
class VersionedConfig {
  private version: int = 0;
  private lock: RWLock = new RWLock();

  updateIfNeeded(): void {
    let readLock = this.lock.readLock();
    readLock.lock();
    try {
      if (this.version == 0) {
        let writeLock = this.lock.writeLock();
        writeLock.lock(); // 错误：持有读锁时申请同一个RWLock的写锁。
        try {
          this.version = 1;
        } finally {
          writeLock.unlock();
        }
      }
    } finally {
      readLock.unlock();
    }
  }
}

function updateVersionedConfig(config: VersionedConfig): void {
  config.updateIfNeeded();
}

function reproduceAndDumpRWLockUpgrade(): void {
  let config = new VersionedConfig();
  taskpool.execute(updateVersionedConfig, config);

  // 等待任务进入RWLock写锁等待队列。
  let rwWriteWaitFound = false;
  while (!rwWriteWaitFound) {
    let states: CoroutineDumpInfo[] = CoroutineDump.dumpCoroutineInfo();
    for (let i = 0; i < states.length; i++) {
      if (states[i].status == 'BLOCKED' && states[i].waitReason == 'RWLOCK_WRITE') {
        rwWriteWaitFound = true;
        break;
      }
    }
  }

  // 调用前文辅助函数，再采集并打印当前锁等待快照。
  printLockWaitSnapshot();
}

reproduceAndDumpRWLockUpgrade();
```

该任务的状态快照可能包含以下关键内容：

```text
Task: updateIfNeeded
WaitReason: RWLOCK_WRITE
WaitMode: WRITELOCK
Readers: 1
Writers: 1
CallStack:
Panda call stack:
   0: 0x7e41acfc0080 in std.core.WriteLock::lock (managed)
   1: 0x7e41acfc0000 in lock_guide.VersionedConfig::updateIfNeeded (managed)
   2: 0x7e41acfbe000 in lock_guide.ETSGLOBAL::updateVersionedConfig (managed)
----------
```

`RWLOCK_WRITE`和`WRITELOCK`说明任务正在等待写锁，`Readers`和`Writers`是任务进入等待时记录的数量，不代表采集完成后的实时状态。调用栈同时显示该任务停在`updateIfNeeded()`中的`WriteLock.lock()`，应进一步检查该路径是否仍持有读锁。

## 问题排查建议

- 首先确认等待是否持续存在。短时间出现MUTEX_LOCK、RWLOCK_READ或RWLOCK_WRITE通常只是正常锁竞争。
- 如果多次快照显示相同任务停留在相同加锁栈帧，检查对应代码是否遗漏unlock()、是否在锁内执行耗时操作，以及多个锁的获取顺序是否一致。
- 如果出现RWLOCK_WRITE，重点检查等待写锁的路径是否尚未释放同一个RWLock的读锁；如果出现RWLOCK_READ，检查是否存在长期持有的写锁。
- 调用栈没有有效托管栈帧时，应结合任务名称、业务日志和其他运行时信息继续定位，不能仅根据等待原因认定存在死锁。
- 单个计数器或状态标志优先考虑[原子类型使用指导 (ArkTS-Sta)](arkts-sta-atomics-guide.md)。
- 集合类高频并发读写优先考虑ConcurrentHashMap、ConcurrentSet、ConcurrentQueue等并发容器。

相关API说明请参见[Mutex (互斥锁)](../reference/apis-arkts/arkts-sta-mutex.md)、[RWLock (读写锁)](../reference/apis-arkts/arkts-sta-rwlock.md)、[AsyncLock (异步锁)](../reference/apis-arkts/arkts-sta-asynclock.md)和[静态并发状态信息检测](../reference/apis-arkts/arkts-sta-concurrency-state-detection.md)。
