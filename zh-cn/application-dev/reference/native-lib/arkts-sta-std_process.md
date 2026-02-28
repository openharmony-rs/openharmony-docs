# StdProcess (进程管理标准库)

提供系统进程信息查询及跨进程交互能力，支持环境变量管理、系统资源配置等高级操作。

> **说明：**
>
> ArkTS版本：该标准库接口仅适用于ArkTS-Sta。

## StdProcess.uid

uid(): int

获取进程的用户标识符，用于标识创建当前线程的用户的id。

**返回值：**

| 类型 | 说明                           |
| ---- | ----------------------------- |
| int | 返回进程的用户标识符，大于0的整数。 |

**示例：**

```js
let uid = StdProcess.uid();
```

## StdProcess.pid

pid(): int

获取进程的唯一标识符，用于标识当前进程的id。

**返回值：**

| 类型 | 说明                           |
| ---- | ----------------------------- |
| int | 返回当前进程的进程id，大于0的整数。 |

**示例：**

```js
let pid = StdProcess.pid();
```

## StdProcess.tid

tid(): int

获取线程的唯一标识符，用于标识当前线程的id。

**返回值：**

| 类型 | 说明                           |
| ---- | ----------------------------- |
| int | 返回当前线程的线程id，大于0的整数。 |

**示例：**

```js
let tid = StdProcess.tid();
```

## StdProcess.is64Bit

is64Bit(): boolean

检查运行环境是否为64位。

**返回值：**

| 类型    | 说明                                                     |
| ------- | ------------------------------------------------------- |
| boolean | 返回判断结果。如果运行环境是64位则返回true，否则返回false。 |

**示例：**

```js
let result = StdProcess.is64Bit();
```

## StdProcess.getStartRealtime

getStartRealtime(): long

获取系统启动到进程启动的实时时间（以毫秒为单位）。

**返回值：**

| 类型   | 说明                           |
| ------ | ----------------------------- |
| long  | 返回经过的实时时间。单位：毫秒。 |

**示例：**

```js
let realtime = StdProcess.getStartRealtime();
```

## StdProcess.getPastCpuTime

getPastCpuTime(): long

获取进程启动到当前时间的CPU时间（以毫秒为单位）。

**返回值：**

| 类型   | 说明                          |
| ------ | ----------------------------- |
| long | 返回经过的CPU时间。单位：毫秒。 |

**示例：**

```js
let result = StdProcess.getPastCpuTime();
```

## StdProcess.abort

abort(): void

该方法会导致进程立即退出并生成一个核心文件，谨慎使用。

**示例：**

```js
StdProcess.abort();
```

## StdProcess.uptime

uptime(): long

获取当前系统已运行的时间（以秒为单位）。

**返回值：**

| 类型   | 说明                          |
| ------ | ---------------------------- |
| long | 当前系统已运行的时间。单位：秒。|

**示例：**

```js
let time = StdProcess.uptime();
```

## StdProcess.on 

on(type: string, listener: EventListener): void

注册标准进程事件监听器，用于捕获当前线程中的异常事件。

当对应事件触发时，注册的listener将被回调，用于异常处理。

事件触发时会抛出错误信息，建议使用try-catch逻辑进行处理。

**参数：**

