# ArkTS-Sta EAWorker迁移指导
## 为什么需要迁移到EAWorker
ArkTS-Dyn 运行时采用单线程架构，其并发模型基于 Worker API 构建。该 API 继承自 W3C 的 Web Worker 标准，原本主要适用于 Web 场景，核心是将线程划分为宿主线程与 Worker 线程两种角色。随着 ArkTS-Sta 引入共享并发特性，原有 Worker API 的局限性逐渐显现 —— 其基于 Web 场景设计的线程角色划分，在多线程环境下会增加开发者的理解难度和使用门槛。为此，ArkTS-Sta 推出了全新的并发 API：EAWorker。EAWorker 是 "Exclusive ArkTS Worker" 的缩写，顾名思义，它在多线程环境中依然保持线程独占性，与传统 Worker 一样隐式绑定事件循环以处理异步任务。但相比之下，EAWorker 有两处关键改进：

1. 统一线程语义：取消了宿主线程与 Worker 线程的角色区分，所有线程通过一致的语义交互，简化了多线程编程模型。
1. 贴近传统线程的生命周期管理：借鉴 C++ 或 Java 中 Thread 的设计思路，提供更符合开发者直觉的生命周期控制方式，让线程管理更直观易用。

这一升级使 ArkTS 在支持共享并发的同时，大幅降低了多线程编程的理解与使用成本。
Worker API的使用场景是在后台线程中运行脚本，以执行耗时操作，避免计算密集型或高延迟任务阻塞宿主线程。EAWorker的使用场景与Worker API相同。

## EAWorker介绍
EAWorker的作用和使用场景和Worker API一样，主要作用是为应用程序提供一个多线程的运行环境，在后台线程中运行一个任务进行耗时操作，极大避免类似于计算密集型或高延迟的任务阻塞宿主线程的运行。

