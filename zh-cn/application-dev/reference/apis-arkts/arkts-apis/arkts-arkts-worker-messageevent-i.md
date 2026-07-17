# MessageEvent

消息类，持有Worker线程间传递的数据，MessageEvent类继承Event。

**继承/实现关系：** MessageEvent extends [Event](arkts-arkts-worker-event-i.md)

**起始版本：** 7

<!--Device-unnamed-export interface MessageEvent<T> extends Event--><!--Device-unnamed-export interface MessageEvent<T> extends Event-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## data

```TypeScript
readonly data: T
```

异常发生时传递的数据。

**类型：** T

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MessageEvent-readonly data: T--><!--Device-MessageEvent-readonly data: T-End-->

**系统能力：** SystemCapability.Utils.Lang

