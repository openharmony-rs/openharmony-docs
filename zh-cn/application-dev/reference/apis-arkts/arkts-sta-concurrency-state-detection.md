# 静态并发状态信息检测
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

静态并发状态信息检测用于获取当前进程中阻塞状态静态并发任务的运行状态、锁等待状态和调用栈，帮助开发者分析任务长时间未继续执行、Mutex等待或RWLock等待等问题。


> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
> - 本接口仅用于调试和问题定位，不建议在业务逻辑中依赖快照内容进行流程控制。
> - 当前仅为Mutex和RWLock等待提供锁等待信息。其他状态下，`waitReason`和`lockMode`为`NONE`，读写锁数量为0。

## CoroutineDumpInfo

描述一个静态并发任务的状态信息。该类型由系统创建，开发者不能直接构造。

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| workerName | string | 是 | 否 | 执行该任务的工作线程名称。 |
| isMain | boolean | 是 | 否 | 是否为主工作线程。`true`表示主工作线程，`false`表示其他工作线程。 |
| coroutineName | string | 是 | 否 | 静态并发任务名称。 |
| status | string | 是 | 否 | 任务状态。<br>`CREATED`：任务已经创建，但尚未开始运行。<br>`RUNNABLE`：任务可以运行，正在等待调度。<br>`RUNNING`：任务正在运行。<br>`BLOCKED`：任务已暂停运行，正在等待事件或资源。<br>`TERMINATING`：任务正在结束。<br>`UNKNOWN`：无法识别任务状态。 |
| type | string | 是 | 否 | 运行时任务类型。<br>`FINALIZER`：执行对象终结处理的运行时任务。<br>`MUTATOR`：执行应用代码的任务。<br>`SCHEDULER`：执行任务调度操作的运行时任务。<br>`UNKNOWN`：无法识别任务类型。 |
| waitReason | string | 是 | 否 | 等待原因。<br>`NONE`：未记录Mutex或RWLock等待原因。<br>`MUTEX_LOCK`：正在等待获取Mutex。<br>`RWLOCK_READ`：正在等待获取RWLock读锁。<br>`RWLOCK_WRITE`：正在等待获取RWLock写锁。 |
| lockMode | string | 是 | 否 | 请求的锁模式。<br>`NONE`：未请求Mutex或RWLock。<br>`MUTEX`：请求获取Mutex。<br>`READLOCK`：请求获取RWLock读锁。<br>`WRITELOCK`：请求获取RWLock写锁。 |
| readerCount | int | 是 | 否 | 任务进入RWLock等待时记录的读锁数量；其他情况下为0。 |
| writerCount | int | 是 | 否 | 任务进入RWLock等待时记录的写锁数量；其他情况下为0。 |
| callStack | string | 是 | 否 | 采集到的任务调用栈。任务没有可遍历的托管栈帧时，例如任务尚未开始执行托管方法，或运行时调度任务当前没有托管调用，该字段仅包含调用栈标题，不包含具体栈帧。 |

`CoroutineDumpInfo`用于提供可按属性读取的结构化状态数据，不定义固定的日志输出格式。直接将对象传入`console.info()`时，日志系统无法完整展开对象内部保存的属性。下面提供一个打印辅助函数，显式读取每个只读属性，便于开发者查看完整的状态信息。

该函数仅为文档示例，不属于本模块提供的接口。函数将调用栈与其他属性分开输出，开发者可以根据实际日志系统的单条日志长度限制，对`callStack`进一步分段处理。

```ts
function printStateInfo(info: CoroutineDumpInfo): void {
    console.info('WorkerName: ' + info.workerName)
    console.info('IsMain: ' + info.isMain)
    console.info('Task: ' + info.coroutineName)
    console.info('Status: ' + info.status)
    console.info('Type: ' + info.type)
    console.info('WaitReason: ' + info.waitReason)
    console.info('LockMode: ' + info.lockMode)
    console.info('Readers: ' + info.readerCount)
    console.info('Writers: ' + info.writerCount)
    console.info('CallStack:')
    console.info(info.callStack)
}
```

## dumpCoroutineInfo

static dumpCoroutineInfo(): CoroutineDumpInfo[]

