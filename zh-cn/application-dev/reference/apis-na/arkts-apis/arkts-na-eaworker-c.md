# EAWorker(定义ArkTS的独占线程任务执行器)

支持优先级的并发任务执行器，以独占线程模式执行异步任务。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class EAWorker--><!--Device-unnamed-export class EAWorker-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(needInterop: boolean = false)
```

构造一个EAWorker实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-constructor(needInterop: boolean = false)--><!--Device-EAWorker-constructor(needInterop: boolean = false)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| needInterop | boolean | 是 | 是否需要互操作能力。true表示支持互操作，false表示不支持，默认值为false。 |

## constructor

```TypeScript
constructor(name: string, needInterop: boolean = false)
```

构造一个指定名称的EAWorker实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-constructor(name: string, needInterop: boolean = false)--><!--Device-EAWorker-constructor(name: string, needInterop: boolean = false)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Worker的名称。 |
| needInterop | boolean | 是 | 是否需要互操作能力。true表示支持互操作，false表示不支持，默认值为false。 |

## constructor

```TypeScript
constructor(task: () => void, needInterop: boolean = false)
```

构造一个包含任务函数的EAWorker实例，在调用start方法后执行指定任务。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-constructor(task: () => void, needInterop: boolean = false)--><!--Device-EAWorker-constructor(task: () => void, needInterop: boolean = false)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | () =&gt; void | 是 | 要执行的任务函数。 |
| needInterop | boolean | 是 | 是否需要互操作能力。true表示支持互操作，false表示不支持，默认值为false。 |

## constructor

```TypeScript
constructor(name: string, task: () => void, needInterop: boolean = false)
```

构造一个指定名称并包含任务函数的EAWorker实例，在调用start方法后执行指定任务。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-constructor(name: string, task: () => void, needInterop: boolean = false)--><!--Device-EAWorker-constructor(name: string, task: () => void, needInterop: boolean = false)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Worker的名称。 |
| task | () =&gt; void | 是 | 要执行的任务函数。 |
| needInterop | boolean | 是 | 是否需要互操作能力。true表示支持互操作，false表示不支持，默认值为false。 |

## current

```TypeScript
static current(): EAWorker | undefined
```

返回当前线程的Worker实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-static current(): EAWorker | undefined--><!--Device-EAWorker-static current(): EAWorker | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EAWorker](arkts-na-eaworker-c.md) | 当前线程的Worker实例，不在Worker上下文中时返回undefined。 |

## getName

```TypeScript
getName(): string
```

返回Worker的名称。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-getName(): string--><!--Device-EAWorker-getName(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Worker的名称。 |

## getPriority

```TypeScript
getPriority(): WorkerPriority
```

返回Worker的优先级。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-getPriority(): WorkerPriority--><!--Device-EAWorker-getPriority(): WorkerPriority-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WorkerPriority](arkts-na-eaworker-workerpriority-e.md) | Worker的优先级。 |

## getUncaughtExceptionHandler

```TypeScript
getUncaughtExceptionHandler(): ((error: Error) => void) | undefined
```

返回Worker的未捕获异常处理器。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-getUncaughtExceptionHandler(): ((error: Error) => void) | undefined--><!--Device-EAWorker-getUncaughtExceptionHandler(): ((error: Error) => void) | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ((error: Error) =&gt; void) | 未捕获异常处理函数，未设置时返回undefined。 |

## getWorkerId

```TypeScript
getWorkerId(): int | undefined
```

返回Worker的ID。未调用start方法时返回undefined。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-getWorkerId(): int | undefined--><!--Device-EAWorker-getWorkerId(): int | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Worker的ID，未启动时返回undefined。 |

## isAlive

```TypeScript
isAlive(): boolean
```

检查Worker是否存活（已启动）。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-isAlive(): boolean--><!--Device-EAWorker-isAlive(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Worker已启动则返回true，否则返回false。 |

## join

```TypeScript
join(): Job<void>
```

等待Worker执行完成。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-join(): Job<void>--><!--Device-EAWorker-join(): Job<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Job](arkts-na-job-c.md)&lt;void&gt; | Worker执行完成时解析的Job。 |

## main

```TypeScript
static main(): EAWorker
```

返回主线程的Worker实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-static main(): EAWorker--><!--Device-EAWorker-static main(): EAWorker-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EAWorker](arkts-na-eaworker-c.md) | 主线程的Worker实例。 |

## postTask

```TypeScript
postTask(task: () => void): void
```

向Worker提交执行任务。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-postTask(task: () => void): void--><!--Device-EAWorker-postTask(task: () => void): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | () =&gt; void | 是 | 要提交的任务。 |

## postToMain

```TypeScript
static postToMain<R>(coroFun: Function, ...args: FixedArray<Any>): Job<R>
```

向主线程提交任务，并返回包含结果的Job。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-static postToMain<R>(coroFun: Function, ...args: FixedArray<Any>): Job<R>--><!--Device-EAWorker-static postToMain<R>(coroFun: Function, ...args: FixedArray<Any>): Job<R>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| coroFun | Function | 是 | 在主线程上执行的函数。 |
| args | FixedArray&lt;Any&gt; | 是 | 传递给函数的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Job](arkts-na-job-c.md)&lt;R&gt; | 包含函数结果的Job。 |

## quit

```TypeScript
quit(): void
```

终止Worker。等待当前所有任务完成后，停止任务循环并销毁线程资源。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-quit(): void--><!--Device-EAWorker-quit(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## run

```TypeScript
run<R>(task: Function, ...args: FixedArray<Any>): Job<R>
```

在Worker上运行任务，并返回包含结果的Job。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-run<R>(task: Function, ...args: FixedArray<Any>): Job<R>--><!--Device-EAWorker-run<R>(task: Function, ...args: FixedArray<Any>): Job<R>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | Function | 是 | 要执行的任务函数。 |
| args | FixedArray&lt;Any&gt; | 是 | 传递给任务函数的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Job](arkts-na-job-c.md)&lt;R&gt; | 包含任务结果的Job。 |

## setPriority

```TypeScript
setPriority(priority: WorkerPriority): void
```

设置Worker的优先级。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-setPriority(priority: WorkerPriority): void--><!--Device-EAWorker-setPriority(priority: WorkerPriority): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priority | [WorkerPriority](arkts-na-eaworker-workerpriority-e.md) | 是 | 要设置的优先级。 |

## setUncaughtExceptionHandler

```TypeScript
setUncaughtExceptionHandler(handler: (error: Error) => void): void
```

设置Worker的未捕获异常处理器。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-setUncaughtExceptionHandler(handler: (error: Error) => void): void--><!--Device-EAWorker-setUncaughtExceptionHandler(handler: (error: Error) => void): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | (error: Error) =&gt; void | 是 | 未捕获异常发生时调用的处理函数。 |

## start

```TypeScript
start(): void
```

启动Worker，开始接收和执行任务。EAWorker实例仅能启动一次。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EAWorker-start(): void--><!--Device-EAWorker-start(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