为了兼容ArkTS-Dyn基于事件循环的异步能力（如[setTimeout](../reference/common/js-apis-timer.md#settimeout)、[setInterval](../reference/common/js-apis-timer.md#setinterval)），EAWorker API必须同时包含线程、事件循环和消息发送处理的 API。与 Worker API类似，EAWorker API中的线程API语言类似于Java Thread。在典型场景下，开发者创建一个EAWorker实例，并在创建时给构造器传递一个EAWorker需要执行的线程任务。EAWorker实例启动后，必须显式调用 [start](../reference/native-lib/eaworker_managed.md#start) 启动事件循环；停止时需通过 [quit](../reference/native-lib/eaworker_managed.md#quit)来结束事件循环。开发者通过[MessageHandler](../reference/native-lib/message_handler.md)定义消息[Message](../reference/native-lib/message.md)（消息队列中的一个消息，消息可以携带数据和回调函数）的处理逻辑，一个事件循环可以绑定多个`MessageHandler`来处理不同类型和来源的消息。消息的发送也通过调用`MessageHandler`的API来完成，因此不同的消息可以绑定不同的消息处理逻辑。

EAWorker API中宿主线程和Worker线程的API没有区分，只有一种EAWorker API。所有EAWorker线程共享一个ArkTS-Sta运行时，除了EAWorker本身的开销外，不需要像Worker API一样创建独立的运行时。EAWorker线程之间的通信既可以通过消息传递，也可以利用ArkTS-Sta的共享内存特性。


## ThreadWorker API迁移

### constructor

constructor(scriptURL: string, options?: WorkerOptions)

ThreadWorker构造函数。

**ArkTS-Dyn**
```ts
import { worker } from '@kit.ArkTS';

// worker文件所在路径："entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.ThreadWorker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```

**ArkTS-Sta**
```ts
// 把ArkTS-Dyn中worker.ets里的任务改造成回调，传入EAWorker构造器第二个入参
const workerInstance = new EAWorker("WorkerThread", ()=>{console.info("等价worker.ets的回调");});
workerInstance.start();
```

### postMessage

postMessage(message: Object, transfer: ArrayBuffer[]): void

宿主线程通过转移对象所有权的方式向Worker线程发送消息。

**ArkTS-Dyn**
```ts
// Worker.ets
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

// 创建worker线程中与宿主线程通信的对象
const workerPort = worker.workerPort

// worker线程接收宿主线程信息
workerPort.onmessage = (e: MessageEvents): void => {
  // data：宿主线程发送的信息
  let data: number = e.data;
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
```ts
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
            // 宿主线程接收worker线程信息
            workerInstance.onmessage = (e: MessageEvents): void => {
              // data：worker线程发送的信息
              let data: number = e.data;
              console.info("main thread data is  " + data);
              // 销毁Worker对象
              workerInstance.terminate();
            }

            // 在调用terminate后，执行onexit
            workerInstance.onexit = (code) => {
              console.info("main thread terminate");
            }

            workerInstance.onAllErrors = (err: ErrorEvent) => {
              console.info("main error message " + err.message);
            }
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

**ArkTS-Sta**
```ts
// Index.ets

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import hilog from '@ohos.hilog';


@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            const currentworker = EAWorker.current()

            // 宿主线程中创建EAWorker对象并调用start()方法启动
            const workerInstance = new EAWorker("example worker");
            workerInstance.start();

            // 宿主线程接收EAWorker线程信息
            const currentCB = (msg: concurrency.Message) => {
              // data：worker线程发送的信息
              let data: Int8Array = msg.getObject() as Int8Array;
              console.info("main thread data is  " + data);
              // 销毁EAWorker对象
              workerInstance.quit();

              // 原本onexit的回调的逻辑可以放在这里
              console.info("main thread terminate");
            }
            let currentHandler = new concurrency.MessageHandler(currentCB, currentworker);

            // 向EAworker线程传递信息
            const workerCB = (msg: concurrency.Message) => {
              // data：宿主线程发送的信息
              let data: ArrayBuffer = msg.getObject() as ArrayBuffer;
              // 往收到的buffer里写入数据
              const view = new Int8Array(data).fill(3);
              // EAWorker线程向宿主线程发送信息
              let resultMessage = new concurrency.Message(1, view, currentHandler);
              resultMessage.sendToTarget();
            }
            let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

            const buffer = new ArrayBuffer(8);
            let workerMessage = new concurrency.Message(1, buffer, workerHandler);
            workerMessage.sendToTarget();

            workerInstance.setUncaughtExceptionHandler((err: Error) => {
              console.info("main error message " + err.message);
            })
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### postMessage

postMessage(message: Object, options?: PostMessageOptions): void

宿主线程通过转移对象所有权或者拷贝数据的方式向Worker线程发送消息。

**ArkTS-Dyn**
```ts
const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

**ArkTS-Sta**
```ts
const workerInstance = new EAWorker("worker");
workerInstance.start();
let workerHandler = new concurrency.MessageHandler((msg: concurrency.Message) => {}, workerInstance);

let workerMessage = new concurrency.Message(1, "hello world", workerHandler);
workerHandler.sendMessage(workerMessage);

let buffer = new ArrayBuffer(8);
workerMessage = new concurrency.Message(1, buffer, workerHandler);
workerHandler.sendMessage(workerMessage);
```


### postMessageWithSharedSendable

postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void

宿主线程向Worker线程发送消息，消息中的Sendable对象通过引用传递，消息中的非Sendable对象通过序列化传递。

**ArkTS-Dyn**

<!--code_no_check-->
```ts
// index.ets
// 新建SendableObject实例并通过宿主线程传递至worker线程

import { worker } from '@kit.ArkTS';
import { SendableObject } from './sendable'

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
let object: SendableObject = new SendableObject();
workerInstance.postMessageWithSharedSendable(object);
```

```ts
// sendable.ets
// 定义SendableObject

@Sendable
export class SendableObject {
  a:number = 45;
}
```

<!--code_no_check-->
```ts
// worker文件路径为：entry/src/main/ets/workers/Worker.ets
// Worker.ets
// 接收宿主线程传递至worker线程的数据并访问

import { SendableObject } from '../pages/sendable'
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  let obj: SendableObject = e.data;
  console.info("sendable obj is: " + obj.a);
}
```

**ArkTS-Sta**
```ts
// sendable.ets
// 定义SendableObject

export class SendableObject {
  a:number = 45;
}
```

```ts
// index.ets
// 新建SendableObject实例并通过宿主线程传递至worker线程

import { SendableObject } from './sendable'

// 宿主线程中创建EAWorker对象并调用start()方法启动
const workerInstance = new EAWorker("worker");
workerInstance.start();

const workerCB = (msg: concurrency.Message) => {
  let obj: SendableObject = msg.getObject() as SendableObject;
  console.info("sendable obj is: " + obj.a);
}
let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

let sendableObj: SendableObject = new SendableObject();
let workerMessage = new concurrency.Message(1, sendableObj, workerHandler);
workerHandler.sendMessage(workerMessage);
```


### on

on(type: string, listener: WorkerEventListener): void

向Worker添加一个事件监听，该接口与[addEventListener](#addeventlistener)接口功能一致。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");

          workerInstance.on("alert_on", () => {
            console.info("alert listener callback: alert_on");
          })

          // 使用on添加的事件监听可以多次执行
          workerInstance.dispatchEvent({type: "alert_on", timeStamp: 0}); // timeStamp暂未支持
          workerInstance.dispatchEvent({type: "alert_on", timeStamp: 0}); // timeStamp暂未支持
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

**ArkTS-Sta**
```ts
// Index.ets

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { Callback, emitter } from '@kit.BasicServicesKit';

let callback: Callback<emitter.GenericEventData<void>> = (eventData: emitter.GenericEventData<void>): void => {
  console.info("emitter callback: emitter_on");
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

let worker=new EAWorker("worker");


@Entry
@Component
struct Index {
  @State message: string = 'emitter on';


  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            worker.start();
            worker.run<void>(() => {
              emitter.onGenericEventData("emitter_on", callback);
              // 使用on添加的事件监听可以多次执行
              emitter.emit("emitter_on", options);
              emitter.emit("emitter_on", options);
            });
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### once

once(type: string, listener: WorkerEventListener): void

向Worker添加一个事件监听，事件监听只执行一次便自动删除。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");

          workerInstance.once("alert", () => {
            console.info("alert listener callback");
          })

          workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

          // 使用once添加的事件监听在执行一次后自动删除，无法多次执行
          // workerInstance.dispatchEvent({type: "alert", timeStamp: 0});
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

**ArkTS-Sta**
```ts
// Index.ets

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { Callback, emitter } from '@kit.BasicServicesKit';

let callback: Callback<emitter.GenericEventData<void>> = (eventData: emitter.GenericEventData<void>): void => {
  console.info("emitter callback: emitter_once");
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

let worker=new EAWorker("worker");


@Entry
@Component
struct Index {
  @State message: string = 'emitter once';


  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            worker.start();
            worker.run<void>(() => {
              emitter.onceGenericEventData("emitter_once", callback);
              emitter.emit("emitter_once", options);

              // 使用once添加的事件监听在执行一次后自动删除，无法多次执行
              // emitter.emit("emitter_once", options);
            });
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### off

off(type: string, listener?: WorkerEventListener): void

删除类型为type的事件监听，该接口与[removeEventListener](#removeeventlistener)接口功能一致。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");

          const handler1 = () => console.info("Handler 1");
          const handler2 = () => console.info("Handler 2");

          // 注册两个监听器
          workerInstance.on("alert", handler1);
          workerInstance.on("alert", handler2);

          // 首次触发：两个监听器都会执行
          workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

          // 删除handler1监听器
          workerInstance.off("alert", handler1);

          // 再次触发：只剩handler2会执行
          workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持

          // 删除"alert"类型所有监听器
          workerInstance.off("alert");
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

**ArkTS-Sta**
```ts
// Index.ets
// ArkTS-Sta中，emitter会将emit任务放入FFRT队列去执行，无法判断异步任务执行的具体时间，本示例采用延时执行的方式来模拟ArkTS-Dyn中的同步操作

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { Callback, emitter } from '@kit.BasicServicesKit';

let callback1: Callback<emitter.GenericEventData<void>> = (eventData: emitter.GenericEventData<void>): void => {
  console.info("emitter callback: emitter_off 1");
}

let callback2: Callback<emitter.GenericEventData<void>> = (eventData: emitter.GenericEventData<void>): void => {
  console.info("emitter callback: emitter_off 2");
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

let worker=new EAWorker("worker");


@Entry
@Component
struct Index {
  @State message: string = 'emitter off';


  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            worker.start();
            worker.run<void>(() => {
              // 注册两个监听器
              emitter.onGenericEventData("emitter_off", callback1);
              emitter.onGenericEventData("emitter_off", callback2);
              // 首次触发：两个监听器都会执行
              emitter.emit("emitter_off", options);
              // 通过延时执行代码模拟同步操作
              setTimeout(() => {
                // 删除callback1监听器
                emitter.offGenericEventData("emitter_off", callback1);
              }, 100);
              setTimeout(() => {
                // 再次触发：只剩callback2会执行
                emitter.emit("emitter_off", options);
              }, 200);
              setTimeout(() => {
                // 删除callback2监听器
                emitter.offGenericEventData("emitter_off", callback2);
              }, 300);
            })
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### registerGlobalCallObject

registerGlobalCallObject(instanceName: string, globalCallObject: Object): void

在宿主线程的ThreadWorker实例上注册一个对象，该对象上的方法可以在Worker线程中被调用，详细介绍请参见[callGlobalCallObjectMethod](#callglobalcallobjectmethod)。


**ArkTS-Dyn**
```ts
//Index.ets
const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
class TestObj {
  private message : string = "this is a message from TestObj"
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
workerInstance.postMessage("start worker")
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
  try {
    // 调用方法无入参
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessage", 0) as string;
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
  try {
    // 调用方法有入参
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessageWithInput", 0, "hello there!") as string;
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
}
```

**ArkTS-Sta**

在ArkTS-Dyn中，`registerGlobalCallObject`/`unregisterGlobalCallObject`用于同步跨线程调用对象方法。在ArkTS-Sta中，可以直接跨线程调用对象方法，无需特殊API。

```ts
//Index.ets
const workerInstance = new EAWorker("worker");
workerInstance.start();

class TestObj {
  private message : string = "this is a message from TestObj"
  public getMessage() : string {
    return this.message;
  }
  public getMessageWithInput(str : string) : string {
    return this.message + " with input: " + str;
  }
}
let registerObj = new TestObj();

const workerCB = (msg: concurrency.Message) => {
  try {
    // 调用方法无入参
    let res : string = registerObj.getMessage();
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    let err = error as Error;
    console.error("worker:  error message is " + err.message);
  }
  try {
    // 调用方法有入参
    let res : string = registerObj.getMessageWithInput("hello there!");
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    let err = error as Error;
    console.error("worker:  error message is " + err.message);
  }
}
let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

let workerMessage = new concurrency.Message(workerHandler);
workerHandler.sendMessage(workerMessage);
```


### unregisterGlobalCallObject

unregisterGlobalCallObject(instanceName?: string): void

取消在宿主线程ThreadWorker实例上注册的对象，该方法会释放ThreadWorker实例中与该键相匹配对象的强引用，没有匹配对象时不会报错。

**ArkTS-Dyn**
```ts
const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
class TestObj {
  private message : string = "this is a message from TestObj"
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
//workerInstance.unregisterGlobalCallObject();
workerInstance.postMessage("start worker")
```

**ArkTS-Sta**

ArkTS-Dyn中使用`registerGlobalCallObject`/`unregisterGlobalCallObject`进行同步跨线程调用对象方法。ArkTS-Sta中，可以直接跨线程调用对象方法，无需特殊API。

### terminate

terminate(): void

销毁Worker线程，终止Worker接收消息。

**ArkTS-Dyn**
```ts
const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.terminate();
```

**ArkTS-Sta**
`quit` 会停止接收新消息，并在处理完消息队列中的剩余任务后退出，销毁 EAWorker 线程。

```ts
const workerInstance = new EAWorker("worker");
workerInstance.start();
workerInstance.quit();
```

### onexit

onexit?: (code: number) =&gt; void

回调函数。表示Worker销毁时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中code类型为number，异常退出为1，正常退出为0。

**ArkTS-Dyn**

```ts
const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.onexit = (code) => {
 console.info("onexit");
}

//onexit被执行两种方式：
// main thread：
workerInstance.terminate();

// worker线程：
//workerPort.close()
```

**ArkTS-Sta**

ArkArkTS-Sta不提供ArkTS-Dyn中的`workerPort.close()` API和`onexit`事件监听。这种方式容易导致锁等全局共享状态不一致，从而引发错误。建议开发者使用EAWorker的`quit`方法退出，并在调用这些方法前执行原来在`onexit`回调中的逻辑。

```ts
const workerInstance = new EAWorker("worker");
workerInstance.start();
console.info("onexit");
workerInstance.quit();
```

### onerror

onerror?: (err: ErrorEvent) =&gt; void

回调函数。表示Worker在执行过程中发生异常被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中err类型为[ErrorEvent](#errorevent)，表示收到的异常数据。

**ArkTS-Dyn**
```ts
import { worker, ErrorEvent } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.onerror = (err: ErrorEvent) => {
  console.info("onerror" + err.message);
}
```

**ArkTS-Sta**
```ts
const workerInstance = new EAWorker("worker");
workerInstance.start();
workerInstance.setUncaughtExceptionHandler((err: Error) => {
  console.info("onerror" + err.message);
})
```

### onAllErrors

onAllErrors?: ErrorCallback

回调函数。表示Worker线程生命周期内发生异常被调用的事件处理程序，处理程序在宿主线程中执行。
[onerror](#onerror)仅捕获[onmessage](#onmessage)回调中同步方法产生的异常，无法捕获多线程回调产生的异常和模块化相关异常，且onerror捕获异常后Worker线程进入销毁流程，不可以继续使用。
onAllErrors可以捕获Worker线程的onmessage回调、timer回调以及文件执行等流程产生的全局异常，且onAllErrors捕获异常后Worker线程仍存活可以继续使用。推荐使用onAllErrors代替onerror。


**ArkTS-Dyn**
```ts
import { worker, ErrorEvent } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.onAllErrors = (err: ErrorEvent) => {
  console.info("onAllErrors" + err.message);
}
```

**ArkTS-Sta**
```ts
const workerInstance = new EAWorker("worker");
workerInstance.start();
workerInstance.setUncaughtExceptionHandler((err: Error) => {
  console.info("onAllErrors" + err.message);
})
```

### onmessage

onmessage?: (event: MessageEvents) =&gt; void

回调函数。表示宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中event类型为[MessageEvents](#messageevents)，表示收到的Worker消息数据。

**ArkTS-Dyn**
```ts
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.onmessage = (e: MessageEvents): void => {
 // e : MessageEvents, 用法如下：
 // let data = e.data;
 console.info("onmessage");
}
```

**ArkTS-Sta**
```ts
const currentworker = EAWorker.current()
// 宿主线程接收EAWorker线程信息
const currentCB = (msg: concurrency.Message) => {
  console.info("onmessage");
}
let currentHandler = new concurrency.MessageHandler(currentCB, currentworker);
```

### onmessageerror

onmessageerror?: (event: MessageEvents) =&gt; void

回调函数。表示当Worker对象接收到一条无法被序列化的消息时被调用的事件处理程序，处理程序在宿主线程中执行。其中回调函数中event类型为[MessageEvents](#messageevents)，表示收到的Worker消息数据。


**ArkTS-Dyn**
```ts
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.onmessageerror = (err: MessageEvents) => {
  console.info("onmessageerror");
}
```

**ArkTS-Sta**

ArkTS-Sta中没有`onmessageerror`的使用场景。ArkTS-Sta基于共享内存运行时，因此消息传递过程不设计序列化。

### addEventListener

addEventListener(type: string, listener: WorkerEventListener): void

向Worker添加一个事件监听，该接口与[on](#on)接口功能一致。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");

          workerInstance.addEventListener("alert", () => {
            console.info("alert listener callback");
          })

          // 执行"alert"事件类型的回调
          workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

**ArkTS-Sta**
```ts
// Index.ets

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { Callback, emitter } from '@kit.BasicServicesKit';

let callback: Callback<emitter.GenericEventData<void>> = (eventData: emitter.GenericEventData<void>): void => {
  console.info("emitter callback: emitter_on");
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

let worker=new EAWorker("worker");


@Entry
@Component
struct Index {
  @State message: string = 'emitter on';


  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            worker.start();
            worker.run<void>(() => {
              emitter.onGenericEventData("emitter_on", callback);
              // 执行emitter_on对应的回调
              emitter.emit("emitter_on", options);
            });
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

### removeEventListener

removeEventListener(type: string, callback?: WorkerEventListener): void

删除Worker的事件监听，该接口与[off](#off)接口功能一致。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");

          workerInstance.addEventListener("alert", () => {
            console.info("alert listener callback");
          })
          
          workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持
          
          workerInstance.removeEventListener("alert");
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

**ArkTS-Sta**
```ts
// Index.ets
// ArkTS-Sta中，emitter会将emit任务放入FFRT队列去执行，无法判断异步任务执行的具体时间，本示例采用延时执行的方式来模拟ArkTS-Dyn中的同步操作

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { Callback, emitter } from '@kit.BasicServicesKit';

let callback: Callback<emitter.GenericEventData<void>> = (eventData: emitter.GenericEventData<void>): void => {
  console.info("emitter callback: emitter_off");
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

let worker=new EAWorker("worker");


@Entry
@Component
struct Index {
  @State message: string = 'emitter off';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            worker.start();
            worker.run<void>(() => {
              emitter.onGenericEventData("emitter_off", callback);
              emitter.emit("emitter_off", options);
              // 通过延时执行代码模拟同步操作
              setTimeout(() => {
                emitter.offGenericEventData("emitter_off", callback);
              }, 100);
            });
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```


### dispatchEvent

dispatchEvent(event: Event): boolean

分发定义在Worker的事件。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");

          workerInstance.addEventListener("alert", () => {
            console.info("alert listener callback");
          })

          // 执行"alert"事件类型的回调
          workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp暂未支持
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

**ArkTS-Sta**
```ts
// Index.ets

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { Callback, emitter } from '@kit.BasicServicesKit';

let callback: Callback<emitter.GenericEventData<void>> = (eventData: emitter.GenericEventData<void>): void => {
  console.info("emitter callback: emitter_on");
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

let worker=new EAWorker("worker");


@Entry
@Component
struct Index {
  @State message: string = 'emitter on';


  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            worker.start();
            worker.run<void>(() => {
              emitter.onGenericEventData("emitter_on", callback);
              // 执行emitter_on对应的回调
              emitter.emit("emitter_on", options);
            });
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```


### removeAllListener

removeAllListener(): void

删除Worker所有的事件监听。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
          workerInstance.addEventListener("alert", () => {
            console.info("alert listener callback");
          })
          workerInstance.removeAllListener();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

**ArkTS-Sta**

ArkTS-Sta emitter设计为在整个进程中进行跨线程通信，不同于ArkTS-Dyn中针对某个单一Worker线程绑定事件的订阅，所以没有删除某个Worker所有的事件监听的功能。

## WorkerEventTarget API迁移

### addEventListener

addEventListener(type: string, listener: WorkerEventListener): void

向Worker线程的实例对象添加事件监听。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// worker.ets

import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.addEventListener("alert", () => {
    console.info("alert listener callback");
  })
};
```

**ArkTS-Sta**

ArkTS-Sta EAWorker取消了宿主线程与Worker线程的角色区分，请参考ThreadWoker API的[addEventListener](#addeventlistener)接口迁移示例。

### removeEventListener

removeEventListener(type: string, callback?: WorkerEventListener): void

移除Worker线程实例对象中类型为type的事件监听。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
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

**ArkTS-Sta**

ArkTS-Sta EAWorker取消了宿主线程与Worker线程的角色区分，请参考ThreadWoker API的[removeEventListener](#removeeventlistener)接口迁移示例。

### dispatchEvent

dispatchEvent(event: Event): boolean

在Worker线程将事件对象分发到Worker线程的事件系统，并触发该类型事件的所有监听器回调。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
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

**ArkTS-Sta**

ArkTS-Sta EAWorker取消了宿主线程与Worker线程的角色区分，请参考ThreadWoker API的[dispatchEvent](#dispatchevent)接口迁移示例。


### removeAllListener

removeAllListener(): void

移除Worker线程的实例对象所有的事件监听。

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
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

**ArkTS-Sta**

ArkTS-Sta emitter设计为在整个进程中进行跨线程通信，不同于ArkTS-Dyn中针对某个单一Worker线程绑定事件的订阅，所以没有删除某个Worker所有的事件监听的功能。


## ThreadWorkerGlobalScope API迁移

Worker线程用于与宿主线程通信的类，通过postMessage接口发送消息给宿主线程、close接口销毁Worker线程。ThreadWorkerGlobalScope类继承[GlobalScope](#globalscope)。

### postMessage

postMessage(message: Object, transfer: ArrayBuffer[]): void

Worker线程通过转移对象所有权的方式向宿主线程发送消息。


**ArkTS-Dyn**

```ts
// main thread
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    console.info("receive data from worker.ets");
}
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    let buffer = new ArrayBuffer(8);
    workerPort.postMessage(buffer, [buffer]);
}
```

**ArkTS-Sta**
```ts
const currentworker = EAWorker.current()

const workerInstance = new EAWorker("worker");
workerInstance.start();

const currentCB = (msg: concurrency.Message) => {
  console.info("receive data from worker.ets");
}
let currentHandler = new concurrency.MessageHandler(currentCB, currentworker);

const workerCB = (msg: concurrency.Message) => {
  let buffer = new ArrayBuffer(8);
  let message = new concurrency.Message(1, buffer, currentHandler);
  currentHandler.sendMessage(message);
}
let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

// 向EAworker线程传递信息
let str : string = "hello world";
let workerMessage = new concurrency.Message(1, str, workerHandler);
workerMessage.sendToTarget();
```

### postMessage

postMessage(messageObject: Object, options?: PostMessageOptions): void

Worker线程通过转移对象所有权或者拷贝数据的方式向宿主线程发送消息。


**ArkTS-Dyn**

```ts
// main thread
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    console.info("receive data from worker.ets");
}
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    workerPort.postMessage("receive data from main thread");
}
```

**ArkTS-Sta**
```ts
const currentworker = EAWorker.current()

const workerInstance = new EAWorker("worker");
workerInstance.start();

const currentCB = (msg: concurrency.Message) => {
  console.info("receive data from worker.ets");
}
let currentHandler = new concurrency.MessageHandler(currentCB, currentworker);

const workerCB = (msg: concurrency.Message) => {
  let str : string = "receive data from main thread"
  let message = new concurrency.Message(1, str, currentHandler);
  currentHandler.sendMessage(message);
}
let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

// 向EAworker线程传递信息
let str : string = "hello world";
let workerMessage = new concurrency.Message(1, str, workerHandler);
workerMessage.sendToTarget();
```

### postMessageWithSharedSendable

postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void

Worker线程向宿主线程发送消息，消息中的Sendable对象通过引用传递，消息中的非Sendable对象通过序列化传递。

**ArkTS-Dyn**

<!--code_no_check-->
```ts
// worker文件路径为：entry/src/main/ets/workers/Worker.ets
// Worker.ets
// 新建SendableObject实例并通过worker线程传递至宿主线程

import { SendableObject } from '../pages/sendable'
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  let object: SendableObject = new SendableObject();
  workerPort.postMessageWithSharedSendable(object);
}
```

```ts
// sendable.ets
// 定义SendableObject

@Sendable
export class SendableObject {
  a:number = 45;
}
```

<!--code_no_check-->
```ts
// Index.ets
// 接收worker线程传递至宿主线程的数据并访问其属性

import { worker, MessageEvents } from '@kit.ArkTS';
import { SendableObject } from './sendable'

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
workerInstance.postMessage(1);
workerInstance.onmessage = (e: MessageEvents) => {
  let obj: SendableObject = e.data;
  console.info("sendable index obj is: " + obj.a);
}
```

**ArkTS-Sta**
```ts
// sendable.ets
// 定义SendableObject

export class SendableObject {
  a:number = 45;
}
```

```ts
// index.ets
// 接收EAWorker线程传递至宿主线程的数据并访问其属性

import { SendableObject } from './sendable'

const currentworker = EAWorker.current()

// 宿主线程中创建EAWorker对象并调用start()方法启动
const workerInstance = new EAWorker("worker");
workerInstance.start();

// 宿主线程接收EAWorker传递至宿主线程的数据并访问其属性
const currentCB = (msg: concurrency.Message) => {
  let obj: SendableObject = msg.getObject() as SendableObject;
  console.info("sendable index obj is: " + obj.a);
}
let currentHandler = new concurrency.MessageHandler(currentCB, currentworker);

// EAWorker新建SendableObject实例并传递至宿主线程
const workerCB = (msg: concurrency.Message) => {
  let str: string = "receive start signal from main thread";
  console.info(str);
  let objPost: SendableObject = new SendableObject();
  let message = new concurrency.Message(1, objPost, currentHandler);
  currentHandler.sendMessage(message);
}
let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

// 宿主线程向EAworker线程传递信息
let str: string = "hello world";
let workerMessage = new concurrency.Message(1, str, workerHandler);
workerMessage.sendToTarget(); 
```


### callGlobalCallObjectMethod

callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object

Worker线程调用注册在宿主线程上某个对象的指定方法，调用对于Worker线程是同步的，对于宿主线程是异步的，返回值通过序列化传递。


**ArkTS-Dyn**
```ts
//Index.ets
const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
class TestObj {
  private message : string = "this is a message from TestObj"
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
workerInstance.postMessage("start worker")
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
  try {
    // 调用方法无入参
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessage", 0) as string;
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
  try {
    // 调用方法有入参
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessageWithInput", 0, "hello there!") as string;
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
}
```

**ArkTS-Sta**

```ts
//Index.ets
const workerInstance = new EAWorker("worker");
workerInstance.start();

class TestObj {
  private message : string = "this is a message from TestObj"
  public getMessage() : string {
    return this.message;
  }
  public getMessageWithInput(str : string) : string {
    return this.message + " with input: " + str;
  }
}
let registerObj = new TestObj();

const workerCB = (msg: concurrency.Message) => {
  try {
    // 调用方法无入参
    let res : string = registerObj.getMessage();
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    let err = error as Error;
    console.error("worker:  error message is " + err.message);
  }
  try {
    // 调用方法有入参
    let res : string = registerObj.getMessageWithInput("hello there!");
    console.info("worker:", res)
  } catch (error) {
    // 异常处理
    let err = error as Error;
    console.error("worker:  error message is " + err.message);
  }
}
let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

let workerMessage = new concurrency.Message(workerHandler);
workerHandler.sendMessage(workerMessage);
```


### close

close(): void

销毁Worker线程，终止Worker接收消息。

**ArkTS-Dyn**

```ts
// main thread
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    workerPort.close()
}
```

**ArkTS-Sta**

ArkTS-Sta不提供类似ArkTS-Dyn `workerPort.close()` API和`onexit`事件监听。这种让线程自销毁的方式，容易造成锁等全局共享状态的不一致，从而导致错误。建议开发者使用EAWorker的`quit`方法来退出。

### onmessage

onmessage?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) =&gt; void

回调函数。ThreadWorkerGlobalScope的onmessage属性表示Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用的事件处理程序，处理程序在Worker线程中执行。其中this指调用者对象本身[ThreadWorkerGlobalScope](#threadworkerglobalscope)，ev类型为[MessageEvents](#messageevents)，表示收到的Worker消息数据。

**ArkTS-Dyn**

```ts
// main thread
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    console.info("receive main thread message");
}
```

**ArkTS-Sta**
```ts
const workerInstance = new EAWorker("worker");
workerInstance.start();

const workerCB = (msg: concurrency.Message) => {
  console.info("receive main thread message");
}
let workerHandler = new concurrency.MessageHandler(workerCB, workerInstance);

// 向EAworker线程传递信息
let str : string = "hello world";
let workerMessage = new concurrency.Message(1, str, workerHandler);
workerMessage.sendToTarget();
```

### onmessageerror

onmessageerror?: (this: ThreadWorkerGlobalScope, ev: MessageEvents) =&gt; void

回调函数。ThreadWorkerGlobalScope的onmessageerror属性表示当Worker对象接收到一条无法被反序列化的消息时被调用的事件处理程序，处理程序在Worker线程中执行。其中this指调用者对象本身[ThreadWorkerGlobalScope](#threadworkerglobalscope)，ev类型为[MessageEvents](#messageevents)，表示收到的Worker消息数据。


**ArkTS-Dyn**

```ts
// main thread
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessageerror = (err: MessageEvents) => {
    console.info("worker.ets onmessageerror");
}
```

**ArkTS-Sta**

ArkTS-Sta基于共享内存运行时，消息传递过程不涉及序列化，因此ArkTS-Sta中没有`onmessageerror`的使用场景。

## WorkerEventListener API迁移

事件监听类。

### (event: Event)

(event: Event): void | Promise\<void\>

ArkTS-Sta EAWorker中该功能已经迁移至emitter，请查阅[@ohos.events.emitter](../reference/apis-basic-services-kit/js-apis-emitter.md)了解更多具体用法。

**ArkTS-Dyn**
```ts
// Index.ets

import { worker, Event } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");

workerInstance.addEventListener("alert", (event: Event) => {
  console.info(`event type is: ${JSON.stringify(event.type)}`);
});

const eventToDispatch : Event = { type: "alert", timeStamp: 0 }; // timeStamp暂未支持
workerInstance.dispatchEvent(eventToDispatch);
```

**ArkTS-Sta**
```ts
// Index.ets

'use static'

import { Entry, Text, Column, Component, Button, ClickEvent,Row} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { Callback, emitter } from '@kit.BasicServicesKit';

let eventData: emitter.GenericEventData<string> = {
  data: "alert"
};

let callback: Callback<emitter.GenericEventData<string>> = (eventData: emitter.GenericEventData<string>): void => {
  console.info(`eventData is : ${JSON.stringify(eventData?.data)}`);
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

let worker=new EAWorker("worker");


@Entry
@Component
struct Index {
  @State message: string = 'emitter on';


  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .onClick(() => {
            worker.start();
            worker.run<void>(() => {
              emitter.onGenericEventData("emitter_on", callback);
              emitter.emit("emitter_on", options, eventData);
            });
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

## GlobalScope API迁移

Worker线程自身的运行环境，GlobalScope类继承[WorkerEventTarget](#workereventtarget)。

### onerror

onerror?: (ev: ErrorEvent) =&gt; void

回调函数。GlobalScope的onerror属性表示Worker在执行过程中发生异常被调用的事件处理程序，处理程序在Worker线程中执行。其中回调函数中ev类型为[ErrorEvent](#errorevent)，表示收到的异常数据。


**ArkTS-Dyn**

```ts
// main thread
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets")
```

```ts
// worker.ets
import { worker, ErrorEvent } from '@kit.ArkTS';

const workerPort = worker.workerPort
workerPort.onerror = (err: ErrorEvent) => {
    console.info("worker.ets onerror" + err.message)
}
```

**ArkTS-Sta**

```ts
const workerInstance = new EAWorker("worker");
workerInstance.start();
workerInstance.setUncaughtExceptionHandler((err: Error) => {
  console.info("worker onerror" + err.message);
})
```

## MessageEvents API迁移

消息类，持有Worker线程间传递的数据。

**ArkTS-Sta**
 
参考[onmessage](#onmessage)的迁移方式。

## MessageType API迁移

type MessageType = 'message' | 'messageerror'

表示消息类型。

**ArkTS-Sta**

参考[onmessage](#onmessage)的迁移方式。

## ErrorCallback API迁移

type ErrorCallback = (err: ErrorEvent) => void

表示异常回调类型。

**ArkTS-Sta**

参考[onAllErrors](#onAllErrors)的迁移方式。

## FAQ
### 为何没有单独提供类似Java/C++的线程接口
ArkTS-Sta兼容ArkTS-Dyn基于事件循环的异步语义，如果允许单独的线程API，那程序将存在语言异步语义无法提供的状态，这是无法接受的。

### 如何延迟发送消息
建议使用[setTimeout()](../reference/common/js-apis-timer.md#settimeout)来延迟发送消息。

### 如何进行异常处理
ArkTS-Dyn中由于内存隔离的限制，Worker发生异常时，会向宿主线程发送一个异常信息的消息，而不能通过运行时定义的try/catch机制进行异常处理。ArkTS-Sta中没有了内存隔离的限制后，可以直接使用语言定义的异常处理来处理EAWorker异常退出的场景。

### 如何管理EAWorker的生命周期
EAWorker的线程和事件循环生命周期一致，不分别提供线程退出和事件循环退出的API。EAWorker提供quit接口来退出事件循环并结束线程的执行。
