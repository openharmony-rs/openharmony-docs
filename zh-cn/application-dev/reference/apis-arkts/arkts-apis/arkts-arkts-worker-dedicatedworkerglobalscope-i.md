# DedicatedWorkerGlobalScope

Worker线程自身的运行环境，与宿主线程环境隔离。

**继承/实现关系：** DedicatedWorkerGlobalScope extends [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ThreadWorkerGlobalScope](arkts-arkts-worker-threadworkerglobalscope-i.md)

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

**替代接口：** close

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
```

```TypeScript
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    workerPort.close();
}
```

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

回调函数，表示Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用的事件处理程序，处理程序在Worker线程中执行。其中this指调用者对象本身DedicatedWorkerGlobalScope， ev类型为MessageEvent，表示收到的Worker消息数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onmessage

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

回调函数，表示当Worker对象接收到一条无法被反序列化的消息时被调用的事件处理程序，处理程序在Worker线程中执行。其中this指调用者对象本身DedicatedWorkerGlobalScope， ev类型为MessageEvent，表示收到的Worker消息数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onmessageerror

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

Worker线程向宿主线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** postMessage

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | messageObject 发送至宿主线程的数据。 |
| transfer | Transferable[] | 是 | transfer 数组不可包含null。 |

**示例**

```TypeScript
// Worker.ets
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

// 创建worker线程中与宿主线程通信的对象
const workerPort = worker.workerPort;

// worker线程接收宿主线程信息
workerPort.onmessage = (e: MessageEvents): void => {
  // data：宿主线程发送的信息
  let data: ArrayBuffer = e.data;
  // 往收到的buffer里写入数据
  const view = new Int8Array(data).fill(3);
  // worker线程向宿主线程发送信息
  workerPort.postMessage(view);
}

// worker线程发生error的回调
workerPort.onerror = (err: ErrorEvent) => {
  console.error("worker.ets onerror" + err.message);
}
```

```TypeScript
// Index.ets
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            // 宿主线程中创建Worker对象
            const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
            // 宿主线程向worker线程传递信息
            const buffer = new ArrayBuffer(8);
            workerInstance.postMessage(buffer, [buffer]);

            // 此时buffer的所有权转移到了worker线程，在宿主线程中不可用
            // const view = new Int8Array(buffer).fill(3);

            // 宿主线程接收worker线程信息
            workerInstance.onmessage = (e: MessageEvents): void => {
              // data：worker线程发送的信息
              let data: Int8Array = e.data;
              console.info("main thread data is  " + data);
              // 销毁Worker对象
              workerInstance.terminate();
            }
            // 在调用terminate后，执行onexit
            workerInstance.onexit = (code) => {
              console.info("main thread terminate");
            }
            // 监听Worker错误
            workerInstance.onAllErrors = (err: ErrorEvent) => {
              console.error("main error message " + err.message);
            }
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

```TypeScript
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);

// 填入options参数，buffer的所有权会转移到Worker线程，在宿主线程中将不可用
workerInstance.postMessage(buffer, {transfer: [buffer]});
```

```TypeScript
// Index.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
  console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
  let buffer = new ArrayBuffer(8);
  workerPort.postMessage(buffer, [buffer]);
}
```

```TypeScript
// Index.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    workerPort.postMessage("receive data from main thread");
}
```

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

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

Worker线程向宿主线程发送消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** postMessage

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | messageObject 发送至宿主线程的数据。 |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 否 | 可为postMessage设置的选项。 |

**示例**

```TypeScript
// Index.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    workerPort.postMessage("receive data from main thread");
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
postMessage(messageObject: Object, transfer: ArrayBuffer[]): void
```

Worker线程向宿主线程发送消息。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** postMessage

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | messageObject 发送至宿主线程的数据。 |
| transfer | ArrayBuffer[] | 是 | transfer 数组不可包含null。 |

**示例**

```TypeScript
// Index.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
  console.info("receive data from worker.ets");
}
```

```TypeScript
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
  let buffer = new ArrayBuffer(8);
  workerPort.postMessage(buffer, [buffer]);
}
```

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
