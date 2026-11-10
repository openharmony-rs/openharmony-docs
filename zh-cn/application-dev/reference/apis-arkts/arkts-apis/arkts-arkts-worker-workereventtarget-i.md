# WorkerEventTarget

```TypeScript
export interface WorkerEventTarget
```

用于管理Worker的监听事件。

**起始版本：** 9

<!--Device-unnamed-export interface WorkerEventTarget--><!--Device-unnamed-export interface WorkerEventTarget-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## addEventListener

```TypeScript
addEventListener(type: string, listener: WorkerEventListener): void
```

向Worker线程的实例对象添加事件监听。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-WorkerEventTarget-addEventListener(type: string, listener: WorkerEventListener): void--><!--Device-WorkerEventTarget-addEventListener(type: string, listener: WorkerEventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 是 | 回调的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-worker不支持某api) | The called API is not supported in the worker thread. |

**示例**

```TypeScript
// worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.addEventListener("alert", () => {
    console.info("alert listener callback");
  })
};
```

## dispatchEvent

```TypeScript
dispatchEvent(event: Event): boolean
```

在Worker线程将事件对象分发到Worker线程的事件系统，并触发该类型事件的所有监听器回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-WorkerEventTarget-dispatchEvent(event: Event): boolean--><!--Device-WorkerEventTarget-dispatchEvent(event: Event): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Event](arkts-arkts-worker-event-i.md) | 是 | 需要分发的事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 分发的结果。true表示分发成功，false表示分发失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例**

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

## removeAllListener

```TypeScript
removeAllListener(): void
```

移除Worker线程的实例对象所有的事件监听。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-WorkerEventTarget-removeAllListener(): void--><!--Device-WorkerEventTarget-removeAllListener(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例**

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

## removeEventListener

```TypeScript
removeEventListener(type: string, callback?: WorkerEventListener): void
```

移除Worker线程实例对象中类型为type的事件监听。该接口与off9+接口功能一致。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-WorkerEventTarget-removeEventListener(type: string, callback?: WorkerEventListener): void--><!--Device-WorkerEventTarget-removeEventListener(type: string, callback?: WorkerEventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 需要删除的监听事件类型。事件类型通过addEventListener设置。 |
| callback | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 否 | 需要删除的特定监听器回调函数。如果未传入此参数，则会删除该类型的所有监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例**

```TypeScript
// worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.addEventListener("alert", () => {
    console.info("alert listener callback");
  });

  workerPort.removeEventListener("alert");
};
```
