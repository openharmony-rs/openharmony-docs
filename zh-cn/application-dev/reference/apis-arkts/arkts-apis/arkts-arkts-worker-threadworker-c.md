# ThreadWorker

使用以下方法前，需先构造ThreadWorker实例。ThreadWorker类继承WorkerEventTarget。

**继承/实现关系：** ThreadWorker implements [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md)

**起始版本：** 9

<!--Device-worker-class ThreadWorker implements WorkerEventTarget--><!--Device-worker-class ThreadWorker implements WorkerEventTarget-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## addEventListener

```TypeScript
addEventListener(type: string, listener: WorkerEventListener): void
```

向宿主线程的Worker实例对象添加一个事件监听，该接口与on9+接口功能一致。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-addEventListener(type: string, listener: WorkerEventListener): void--><!--Device-ThreadWorker-addEventListener(type: string, listener: WorkerEventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 是 | 当指定类型的事件发生时调用的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-worker不支持某api) | The called API is not supported in the worker thread. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

// 执行 alert 事件类型的回调
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

```

## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

ThreadWorker构造函数，用于创建一个ThreadWorker实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-constructor(scriptURL: string, options?: WorkerOptions)--><!--Device-ThreadWorker-constructor(scriptURL: string, options?: WorkerOptions)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scriptURL | string | 是 | Worker线程文件的路径。详细规则请参考文件路径注意事项。 |
| options | [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | 否 | 可为Worker实例设置的选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-worker初始化失败) | Worker initialization failed. |
| [10200007](../errorcode-utils.md#10200007-worker文件路径异常) | The worker file path is invalid. |

**示例：**

以下示例展示了在Stage模型的entry模块Index.ets文件中加载Worker线程文件的方法，使用Library加载Worker线程文件的场景参考[文件路径注意事项](../../arkts-utils/worker-introduction.md#文件路径注意事项)。

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

// worker文件所在路径："entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.ThreadWorker('entry/ets/workers/worker.ets', {name: "WorkerThread"});

```

## dispatchEvent

```TypeScript
dispatchEvent(event: Event): boolean
```

分发定义在Worker线程的事件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-dispatchEvent(event: Event): boolean--><!--Device-ThreadWorker-dispatchEvent(event: Event): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Event](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact-event-c.md) | 是 | 需要分发的事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | @throws { BusinessError } 10200004 - The Worker instance is not running. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例：**

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

## off

```TypeScript
off(type: string, listener?: WorkerEventListener): void
```

移除宿主线程的Worker实例对象中类型为type的事件监听，该接口与removeEventListener9+接口功能一致。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-off(type: string, listener?: WorkerEventListener): void--><!--Device-ThreadWorker-off(type: string, listener?: WorkerEventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 需要移除的事件类型。 |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 否 | listener 要移除的事件监听的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-worker不支持某api) | The called API is not supported in the worker thread. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

const handler1 = () => console.info("Handler 1");
const handler2 = () => console.info("Handler 2");

// 注册两个监听器
workerInstance.on("alert", handler1);
workerInstance.on("alert", handler2);

// 首次触发：两个监听器都会执行
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

// 删除 handler1 监听器
workerInstance.off("alert", handler1);

// 再次触发：只剩 handler2 会执行
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

// 删除"alert"类型所有监听器
workerInstance.off("alert");

```

## on

```TypeScript
on(type: string, listener: WorkerEventListener): void
```

向宿主线程的Worker实例对象添加一个事件监听，该接口与addEventListener9+接口功能一致。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-on(type: string, listener: WorkerEventListener): void--><!--Device-ThreadWorker-on(type: string, listener: WorkerEventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 是 | 当指定类型的事件发生时调用的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-worker不支持某api) | The called API is not supported in the worker thread. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.on("alert", () => {
    console.info("alert listener callback");
})

// 使用on添加的事件监听可以多次执行
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

```

## once

```TypeScript
once(type: string, listener: WorkerEventListener): void
```

向宿主线程的Worker实例对象添加一个事件监听，该事件监听只执行一次，执行完后会自动删除。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-once(type: string, listener: WorkerEventListener): void--><!--Device-ThreadWorker-once(type: string, listener: WorkerEventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 监听的事件类型。 |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 是 | listener 当指定类型的事件发生时调用的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-worker不支持某api) | The called API is not supported in the worker thread. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.once("alert", () => {
  console.info("alert listener callback");
})

workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

