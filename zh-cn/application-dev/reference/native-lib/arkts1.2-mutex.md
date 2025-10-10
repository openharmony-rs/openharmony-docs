# Mutex (互斥锁)

Mutex（互斥锁）的作用是为应用程序提供线程同步机制，确保在多线程环境下对共享资源的独占访问。Mutex允许一个线程在任意时刻独占访问临界区，其他线程需要等待该线程释放锁后才能获取访问权。

> **说明：**
>
> ArkTS版本：本模块仅适用于ArkTS-Sta。

## constructor

constructor()

Mutex的构造函数，用于创建Mutex对象。

**示例：**

```ts
let mutexLock = new Mutex();
```

## lock

lock(): void

获取互斥锁。如果锁已被其他线程持有，当前线程将被阻塞，直到锁被释放。

**示例：**

```ts
let mutexLock = new Mutex();
mutexLock.lock();
// 临界区资源 
```

## unlock

unlock(): void

释放互斥锁。允许其他等待的线程获取该锁。

**错误信息：**

| 错误信息                            | 说明                               |
| ---------------------------------- | ---------------------------------- |
| Unable to unlock Mutex: state is already unlocked | 尝试释放未锁定的互斥锁。<br>可能原因：对未锁定的Mutex调用unlock方法。<br>处理步骤：确保只有在成功获取锁后才调用unlock方法。无法保证时，需要捕获异常。 |

**示例：**

```ts
class SharedJob<T> {
  constructor(jobs: Array<T>) {
    this.sharedJob = new CompletableJob<void>();
    SharedJob.completeJob(jobs, this.sharedJob);
  }

  public Await() {
    this.sharedJob.Await();
  }

  private static async completeJob(jobs: Array<T>, sharedJob: CompletableJob<void>) {
    Coroutine.Schedule();
    for (let job of jobs) {
      (job as Job<void>).Await();
    }
    sharedJob.finish();
  }

  private sharedJob: CompletableJob<void>;
}

function exclusiveMutexLockTestWithEAWorker() {
    let mutexLock = new Mutex();
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
                mutexLock.lock();
                // 临界区资源
                count++;
                mutexLock.unlock();
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

exclusiveMutexLockTestWithEAWorker();

```