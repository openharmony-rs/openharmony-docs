# EventTarget

用于管理Worker的监听事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md)

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## addEventListener

```TypeScript
addEventListener(type: string, listener: EventListener): void
```

向Worker添加一个事件监听。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** addEventListener

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 是 | listener 当指定类型的事件发生时调用的回调函数。 |

**示例**

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", () => {
  console.info("alert listener callback");
})
```

## dispatchEvent

```TypeScript
dispatchEvent(event: Event): boolean
```

分发Worker实例上已注册的事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** dispatchEvent

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Event](arkts-arkts-worker-event-i.md) | 是 | 需要分发的事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean |  |

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

let result: boolean = workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

console.info("dispatchEvent result is: ", result);
```

```TypeScript
// worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.addEventListener("alert", () => {
    console.info("alert listener callback");
  });

  workerPort.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持
};
```

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert_add", ()=>{
  console.info("alert listener callback");
})

workerPort.dispatchEvent({type: 'alert_add', timeStamp: 0}); // timeStamp暂未支持
```

分发事件（dispatchEvent）可与监听接口（addEventListener）搭配使用，示例如下：

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (): void => {
    console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", ()=>{
  console.info("alert listener callback");
})

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.dispatchEvent({type:"alert", timeStamp:0}); // timeStamp暂未支持
}
```

## removeAllListener

```TypeScript
removeAllListener(): void
```

移除Worker所有的事件监听。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeAllListener

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.addEventListener("alert", () => {
    console.info("alert listener callback");
})
workerInstance.removeAllListener();
```

```TypeScript
// worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.addEventListener("alert", () => {
    console.info("alert listener callback");
  });

  workerPort.removeAllListener();
};
```

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert_add", ()=>{
  console.info("alert listener callback");
})

workerPort.removeAllListener();
```

## removeEventListener

```TypeScript
removeEventListener(type: string, callback?: EventListener): void
```

移除Worker的事件监听。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeEventListener

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 需要移除的事件类型。 |
| callback | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 否 | 要移除的事件监听的回调函数。 |

**示例**

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", () => {
  console.info("alert listener callback");
})

workerPort.removeEventListener('alert');
```