```

## postMessage

```TypeScript
postMessage(message: Object, transfer: ArrayBuffer[]): void
```

宿主线程通过转移对象所有权的方式向Worker线程发送消息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-postMessage(message: Object, transfer: ArrayBuffer[]): void--><!--Device-ThreadWorker-postMessage(message: Object, transfer: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至Worker线程的数据，该数据对象必须是可序列化对象。支持的参数类型请参考序列化支持类型。 |
| transfer | ArrayBuffer[] | 是 | 表示可转移的ArrayBuffer实例对象数组，该数组中对象的所有权会被转移到Worker线程，转移后该对象仅在Worker线程中可用。该数组不可传入null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |

**示例：**

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

## postMessage

```TypeScript
postMessage(message: Object, options?: PostMessageOptions): void
```

宿主线程可以通过转移对象所有权或拷贝数据的方式向Worker线程发送消息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-postMessage(message: Object, options?: PostMessageOptions): void--><!--Device-ThreadWorker-postMessage(message: Object, options?: PostMessageOptions): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至Worker线程的数据，该数据对象必须是可序列化对象。支持的参数类型请参考序列化支持类型。 |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 否 | 当填入该参数时，其作用与传入ArrayBuffer[]相同，该数组中对象的所有权会被转移到Worker线程，在宿主线程中将变为不可用，仅在Worker线程中可用。若不填入该参数，默认设置为undefined，通过拷贝数据的方式传输信息到Worker线程。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |

**示例：**

```TypeScript
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);

// 填入options参数，buffer的所有权会转移到Worker线程，在宿主线程中将不可用
workerInstance.postMessage(buffer, {transfer: [buffer]});

```

## postMessageWithSharedSendable

```TypeScript
postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void
```

宿主线程向Worker线程发送消息，消息中的Sendable对象通过引用传递，非Sendable对象通过拷贝数据的方式传递。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void--><!--Device-ThreadWorker-postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至Worker线程的数据，该数据对象必须是可序列化或可共享。支持的序列化类型请参考序列化支持类型。支持的共享类型请参考Sendable支持的数据类型。 |
| transfer | ArrayBuffer[] | 否 | 表示可转移的ArrayBuffer实例对象数组，该数组中对象的所有权会被转移到Worker线程，转移后该对象仅在Worker线程中可用。该数组不可传入null。默认值为空数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |

**示例：**

```TypeScript
// Index.ets
// 新建SendableObject实例并通过宿主线程传递至Worker线程

import { worker } from '@kit.ArkTS';
import { SendableObject } from './sendable';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
let object: SendableObject = new SendableObject();
workerInstance.postMessageWithSharedSendable(object);

// 使用postMessage接口传递Sendable对象，使用拷贝数据的方式传递
workerInstance.postMessage(object);

```

```TypeScript
// sendable.ets
// 定义SendableObject

@Sendable
export class SendableObject {
  value:number = 45;
}

```

```TypeScript
// worker文件路径为：entry/src/main/ets/workers/Worker.ets
// Worker.ets
// 接收宿主线程传递至Worker线程的数据并访问

import { SendableObject } from '../pages/sendable';
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (e: MessageEvents) => {
  let obj: SendableObject = e.data;
  console.info("sendable obj is: " + obj.value);
}

```

## registerGlobalCallObject

```TypeScript
registerGlobalCallObject(instanceName: string, globalCallObject: Object): void
```

在宿主线程的ThreadWorker实例上注册一个对象，该对象的方法可在Worker线程中通过callGlobalCallObjectMethod调用。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-registerGlobalCallObject(instanceName: string, globalCallObject: Object): void--><!--Device-ThreadWorker-registerGlobalCallObject(instanceName: string, globalCallObject: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instanceName | string | 是 | 注册对象时使用的键，调用时通过该键值找到被注册的对象。 |
| globalCallObject | Object | 是 | 被注册的对象，ThreadWorker实例会持有该对象的强引用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
class TestObj {
  private message : string = "this is a message from TestObj";
  public getMessage() : string {
    return this.message;
  }
  public getMessageWithInput(str : string) : string {
    return this.message + " with input: " + str;
  }
}
let registerObj = new TestObj();
// 在ThreadWorker实例上注册registerObj
workerInstance.registerGlobalCallObject("myObj", registerObj);
workerInstance.postMessage("start worker");

```

```TypeScript
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
  try {
    // 调用方法无入参
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessage", 0) as string;
    console.info("worker:", res) // worker: this is a message from TestObj
  } catch (error) {
    // 异常处理
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
  try {
    // 调用方法有入参
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessageWithInput", 0, "hello there!") as string;
    console.info("worker:", res); // worker: this is a message from TestObj with input: hello there!
  } catch (error) {
    // 异常处理
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
}

```

## removeAllListener