接口提供静态并发状态信息检测能力，获取当前进程中静态并发任务的状态信息，返回状态信息数组。

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [CoroutineDumpInfo](#coroutinedumpinfo)[] | 静态并发任务状态信息数组。如果当前运行环境不支持状态快照，或者采集到的所有工作线程均不包含处于等待或可运行队列中的任务时，返回空数组。 |

**示例：输出全部状态信息**

下面的示例先在当前任务中持有Mutex、RWLock读锁和RWLock写锁，再通过TaskPool提交三个获取锁的任务。三个TaskPool任务进入等待状态后，调用`dumpCoroutineInfo()`获取状态快照，并逐条输出等待信息和调用栈。

```ts
let mutex = new Mutex();
let readHeldRwLock = new RWLock();
let writeHeldRwLock = new RWLock();

function mutexWaiter(): void {
    mutex.lock();
    mutex.unlock();
}

function rwWriteWaiter(): void {
    readHeldRwLock.writeLock().lock();
    readHeldRwLock.writeLock().unlock();
}

function rwReadWaiter(): void {
    writeHeldRwLock.readLock().lock();
    writeHeldRwLock.readLock().unlock();
}

function printLockWaitInfo(info: CoroutineDumpInfo): void {
    console.info('Task: ' + info.coroutineName)
    console.info('WaitReason: ' + info.waitReason)
    console.info('WaitMode: ' + info.lockMode)
    if (info.waitReason == 'RWLOCK_READ' || info.waitReason == 'RWLOCK_WRITE') {
        console.info('Readers: ' + info.readerCount)
        console.info('Writers: ' + info.writerCount)
    }
    console.info('CallStack:\n' + info.callStack)
    console.info('----------')
}

async function dumpLockWaitInfo(): Promise<void> {
    // 当前任务先持有三个锁，使随后提交的TaskPool任务进入锁等待状态。
    mutex.lock();
    readHeldRwLock.readLock().lock();
    writeHeldRwLock.writeLock().lock();

    const tasks: Promise<Any>[] = [
        taskpool.execute(mutexWaiter),
        taskpool.execute(rwWriteWaiter),
        taskpool.execute(rwReadWaiter),
    ];

    // 状态快照具有时效性，循环采集直到三种锁等待状态均已出现。
    let dump: CoroutineDumpInfo[] = [];
    let allWaitsFound = false;
    while (!allWaitsFound) {
        dump = CoroutineDump.dumpCoroutineInfo();
        let mutexWaitFound = false;
        let rwReadWaitFound = false;
        let rwWriteWaitFound = false;
        for (let i = 0; i < dump.length; i++) {
            if (dump[i].waitReason == 'MUTEX_LOCK') {
                mutexWaitFound = true;
            } else if (dump[i].waitReason == 'RWLOCK_READ') {
                rwReadWaitFound = true;
            } else if (dump[i].waitReason == 'RWLOCK_WRITE') {
                rwWriteWaitFound = true;
            }
        }
        allWaitsFound = mutexWaitFound && rwReadWaitFound && rwWriteWaitFound;
    }

    for (let i = 0; i < dump.length; ++i) {
        if (dump[i].waitReason != 'NONE') {
            printLockWaitInfo(dump[i])
        }
    }

    mutex.unlock();
    readHeldRwLock.readLock().unlock();
    writeHeldRwLock.writeLock().unlock();
    await Promise.all(tasks);
}

function main() {
    dumpLockWaitInfo();
}

// 以下为关键输出示例。任务名称、记录顺序和调用栈地址可能因运行环境而不同。
// Task: mutexWaiter
// WaitReason: MUTEX_LOCK
// WaitMode: MUTEX
// CallStack:
// Panda call stack:
//    0: 0x7e41acfc0080 in std.core.Mutex::lock (managed)
//    1: 0x7e41acfc0000 in concurrency_state_detection.ETSGLOBAL::mutexWaiter (managed)
// ----------
// Task: rwWriteWaiter
// WaitReason: RWLOCK_WRITE
// WaitMode: WRITELOCK
// Readers: 1
// Writers: 1
// CallStack:
// Panda call stack:
//    0: 0x7e41acfc0080 in std.core.WriteLock::lock (managed)
//    1: 0x7e41acfc0000 in concurrency_state_detection.ETSGLOBAL::rwWriteWaiter (managed)
// ----------
// Task: rwReadWaiter
// WaitReason: RWLOCK_READ
// WaitMode: READLOCK
// Readers: 1
// Writers: 1
// CallStack:
// Panda call stack:
//    0: 0x7e41acfc0080 in std.core.ReadLock::lock (managed)
//    1: 0x7e41acfc0000 in concurrency_state_detection.ETSGLOBAL::rwReadWaiter (managed)
// ----------
```
