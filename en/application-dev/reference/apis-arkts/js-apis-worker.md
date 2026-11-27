# @ohos.worker (Starting the Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e42d49ae1e9e7c1c48c6d743fb3a84192d3e7fe7 translatedAt=2026-11-16T06:09:14.892Z pushedAt=2026-11-16T06:31:14.307Z nl=1 -->

A Worker is an independent thread that runs in parallel with the host thread. The thread that creates the Worker is called the host thread, and the Worker's own thread is called the Worker thread. The URL file passed in when creating the Worker is executed in the Worker thread, which can handle time-consuming operations but cannot directly operate the UI.

Worker primarily provides a multithreaded runtime environment for applications, allowing them to separate from the host thread during execution. This enables scripts to run in background threads for time-consuming operations, reducing the likelihood of blocking the host thread during computing-intensive or high-latency tasks. A Worker instance will not be proactively destroyed once it is created. It consumes resources to keep running. Therefore, you should call the API to terminate it in a timely manner.

The context environment of the Worker thread is independent of that of the UI main thread. The Worker thread does not support UI operations.

For details about the precautions for using Worker, see [Precautions for Worker](../../arkts-utils/worker-introduction.md).

> **NOTE**<br>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { worker } from '@kit.ArkTS';
```


## Constants

**System capability**: SystemCapability.Utils.Lang

| Name                              | Type                                                         | Read-Only | Description                                                         |
| --------------------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| workerPort<sup>9+</sup>           | [ThreadWorkerGlobalScope](#threadworkerglobalscope9)         | Yes   | Object used by the Worker thread for communication with the host thread.<br/>**Atomic service API**: This API can be used in atomic services since API version 11.                         |
| parentPort<sup>(deprecated)</sup> | [DedicatedWorkerGlobalScope](#dedicatedworkerglobalscopedeprecated) | Yes   | Object used by the Worker thread for communication with the host thread.<br/>**Note**: Supported since API version 7, deprecated since API version 9. It is recommended to use [workerPort](#constants) instead.|


## WorkerOptions

Provides options that can be set for the Worker instance to create.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-only| Optional| Description|
| ---- | -------- | ---- | ---- | -------------- |
| type | 'classic' \| 'module' | No   | Yes | The mode type of the script executed by the Worker. The module type is not supported. The default value is "classic".<br/>**Atomic Service API**: Since API version 11, this API supports use in atomic services. |
| name | string   | No   | Yes | Name of the Worker.<br/>Default value is undefined, in which case the thread name is 'WorkerThread'.<br/>When a non-default value is set, the corresponding thread name has the prefix 'WorkerThread_'. For example, when name is 'testName', the corresponding thread name is 'WorkerThread_testName'.<br/>The thread name can be obtained through the threadName of [HeapMemoryInfo](js-apis-util.md#heapmemoryinfo24).<br/>**Atomic service API**: This interface supports use in atomic services since API version 11.|
| shared | boolean | No   | Yes | Indicates the Worker sharing feature. This interface is not supported yet. <br/>**Atomic service API**: This interface supports use in atomic services since API version 12.|
| priority<sup>18+</sup> | [ThreadWorkerPriority](#threadworkerpriority18) | No   | Yes | Indicates the Worker thread priority. Default value is MEDIUM. <br/>**Atomic service API**: This interface supports use in atomic services since API version 18.|


## ThreadWorkerPriority<sup>18+</sup>

Enumerates the priorities of the Worker thread. For the mapping between priorities, see [QoS level definition](../../kernel-enhance/qos-guidelines.md#qos-levels).

**System capability**: SystemCapability.Utils.Lang

| Name| Value| Description|
| -------- | -------- | -------- |
| HIGH   | 0    | Applies to user-triggered tasks with visible progress, for example, opening a file. A task completes in seconds. It corresponds to **QOS_USER_INITIATED**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| MEDIUM | 1 | Applies to tasks that complete in seconds. It is the default value of [ThreadWorkerPriority](#threadworkerpriority18) and corresponds to **QOS_DEFAULT**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| LOW | 2 | Applies to tasks that do not require immediate response, such as download. A task completes in several seconds to several minutes. It corresponds to **QOS_UTILITY**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| IDLE | 3 | Applies to background tasks that are invisible to users, such as data synchronization. A task completes in several minutes or even hours. It corresponds to **QOS_BACKGROUND**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| DEADLINE<sup>20+</sup> | 4 | Applies to key tasks that require quick completion, such as page loading. A task completes almost instantly. It corresponds to **QOS_DEADLINE_REQUEST**.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| VIP<sup>20+</sup> | 5 | Applies to user interaction tasks such as UI thread and animation rendering. The tasks are instant. It corresponds to **QOS_USER_INTERACTIVE**.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|



## ThreadWorker<sup>9+</sup>

Before using the following APIs, you must create a ThreadWorker instance. The ThreadWorker class is inherited from [WorkerEventTarget](#workereventtarget9).

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name  | Type                   | Read-only| Optional| Description                                                        |
| ------ | ---------------------- | ---- | --- | ------------------------------------------------------------ |
| onexit<sup>9+</sup> | (code: number) => void | No | Yes | Callback function. Indicates the event handler called when the Worker thread is destroyed. The handler is executed in the host thread. The code parameter of the callback function is of the number type. The value is 1 for abnormal exit and 0 for normal exit. Default value is undefined.<br/>The following errors. Detailed error codes. Refer to [Language basics library error codes](errorcode-utils.md).<br/>- 10200004: The Worker instance is not running.<br/>- 10200005: The called API is not supported in the worker thread.<br/>**Atomic service API**: Supported since API version 11, this property supports use in atomic services.|
| onerror<sup>9+</sup> | (err: [ErrorEvent](#errorevent)) => void | No | Yes | Callback function, used to handle exceptions generated by synchronous code in the onmessage callback function. The handler is executed in the host thread. The err parameter of the callback function is of the [ErrorEvent](#errorevent) type, indicating the received exception data. Default value is undefined.<br/>The following errors. Detailed error codes. Refer to [Language basics library error codes](errorcode-utils.md).<br/>- 10200004: The Worker instance is not running.<br/>- 10200005: The called API is not supported in the worker thread.<br/>**Atomic service API**: Supported since API version 11, this property supports use in atomic services.|
| onAllErrors<sup>18+</sup> | [ErrorCallback](#errorcallback18) | No | Yes | Callback function. Indicates the event handler called when an exception occurs during the lifecycle of the Worker thread. The handler is executed in the host thread. Default value is undefined.<br/>The following errors. Detailed error codes. Refer to [Language basics library error codes](errorcode-utils.md).<br/>- 10200004: The Worker instance is not running.<br/>- 10200005: The called API is not supported in the worker thread.<br/>**Atomic service API**: Supported since API version 18, this property supports use in atomic services.|
| onmessage<sup>9+</sup> | (event: [MessageEvents](#messageevents9)) => void | No | Yes | Callback function. Indicates the event handler called when the host thread receives a message sent by the Worker it created through the workerPort.[postMessage](#postmessage9-3) or workerPort.[postMessageWithSharedSendable](#postmessagewithsharedsendable12-1) interface. The handler is executed in the host thread. Where the callback function's event is of the [MessageEvents](#messageevents9) type, indicating the received message data sent by the Worker thread. Default value is undefined.<br/>The following errors. Detailed error codes. Refer to [Language basics library error codes](errorcode-utils.md).<br/>- 10200004: The Worker instance is not running.<br/>- 10200005: The called API is not supported in the worker thread.<br/>**Atomic service API**: Supported since API version 11, this property supports use in atomic services.|
| onmessageerror<sup>9+</sup> | (event: [MessageEvents](#messageevents9)) => void | No | Yes | Callback function. Used to handle messages received by the Worker object that cannot be serialized. The handler is executed in the host thread. The event is of the [MessageEvents](#messageevents9) type, indicating the received Worker message data. Default value is undefined.<br/>The following errors. Detailed error codes. Refer to [Language basics library error codes](errorcode-utils.md).<br/>- 10200004: The Worker instance is not running.<br/>- 10200005: The called API is not supported in the worker thread.<br/>**Atomic service API**: Supported since API version 11, this property supports use in atomic services.|

When using the Worker module, for API version 18 and later, it is recommended to register the onAllErrors callback in the host thread to capture various exceptions during the Worker thread lifecycle. For versions earlier than API version 18, register the onerror callback. If neither onAllErrors nor onerror is registered, a crash occurs when an exception happens in the Worker thread. Note that the onerror interface can only capture synchronous exceptions in the onmessage callback. After an exception is captured, the Worker thread enters the destruction process and cannot be used further.

The behavior differences between **onAllErrors** and **onerror** are as follows:

1. Exception capture range

    **onAllErrors** can capture global exceptions generated during the **onmessage** callback, timer callback, and file execution of the Worker thread.

    **onerror** can capture only exceptions generated by synchronous methods within the **onmessage** callback of the Worker thread. It cannot capture exceptions from multithreaded callbacks or modularization-related exceptions.

2. Thread status after exception capture

    After an exception is captured by **onAllErrors**, the Worker thread remains alive and can continue to be used. This allows you to perform additional operations after an exception is captured, without worrying about the thread being terminated.

    Once an exception is captured by **onerror**, the Worker thread enters the destruction process and cannot be used. This means that after **onerror** is triggered, the Worker thread will be terminated, and subsequent operations cannot proceed.

3. Applicable scenarios

    **onAllErrors** applies to scenarios where all types of exceptions in the Worker thread need to be captured, especially in complex scenarios where the Worker thread must continue running after an exception occurs.

    **onerror** is appropriate for simple scenarios where only synchronous exceptions in the **onmessage** callback need to be captured. Since the thread is destroyed after an exception is captured, it is best used when the Worker thread is not needed afterward.

    **onAllErrors** is recommended because it provides more comprehensive exception capture capabilities and does not lead to thread termination.

### constructor<sup>9+</sup>

constructor(scriptURL: string, options?: WorkerOptions)

A constructor used to create a ThreadWorker instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                           | Mandatory| Description                                                        |
| --------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| scriptURL | string                          | Yes  | URL of the Worker thread file.<br>For details about the rules, see [Precautions for File URLs](../../arkts-utils/worker-introduction.md#precautions-for-file-urls).|
| options   | [WorkerOptions](#workeroptions) | No   | Options for Worker construction. If this parameter is not specified, each property takes its default value. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200003 | Worker initialization failed. |
| 10200007 | The worker file path is invalid. |

**Example**

The following example shows how to load the Worker thread file in the Index.ets file of the entry module in the Stage model. For the scenario of loading the Worker thread file using Library, see [File path notes](../../arkts-utils/worker-introduction.md#precautions-for-file-urls).

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

// URL of the Worker file: "entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.ThreadWorker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```


