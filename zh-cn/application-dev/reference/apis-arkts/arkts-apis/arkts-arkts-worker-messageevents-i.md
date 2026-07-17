# MessageEvents

消息类，持有Worker线程间传递的数据。

**继承/实现关系：** MessageEvents extends [Event](arkts-arkts-worker-event-i.md)

**起始版本：** 9

<!--Device-unnamed-export interface MessageEvents extends Event--><!--Device-unnamed-export interface MessageEvents extends Event-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## data

```TypeScript
readonly data: any
```

异常发生时传递的数据。

**类型：** any

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MessageEvents-readonly data: any--><!--Device-MessageEvents-readonly data: any-End-->

**系统能力：** SystemCapability.Utils.Lang

