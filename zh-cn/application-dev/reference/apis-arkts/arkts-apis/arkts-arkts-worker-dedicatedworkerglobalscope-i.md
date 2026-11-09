# DedicatedWorkerGlobalScope

```TypeScript
export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope
```

Worker线程自身的运行环境，与宿主线程环境隔离。

**继承/实现关系：** DedicatedWorkerGlobalScope extends [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ThreadWorkerGlobalScope](arkts-arkts-worker-threadworkerglobalscope-i.md)

<!--Device-unnamed-export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope--><!--Device-unnamed-export interface DedicatedWorkerGlobalScope extends WorkerGlobalScope-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## close

```TypeScript
close(): void
```

销毁Worker线程，终止Worker接收消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [close](arkts-arkts-worker-threadworkerglobalscope-i.md#close)

<!--Device-DedicatedWorkerGlobalScope-close(): void--><!--Device-DedicatedWorkerGlobalScope-close(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

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

## onmessage

```TypeScript
onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void
```

回调函数，表示Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用的事件处理程序，处理程序在Worker线程中执行。其中this指调用者对象本身DedicatedWorkerGlobalScope，ev类型为MessageEvent，表示收到的Worker消息数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [onmessage](arkts-arkts-worker-threadworkerglobalscope-i.md#onmessage)

<!--Device-DedicatedWorkerGlobalScope-onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void--><!--Device-DedicatedWorkerGlobalScope-onmessage?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| this | [DedicatedWorkerGlobalScope](arkts-arkts-worker-dedicatedworkerglobalscope-i.md) | 是 |  |
| ev | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | 是 |  |

## onmessageerror

```TypeScript
onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void
```

回调函数，表示当Worker对象接收到一条无法被反序列化的消息时被调用的事件处理程序，处理程序在Worker线程中执行。其中this指调用者对象本身DedicatedWorkerGlobalScope，ev类型为MessageEvent，表示收到的Worker消息数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [onmessageerror](arkts-arkts-worker-threadworkerglobalscope-i.md#onmessageerror)

<!--Device-DedicatedWorkerGlobalScope-onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void--><!--Device-DedicatedWorkerGlobalScope-onmessageerror?: (this: DedicatedWorkerGlobalScope, ev: MessageEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| this | [DedicatedWorkerGlobalScope](arkts-arkts-worker-dedicatedworkerglobalscope-i.md) | 是 |  |
| ev | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | 是 |  |

## postMessage

```TypeScript
postMessage(messageObject: Object, transfer: Transferable[]): void
```

Worker线程通过转移对象所有权的方式向宿主线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [postMessage](arkts-arkts-worker-threadworkerglobalscope-i.md#postmessage)

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: Transferable[]): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: Transferable[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | 发送至宿主线程的数据，该数据对象必须是可序列化对象，序列化支持类型见序列化支持类型。 |
| transfer | Transferable[] | 是 | 暂不支持该参数类型。 |

**示例**

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
postMessage(messageObject: Object, options?: PostMessageOptions): void
```

Worker线程通过转移对象所有权或者拷贝数据的方式向宿主线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [postMessage](arkts-arkts-worker-threadworkerglobalscope-i.md#postmessage)

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | 发送至宿主线程的数据，该数据对象必须是可序列化对象，序列化支持类型见序列化支持类型。 |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 否 | 当填入该参数时，与传入ArrayBuffer[]的作用一致，该数组中对象的所有权会被转移到宿主线程，在Worker线程中将会变为不可用，仅在宿主线程中可用。若不填入该参数，默认设置为 undefined，通过拷贝数据的方式传输信息到宿主线程。 |

**示例**

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

Worker线程通过转移对象所有权的方式向宿主线程发送消息。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [postMessage](arkts-arkts-worker-threadworkerglobalscope-i.md#postmessage)

<!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void--><!--Device-DedicatedWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | 发送至宿主线程的数据，该数据对象必须是可序列化对象，序列化支持类型见序列化支持类型。 |
| transfer | ArrayBuffer[] | 是 | 表示可转移的ArrayBuffer实例对象数组，该数组中对象的所有权会被转移到宿主线程，在Worker线程中将会变为不可用，仅在宿主线程中可用，数组不可传入null。 |

**示例**

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