### postMessage<sup>9+</sup>

postMessage(message: Object, transfer: ArrayBuffer[]): void

Sends a message from the host thread to the Worker thread by transferring object ownership.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 11.

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| message  | Object        | Yes   | Data sent to the Worker. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| transfer | ArrayBuffer[] | Yes  | ArrayBuffer instance holding an array of objects for which the ownership is transferred to the Worker thread. After the transfer, the objects are available only in the Worker thread. The array cannot be null.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |

**Example**

```ts
// Worker.ets
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

// Create an object in the Worker thread for communicating with the host thread.
const workerPort = worker.workerPort;

// The Worker thread receives information from the host thread.
workerPort.onmessage = (e: MessageEvents): void => {
  // data carries the information sent by the host thread.
  let data: ArrayBuffer = e.data;
  // Write data to the received buffer.
  const view = new Int8Array(data).fill(3);
  // The Worker thread sends information to the host thread.
  workerPort.postMessage(view);
}

// Trigger a callback when an error occurs in the Worker thread.
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
            // Create a Worker instance in the host thread.
            const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
            // The host thread transfers information to the Worker thread.
            const buffer = new ArrayBuffer(8);
            workerInstance.postMessage(buffer, [buffer]);

            // The ownership of the buffer is transferred to the Worker thread and is unavailable in the host thread.
            // const view = new Int8Array(buffer).fill(3);

            // The host thread receives information from the Worker thread.
            workerInstance.onmessage = (e: MessageEvents): void => {
              // data carries the information sent by the Worker thread.
              let data: Int8Array = e.data;
              console.info("main thread data is  " + data);
              // Terminate the Worker instance.
              workerInstance.terminate();
            }
            // Call onexit().
            workerInstance.onexit = (code) => {
              console.info("main thread terminate");
            }
            // Listen for Worker errors.
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

### postMessage<sup>9+</sup>

postMessage(message: Object, options?: PostMessageOptions): void

Sends a message from the host thread to the Worker thread by transferring object ownership or copying data. Pass-by-copy is used to pass [Sendable objects](../../arkts-utils/arkts-sendable.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                                     | Mandatory| Description                                                        |
| ------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| message | Object                                    | Yes  | Data sent to the Worker. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| options | [PostMessageOptions](#postmessageoptions) | No  | If this parameter is specified, the data is sent to the Worker thread through ownership transfer. Such data will become unavailable in the host main thread and only remain accessible within the Worker thread.<br>If this parameter is not specified, the default value **undefined** is used, and data is transferred to the Worker thread through copying.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |

**Example**

```ts
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);

// When the options parameter is specified, the ownership of the buffer is transferred to the Worker thread and will no longer be accessible from the host thread.
workerInstance.postMessage(buffer, {transfer: [buffer]});
```


### postMessageWithSharedSendable<sup>12+</sup>

postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void

Sends a message from the host thread to the Worker thread. In the message, a [Sendable object](../../arkts-utils/arkts-sendable.md) is passed by reference, and a non-Sendable object is passed by copy.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| message | Object | Yes | Data sent to the Worker. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). If data sharing is required, see [Sendable supported data types](../../arkts-utils/arkts-sendable.md#sendable-data-types) for supported types. |
| transfer | ArrayBuffer[] | No| ArrayBuffer instance holding an array of objects for which the ownership is transferred to the Worker thread. After the transfer, the objects are available only in the Worker thread. The array cannot be null. The default value is an empty array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |

**Example**

<!--code_no_check-->
```ts
// Index.ets
// Create a SendableObject instance and pass it to the Worker thread through the host thread.

import { worker } from '@kit.ArkTS';
import { SendableObject } from './sendable';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
let object: SendableObject = new SendableObject();
workerInstance.postMessageWithSharedSendable(object);

// Use the postMessage API to pass Sendable objects by copying the data.
workerInstance.postMessage(object);
```

```ts
// sendable.ets
// Define SendableObject.

@Sendable
export class SendableObject {
  value:number = 45;
}
```

<!--code_no_check-->
```ts
// The worker file path is entry/src/main/ets/workers/Worker.ets.
// Worker.ets
// Receive and access the data passed from the host thread to the Worker thread.

import { SendableObject } from '../pages/sendable';
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (e: MessageEvents) => {
  let obj: SendableObject = e.data;
  console.info("sendable obj is: " + obj.value);
}
```


### on<sup>9+</sup>

on(type: string, listener: WorkerEventListener): void

Adds an event listener for the Worker instance of the host thread. This API provides the same functionality as [addEventListener<sup>9+</sup>](#addeventlistener9).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                        | Mandatory| Description                  |
| -------- | -------------------------------------------- | ---- | ---------------------- |
| type     | string                                       | Yes  | Type of the event to listen for.      |
| listener | [WorkerEventListener](#workereventlistener9) | Yes| Callback to invoke when an event of the specified type occurs.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                  |
| -------- | -------------------------------------------- |
| 10200004 | The Worker instance is not running.              |
| 10200005 | The called API is not supported in the worker thread. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.on("alert", () => {
    console.info("alert listener callback");
})

// Event listeners added using on can be executed multiple times.
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.
```


### once<sup>9+</sup>

once(type: string, listener: WorkerEventListener): void

