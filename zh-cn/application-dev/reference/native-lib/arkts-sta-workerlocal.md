# WorkerLocal (工作线程本地存储)

WorkerLocal为多线程环境提供了线程本地存储机制，允许每个工作线程拥有自己的独立数据副本，无需担心线程安全问题。可以使用WorkerLocal API创建线程在本地的变量，这些变量在每个线程中都是独立存在的，互不干扰。WorkerLocal适用于需要在多线程环境中维护线程特定状态的场景。

> **说明：**
>
> ArkTS版本：该标准库接口仅适用于ArkTS-Sta。
> 

## constructor

constructor()

默认构造函数，创建一个无初始值和初始化函数的WorkerLocal对象。

**示例：**

```ts
// 创建无初始化函数的WorkerLocal
let wl = new WorkerLocal<int>();
```

## constructor

constructor(init: () => T)

创建一个有初始化函数的WorkerLocal对象，在不同线程首次调用[get](#get)函数时，会触发该初始化函数，将WorkerLocal在该线程的值置为初始化函数的返回值。

**参数：**

| 参数名     | 类型     | 必填     | 说明     |
| ---------- | --------- | --------- | --------- | 
| init       | () => T   | 是        |初始化函数，在不同线程首次调用get()时会触发该函数初始化线程本地值。如不提供，则必须手动调用set()设置初始值。|

**示例：**

```ts
let str = 'workerLocal';
let wl = new WorkerLocal<string>(() => str);

// 主线程
console.info("Main thread initial value: ", wl.get()); // 应输出'workerLocal'
wl.set('main');
console.info("Main thread's value after set: ", wl.get()); // 应输出'main'

//工作线程
taskpool.execute(() =>{
    console.info("Worker thread initial value: ", wl.get()); // 应输出'workerLocal'
    wl.set('subWorker');
    console.info("Worker thread after set: ", wl.get()); // 应输出'subWorker'
})

// 验证主线程不受影响
console.info("Main thread final value: ", wl.get());  // 应输出'main'

// 运行结果
// Main thread initial value: workerLocal
// Main thread's value after set: main
// Worker thread initial value: workerLocal
// Worker thread after set: subWorker
// Main thread final value: main
```

## get

get(): T

获取WorkerLocal对象在当前线程的值。未提供初始化函数且未调用过[set](#set)函数设置值时，会抛出初始化异常。

**返回值：**

| 类型      | 说明      |
| ----------| ----------|
| T| WorkerLocal对象在当前线程的值。 |

**示例：**

```ts
async function getTest(){
    let wl = new WorkerLocal<number>();

    // 主线程操作
    try {
        wl.get();
        console.error("Call get() before set() without \'init'\ should throw an error.");
    } catch (err) {
        console.info("Main thread: WorkerLocal value not initialized. Call set() first or provide an init function.");
    }

    wl.set(1);
    console.info("Main thread after first set: ", wl.get()); // 应输出1
    wl.set(wl.get() + 1);
    console.info("Main thread after second set: ", wl.get()); // 应输出2

    // 工作线程操作
    await taskpool.execute(() => {
        try {
            wl.get();
            console.error("Call get() before set() without \'init'\ should throw an error.");
        } catch (err) {
            console.info("Worker thread: WorkerLocal value not initialized. Call set() first or provide an init function.");
        }
        wl.set(1);
        console.info("Worker thread after first set: ", wl.get()); // 应输出1
        wl.set(wl.get() + 1);
        console.info("Worker thread after second set: ", wl.get()); // 应输出2
        wl.delete();
        try {
            wl.get();
            console.error("Call get() after delete() without \'init'\ should throw an error.");
        } catch (err){
            console.info("Worker thread: WorkerLocal value not initialized. Call set() first or provide an init function.");
        }
    })

    //验证主线程值不受工作线程操作的影响
    console.info("Main thread final value: ", wl.get()); // 应输出2
}

// 运行结果
// Worker thread: WorkerLocal value not initialized. Call set() first or provide an init function.
// Main thread after first set: 1
// Main thread after second set: 2
// Worker thread: WorkerLocal value not initialized. Call set() first or provide an init function.
// Worker thread after first set: 1
// Worker thread after second set: 2
// Worker thread: WorkerLocal value not initialized. Call set() first or provide an init function.
// Main thread final value: 2
```

## set

set(value: T): void

设置WorkerLocal对象在当前线程的值。

**参数：**

| 参数名     | 类型     | 必填     | 说明     |
| ---------- | -------- | --------| ---------|
| value      | T        | 是      | 要设置的WorkerLocal对象在当前线程的值。 |

**示例：**

```ts
let str = 'workerLocal';
let wl = new WorkerLocal<string>(() => str);

// 主线程
console.info("Main thread initial value: ", wl.get()); // 应输出'workerLocal'
wl.set('main');
console.info("Main thread's value after set: ", wl.get()); // 应输出'main'

// 运行结果
// Main thread initial value: workerLocal
// Main thread's value after set: main
```

## delete

delete(): void

删除WorkerLocal对象在当前线程的值。用户可在退出线程前调用，以清理不必要的内存占用。

**示例：**

```ts
let str = 'workerLocal';
let wl = new WorkerLocal<string>(() => str);

// 主线程
console.info("Main thread initial value: ", wl.get()); // 应输出'workerLocal'
wl.set('main');
console.info("Main thread's value after set: ", wl.get()); // 应输出'main'

//工作线程
taskpool.execute(() =>{
    console.info("Worker thread initial value: ", wl.get()); // 应输出'workerLocal'
    wl.set('subWorker');
    console.info("Worker thread after set: ", wl.get()); // 应输出'subWorker'
    wl.delete();
    console.info("Worker thread after delete: ", wl.get()); // 应再次输出'workerLocal'
})

// 验证主线程不受影响
console.info("Main thread final value: ", wl.get());  // 应输出'main'

// 运行结果
// Main thread initial value: workerLocal
// Main thread's value after set: main
// Worker thread initial value: workerLocal
// Worker thread after set: subWorker
// Worker thread after delete: workerLocal
// Main thread final value: main
```