# Worker

```TypeScript
class Worker implements EventTarget
```

Worker类包含所有Worker功能。

**继承/实现关系：** Worker implements [EventTarget](arkts-arkts-worker-eventtarget-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ThreadWorker](arkts-arkts-worker-threadworker-c.md)

<!--Device-worker-class Worker implements EventTarget--><!--Device-worker-class Worker implements EventTarget-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

Worker构造函数。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [constructor](arkts-arkts-worker-threadworker-c.md#constructor)

<!--Device-Worker-constructor(scriptURL: string, options?: WorkerOptions)--><!--Device-Worker-constructor(scriptURL: string, options?: WorkerOptions)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scriptURL | string | 是 | Worker线程文件的路径，详细参考文件路径注意事项。 |
| options | [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | 否 | Worker构造的选项。 |

**示例**

此处以在Stage模型的entry模块Index.ets文件中加载Worker线程文件为例，使用Library加载Worker线程文件的场景参考[文件路径注意事项](../../../arkts-utils/worker-introduction.md#文件路径注意事项)。

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

// worker文件所在路径："entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.Worker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```

## off

```TypeScript
off(type: string, listener?: EventListener): void
```

移除类型为type的事件监听，该接口与removeEventListener接口功能一致。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [off](arkts-arkts-worker-threadworker-c.md#off)

<!--Device-Worker-off(type: string, listener?: EventListener): void--><!--Device-Worker-off(type: string, listener?: EventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 需要删除的事件类型。事件类型通过on设置。 |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 否 | 需要删除的特定监听器回调函数。如果未传入此参数，则会删除该类型的所有监听器。 |

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
// 使用on接口、once接口或addEventListener接口创建“alert”事件，使用off接口删除事件。
workerInstance.off("alert");
```

## on

```TypeScript
on(type: string, listener: EventListener): void
```

向Worker添加一个事件监听，该接口与addEventListener接口功能一致。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [on](arkts-arkts-worker-threadworker-c.md#on)

<!--Device-Worker-on(type: string, listener: EventListener): void--><!--Device-Worker-on(type: string, listener: EventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 是 | 事件触发时的回调函数。 |

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.on("alert", () => {
    console.info("alert listener callback");
})
```

## once

```TypeScript
once(type: string, listener: EventListener): void
```

向Worker添加一个事件监听，该事件监听只执行一次，执行完后会自动删除。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [once](arkts-arkts-worker-threadworker-c.md#once)

<!--Device-Worker-once(type: string, listener: EventListener): void--><!--Device-Worker-once(type: string, listener: EventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 是 | 事件触发时的回调函数。 |

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.once("alert", () => {
    console.info("alert listener callback");
})
```

## onerror

```TypeScript
onerror?: (err: ErrorEvent) => void
```

回调函数。表示Worker在执行过程中发生异常被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中err类型为ErrorEvent，表示收到的异常数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [onerror](arkts-arkts-worker-threadworker-c.md#onerror)

<!--Device-Worker-onerror?: (err: ErrorEvent) => void--><!--Device-Worker-onerror?: (err: ErrorEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | 是 |  |

## onexit

```TypeScript
onexit?: (code: number) => void
```

回调函数。表示Worker销毁时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中code类型为number，异常退出为1，正常退出为0。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [onexit](arkts-arkts-worker-threadworker-c.md#onexit)

<!--Device-Worker-onexit?: (code: number) => void--><!--Device-Worker-onexit?: (code: number) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 |  |

## onmessage

```TypeScript
onmessage?: (event: MessageEvent) => void
```

回调函数。表示宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中event类型为MessageEvent，表示收到的Worker消息数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [onmessage](arkts-arkts-worker-threadworker-c.md#onmessage)

<!--Device-Worker-onmessage?: (event: MessageEvent) => void--><!--Device-Worker-onmessage?: (event: MessageEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | 是 |  |

## onmessageerror

```TypeScript
onmessageerror?: (event: MessageEvent) => void
```

回调函数。表示当Worker对象接收到一条无法被序列化的消息时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中event类型为MessageEvent，表示收到的Worker消息数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [onmessageerror](arkts-arkts-worker-threadworker-c.md#onmessageerror)

<!--Device-Worker-onmessageerror?: (event: MessageEvent) => void--><!--Device-Worker-onmessageerror?: (event: MessageEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | 是 |  |

## postMessage

```TypeScript
postMessage(message: Object, transfer: ArrayBuffer[]): void
```

宿主线程通过转移对象所有权的方式向Worker线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [postMessage](arkts-arkts-worker-threadworker-c.md#postmessage)

<!--Device-Worker-postMessage(message: Object, transfer: ArrayBuffer[]): void--><!--Device-Worker-postMessage(message: Object, transfer: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至Worker的数据对象必须是可序列化对象，序列化支持类型见序列化支持类型。 |
| transfer | ArrayBuffer[] | 是 | 表示可转移的ArrayBuffer实例对象数组，所有权会转移到Worker线程，仅在该线程中可用。数组不可传入null。 |

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

## postMessage

```TypeScript
postMessage(message: Object, options?: PostMessageOptions): void
```

宿主线程通过转移对象所有权或者拷贝数据的方式向Worker线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [postMessage](arkts-arkts-worker-threadworker-c.md#postmessage)

<!--Device-Worker-postMessage(message: Object, options?: PostMessageOptions): void--><!--Device-Worker-postMessage(message: Object, options?: PostMessageOptions): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至Worker的数据，该数据对象必须是可序列化对象，序列化支持类型见序列化支持类型。 |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 否 | 当填入该参数时，与传入ArrayBuffer[]的作用一致，该数组中对象的所有权会被转移到Worker线程，在宿主线程中将变为不可用，仅在Worker线程中可用。若不填入该参数，默认设置为undefined，通过拷贝数据的方式传输信息到Worker线程。 |

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

## terminate

```TypeScript
terminate(): void
```

销毁Worker线程，终止Worker接收消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [terminate](arkts-arkts-worker-threadworker-c.md#terminate)

<!--Device-Worker-terminate(): void--><!--Device-Worker-terminate(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.terminate();
```
