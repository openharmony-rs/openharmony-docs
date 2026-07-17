# DedicatedWorkerGlobalScope

Worker线程自身的运行环境，与宿主线程环境隔离。

**继承/实现关系：** DedicatedWorkerGlobalScope extends [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** ThreadWorkerGlobalScope

<!--Device-unnamed-export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope--><!--Device-unnamed-export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## close

```TypeScript
close(): void
```

销毁Worker线程，终止Worker接收消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** close

<!--Device-DedicatedWorkerGlobalScope-close(): void--><!--Device-DedicatedWorkerGlobalScope-close(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");

```

```TypeScript
// worker.ets
import { worker } from '@kit.ArkTS';

const parentPort = worker.parentPort;
parentPort.onmessage = (): void => {
    parentPort.close()
}

```

## postMessage

```TypeScript
postMessage(messageObject: Object, transfer: Transferable[]): void
```

Worker线程向宿主线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** postMessage

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: Transferable[]): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: Transferable[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | messageObject 发送至宿主线程的数据。 |
| transfer | Transferable[] | 是 | transfer 数组不可包含null。 |

## postMessage

```TypeScript
postMessage(messageObject: Object, options?: PostMessageOptions): void
```

Worker线程向宿主线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** postMessage

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | messageObject 发送至宿主线程的数据。 |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 否 | 可为postMessage设置的选项。 |

**示例：**

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
import { ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const parentPort = worker.parentPort;
parentPort.onmessage = (e: MessageEvents) => {
  parentPort.postMessage("receive data from main thread");
}

```

## postMessage

```TypeScript
postMessage(messageObject: Object, transfer: ArrayBuffer[]): void
```

Worker线程向宿主线程发送消息。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** postMessage

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | messageObject 发送至宿主线程的数据。 |
| transfer | [ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md)[] | 是 | transfer 数组不可包含null。 |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    // let data = e.data;
    console.info("receive data from worker.ets");
}

```

```TypeScript
// worker.ets
import { DedicatedWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.onmessage = (): void => {
    // let data = e.data;
    let buffer = new ArrayBuffer(5)
    workerPort.postMessage(buffer, [buffer]);
}

```

## onmessage

```TypeScript
onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void
```

onmessage属性用于指定当Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用的事件处理程序，该事件处理程序在Worker线程中执行。

**类型：** (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onmessage

<!--Device-DedicatedWorkerGlobalScope-onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void--><!--Device-DedicatedWorkerGlobalScope-onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

## onmessageerror

```TypeScript
onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void
```

onmessage属性用于指定当Worker线程收到一条无法被反序列化的消息时被调用的事件处理程序，该事件处理程序在Worker线程中执行。

**类型：** (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onmessageerror

<!--Device-DedicatedWorkerGlobalScope-onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void--><!--Device-DedicatedWorkerGlobalScope-onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

