# GlobalScope

Worker线程自身的运行环境，GlobalScope类继承WorkerEventTarget。

**继承/实现关系：** GlobalScope extends [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## onerror

```TypeScript
onerror?: (ev: ErrorEvent) => void
```

Worker在执行过程中发生异常被调用的回调函数，该回调函数在Worker线程中执行。 其中ev类型为ErrorEvent，表示收到的异常数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ev | [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | 是 |  |

## name

```TypeScript
readonly name: string
```

Worker的名字，new Worker时指定。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## self

```TypeScript
readonly self: GlobalScope & typeof globalThis
```

GlobalScope本身。

**类型：** [GlobalScope](arkts-arkts-worker-globalscope-i.md) & typeof globalThis

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
