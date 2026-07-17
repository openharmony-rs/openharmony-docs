# WorkerGlobalScope

Worker线程自身的运行环境，与宿主线程环境隔离。

**继承/实现关系：** WorkerGlobalScope extends [EventTarget](arkts-arkts-worker-eventtarget-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** GlobalScope

<!--Device-unnamed-declare interface WorkerGlobalScope extends EventTarget--><!--Device-unnamed-declare interface WorkerGlobalScope extends EventTarget-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## name

```TypeScript
readonly name: string
```

Worker的名字，new Worker时指定。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

<!--Device-WorkerGlobalScope-readonly name: string--><!--Device-WorkerGlobalScope-readonly name: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## onerror

```TypeScript
onerror?: (ev: ErrorEvent) => void
```

onerror属性用于指定Worker在执行过程中发生异常被调用的回调函数，该回调函数在Worker线程中执行。

**类型：** (ev: ErrorEvent) => void

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onerror

<!--Device-WorkerGlobalScope-onerror?: (ev: ErrorEvent) => void--><!--Device-WorkerGlobalScope-onerror?: (ev: ErrorEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

## self

```TypeScript
readonly self: WorkerGlobalScope & typeof globalThis
```

为self指定的type属性。

**类型：** WorkerGlobalScope & typeof globalThis

**起始版本：** 7

**废弃版本：** 9

**替代接口：** self

<!--Device-WorkerGlobalScope-readonly self: WorkerGlobalScope & typeof globalThis--><!--Device-WorkerGlobalScope-readonly self: WorkerGlobalScope & typeof globalThis-End-->

**系统能力：** SystemCapability.Utils.Lang