| 参数名 | 类型   | 必填 | 说明      |
| ------ | ------ | ---- | ------- |
| type     | string | 是   | 事件类型，支持取值及对应含义如下所示：<br> 'unhandledPromiseRejection': 注册未处理Promise拒绝的监听器。<br> 'uncaughtError': 注册未捕获异常的监听器。|
| listener | [EventListener](#eventlistener) | 是 | 事件回调函数。`unhandledPromiseRejection`对应[RejectedObjectListener](#rejectedobjectlistener)，`uncaughtError`对应[UncaughtErrorListener](#uncaughterrorlistener)。|

**示例：**

```ts
let listener: StdProcess.RejectedObjectListener = (reason: Error, target: Object) => {
    console.info("unhandled rejection detected");
    console.info("reason.name:", reason.name);
    console.info("reason.message:", reason.message);
    if (reason.stack) {
        console.info("reason.stack:", reason.stack);
    }
}
try {
    StdProcess.on("unhandledPromiseRejection", listener);
    new Promise<void>((res, reject) => {
        reject(new Error(("uncaught rejection")))
    })
} catch (e) {
    console.info("caught exception:", (e as Error).message);
}
```

## EventListener

type EventListener = RejectedObjectListener | UncaughtErrorListener

事件监听器类型，可以是拒绝对象监听器或未捕获异常监听器。不同异常场景应使用的回调类型如下：

| 场景 | 事件类型（type） | 监听回调类型 |
| ------ | ------ | ------ |
| Promise未处理拒绝 | unhandledPromiseRejection | [RejectedObjectListener](#rejectedobjectlistener) |
| 进程内其他未捕获异常 | uncaughtError | [UncaughtErrorListener](#uncaughterrorlistener) |

| 类型 | 说明   |
| ------ | ------ |
| [RejectedObjectListener](#rejectedobjectlistener)     | 拒绝对象监听器回调函数，用于处理未处理的Promise拒绝。 |
| [UncaughtErrorListener](#uncaughterrorlistener)      | 未捕获的异常监听器回调函数，用于处理进程中未被捕获的异常。 |

## RejectedObjectListener

type RejectedObjectListener = (reason: Error, obj: Object) => void

拒绝对象监听器回调函数，用于处理未处理的Promise拒绝。

**参数：**

| 参数名 | 类型   | 必填 | 说明      |
| ------ | ------ | ---- | ------- |
| reason     | Error | 是   | 异步拒绝的原因。|
| obj | Object | 是 | 被拒绝的Promise对象。|

**示例：**

```ts
let promiseRejectedListener: StdProcess.RejectedObjectListener = (reason: Error, obj: Object) => {
    console.info("unhandled promise rejection");
    console.info("reason:", reason.message);
}

StdProcess.on("unhandledPromiseRejection", promiseRejectedListener);
new Promise<void>((res, reject) => {
    reject(new Error("promise rejected"));
});
```

## UncaughtErrorListener

type UncaughtErrorListener = (error: Object) => void

未捕获的异常监听器回调函数。用于处理进程中未被捕获的异常。

**参数：**

| 参数名 | 类型   | 必填 | 说明      |
| ------ | ------ | ---- | ------- |
| error     | Object | 是   | 未被捕获的异常对象。|

**示例：**

```ts
let uncaughtErrorListener: StdProcess.UncaughtErrorListener = (error: Object) => {
    console.info("uncaught process error:", error.toString());
}

StdProcess.on("uncaughtError", uncaughtErrorListener);
throw new Error("uncaught error in process");
```

## ProcessManager

提供与系统进程进行交互的接口，用于获取进程特有和系统特有的信息。

### getUidForName

getUidForName(v: string): int

根据指定的用户名，从系统的用户数据库中获取该用户uid。

**参数：**

| 参数名 | 类型   | 必填 | 说明      |
| ------ | ------ | ---- | ------- |
| v      | string | 是   | 用户名。 |

**返回值：**

| 类型   | 说明                               |
| ------ | --------------------------------- |
| int    | 获取用户uid，如果用户不存在则返回-1。|

**示例：**

```js
let processManager = new StdProcess.ProcessManager();
let uid = processManager.getUidForName("tool");
```

### getThreadPriority

getThreadPriority(v: int): int

根据指定的tid获取线程优先级。

**参数：**

| 参数名 | 类型   | 必填 | 说明                            |
| ------ | ------ | ---- | ----------------------------- |
| v      | int | 是   | 指定的线程tid。大于等于0的整数。 |

**返回值：**

| 类型   | 说明                                          |
| ------ | -------------------------------------------- |
| int    | 返回线程的优先级。优先级顺序取决于当前操作系统。 |

> **说明：**
>
> 在Unix语义下，优先级范围通常为[-20, 19]，数值越小优先级越高，0为默认优先级。-1既可能表示查询失败，也可能是合法优先级值。建议结合tid是否有效综合判断。

**示例：**

```js
let processManager = new StdProcess.ProcessManager();
let tid = StdProcess.tid();
let pres0 = processManager.getThreadPriority(tid); // 合法线程优先级
let invalidTid = 999999;
let pres1 = processManager.getThreadPriority(invalidTid); // 线程不存在时返回-1
```

### getSystemConfig

getSystemConfig(name: int): long

获取系统配置信息，name用于指定系统配置项编号。

**参数：**

| 参数名  | 类型   | 必填  | 说明                          |
| ------ | ------ | ---- | ------------------------------ |
| name   | int | 是   | 指定系统配置参数名（配置项编号）。非负整数。 |

**常见配置项示例：**

| 配置项（示例） | name取值 | 配置项含义 | 返回值含义 |
| ------ | ------ | ------ | ------ |
| _SC_ARG_MAX | 0 | 进程可接收命令行参数总长度上限 | 最大参数长度（字节） |
| _SC_CLK_TCK | 2 | 每秒时钟滴答数 | 每秒滴答数 |
| _SC_OPEN_MAX | 4 | 进程可打开文件描述符数上限 | 最大文件描述符数量 |
| _SC_PAGE_SIZE | 8 | 内存页大小 | 页大小（字节） |

**返回值：**

| 类型   | 说明                                    |
| ------ | -------------------------------------  |
| long   | 返回系统配置信息。如果配置不存在，返回-1。 |

**示例：**

```js
let processManager = new StdProcess.ProcessManager();
let _SC_ARG_MAX = 0;  // 进程可接收命令行参数总长度上限
let argMax = processManager.getSystemConfig(_SC_ARG_MAX); // 单位：字节
```

### getEnvironmentVar

getEnvironmentVar(name: string): string

获取环境变量对应的值，如果值不存在，返回空字符串。

**参数：**

| 参数名 | 类型    | 必填 | 说明         |
| ------ | ------ | ---- | ----------- |
| name   | string | 是   | 环境变量名。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ----------------------- |
| string | 返回环境变量名对应的值。  |

**示例：**

```js
let processManager = new StdProcess.ProcessManager();
let pres = processManager.getEnvironmentVar("PATH");
```

### exit

exit(code: int): void

终止程序。

请谨慎使用此接口，此接口调用后应用会退出，如果入参非0会产生数据丢失或者异常情况。

**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | ------------- |
| code   | int | 是   | 进程的退出码。0~255的整数。 |

**示例：**

```js
let processManager = new StdProcess.ProcessManager();
processManager.exit(0);
```

### kill

kill(signal: int, pid: int): boolean

发送signal到指定的进程，结束指定进程。

**参数：**

| 参数名  | 类型   | 必填 | 说明                               |
| ------ | ------ | ---- | ---------------------------------- |
| signal | int | 是   | 发送特定的信号给目标进程。1~64的整数。|
| pid    | int | 是   | 进程的id。大于0的整数。              |

**返回值：**

| 类型    | 说明                                                      |
| ------- | -------------------------------------------------------- |
| boolean | 信号是否发送成功。如果信号发送成功则返回true，否则返回false。 |

**示例：**

```js
let processManager = new StdProcess.ProcessManager();
let pres = StdProcess.pid();
let result = processManager.kill(28, pres);
```
