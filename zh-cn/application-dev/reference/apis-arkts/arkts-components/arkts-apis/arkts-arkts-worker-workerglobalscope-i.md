# WorkerGlobalScope

Worker线程自身的运行环境，与宿主线程环境隔离。

**继承/实现关系：** WorkerGlobalScope extends [EventTarget](arkts-arkts-worker-eventtarget-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [GlobalScope](arkts-arkts-worker-globalscope-i.md)

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## onerror

```TypeScript
onerror?: (ev: ErrorEvent) => void
```

onerror属性用于指定Worker在执行过程中发生异常被调用的回调函数，该回调函数在Worker线程中执行。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onerror

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

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

**系统能力：** SystemCapability.Utils.Lang

## self

```TypeScript
readonly self: WorkerGlobalScope & typeof globalThis
```

为self指定的type属性。

**类型：** [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md) & typeof globalThis

**起始版本：** 7

**废弃版本：** 9

**替代接口：** self

**系统能力：** SystemCapability.Utils.Lang
