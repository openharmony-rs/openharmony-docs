# EventListener

事件监听类用于处理事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** WorkerEventListener

<!--Device-unnamed-export interface EventListener--><!--Device-unnamed-export interface EventListener-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## constructor

```TypeScript
(evt: Event): void | Promise<void>
```

指定要调用的回调函数。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** (event:

<!--Device-EventListener-(evt: Event): void | Promise<void>--><!--Device-EventListener-(evt: Event): void | Promise<void>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | [Event](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact-event-c.md) | 是 | evt evt 回调的事件类。 |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.addEventListener("alert", ()=>{
    console.info("alert listener callback");
})

```