```TypeScript
removeAllListener(): void
```

移除宿主线程中Worker实例对象的所有事件监听。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-removeAllListener(): void--><!--Device-ThreadWorker-removeAllListener(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.addEventListener("alert", () => {
    console.info("alert listener callback");
})
workerInstance.removeAllListener();

```

## removeEventListener

```TypeScript
removeEventListener(type: string, callback?: WorkerEventListener): void
```

移除宿主线程的Worker实例对象中类型为type的事件监听，该接口与off9+接口功能一致。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-removeEventListener(type: string, callback?: WorkerEventListener): void--><!--Device-ThreadWorker-removeEventListener(type: string, callback?: WorkerEventListener): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 需要移除的事件类型。 |
| callback | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 否 | 移除监听事件后执行的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

workerInstance.removeEventListener("alert");

```

## terminate

```TypeScript
terminate(): void
```

销毁Worker线程，终止Worker接收消息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-terminate(): void--><!--Device-ThreadWorker-terminate(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.terminate();

```

## unregisterGlobalCallObject

```TypeScript
unregisterGlobalCallObject(instanceName?: string): void
```

取消在宿主线程ThreadWorker实例上注册的对象，该方法会释放ThreadWorker实例与目标对象之间的强引用。如果无匹配对象，该方法不会报错。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-unregisterGlobalCallObject(instanceName?: string): void--><!--Device-ThreadWorker-unregisterGlobalCallObject(instanceName?: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instanceName | string | 否 | 注册对象时使用的键。此参数不填时，会释放ThreadWorker实例中所有已注册的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |

**示例：**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
class TestObj {
  private message : string = "this is a message from TestObj";
  public getMessage() : string {
    return this.message;
  }
  public getMessageWithInput(str : string) : string {
    return this.message + " with input: " + str;
  }
}
let registerObj = new TestObj();
workerInstance.registerGlobalCallObject("myObj", registerObj);
// 取消对象注册
workerInstance.unregisterGlobalCallObject("myObj");
// 取消ThreadWorker实例上的所有对象注册
workerInstance.postMessage("start worker");

```

## onAllErrors

```TypeScript
onAllErrors?: ErrorCallback
```

表示Worker线程生命周期内发生异常被调用的事件处理程序，处理程序在宿主线程中执行。

onerror接口仅能捕获onmessage回调中同步方法产生的异常，无法捕获多线程回调和模块化相关异常。一旦捕获异常，Worker线程会进入销毁流程，无法继续使用。

onAllErrors接口可以捕获Worker线程的onmessage回调、timer回调以及文件执行等流程中产生的全局异常。捕获异常后，Worker线程仍然存活，可以继续使用。推荐使用onAllErrors替代onerror。

**类型：** ErrorCallback

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-onAllErrors?: ErrorCallback--><!--Device-ThreadWorker-onAllErrors?: ErrorCallback-End-->

**系统能力：** SystemCapability.Utils.Lang

## onerror

```TypeScript
onerror?: (err: ErrorEvent) => void
```

用于处理onmessage回调函数中同步代码产生的异常，处理程序在宿主线程中执行。回调函数的err类型为ErrorEvent，表示收到的异常数据。

**类型：** (err: ErrorEvent) =&gt; void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-onerror?: (err: ErrorEvent) => void--><!--Device-ThreadWorker-onerror?: (err: ErrorEvent) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

## onexit

```TypeScript
onexit?: (code: number) => void
```

当Worker线程销毁时被调用的事件处理程序，该处理程序在宿主线程中执行。回调函数的code参数类型为number，异常退出时code为1，正常退出时code为0。默认值为undefined。

**类型：** (code: number) =&gt; void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-onexit?: (code: number) => void--><!--Device-ThreadWorker-onexit?: (code: number) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

## onmessage

```TypeScript
onmessage?: (event: MessageEvents) => void
```

表示宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中event类型为MessageEvents，表示收到的Worker线程发送的消息数据。

**类型：** (event: MessageEvents) =&gt; void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-onmessage?: (event: MessageEvents) => void--><!--Device-ThreadWorker-onmessage?: (event: MessageEvents) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

## onmessageerror

```TypeScript
onmessageerror?: (event: MessageEvents) => void
```

当Worker线程收到一条无法被序列化的消息时被调用的事件处理程序，该事件处理程序在宿主线程中执行。其中回调函数中event类型为MessageEvents，表示收到的消息数据。

**类型：** (event: MessageEvents) =&gt; void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorker-onmessageerror?: (event: MessageEvents) => void--><!--Device-ThreadWorker-onmessageerror?: (event: MessageEvents) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

