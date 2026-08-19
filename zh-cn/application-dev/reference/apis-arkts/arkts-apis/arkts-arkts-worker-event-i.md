# Event

事件类。

**起始版本：** 7

<!--Device-unnamed-export interface Event--><!--Device-unnamed-export interface Event-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## timeStamp

```TypeScript
readonly timeStamp: number
```

事件创建时的时间戳，单位为ms，目前不支持。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Event-readonly timeStamp: number--><!--Device-Event-readonly timeStamp: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## type

```TypeScript
readonly type: string
```

指定事件的类型。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Event-readonly type: string--><!--Device-Event-readonly type: string-End-->

**系统能力：** SystemCapability.Utils.Lang