Adds an event listener for the Worker instance of the host thread and removes the listener after it is invoked once.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                        | Mandatory| Description                  |
| -------- | -------------------------------------------- | ---- | ---------------------- |
| type     | string                                       | Yes  | Type of the event to listen for.      |
| listener | [WorkerEventListener](#workereventlistener9) | Yes| Callback to invoke when an event of the specified type occurs.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                  |
| -------- | -------------------------------------------- |
| 10200004 | The Worker instance is not running.              |
| 10200005 | The called API is not supported in the worker thread. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.once("alert", () => {
  console.info("alert listener callback");
})

workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.
```


### off<sup>9+</sup>

off(type: string, listener?: WorkerEventListener): void

Removes the event listener of the Worker instance in the host thread. This API provides the same functionality as [removeEventListener<sup>9+</sup>](#removeeventlistener9).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                        | Mandatory| Description                        |
| -------- | -------------------------------------------- | ---- | ---------------------------- |
| type     | string                                       | Yes   | Type of the event to delete. The event type is set through [on<sup>9+</sup>](#on9). |
| listener | [WorkerEventListener](#workereventlistener9) | No| Callback for which the listener is to be removed. If this parameter is not passed, all listeners of the specified type are removed.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                  |
| -------- | -------------------------------------------- |
| 10200004 | The Worker instance is not running.              |
| 10200005 | The called API is not supported in the worker thread. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

const handler1 = () => console.info("Handler 1");
const handler2 = () => console.info("Handler 2");

// Register two listeners.
workerInstance.on("alert", handler1);
workerInstance.on("alert", handler2);

// First trigger: Both listeners are executed.
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.

// Remove the handler1 listener.
workerInstance.off("alert", handler1);

// Second trigger: Only handler2 is executed.
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.

// Remove all listeners of the alert type.
workerInstance.off("alert");
```

### registerGlobalCallObject<sup>11+</sup>

registerGlobalCallObject(instanceName: string, globalCallObject: Object): void

Registers an object with the ThreadWorker instance of the host thread. In this way, the methods of the object can be called in the Worker thread through [callGlobalCallObjectMethod](#callglobalcallobjectmethod11).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| instanceName  | string        | Yes  | Key used for registration, based on which the registered object is identified during method calling.|
| globalCallObject | Object | Yes  | Object to register. The ThreadWorker instance holds a strong reference to the object.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |

**Example**
```ts
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
// Register registerObj with the ThreadWorker instance.
workerInstance.registerGlobalCallObject("myObj", registerObj);
workerInstance.postMessage("start worker");
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
  try {
    // The method to call does not carry an input parameter.
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessage", 0) as string;
    console.info("worker:", res) // worker: this is a message from TestObj
  } catch (error) {
    // Exception handling.
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
  try {
    // The method to call carries input parameters.
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessageWithInput", 0, "hello there!") as string;
    console.info("worker:", res); // worker: this is a message from TestObj with input: hello there!
  } catch (error) {
    // Exception handling.
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
}
```

### unregisterGlobalCallObject<sup>11+</sup>

unregisterGlobalCallObject(instanceName?: string): void

Unregisters an object with the ThreadWorker instance of the host thread. This API releases the strong reference between the ThreadWorker instance and the target object. No error is reported if no object is matched.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| instanceName  | string        | No  | Key used for registration. If this parameter is left blank, all registered objects registered in the ThreadWorker instance are unregistered.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**
```ts
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
// Unregister the object.
workerInstance.unregisterGlobalCallObject("myObj");
// Unregister all objects from the ThreadWorker instance.
workerInstance.postMessage("start worker");
```

### terminate<sup>9+</sup>

terminate(): void

The host thread actively destroys the Worker thread and stops the Worker thread from receiving messages.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.terminate();
```


### addEventListener<sup>9+</sup>

addEventListener(type: string, listener: WorkerEventListener): void

Adds an event listener for the Worker instance of the host thread. This API provides the same functionality as [on<sup>9+</sup>](#on9).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                        | Mandatory| Description            |
| -------- | -------------------------------------------- | ---- | ---------------- |
| type     | string                                       | Yes  | Type of the event to listen for.|
| listener | [WorkerEventListener](#workereventlistener9) | Yes  | Callback to invoke when an event of the specified type occurs.    |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                  |
| -------- | -------------------------------------------- |
| 10200004 | The Worker instance is not running.              |
| 10200005 | The called API is not supported in the worker thread. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

// Execute the callback of the alert type.
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.
```


### removeEventListener<sup>9+</sup>

removeEventListener(type: string, callback?: WorkerEventListener): void

Removes the event listener of the Worker instance in the host thread. This API provides the same functionality as [off<sup>9+</sup>](#off9).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                        | Mandatory| Description                        |
| -------- | -------------------------------------------- | ---- | ---------------------------- |
| type     | string                                       | Yes   | Type of the listener event to remove. The event type is set through [addEventListener<sup>9+</sup>](#addeventlistener9). |
| callback | [WorkerEventListener](#workereventlistener9) | No | Callback for which the listener is to be removed. If this parameter is not passed, all listeners of the specified type are removed. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.

workerInstance.removeEventListener("alert");
```


### dispatchEvent<sup>9+</sup>

dispatchEvent(event: Event): boolean

Dispatches an event object to the event system of the Worker thread. The event system automatically triggers the callback functions of all registered listeners for that event type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type           | Mandatory| Description            |
| ------ | --------------- | ---- | ---------------- |
| event  | [Event](#event) | Yes  | Event to dispatch.|

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| boolean | Dispatch result. The value **true** is returned if the dispatch is successful; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

let result: boolean = workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.

console.info("dispatchEvent result is: ", result);
```

The **dispatchEvent** API can be used together with the **on**, **once**, and **addEventListener** APIs. For details, see [Using dispatchEvent with addEventListener](#using-dispatchevent-with-addeventlistener).


### removeAllListener<sup>9+</sup>

removeAllListener(): void

Removes all event listeners of the Worker instance in the host thread.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.addEventListener("alert", () => {
    console.info("alert listener callback");
})
workerInstance.removeAllListener();
```

## WorkerEventTarget<sup>9+</sup>

Manages an event listener for the Worker thread.

### addEventListener<sup>9+</sup>

addEventListener(type: string, listener: WorkerEventListener): void

Adds an event listener for the Worker instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                        | Mandatory| Description            |
| -------- | -------------------------------------------- | ---- | ---------------- |
| type     | string                                       | Yes  | Type of the event to listen for.|
| listener | [WorkerEventListener](#workereventlistener9) | Yes  | Callback to invoke when an event of the specified type occurs.    |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                  |
| -------- | -------------------------------------------- |
| 10200004 | The Worker instance is not running.              |
| 10200005 | The called API is not supported in the worker thread. |

**Example**

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


### removeEventListener<sup>9+</sup>

removeEventListener(type: string, callback?: WorkerEventListener): void

Removes the event listener of the Worker instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                        | Mandatory| Description                        |
| -------- | -------------------------------------------- | ---- | ---------------------------- |
| type     | string                                       | Yes   | Type of the listener event to delete. The event type is set through [addEventListener<sup>9+</sup>](#addeventlistener9-1).     |
| callback | [WorkerEventListener](#workereventlistener9) | No | Callback for which the listener is to be removed. If this parameter is not passed, all listeners of the specified type are removed. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

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


### dispatchEvent<sup>9+</sup>

dispatchEvent(event: Event): boolean

Dispatches an event object to the event system of the Worker thread. The event system automatically triggers the callback functions of all registered listeners for that event type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type           | Mandatory| Description            |
| ------ | --------------- | ---- | ---------------- |
| event  | [Event](#event) | Yes  | Event to dispatch.|

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| boolean | Dispatch result. The value **true** is returned if the dispatch is successful; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

```ts
// worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.addEventListener("alert", () => {
    console.info("alert listener callback");
  });

  workerPort.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.
};
```

The **dispatchEvent** API can be used together with the **addEventListener** API. For details, see [Using dispatchEvent with addEventListener](#using-dispatchevent-with-addeventlistener).


### removeAllListener<sup>9+</sup>

removeAllListener(): void

Removes all event listeners from the Worker instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

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


## ThreadWorkerGlobalScope<sup>9+</sup>

Implements communication between the Worker thread and the host thread. The **ThreadWorkerGlobalScope** class inherits from [GlobalScope](#globalscope9).

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name  | Type                   | Read-only| Optional| Description                                                        |
| ------ | ---------------------- | ---- | --- | ------------------------------------------------------------ |
| onmessage<sup>9+</sup> | (this: [ThreadWorkerGlobalScope](#threadworkerglobalscope9), ev: [MessageEvents](#messageevents9)) => void | No | Yes | Callback function. Indicates the event handler called when the Worker thread receives a message sent by its host thread through the [postMessage](#postmessage9-1) or [postMessageWithSharedSendable](#postmessagewithsharedsendable12) interface. The handler is executed in the Worker thread. Here, this refers to the caller object itself [ThreadWorkerGlobalScope](#threadworkerglobalscope9), and ev is of type [MessageEvents](#messageevents9), indicating the message data sent by the host thread. The default value is undefined.<br/>**Atomic service API**: Since API version 11, this property supports use in atomic services.|
| onmessageerror<sup>9+</sup> | (this: [ThreadWorkerGlobalScope](#threadworkerglobalscope9), ev: [MessageEvents](#messageevents9)) => void | No | Yes | Callback function. Indicates the event handler called when the Worker object of the Worker thread receives a message that cannot be deserialized. The handler is executed in the Worker thread. Here, this refers to the caller object itself [ThreadWorkerGlobalScope](#threadworkerglobalscope9), and ev is of type [MessageEvents](#messageevents9), indicating the received message data. The default value is undefined.<br/>**Atomic service API**: Since API version 11, this property supports use in atomic services.|

### postMessage<sup>9+</sup>

postMessage(messageObject: Object, transfer: ArrayBuffer[]): void;

Sends a message from the Worker thread to the host thread by transferring object ownership.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| messageObject  | Object        | Yes   | Data sent to the host thread. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| transfer | ArrayBuffer[] | Yes  | ArrayBuffer instance holding an array of objects for which the ownership is transferred to the host thread. After the transfer, the objects are available only in the host thread. The array cannot be null.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |

**Example**

```ts
// Index.ets
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

### postMessage<sup>9+</sup>

postMessage(messageObject: Object, options?: PostMessageOptions): void

Sends a message from the Worker thread to the host thread by transferring object ownership or copying data. Pass-by-copy is used to pass [Sendable objects](../../arkts-utils/arkts-sendable.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                                     | Mandatory| Description                                                        |
| ------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| messageObject | Object                                    | Yes  | Data sent to the host thread. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| options | [PostMessageOptions](#postmessageoptions) | No  | If this parameter is specified, it functions the same as **ArrayBuffer[]**. Specifically, the ownership of the objects in the array is transferred to the host thread and becomes unavailable in the Worker thread. The objects are available only in the host thread.<br>If this parameter is not specified, the default value **undefined** is used, and information is transferred to the host thread by copying data.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |

**Example**

```ts
// Index.ets
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


### postMessageWithSharedSendable<sup>12+</sup>

postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void

Sends a message from the Worker thread to the host thread. In the message, a [Sendable object](../../arkts-utils/arkts-sendable.md) is passed by reference, and a non-Sendable object is passed by copy.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| message | Object | Yes | Data sent to the host thread. This data object must be serializable or shareable. For serialization supported types, see [Sequenceable Data Types](#sequenceable-data-types). For shareable supported types, see [Sendable supported data types](../../arkts-utils/arkts-sendable.md#sendable-data-types). |
| transfer | ArrayBuffer[] | No| ArrayBuffer instance holding an array of objects for which the ownership is transferred to the host thread. After the transfer, the objects are available only in the host thread. The array cannot be null. The default value is an empty array.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |

**Example**

<!--code_no_check-->
```ts
// The worker file path is entry/src/main/ets/workers/Worker.ets.
// Worker.ets
// Create a SendableObject instance and pass it to the host thread through the Worker thread.

import { SendableObject } from '../pages/sendable';
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  let object: SendableObject = new SendableObject();
  workerPort.postMessageWithSharedSendable(object);
}
```

```ts
// sendable.ets
// Define SendableObject.

@Sendable
export class SendableObject {
  a:number = 45;
}
```

<!--code_no_check-->
```ts
// Index.ets
// Receive the data passed from the Worker thread to the host thread and access its properties.

import { worker, MessageEvents } from '@kit.ArkTS';
import { SendableObject } from './sendable';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
workerInstance.postMessage(1);
workerInstance.onmessage = (e: MessageEvents) => {
  let obj: SendableObject = e.data;
  console.info("sendable index obj is: " + obj.a);
}
```


### callGlobalCallObjectMethod<sup>11+</sup>

callGlobalCallObjectMethod(instanceName: string, methodName: string, timeout: number, ...args: Object[]): Object

Calls a method of an object registered with the host thread. This API is called by the Worker thread. The invoking is synchronous for the Worker thread and asynchronous for the host thread. The return value is passed by copy.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                                     | Mandatory| Description                                                        |
| ------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| instanceName | string                                    | Yes  | Key used for registration. It is used to search for the object in the host thread.|
| methodName | string | Yes| Name of the method to call. This method cannot be modified by async or generator, or return results asynchronously by using the asynchronous mechanism at the bottom layer. Otherwise, an exception is thrown.|
| timeout | number | Yes | Indicates the maximum wait time from when the call is initiated from the Worker thread to when the target method is executed in the main thread, in ms, as an integer, in the range [1-5000]ms. If the value is out of range, the wait time for this call is 5000ms.<br>Before API version 21, in debug mode, the maximum wait time is limited by this parameter. <br> Since API version 21, in debug mode, the maximum wait time is not limited by this parameter and can wait indefinitely.|
| args | Object[] | No| Array of parameters in the method.|

**Return value**

| Type                                 | Description                           |
| ------------------------------------- | ------------------------------- |
| Object | Return value of the method in the host thread. The return value must be serializable. For details, see [Sequenceable Data Types](#sequenceable-data-types).|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                               |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |
| 10200019 | The globalCallObject is not registered. |
| 10200020 | The method to be called is not callable or is an async method or a generator. |
| 10200021 | The global call exceeds the timeout. |

**Example**
```ts
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
// Register registerObj with the ThreadWorker instance.
workerInstance.registerGlobalCallObject("myObj", registerObj);
workerInstance.postMessage("start worker");
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
  try {
    // The method to call does not carry an input parameter.
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessage", 0) as string;
    console.info("worker:", res); // worker: this is a message from TestObj
  } catch (error) {
    // Exception handling.
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
  try {
    // The method to call carries input parameters.
    let res : string = workerPort.callGlobalCallObjectMethod("myObj", "getMessageWithInput", 0, "hello there!") as string;
    console.info("worker:", res); // worker: this is a message from TestObj with input: hello there!
  } catch (error) {
    // Exception handling.
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
}
```

### close<sup>9+</sup>

close(): void

Terminates the Worker thread to stop it from receiving messages.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                     |
| -------- | ------------------------------- |
| 10200004 | The Worker instance is not running. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
```

```ts
// worker.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerPort = worker.workerPort;
workerPort.onmessage = (e: MessageEvents): void => {
    workerPort.close();
}
```

### postMessageAtFront

postMessageAtFront?(message: Object, priority: Priority, transfer?: ArrayBuffer[]): void

The Worker thread sends a queue-jumping message to the host thread. [Sendable objects](../../arkts-utils/arkts-sendable.md) in the message are passed by reference, and non-Sendable objects are passed by copying data.

> **NOTE**
> - If a Worker thread sends a queue-jumping message to the host thread, the message can jump the queue and is sent by priority.
> - If a queue-jumping message is sent between Worker threads, the message can only jump the queue, without priority.
> - The postMessage and postMessageWithSharedSendable interfaces send messages to the host thread at HIGH priority by default, without queue-jumping.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| --------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| message | Object | Yes | Data sent to the host thread. This data object must be serializable or shareable. For serialization supported types, see [Sequenceable Data Types](#sequenceable-data-types). For shareable supported types, see [Sendable supported data types](../../arkts-utils/arkts-sendable.md#sendable-data-types). |
| priority | [Priority](#priority) | Yes | Priority of the message to be sent. |
| transfer | ArrayBuffer[] | No | ArrayBuffer instance holding an array of objects for which the ownership is transferred to the host thread. After the transfer, the objects are available only in the host thread. The array cannot be null. The default value is an empty array. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID | Error Message                                |
| -------- | ----------------------------------------- |
| 10200004 | The Worker instance is not running.           |
| 10200006 | An exception occurred during serialization. |

**Example**

<!--code_no_check-->
```ts
// The Worker file path is: entry/src/main/ets/workers/Worker.ets
// Worker.ets

import { MessageEvents, ThreadWorkerGlobalScope, worker, Priority } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  workerPort.postMessage("1");
  workerPort.postMessage("2");
  // Way 1: Use the optional chaining operator (recommended, most concise).
  workerPort.postMessageAtFront?.("3-idle", Priority.IDLE);
  workerPort.postMessageAtFront?.("4-immediate", Priority.IMMEDIATE);

  // Way 2: Use non-null assertion and call directly (requires certainty that it exists).
  workerPort.postMessageAtFront!("5-low", Priority.LOW);

  // Way 3: Check whether the method exists before using it.
  if (workerPort.postMessageAtFront) {
    workerPort.postMessageAtFront("6-high", Priority.HIGH);
  } else {
    workerPort.postMessageWithSharedSendable("6-high");
  }
}
```

<!--code_no_check-->
```ts
// Index.ets
// Receive data that the Worker thread passes to the host thread.

import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
workerInstance.postMessage("start");
workerInstance.onmessage = (e: MessageEvents) => {
  // Simulate a time-consuming operation.
  let start = new Date().getTime();
  while (new Date().getTime() - start < 1000) {
    continue;
  }
  let res: string = e.data as string;
  // Execution result:
  // result is: 1
  // result is: 4-immediate
  // result is: 6-high
  // result is: 2
  // result is: 5-low
  // result is: 3-idle
  console.info("result is: " + res);
}
```

If the passed parameter is an object literal, you need to [explicitly annotate the type of the object literal](../../quick-start/typescript-to-arkts-migration-guide.md#object-literal-must-correspond-to-some-explicitly-declared-class-or-interface).

<!--code_no_check-->
```ts
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent, Priority } from '@kit.ArkTS';

class ClassA {
  public obj: string = ""
}

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  // When the optional chaining operator is used to call the API, passing an object literal causes a compilation error. The type of the object literal must be explicitly annotated.
  // workerPort.postMessageAtFront?.({obj: "obj"}, Priority.HIGH);

  let classAInstance: ClassA = { obj: "obj" };
  workerPort.postMessageAtFront?.(classAInstance, Priority.HIGH);

  // Use non-null assertion and call directly. An object literal can be passed directly.
  workerPort.postMessageAtFront!({ obj: "obj" }, Priority.HIGH);
  // Check whether the method exists before using it. An object literal can be passed directly.
  if (workerPort.postMessageAtFront) {
    workerPort.postMessageAtFront({ obj: "obj" }, Priority.HIGH);
  } else {
    workerPort.postMessageWithSharedSendable({ obj: "obj" });
  }
}
```

## WorkerEventListener<sup>9+</sup>

Implements event listening.

### (event: Event)<sup>9+</sup>

(event: Event): void | Promise&lt;void&gt;

Specifies the callback function to be called.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type           | Mandatory| Description          |
| ------ | --------------- | ---- | -------------- |
| event  | [Event](#event) | Yes  | Event class for the callback to invoke.|

**Return value**

| Type                                 | Description                           |
| ------------------------------------- | ------------------------------- |
| void&nbsp;\|&nbsp;Promise&lt;void&gt; | Returns no value or returns a **Promise**.|

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message                                  |
| -------- | -------------------------------------------- |
| 10200004 | The Worker instance is not running.              |
| 10200005 | The called API is not supported in the worker thread. |

**Example**

```ts
// Index.ets
import { worker, Event } from "@kit.ArkTS"

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", (event: Event) => {
  console.info("event type is: ", JSON.stringify(event.type));
});

const eventToDispatch : Event = { type: "alert", timeStamp: 0 }; // timeStamp is not supported.
workerInstance.dispatchEvent(eventToDispatch);
```


## GlobalScope<sup>9+</sup>

Implements the running environment of the Worker thread. The **GlobalScope** class inherits from [WorkerEventTarget](#workereventtarget9).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

| Name| Type                                                        | Read-only| Optional| Description                                 |
| ---- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------- |
| name | string                                                       | Yes  | No  | Worker instance specified when there is a new Worker instance.|
| self | [GlobalScope](#globalscope9)&nbsp;&amp;&nbsp;typeof&nbsp;globalThis | Yes  | No  | GlobalScope itself.                    |
| onerror | (ev: [ErrorEvent](#errorevent)) => void | No  | Yes  | Callback function invoked when an exception occurs during Worker execution. It is executed in the Worker thread. **ev** indicates the exception data received. The default value is **undefined**.|


## MessageEvents<sup>9+</sup>

Holds the data transferred between Worker threads. The class inherits from [Event](#event).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-only| Optional| Description              |
| ---- | ---- | ---- | ---- | ------------------ |
| data | any  | Yes  | No  | Data transferred between threads.|

## MessageType

type MessageType = 'message' | 'messageerror'

Defines the message type. Reserved data type, which is not implemented yet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Type | Description              |
| ---- | ------------------ |
| 'message'  | The message type is message, fixed at **'message'**.|
| 'messageerror'  | The message type is messageerror, fixed at **'messageerror'**.|

## ErrorCallback<sup>18+</sup>

type ErrorCallback = (err: ErrorEvent) => void

Defines an error callback.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                           | Mandatory| Description                                                        |
| --------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| err | [ErrorEvent](#errorevent)               | Yes   | Error event class, indicating the exception information that occurs during Worker execution. |

## Worker<sup>(deprecated)</sup>

Before using the following APIs, you must create a Worker instance. The **Worker** class inherits from [EventTarget](#eventtargetdeprecated).

> **NOTE**<br/>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker](#threadworker9) instead.

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name  | Type                   | Read-only| Optional| Description                                                        |
| ------ | ---------------------- | ---- | --- | ------------------------------------------------------------ |
| onexit<sup>(deprecated)</sup> | (code: number) => void | No | Yes | Callback function. Indicates the event handler called when the Worker is destroyed. The handler is executed in the host thread. In the callback function, the type of code is number, where 1 indicates abnormal exit and 0 indicates normal exit. Default value is undefined.<br/>**Note**: Supported since API version 7, deprecated since API version 9. Recommended to use [ThreadWorker.onexit](#properties) instead.|
| onerror<sup>(deprecated)</sup> | (err: [ErrorEvent](#errorevent)) => void | No | Yes | Callback function. Indicates the event handler called when an exception occurs during Worker execution. The handler is executed in the host thread. In the callback function, the type of err is [ErrorEvent](#errorevent), which indicates the received exception data. Default value is undefined.<br/>**Note**: Supported since API version 7, deprecated since API version 9. Recommended to use [ThreadWorker.onerror](#properties) instead.|
| onmessage<sup>(deprecated)</sup> | (event: [MessageEvent](#messageeventt)) => void | No | Yes | Callback function. Indicates the event handler called when the host thread receives a message sent by the Worker it created through the workerPort.postMessage interface. The handler is executed in the host thread. In the callback function, the type of event is [MessageEvent](#messageeventt), which indicates the received Worker message data. Default value is undefined.<br/>**Note**: Supported since API version 7, deprecated since API version 9. Recommended to use [ThreadWorker.onmessage](#properties) instead.|
| onmessageerror<sup>(deprecated)</sup> | (event: [MessageEvent](#messageeventt)) => void | No | Yes | Callback function. Indicates the event handler called when the Worker object receives a message that cannot be serialized. The handler is executed in the host thread. In the callback function, the type of event is [MessageEvent](#messageeventt), which indicates the received Worker message data. Default value is undefined.<br/>**Note**: Supported since API version 7, deprecated since API version 9. Recommended to use [ThreadWorker.onmessageerror](#properties) instead.|

### constructor<sup>(deprecated)</sup>

constructor(scriptURL: string, options?: WorkerOptions)

A constructor used to create a Worker instance.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker.constructor<sup>9+</sup>](#constructor9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name   | Type                           | Mandatory| Description                                                        |
| --------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| scriptURL | string                          | Yes  | URL of the Worker thread file. For details about the rules, see [Precautions for File URLs](../../arkts-utils/worker-introduction.md#precautions-for-file-urls).|
| options   | [WorkerOptions](#workeroptions) | No  | Options that can be set for the Worker instance.                                          |

**Example**

This example loads a Worker thread file in the Index.ets file of the entry module in the stage model. For the scenario of loading a Worker thread file using Library, see [File Path Notes](../../arkts-utils/worker-introduction.md#precautions-for-file-urls).

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

// URL of the Worker file: "entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.Worker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```

### postMessage<sup>(deprecated)</sup>

postMessage(message: Object, transfer: ArrayBuffer[]): void

Sends a message from the host thread to the Worker thread by transferring object ownership.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker.postMessage<sup>9+</sup>](#postmessage9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| message  | Object        | Yes   | The data object sent to the Worker must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| transfer | ArrayBuffer[] | Yes  | ArrayBuffer instance holding an array of objects for which the ownership is transferred to the Worker thread. After the transfer, the objects are available only in the Worker thread. The array cannot be null.|

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```

### postMessage<sup>(deprecated)</sup>

postMessage(message: Object, options?: PostMessageOptions): void

Sends a message from the host thread to the Worker thread by transferring object ownership or copying data.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker.postMessage<sup>9+</sup>](#postmessage9-1) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                                     | Mandatory| Description                                                        |
| ------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| message | Object                                    | Yes  | Data sent to the Worker. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| options | [PostMessageOptions](#postmessageoptions) | No  | If this parameter is specified, it functions the same as **ArrayBuffer[]**. Specifically, the ownership of the objects in the array is transferred to the Worker thread and becomes unavailable in the host thread. The objects are available only in the Worker thread.<br>If this parameter is not specified, the default value **undefined** is used, and information is transferred to the Worker thread by copying data.|

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);
```


### on<sup>(deprecated)</sup>

on(type: string, listener: EventListener): void

Adds an event listener for the Worker thread. This API provides the same functionality as [addEventListener<sup>(deprecated)</sup>](#addeventlistenerdeprecated).

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker.on<sup>9+</sup>](#on9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                     | Mandatory| Description            |
| -------- | ----------------------------------------- | ---- | ---------------- |
| type     | string                                    | Yes  | Type of the event to listen for.|
| listener | [EventListener](#eventlistenerdeprecated) | Yes   | Callback function when the event is triggered. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.on("alert", () => {
    console.info("alert listener callback");
})
```


### once<sup>(deprecated)</sup>

once(type: string, listener: EventListener): void

Adds an event listener for the Worker thread and removes the event listener after it is invoked once.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker.once<sup>9+</sup>](#once9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                     | Mandatory| Description            |
| -------- | ----------------------------------------- | ---- | ---------------- |
| type     | string                                    | Yes  | Type of the event to listen for.|
| listener | [EventListener](#eventlistenerdeprecated) | Yes | Callback function when the event is triggered. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.once("alert", () => {
    console.info("alert listener callback");
})
```


### off<sup>(deprecated)</sup>

off(type: string, listener?: EventListener): void

Removes an event listener for the Worker thread. This API provides the same functionality as [removeEventListener<sup>(deprecated)</sup>](#removeeventlistenerdeprecated).

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker.off<sup>9+</sup>](#off9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                     | Mandatory| Description                |
| -------- | ----------------------------------------- | ---- | -------------------- |
| type     | string                                    | Yes   | Type of the event to delete. The event type is set through [on<sup>(deprecated)</sup>](#ondeprecated). |
| listener | [EventListener](#eventlistenerdeprecated) | No   | Callback for which the listener is to be removed. If this parameter is not passed, all listeners of the specified type are removed. |

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
// Use the on, once, or addEventListener API to create the "alert" event, and use the off API to remove the event.
workerInstance.off("alert");
```


### terminate<sup>(deprecated)</sup>

terminate(): void

Terminates the Worker thread to stop it from receiving messages.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorker.terminate<sup>9+</sup>](#terminate9) instead.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.terminate();
```


## EventTarget<sup>(deprecated)</sup>
> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [WorkerEventTarget<sup>9+</sup>](#workereventtarget9) instead.

### addEventListener<sup>(deprecated)</sup>

addEventListener(type: string, listener: EventListener): void

Adds an event listener for the Worker thread. This API provides the same functionality as [on<sup>(deprecated)</sup>](#ondeprecated).

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [addEventListener<sup>9+</sup>](#addeventlistener9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                     | Mandatory| Description            |
| -------- | ----------------------------------------- | ---- | ---------------- |
| type     | string                                    | Yes  | Type of the event to listen for.|
| listener | [EventListener](#eventlistenerdeprecated) | Yes  | Callback function invoked upon event triggering.|

**Example**

```ts
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", () => {
  console.info("alert listener callback");
})
```


### removeEventListener<sup>(deprecated)</sup>

removeEventListener(type: string, callback?: EventListener): void

Removes an event listener for the Worker thread. This API provides the same functionality as [off<sup>(deprecated)</sup>](#offdeprecated).

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [removeEventListener<sup>9+</sup>](#removeeventlistener9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type                                     | Mandatory| Description                    |
| -------- | ----------------------------------------- | ---- | ------------------------ |
| type     | string                                    | Yes   | Type of the event to remove. The event type is set through [addEventListener<sup>(deprecated)</sup>](#addeventlistenerdeprecated). |
| callback | [EventListener](#eventlistenerdeprecated) | No   | Callback for which the listener is to be removed. If this parameter is not passed, all listeners of the specified type are removed. |

**Example**

```ts
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", () => {
  console.info("alert listener callback");
})

workerPort.removeEventListener('alert');
```


### dispatchEvent<sup>(deprecated)</sup>

dispatchEvent(event: Event): boolean

Dispatches the events registered on the Worker instance.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [dispatchEvent<sup>9+</sup>](#dispatchevent9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type           | Mandatory| Description            |
| ------ | --------------- | ---- | ---------------- |
| event  | [Event](#event) | Yes  | Event to dispatch.|

**Return value**

| Type   | Description                           |
| ------- | ------------------------------- |
| boolean | Dispatch result. The value **true** is returned if the dispatch is successful; otherwise, **false** is returned.|

**Example**

```ts
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert_add", ()=>{
  console.info("alert listener callback");
})

workerPort.dispatchEvent({type: 'alert_add', timeStamp: 0}); // timeStamp is not supported yet.
```

The **dispatchEvent** API can be used together with the **addEventListener** API. The sample code is as follows:

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (): void => {
    console.info("receive data from worker.ets");
}
```

```ts
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert", ()=>{
  console.info("alert listener callback");
})

workerPort.onmessage = (event: MessageEvents) => {
  workerPort.dispatchEvent({type:"alert", timeStamp:0}); // timeStamp is not supported yet.
}
```

### removeAllListener<sup>(deprecated)</sup>

removeAllListener(): void

Removes all event listeners for the Worker thread.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [removeAllListener<sup>9+</sup>](#removealllistener9) instead.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
// worker.ets
import { DedicatedWorkerGlobalScope, ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.addEventListener("alert_add", ()=>{
  console.info("alert listener callback");
})

workerPort.removeAllListener();
```


## DedicatedWorkerGlobalScope<sup>(deprecated)</sup>

Implements communication between the Worker thread and the host thread. This class inherits from [WorkerGlobalScope](#workerglobalscopedeprecated).

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorkerGlobalScope<sup>9+</sup>](#threadworkerglobalscope9) instead.

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name  | Type                   | Read-only| Optional| Description                                                        |
| ------ | ---------------------- | ---- | --- | ------------------------------------------------------------ |
| onmessage<sup>(deprecated)</sup> | (this: [DedicatedWorkerGlobalScope](#dedicatedworkerglobalscopedeprecated), ev: [MessageEvent](#messageeventt)) => void | No | Yes | Callback function, indicating the event handler called when the Worker thread receives a message sent by its host thread through the postMessage interface. The handler is executed in the Worker thread. Here, this refers to the caller object itself [DedicatedWorkerGlobalScope](#dedicatedworkerglobalscopedeprecated), and ev is of type [MessageEvent](#messageeventt), indicating the received Worker message data. The default value is undefined.<br/>**Note**: Supported since API version 7, deprecated since API version 9. It is recommended to use [ThreadWorkerGlobalScope.onmessage](#properties-2) instead. |
| onmessageerror<sup>(deprecated)</sup> | (this: [DedicatedWorkerGlobalScope](#dedicatedworkerglobalscopedeprecated), ev: [MessageEvent](#messageeventt)) => void | No | Yes | Callback function, indicating the event handler called when the Worker object receives a message that cannot be deserialized. The handler is executed in the Worker thread. Here, this refers to the caller object itself [DedicatedWorkerGlobalScope](#dedicatedworkerglobalscopedeprecated), and ev is of type [MessageEvent](#messageeventt), indicating the received Worker message data. The default value is undefined.<br/>**Note**: Supported since API version 7, deprecated since API version 9. It is recommended to use [ThreadWorkerGlobalScope.onmessageerror](#properties-2) instead. |

### postMessage<sup>(deprecated)</sup>

postMessage(messageObject: Object, transfer: Transferable[]): void

Sends a message from the Worker thread to the host thread by transferring object ownership.

> **NOTE**<br>
> This API is deprecated since API version 9. You are advised to use [ThreadWorkerGlobalScope<sup>9+</sup>.postMessage<sup>9+</sup>](#postmessage9-2).

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                                     | Mandatory| Description                                                        |
| ------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| messageObject | Object                                    | Yes  | Data sent to the host thread. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| transfer| Transferable[]                            | Yes  | Currently, this parameter is not supported.                                        |

### postMessage<sup>(deprecated)</sup>

postMessage(messageObject: Object, transfer: ArrayBuffer[]): void

Sends a message from the Worker thread to the host thread by transferring object ownership.

> **NOTE**<br>
> The **postMessage** API is supported since API version 9 and deprecated since API version 9. You are advised to use [ThreadWorkerGlobalScope<sup>9+</sup>.postMessage<sup>9+</sup>](#postmessage9-2) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| messageObject  | Object        | Yes   | Data sent to the host thread. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| transfer | ArrayBuffer[] | Yes  | ArrayBuffer instance holding an array of objects for which the ownership is transferred to the host thread. After the transfer, the objects are available only in the host thread. The array cannot be null.|

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (e: MessageEvents): void => {
    // let data = e.data;
    console.info("receive data from worker.ets");
}
```
```ts
// worker.ets
import { DedicatedWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: DedicatedWorkerGlobalScope = worker.parentPort;

workerPort.onmessage = (): void => {
    // let data = e.data;
    let buffer = new ArrayBuffer(5)
    workerPort.postMessage(buffer, [buffer]);
}
```

### postMessage<sup>(deprecated)</sup>

postMessage(messageObject: Object, options?: PostMessageOptions): void

Sends a message from the Worker thread to the host thread by transferring object ownership or copying data.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorkerGlobalScope<sup>9+</sup>.postMessage<sup>9+</sup>](#postmessage9-3).

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type                                     | Mandatory| Description                                                        |
| ------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| messageObject | Object                                    | Yes  | Data sent to the host thread. This data object must be a serializable object. For supported serialization types, see [Sequenceable Data Types](#sequenceable-data-types). |
| options | [PostMessageOptions](#postmessageoptions) | No  | If this parameter is specified, it functions the same as **ArrayBuffer[]**. Specifically, the ownership of the objects in the array is transferred to the host thread and becomes unavailable in the Worker thread. The objects are available only in the host thread.<br>If this parameter is not specified, the default value **undefined** is used, and information is transferred to the host thread by copying data.|

**Example**

<!--no_check-->
```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
workerInstance.onmessage = (): void => {
    console.info("receive data from worker.ets");
}
```
```ts
// worker.ets
import { ErrorEvent, MessageEvents, worker } from '@kit.ArkTS';

const parentPort = worker.parentPort;
parentPort.onmessage = (e: MessageEvents) => {
  parentPort.postMessage("receive data from main thread");
}
```

### close<sup>(deprecated)</sup>

close(): void

Terminates the Worker thread to stop it from receiving messages.

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ThreadWorkerGlobalScope<sup>9+</sup>.close<sup>9+</sup>](#close9).

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.postMessage("hello world");
```
```ts
// worker.ets
import { worker } from '@kit.ArkTS';

const parentPort = worker.parentPort;
parentPort.onmessage = (): void => {
    parentPort.close()
}
```


## PostMessageOptions

Defines the object for which the ownership is to be transferred during data transfer. The object must be an ArrayBuffer instance. After the ownership is transferred, the object becomes unavailable in the sender and can be used only in the receiver.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

| Name    | Type    | Read-only| Optional| Description                             |
| -------- | -------- | ---- | ---- | --------------------------------- |
| transfer | Object[] | No  | Yes  | **ArrayBuffer** array used to transfer the ownership. The array cannot be **null**. The default value is **undefined**.|


## Event

Defines the event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name     | Type  | Read-only| Optional| Description                                        |
| --------- | ------ | ---- | ---- | -------------------------------------------- |
| type      | string | Yes  | No  | Type of the event.                            |
| timeStamp | number | Yes | No | Timestamp when the event is created, in ms. Not supported currently. |


## EventListener<sup>(deprecated)</sup>

Defines an event listener.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [WorkerEventListener<sup>9+</sup>](#workereventlistener9) instead.

### (evt: Event)<sup>(deprecated)</sup>

(evt: Event): void | Promise&lt;void&gt;

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [(event: Event)](#event-event9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type           | Mandatory| Description          |
| ------ | --------------- | ---- | -------------- |
| evt    | [Event](#event) | Yes  | Event class for the callback to invoke.|

**Return value**

| Type                                 | Description                           |
| ------------------------------------- | ------------------------------- |
| void&nbsp;\|&nbsp;Promise&lt;void&gt; | Returns no value or returns a **Promise**.|

**Example**

```ts
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.Worker("entry/ets/workers/worker.ets");
workerInstance.addEventListener("alert", ()=>{
    console.info("alert listener callback");
})
```


## ErrorEvent

Provides detailed information about the exception that occurs during worker execution. This class inherits from [Event](#event).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

| Name    | Type  | Read-only| Optional| Description                |
| -------- | ------ | ---- | ---- | -------------------- |
| message  | string | Yes  | No  | Information about the exception.|
| filename | string | Yes  | No  | File where the exception is located.|
| lineno   | number | Yes  | No  | Serial number of the line where the exception is located.    |
| colno    | number | Yes  | No  | Serial number of the column where the exception is located.    |
| error    | Object | Yes   | No   | Exception object.           |


## MessageEvent\<T\>

Holds the data transferred between Worker threads. The class inherits from [Event](#event).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-only| Optional| Description              |
| ---- | ---- | ---- | ---- | ------------------ |
| data | T    | Yes  | No  | Data transferred between threads.|


## WorkerGlobalScope<sup>(deprecated)</sup>

Implements the running environment of the Worker thread. The **WorkerGlobalScope** class inherits from [EventTarget](#eventtargetdeprecated).

> **NOTE**<br>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [GlobalScope<sup>9+</sup>](#globalscope9) instead.

**System capability**: SystemCapability.Utils.Lang

| Name| Type                                                        | Read-only| Optional| Description                                 |
| ---- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------- |
| name | string                                                       | Yes  | No  | Worker instance specified when there is a new Worker instance.|
| self | [WorkerGlobalScope](#workerglobalscopedeprecated)&nbsp;&amp;&nbsp;typeof&nbsp;globalThis | Yes  | No  | WorkerGlobalScope.              |
| onerror | (ev: [ErrorEvent](#errorevent)) => void | No| Yes| Callback function invoked when an exception occurs during Worker execution. It is executed in the Worker thread. **ev** indicates the exception data received. The default value is **undefined**.|

## Priority

Indicates the priority for sending messages.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Utils.Lang

| Name | Value | Description |
| -------- | -------- | -------- |
| IMMEDIATE | 1 | Immediate execution priority. Indicates that the message is sent with priority over HIGH. |
| HIGH | 2 | High priority. Indicates that the message is sent with priority over LOW. |
| LOW | 3 | Low priority. Indicates that the message is sent with priority over IDLE. |
| IDLE | 4 | Background priority. Indicates that the message is sent only when there are no messages of other priorities. |

## More Information

### Sequenceable Data Types

The following object types are supported: basic types except Symbol, Date, String, RegExp, Array, Map, Set, Object (simple objects only, for example, objects created using **{}** or **new Object**), ArrayBuffer, and TypedArray. (Note that only properties can be transferred for common objects. Prototypes and methods cannot be transferred.)

Exception: When an object created through a custom class is passed, no serialization error occurs. However, the properties (such as Function) of the custom class cannot be passed through serialization.
> **NOTE**<br>
> An FA project of API version 9 is used as an example.

```ts
// Index.ets
import { worker, MessageEvents } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("workers/worker.ets");
workerInstance.postMessage("message from main thread to worker");
workerInstance.onmessage = (d: MessageEvents): void => {
  // When the Worker thread passes myModel, data is myModel. data has no init method.
  let data: Record<string, Object> = d.data as Record<string, Object>;
  console.info('name:', data.name);// name: default name
  console.info('init:', data.init === undefined);// init: true
}
```
```ts
// worker.ets
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort = worker.workerPort;
class MyModel {
    name = "default name";
    init() {
        this.name = "MyModel";
    }
}
workerPort.onmessage = (d: MessageEvents): void => {
  console.info("worker.ets onmessage");
  let data: string = d.data;
  let func1 = () => {
    console.info("post message is function");
  }
  // workerPort.postMessage(func1); A serialization error occurs when passing func1.
  let myModel = new MyModel();
  workerPort.postMessage(myModel);     // Pass myModel without serialization errors, but functions in myModel are lost.
}
workerPort.onmessageerror = () => {
    console.error("worker.ets onmessageerror");
}
workerPort.onerror = (err: ErrorEvent) => {
    console.error("worker.ets onerror" + err.message);
}
```

### Memory Model
The Worker thread is implemented based on the actor model. In the Worker interaction process, the host thread can create multiple Worker threads. The running environments of Worker threads are isolated from each other. Objects are transferred through serialization, reference passing, or ownership transfer. After the Worker threads complete computing tasks, the results are returned to the host thread.

Each actor concurrently processes tasks of the host thread. For each actor, there is a message queue and a single-thread execution module. The message queue receives requests from the host thread and other actors; the single-thread execution module serially processes requests, sends requests to other actors, and creates new actors. These isolated actors use the asynchronous mode and can run concurrently.

## Sample Code
> **NOTE**<br>
> Only the FA model is supported in API version 8 and earlier versions. If you want to use API version 8 or earlier, change the API for constructing the Worker instance and the API for creating an object in the Worker thread for communicating with the host thread.<br>
### FA Model
> The following uses API version 9 as an example.

```ts
// Main thread (The following assumes that the workers directory and pages directory are at the same level.)
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

// Create a Worker instance in the host thread.
const workerInstance = new worker.ThreadWorker("workers/worker.ets");

// The host thread transfers information to the Worker thread.
const buffer = new ArrayBuffer(8);
workerInstance.postMessage(buffer, [buffer]);

// The host thread receives information from the Worker thread.
workerInstance.onmessage = (e: MessageEvents): void => {
    // data carries the information sent by the Worker thread.
    let data: Int8Array = e.data;
    console.info("main thread onmessage");

    // Terminate the Worker instance.
    workerInstance.terminate();
}

// Call onexit().
workerInstance.onexit = (code) => {
    console.info("main thread terminate");
}

workerInstance.onerror = (err: ErrorEvent) => {
    console.error("main error message " + err.message);
}
```
```ts
// worker.ets
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

// Create an object in the Worker thread for communicating with the host thread.
const workerPort = worker.workerPort;

// The Worker thread receives information from the host thread.
workerPort.onmessage = (e: MessageEvents): void => {
    // data carries the information sent by the host thread.
    let data: ArrayBuffer = e.data;
    const view = new Int8Array(data).fill(3);
    console.info("worker.ets onmessage");

    // The Worker thread sends information to the host thread.
    workerPort.postMessage(view);
}

// Trigger a callback when an error occurs in the Worker thread.
workerPort.onerror = (err: ErrorEvent) => {
    console.error("worker.ets onerror");
}
```
Add the following configuration to the module-level **entry/build-profile.json5** file:
```json
  "buildOption": {
    "sourceOption": {
      "workers": [
        "./src/main/ets/entryability/workers/worker.ets"
      ]
    }
  }
```
### Stage Model
> The following uses API version 18 as an example.
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
            // Create a Worker instance in the host thread.
            const workerInstance = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
            // The host thread transfers information to the Worker thread.
            const buffer = new ArrayBuffer(8);
            workerInstance.postMessage(buffer);
            // The host thread receives information from the Worker thread.
            workerInstance.onmessage = (e: MessageEvents): void => {
              // data carries the information sent by the Worker thread.
              let data: Int8Array = e.data;
              console.info("main thread data is  " + data);
              // Terminate the Worker instance.
              workerInstance.terminate();
            }
            // Call onexit().
            workerInstance.onexit = (code) => {
              console.info("main thread terminate");
            }

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
```ts
// Worker.ets
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

// Create an object in the Worker thread for communicating with the host thread.
const workerPort = worker.workerPort;

// The Worker thread receives information from the host thread.
workerPort.onmessage = (e: MessageEvents): void => {
  // data carries the information sent by the host thread.
  let data: ArrayBuffer = e.data;
  // Write data to the received buffer.
  const view = new Int8Array(data).fill(3);
  // The Worker thread sends information to the host thread.
  workerPort.postMessage(view);
}

// Trigger a callback when an error occurs in the Worker thread.
workerPort.onerror = (err: ErrorEvent) => {
  console.error("worker.ets onerror" + err.message);
}
```
Add the following configuration to the module-level **entry/build-profile.json5** file:
```json
  "buildOption": {
    "sourceOption": {
      "workers": [
        "./src/main/ets/workers/Worker.ets"
      ]
    }
  }
```
<!--no_check-->


### Using dispatchEvent with addEventListener

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
          const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

          // Usage 1:
          workerInstance.on("alert_on", () => {
            console.info("alert listener callback: alert_on");
          })
          workerInstance.once("alert_once", () => {
            console.info("alert listener callback: alert_once");
          })
          workerInstance.addEventListener("alert_add", () => {
            console.info("alert listener callback: alert_add");
          })

          // The event listener created by once is removed after being executed once.
          workerInstance.dispatchEvent({type:"alert_once", timeStamp:0}); // timeStamp is not supported yet.
          // The event listener created by on will not be proactively deleted.
          workerInstance.dispatchEvent({type: "alert_on", timeStamp: 0}); // timeStamp is not supported yet.
          workerInstance.dispatchEvent({type: "alert_on", timeStamp: 0}); // timeStamp is not supported yet.
          // The event listener created by addEventListener will not be proactively deleted.
          workerInstance.dispatchEvent({type: "alert_add", timeStamp: 0}); // timeStamp is not supported yet.
          workerInstance.dispatchEvent({type: "alert_add", timeStamp: 0}); // timeStamp is not supported yet.

          // Usage 2:
          // The event type can be customized, and the special types "message", "messageerror", and "error" exist.
          // When type = "message", the event handler defined by onmessage will also be executed.
          // When type = "messageerror", the event handler defined by onmessageerror will also be executed.
          // When type = "error", the event handler defined by onerror will also be executed.
          // removeEventListener or off can be used to remove an event listener that is created by addEventListener, on, or once.

          workerInstance.addEventListener("message", () => {
            console.info("message listener callback");
          })
          workerInstance.onmessage = (e: MessageEvents): void => {
            console.info("onmessage : message listener callback");
          }
          // When dispatchEvent is called to distribute the "message" event, the callback passed in addEventListener and onmessage will be invoked.
          workerInstance.dispatchEvent({type: "message", timeStamp: 0}); // timeStamp is not supported yet.

          // Send a message to the Worker thread.
          workerInstance.postMessage("test");
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

```ts
// worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (event: MessageEvents) => {
  console.info("worker thread recv data is: ", event.data);
  let data: string = event.data;
  const workerHandler1 = () => console.info("Handler 1 is: ", data);
  const workerHandler2 = () => console.info("Handler 2 is: ", data);

  // Register two listeners.
  workerPort.addEventListener("workerListener", workerHandler1);
  workerPort.addEventListener("workerListener", workerHandler2);

  // Register two listeners for workerListener. Both listeners are executed.
  workerPort.dispatchEvent({type: "workerListener", timeStamp: 0}); // timeStamp is not supported yet.

  // Remove the workerHandler1 listener.
  workerPort.removeEventListener("workerListener", workerHandler1); // timeStamp is not supported yet.

  // The workerHandler1 listener has been removed, and only workerHandler2 is executed.
  workerPort.dispatchEvent({type: "workerListener", timeStamp: 0}); // timeStamp is not supported yet.

  // Remove all event listeners.
  workerPort.removeAllListener();
};
```