# RWLock (读写锁)

RWLock（读写锁）的作用是为应用程序提供更细粒度的线程同步机制，允许多个读线程同时访问共享资源，但写线程需要独占访问。这种机制在读多写少的场景下能显著提高并发性能。

> **说明：**
>
> 本模块仅适用于ArkTS-Sta。

## constructor

constructor()

RWLock的构造函数，用于创建RWLock对象。

**示例：**

```ts
let rwLock = new RWLock();
```

## readLock

readLock(): ReadLock

获取读锁对象。读锁允许共享访问，多个线程可以同时持有读锁。

**返回值：**

| 类型              | 说明              |
| ----------------  | ---------------- |
| [ReadLock](#readlock-1) | 读锁对象，用于进行共享读操作。 |

**示例：**

```ts
let rwLock = new RWLock();
let readLock = rwLock.readLock();
```

## writeLock

writeLock(): WriteLock

获取写锁对象。写锁提供独占访问，同一时刻只能有一个线程持有写锁。

**返回值：**

| 类型              | 说明              |
| ----------------  | ---------------- |
| [WriteLock](#writelock-1) | 写锁对象，用于进行独占写操作。 |

**示例：**

```ts
let rwLock = new RWLock();
let writeLock = rwLock.writeLock();
```

## ReadLock

读锁类，提供共享读访问。

### lock

lock(): void

获取读锁。如果没有线程持有写锁，读锁会立即被获取；否则当前线程将被阻塞，直到写锁被释放。请配合[unlock](#unlock)使用防止发生死锁。

**示例：**

```ts
let rwLock = new RWLock();
let readLock = rwLock.readLock();
readLock.lock();
// 临界区资源 
```

### unlock

unlock(): void

释放读锁。

**错误信息：**

| 错误信息                            | 说明                               |
| ---------------------------------- | ---------------------------------- |
| Unable to unlock ReadLock: state is already unlocked or write-locked | 尝试释放未锁定的读锁或处于写锁状态。<br>可能原因：对未锁定的ReadLock调用unlock方法，或者在写锁状态下尝试释放读锁。<br>处理步骤：确保只有在成功获取读锁后才调用unlock方法。无法保证时，需要捕获异常。 |

**示例：**

```ts
let rwLock = new RWLock();
let readLock = rwLock.readLock();
readLock.lock();
// 临界区资源 
readLock.unlock();
```

**读锁共享示例：**

```ts
class SharedJob<T> {
  private jobs: Array<T>;

  constructor(jobs: Array<T>) {
    this.jobs = jobs;
  }

  public Await() {
    for (let job of this.jobs) {
      (job as Job<void>).Await();
    }
  }
}

function sharedReadLockTestWithEAWorker() {
  const coroutines = 10;

  let readLock = new RWLock().readLock();
  let completionFlags = new Array<boolean>(coroutines);
  let jobs = new Array<Job<void>>(coroutines);
  let workers = new Array<EAWorker>(coroutines);

  // 初始化完成标志
  for (let i: int = 0; i < coroutines; ++i) {
    completionFlags[i] = false;
  }

  for (let i = 0; i < coroutines; ++i) {
    const id = i;
    workers[i] = new EAWorker(`Worker-${id}`);
    workers[i].start();

    jobs[i] = workers[i].run<void>(() => {
      readLock.lock();
      // 临界区资源
      completionFlags[id] = true;

      let allEntered = false;
      while (!allEntered) {
        allEntered = true;
        for (let j = 0; j < coroutines; ++j) {
          if (!completionFlags[j]) {
            allEntered = false;
            break;
          }
        }
        if (!allEntered) {
          Coroutine.Schedule();
        }
      }
      readLock.unlock();
    });
  }

  // 等待所有任务完成
  let sharedJob = new SharedJob<Job<void>>(jobs);
  sharedJob.Await();

  for (let worker of workers) {
    worker.quitSafely();
  }

  console.info("No deadlock occurred");
}

sharedReadLockTestWithEAWorker();
```

## WriteLock

写锁类，提供独占写访问。

### lock

lock(): void

获取写锁。如果没有任何线程持有读锁或写锁，写锁会立即被获取；否则当前线程将被阻塞，直到所有读锁和写锁都被释放。请配合[unlock](#unlock-1)使用防止发生死锁。

**示例：**

```ts
let rwLock = new RWLock();
let writeLock = rwLock.writeLock();
writeLock.lock();
// 临界区资源
```

### unlock

unlock(): void

释放写锁。

**错误信息：**

| 错误信息                            | 说明                               |
| ---------------------------------- | ---------------------------------- |
| Unable to unlock WriteLock: state is already unlocked or read-locked | 尝试释放未锁定的写锁或处于读锁状态。<br>可能原因：对未锁定的WriteLock调用unlock方法，或者在读锁状态下尝试释放写锁。<br>处理步骤：确保只有在成功获取写锁后才调用unlock方法。无法保证时，需要捕获异常。 |

**示例：**
```ts
let rwLock = new RWLock();
let writeLock = rwLock.writeLock();
writeLock.lock();
// 临界区资源
writeLock.unlock();
```

**写锁互斥示例：**

```ts
class SharedJob<T> {
  private jobs: Array<T>;

  constructor(jobs: Array<T>) {
    this.jobs = jobs;
  }

  public Await() {
    for (let job of this.jobs) {
      (job as Job<void>).Await();
    }
  }
}

function exclusiveWriteLockTestWithEAWorker() {
  let writeLock = new RWLock().writeLock();
  const coroutines = 10;
  const workload = 1000;

  let count = 0;
  let jobs = new Array<Job<void>>(coroutines);
  let workers = new Array<EAWorker>(coroutines);

  for (let i = 0; i < coroutines; ++i) {
    const id = i.toInt();
    workers[i] = new EAWorker(`Worker-${id}`);
    workers[i].start();

    jobs[id] = workers[i].run<void>(() => {
      for (let j = 0; j < workload; ++j) {
        writeLock.lock();
        //临界区资源
        count++;
        writeLock.unlock();
      }
    });
  }

  // 等待所有任务完成
  let sharedJob = new SharedJob<Job<void>>(jobs);
  sharedJob.Await();

  for (let worker of workers) {
    worker.quitSafely();
  }

  console.info("Excepted count 10000, the real output is : " + count);
}

exclusiveWriteLockTestWithEAWorker();
```

