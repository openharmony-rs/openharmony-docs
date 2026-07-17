# ThreadWorkerGlobalScope

Worker线程用于与宿主线程通信的类。其中postMessage接口用于向宿主线程发送消息，close接口用于销毁Worker线程。ThreadWorkerGlobalScope类继承GlobalScope9+。

**继承/实现关系：** ThreadWorkerGlobalScope extends [GlobalScope](arkts-arkts-worker-globalscope-i.md)

**起始版本：** 9

<!--Device-unnamed-export interface ThreadWorkerGlobalScope extends GlobalScope--><!--Device-unnamed-export interface ThreadWorkerGlobalScope extends GlobalScope-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## callGlobalCallObjectMethod

```TypeScript
callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object
```

Worker线程调用宿主线程上注册的对象的指定方法，此调用对Worker线程同步，对宿主线程异步，返回值通过数据拷贝传递。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object--><!--Device-ThreadWorkerGlobalScope-callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instanceName | string | 是 | 注册对象时使用的键，用于在宿主线程中查找对象。 |
| methodName | string | 是 | 在已注册对象上调用的方法名。该方法不能使用async修饰，也不能基于底层异步机制返回结果，否则会抛出异常。 |
| timeout | number | 是 | 表示从Worker线程发起调用开始到在主线程中执行目标方法的最大等待时间，单位为ms，取整数，取值范围为[1-5000]。也可取特殊值0，此时表示本次调用等待时间为5000ms。该值应为整数。<br>单位：ms。 |
| args | Object[] | 是 | 注册对象上所调用方法的参数数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 返回值为调用方法在宿主线程的返回值，无返回值时返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200019](../errorcode-utils.md#10200019-调用未注册对象的方法错误) | The globalCallObject is not registered. |
| [10200020](../errorcode-utils.md#10200020-调用注册对象上的方法类型错误) | The method to be called is not callable or is an async method or a generator. |
| [10200021](../errorcode-utils.md#10200021-全局调用等待超时错误) | The global call exceeds the timeout. |

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
    console.info("worker:", res); // worker: this is a message from TestObj
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

## close

```TypeScript
close(): void
```

销毁Worker线程，终止Worker接收消息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-close(): void--><!--Device-ThreadWorkerGlobalScope-close(): void-End-->

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

## postMessage

```TypeScript
postMessage(messageObject: Object, transfer: ArrayBuffer[]): void
```

Worker线程通过转移对象所有权的方式向宿主线程发送消息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void--><!--Device-ThreadWorkerGlobalScope-postMessage(messageObject: Object, transfer: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | 发送至宿主线程的数据，该数据对象必须是可序列化对象。支持的参数类型请参考序列化支持类型。 |
| transfer | [ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md)[] | 是 | 表示可转移的ArrayBuffer实例对象数组，该数组中对象的所有权会被转移到宿主线程，转移后该对象仅在宿主线程中可用。该数组不可传入null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |

**示例：**

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

## postMessage

```TypeScript
postMessage(messageObject: Object, options?: PostMessageOptions): void
```

Worker线程通过转移对象所有权或拷贝数据的方式向宿主线程发送消息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void--><!--Device-ThreadWorkerGlobalScope-postMessage(messageObject: Object, options?: PostMessageOptions): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| messageObject | Object | 是 | 发送至宿主线程的数据，该数据对象必须是可序列化对象。支持的参数类型请参考序列化支持类型。 |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 否 | 当填入该参数时，其作用与传入ArrayBuffer[]相同，该数组中对象的所有权会被转移到宿主线程，在Worker线程中将变为不可用，仅在宿主线程中可用。若不填入该参数，默认设置为undefined，通过拷贝数据的方式传输信息到宿主线程。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |

**示例：**

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

## postMessageAtFront

```TypeScript
postMessageAtFront?(message: Object, priority: Priority, transfer?: ArrayBuffer[]): void
```

Worker线程通过转移对象所有权的方式向宿主线程发送插队消息，并插入到对应优先级队列的队头。除Worker线程向主线程发送的场景外，该接口与postMessage功能一致。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-postMessageAtFront?(message: Object, priority: Priority, transfer?: ArrayBuffer[]): void--><!--Device-ThreadWorkerGlobalScope-postMessageAtFront?(message: Object, priority: Priority, transfer?: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至宿主线程的数据，该数据对象必须是可序列化或可共享。支持的序列化类型请参考序列化支持类型。支持的共享类型请参考Sendable支持的数据类型。 |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | 是 | Worker EventHandler的优先级。 |
| transfer | [ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md)[] | 否 | 表示可转移的ArrayBuffer实例对象数组，该数组中对象的所有权会被转移到主线程，转移后该对象仅在主线程中可用。该数组不可传入null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |

**示例：**

```TypeScript
// worker文件路径为：entry/src/main/ets/workers/Worker.ets
// Worker.ets

import { MessageEvents, ThreadWorkerGlobalScope, worker, Priority } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  workerPort.postMessage("1");
  workerPort.postMessage("2");
  // 方式1：使用可选链操作符（推荐，最简洁）
  workerPort.postMessageAtFront?.("3-idle", Priority.IDLE);
  workerPort.postMessageAtFront?.("4-immediate", Priority.IMMEDIATE);

  // 方式2：使用非空断言，直接调用（需要确定它一定存在）
  workerPort.postMessageAtFront!("5-low", Priority.LOW);

  // 方式3：判断方法存在后再使用
  if (workerPort.postMessageAtFront) {
    workerPort.postMessageAtFront("6-high", Priority.HIGH);
  } else {
    workerPort.postMessageWithSharedSendable("6-high");
  }
}

```

```TypeScript
// Index.ets
// 接收Worker线程传递至宿主线程的数据

import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
workerInstance.postMessage("start");
workerInstance.onmessage = (e: MessageEvents) => {
  // 模拟耗时操作
  let start = new Date().getTime();
  while (new Date().getTime() - start < 1000) {
    continue;
  }
  let res: string = e.data as string;
  // 执行效果：
  // result is: 1
  // result is: 4-immediate
  // result is: 6-high
  // result is: 2
  // result is: 5-low
  // result is: 3-idle
  console.info("result is: " + res);
}

```

如果传递的参数是对象字面量的话，需要[显式标注对象字面量的类型](../../quick-start/typescript-to-arkts-migration-guide.md#需要显式标注对象字面量的类型)。

```TypeScript
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent, Priority } from '@kit.ArkTS';

class ClassA {
  public obj: string = ""
}

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  // 使用可选链操作符调用接口，传递字面量对象时会编译报错，需要显式标注对象字面量的类型。
  // workerPort.postMessageAtFront?.({obj: "obj"}, Priority.HIGH);

  let classAInstance: ClassA = { obj: "obj" };
  workerPort.postMessageAtFront?.(classAInstance, Priority.HIGH);

  // 使用非空断言，直接调用。可以直接传递对象字面量。
  workerPort.postMessageAtFront!({ obj: "obj" }, Priority.HIGH);
  // 判断方法存在后再使用。可以直接传递对象字面量。
  if (workerPort.postMessageAtFront) {
    workerPort.postMessageAtFront({ obj: "obj" }, Priority.HIGH);
  } else {
    workerPort.postMessageWithSharedSendable({ obj: "obj" });
  }
}

```

## postMessageWithSharedSendable

```TypeScript
postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void
```

Worker线程向宿主线程发送消息，消息中的Sendable对象通过引用传递，非Sendable对象通过拷贝数据的方式传递。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void--><!--Device-ThreadWorkerGlobalScope-postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | Object | 是 | 发送至宿主线程的数据，该数据对象必须是可序列化或可共享。支持的序列化类型请参考序列化支持类型。支持的共享类型请参考Sendable支持的数据类型。 |
| transfer | [ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md)[] | 否 | 表示可转移的ArrayBuffer实例对象数组，该数组中对象的所有权会被转移到宿主线程，转移后该对象仅在宿主线程中可用。该数组不可传入null。默认值为空数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |

**示例：**

```TypeScript
// worker文件路径为：entry/src/main/ets/workers/Worker.ets
// Worker.ets
// 新建SendableObject实例并通过Worker线程传递至宿主线程

import { SendableObject } from '../pages/sendable';
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  let object: SendableObject = new SendableObject();
  workerPort.postMessageWithSharedSendable(object);
}

```

```TypeScript
// sendable.ets
// 定义SendableObject

@Sendable
export class SendableObject {
  a:number = 45;
}

```

```TypeScript
// Index.ets
// 接收Worker线程传递至宿主线程的数据并访问其属性

import { worker, MessageEvents } from '@kit.ArkTS';
import { SendableObject } from './sendable';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
workerInstance.postMessage(1);
workerInstance.onmessage = (e: MessageEvents) => {
  let obj: SendableObject = e.data;
  console.info("sendable index obj is: " + obj.a);
}

```

## onmessage

```TypeScript
onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void
```

当Worker线程收到来自其宿主线程通过postMessage接口发送的消息时调用的事件处理程序，该事件处理程序在Worker线程中执行。其中this指调用者对象本身ThreadWorkerGlobalScope，ev类型为MessageEvents，表示收到的消息数据。

**类型：** (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void--><!--Device-ThreadWorkerGlobalScope-onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

## onmessageerror

```TypeScript
onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void
```

当Worker线程收到一条无法被反序列化的消息时调用的事件处理程序，该事件处理程序在Worker线程中执行。其中this指调用者对象本身ThreadWorkerGlobalScope，ev类型为MessageEvents，表示收到的消息数据。

**类型：** (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadWorkerGlobalScope-onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void--><!--Device-ThreadWorkerGlobalScope-onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

