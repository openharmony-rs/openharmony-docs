# Worker

Worker类包含所有Worker功能。

**继承/实现关系：** Worker implements [EventTarget](arkts-arkts-worker-eventtarget-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ThreadWorker](arkts-arkts-worker-threadworker-c.md)

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

创建一个worker实例。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** constructor

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scriptURL | string | 是 | scriptURL worker执行的脚本URL。 |
| options | [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | 否 | 可为worker设置的选项。 |

**示例**

以下示例展示了在Stage模型的entry模块Index.ets文件中加载Worker线程文件的方法，使用Library加载Worker线程文件的场景参考[文件路径注意事项](../../../arkts-utils/worker-introduction.md#文件路径注意事项)。

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

// worker文件所在路径："entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.ThreadWorker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```

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

移除Worker的事件监听。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** off

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 需要移除的事件类型。 |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 否 | listener 要移除的事件监听的回调函数。 |

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

向Worker添加一个事件监听。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | type 向Worker添加一个事件监听。 |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 是 | listener 当指定类型的事件发生时调用的回调函数。 |

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

向Worker添加一个事件监听， 该事件监听只执行一次，执行完后会自动删除。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** once

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [EventListener](arkts-arkts-worker-eventlistener-i.md) | 是 | listener 当指定类型的事件发生时调用的回调函数。 |

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

**替代接口：** onerror

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

**替代接口：** onexit

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 |  |

## onmessage

```TypeScript
onmessage?: (event: MessageEvent) => void
```

回调函数。表示宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中event类型为MessageEvent， 表示收到的Worker消息数据。默认值为undefined。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** onmessage

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

**替代接口：** onmessageerror

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [MessageEvent](arkts-arkts-worker-messageevent-i.md) | 是 |  |

## postMessage

```TypeScript
postMessage(message: Object, transfer: ArrayBuffer[]): void
```

向Worker线程发送消息。 数据通过结构化克隆算法传递。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** postMessage

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至Worker的数据。 |
| transfer | ArrayBuffer[] | 是 | transfer 可转移的ArrayBuffer实例对象。 transferList数组不可包含null。 |

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

向Worker线程发送消息。 数据通过结构化克隆算法传递。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** postMessage

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至Worker的数据。 |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 否 | 可为postMessage设置的选项。 transferList数组不可包含null。 |

**示例**

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

由宿主线程主动销毁Worker线程并停止Worker线程接收消息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** terminate

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.terminate();
```

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.terminate();
```
