# EAWorker（独占线程任务执行器）(ArkTS)

EAWorker类为开发者提供了以独占线程模式执行异步任务的接口。通过创建EAWorker实例，系统会自动分配专属工作线程，开发者可重用该实例执行不同任务，有效提升线程资源利用率。  
> **说明：**
>
> 使用完毕后，必须显式调用[join](#join)方法来释放线程资源，以避免内存泄漏。

文档中涉及的概念及解释：
- 互操作（interop）：ArkTS1.2和ArkTS1.1代码相互操作。由于ArkTS1.1运行时为单线程实例，因此支持互操作的EAWorker会持有不同的ArkTS1.1运行时实例用于执行ArkTS1.1字节码，对应的ArkTS1.1中全局变量在不同的线程中也对应不同的实例。

## constructor
constructor(needInterop?: boolean = false)

EAWorker的构造器，用于创建支持或者不支持interop能力的EAWorker。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数:**
| 参数名         | 类型      | 必填| 说明                                                                        |
|----------------|-----------|-------|----------------------------------------------------------------------------|
| needInterop  | boolean | 否    | 参数用于控制创建的EAWorker实例是否支持interop。true表示支持互操作，false表示不支持互操作。默认值为false。 |

**示例：**
```ts
// 创建基础实例（不开启互操作）
let worker = new EAWorker();

// 创建支持ArkTS1.1互操作的实例
let interopWorker = new EAWorker(true);
```

## constructor
constructor(name: string, needInterop?: boolean = false)

EAWorker的构造器，用于创建指定名称的支持或者不支持互操作能力的EAWorker。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数:**
| 参数名         | 类型      | 必填| 说明                                                                        |
|----------------|-----------|-------|----------------------------------------------------------------------------|
| name  | string | 是    | EAWorker实例的名称。 |
| needInterop  | boolean | 否    | 参数用于控制创建的EAWorker实例是否支持互操作。true表示支持互操作，false表示不支持互操作。默认值为false。 |

**示例：**
```ts
// 创建指定名称的基础实例
let worker = new EAWorker("MyWorker");

// 创建指定名称的支持互操作的实例
let interopWorker = new EAWorker("InteropWorker", true);
```

## constructor
constructor(task: ()=> void, needInterop?: boolean = false)

EAWorker的构造器，用于创建支持或不支持互操作能力的EAWorker，并在调用EAWorker对象的[start](#start)方法后执行指定任务。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数:**
| 参数名         | 类型      | 必填| 说明                                                                        |
|----------------|-----------|-------|----------------------------------------------------------------------------|
| task  | ()=> void | 是    | 调用EAWorker对象的start方法后要执行的任务函数。|
| needInterop  | boolean | 否    | 参数用于控制创建的EAWorker实例是否支持互操作。true表示支持互操作，false表示不支持互操作。默认值为false。 |

**示例：**
```ts
// 创建包含初始任务的实例
let worker = new EAWorker(() => {
    console.info("Task execute");
});
```

## constructor
constructor(name: string, task: ()=> void, needInterop?: boolean = false)

EAWorker的构造器用于创建指定名称、支持或不支持互操作能力的EAWorker，并在调用EAWorker对象的[start](#start)方法后执行指定任务。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数:**
| 参数名         | 类型      | 必填| 说明                                                                        |
|----------------|-----------|-------|----------------------------------------------------------------------------|
| name  | string | 是    | 表示EAWorker实例的名称。 |
| task  | ()=> void | 是    | 调用EAWorker对象的start方法后要执行的任务函数。 |
| needInterop  | boolean | 否    | 参数用于控制创建的EAWorker实例是否支持互操作。true表示支持互操作，false表示不支持互操作。默认值为false。 |

**示例：**
```ts
// 创建带有初始任务并指定名称的实例
let worker = new EAWorker("TaskWorker", () => {
    console.info("Task execute");
});
```

## getWorkerId
getWorkerId(): int | undefined

获取当前EAWorker实例的ID。如果未调用[start](#start)方法，返回undefined。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| int \| undefined   | 返回当前EAWorker实例的ID。 |

**示例：**
```ts
let worker = new EAWorker();
worker.start();
let workerId = worker.getWorkerId();
console.info("Worker ID: " + workerId);
```

## getName
getName(): string

获取当前EAWorker实例的名称。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| string   | 返回EAWorker实例的名称。 |

**示例：**
```ts
let worker = new EAWorker("MyWorker");
let name = worker.getName();
console.info("Worker name: " + name); // 输出Worker name：MyWorker
```

## start
start(): void

启动EAWorker实例的任务循环，开始接收和执行任务。主线程的Worker禁止调用start方法。EAWorker实例仅能启动一次。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**示例：**
```ts
let worker = new EAWorker();
worker.start();
```

## isAlive
isAlive(): boolean

检查当前EAWorker实例是否已经start，如果当前实例调用过start方法，则返回true，否则返回false。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果EAWorker实例已启动，返回true；否则，返回false。 |

**示例：**
```ts
let worker = new EAWorker();
worker.start();
if (worker.isAlive()) {
    console.info("Worker is alive"); // Worker is alive
}
```

## setPriority
setPriority(newPriority: WorkerPriority): void

设置EAWorker实例的优先级。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|newPriority|[WorkerPriority](#workerpriority)|是|要设置的优先级值。|

**示例：**
```ts
let worker = new EAWorker();
worker.setPriority(WorkerPriority.PRIORITY_HIGH);
```

## getPriority
getPriority(): WorkerPriority

返回当前EAWorker实例的优先级。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| [WorkerPriority](#workerpriority)   | 返回当前EAWorker实例的优先级。 |

**示例：**
```ts
let worker = new EAWorker();
worker.start();
worker.setPriority(WorkerPriority.PRIORITY_HIGH)
let priority = worker.getPriority();
console.info("Worker priority: " + priority);
```

## quit
quit(): void

立即停止EAWorker实例，清空当前队列中的任务并退出任务循环，主线程禁止调用退出。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**示例：**
```ts
let worker = new EAWorker();
worker.quit();
```

## quitSafely
quitSafely(): void

安全停止EAWorker实例，等待当前队列中任务完成后销毁当前实例的任务循环，主线程禁止退出。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**示例：**
```ts
let worker = new EAWorker();
worker.quitSafely();
```

## setUncaughtExceptionHandler
setUncaughtExceptionHandler(eh: (e: Error) => void): void

设置未捕获异常处理器。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|eh|(e: Error) => void|是|异常处理函数。|

**示例：**
```ts
let worker = new EAWorker();
worker.setUncaughtExceptionHandler((error: Error) => {
    console.error("Uncaught exception: " + error.message);
});
```

## getUncaughtExceptionHandler
getUncaughtExceptionHandler(): (e: Error) => void

获取当前设置的未捕获异常处理器。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| (e: Error) => void   | 当前设置的异常处理函数。 |

**示例：**
```ts
let worker = new EAWorker();
let handler = worker.getUncaughtExceptionHandler();
```

## main
static main(): EAWorker

获取主线程的EAWorker实例。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| EAWorker   | 返回主线程的EAWorker实例。 |

**示例：**
```ts
let mainWorker = EAWorker.main();
```

## current
static current(): EAWorker | undefined

获取当前线程的EAWorker实例。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| EAWorker   | 返回当前线程的EAWorker实例。 |

**示例：**
```ts
let currentWorker = EAWorker.current();
```

## postTask
postTask(callback: ()=>void): boolean

向EAWorker提交任务。

**ArkTS版本：** 本接口仅支持ArkTS1.2。

**参数：**
|参数名|类型|必填|说明|
|-----|----|--|----|
|callback|()=>void|是|要执行的任务函数。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| boolean   | 如果成功提交任务则返回true，否则返回false。 |

**示例：**
```ts
let worker = new EAWorker();
worker.start();
worker.postTask(() => {
    console.info("Task executed");
});
```

## run
run\<R\>(task: Function, ...args?: NullishType[]): Job\<R\>

向当前Worker线程提交异步任务。需通过已创建的EAWorker实例调用，任务将在该实例绑定的独占线程中执行，使用该接口请在泛型中指定返回值类型。

> **说明：**
> 
> 若未声明泛型类型场景下调用接口得到返回值后调用Await方法，会抛出类型转换错误。

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**参数：**
| 参数名  | 类型              | 必填  | 说明           |
| ---- | --------------- | --- | ------------ |
| task | Function        | 是   | 开发者期望执行的任务函数。 |
| args | NullishType[]   | 否   |  任务函数的参数列表。默认值undefined。|

**返回值：**
| 类型       | 说明                 |
| -------- | ------------------ |
| Job\<R\>   | 任务执行句柄，可通过[Await](./job.md#await)获取异步结果。 |

**示例：**

基础任务执行。
```ts
// 定义任务函数
function logNumber(arg: int): int {
    console.info(0x0000, "testTag", "Received number: " + arg);
    return arg * 2;
}

// 创建 Worker 并提交任务
const worker = new EAWorker();
worker.start();
const job = worker.run<int>(logNumber, 42);

// 获取异步结果
console.info(0x0000, "testTag", "Result: " + job.Await());  // 输出：Result: 84
```
创建支持与ArkTS1.1互操作的EAWorker并执行任务。
```ts
// ArkTS1.1 文件 taskFile.ets
export function task(a: number): string {
    console.info(0x0000, "testTag", "ArkTS 1.1 task called: " + a); // 输出：ArkTS 1.1 task called: 1
    return "success";
}
```

```ts
// ArkTS1.2 文件
let eaw = new EAWorker(true);
eaw.start();
let job = eaw.run<string>((a:number): string => {
    let arg = ESObject.wrapInt(a);
    let mod = ESObject.load("taskFile");
    return mod.getProperty("task").invoke(arg).toString()
}, 1)
console.info(0x0000, "testTag", "res: " + job.Await()); // 输出：res: success
```

## join
join(): void

主动销毁Worker线程资源。调用此接口会向EAWorker提交任务请求释放当前EAWorker实例绑定的线程，停止接收新任务并回收系统资源。

> **说明：**
> 
> 开发者调用join之后，EAWorker实例不会立即被回收，但系统线程资源已经销毁。因此，调用join后不应继续使用EAWorker实例提交任务。

**ArkTS版本：** 该接口仅适用于ArkTS1.2。

**示例：**
```ts
let eaw = new EAWorker();
eaw.start();
eaw.run<void>(() => {
    console.info(0x0000, "testTag", "hello");
});

eaw.join();
```

## WorkerPriority
表示EAWorker线程的优先级的枚举值，开发者可以通过调用[setPriority](#setpriority)为EAWorker设置线程QoS(quality-of-service)等级，对应关系参考[QoS等级定义](../../napi/qos-guidelines.md#qos等级定义)。

|名称|值|说明|
|-|-|-|
|PRIORITY_IDLE|0|线程优先级为后台任务。|
|PRIORITY_LOW|1|线程优先级低。|
|PRIORITY_DEFAULT|2|线程优先级中。|
|PRIORITY_HIGH|3|线程优先级高。|
