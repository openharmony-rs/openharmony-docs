# ThreadWorker

```TypeScript
class ThreadWorker implements WorkerEventTarget
```

Before using the following APIs, you must create a ThreadWorker instance. The ThreadWorker class inherits from WorkerEventTarget.

**Inheritance/Implementation:** ThreadWorker implements [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md)

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## addEventListener

```TypeScript
addEventListener(type: string, listener: WorkerEventListener): void
```

Adds an event listener for the Worker thread. This API provides the same functionality as on9+.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event to listen for. |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | Yes | Callback to invoke when an event of the specified type occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

// Execute the callback of the alert type.
workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.
```

## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

A constructor used to create a ThreadWorker instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scriptURL | string | Yes | URL of the Worker thread file. For details about the rules, see Precautions for File URLs. |
| options | [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | No | Options that can be set for the Worker instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-failed-to-initialize-the-worker-instance) | Worker initialization failed. |
| [10200007](../errorcode-utils.md#10200007-abnormal-worker-file-path) | The worker file path is invalid. |

**Examples**

The following uses the Index.ets file in the entry module of the stage model as an example to describe how to load the worker file. For details about how to use the library to load the Worker thread file, see [Precautions for File URLs](../../../arkts-utils/worker-introduction.md#precautions-for-file-urls).

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

// URL of the Worker file: "entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.ThreadWorker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```

## dispatchEvent

```TypeScript
dispatchEvent(event: Event): boolean
```

Dispatches the event defined for the Worker thread.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Event](arkts-arkts-worker-event-i.md) | Yes | Event to dispatch. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

let result: Boolean = workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.

console.info("dispatchEvent result is: ", result);
```

## off

```TypeScript
off(type: string, listener?: WorkerEventListener): void
```

Removes an event listener for the Worker thread. This API provides the same functionality as removeEventListener9 +.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event for which the event listener is removed. |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | No | listener Callback of the event listener to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

**Examples**

```TypeScript
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

## on

```TypeScript
on(type: string, listener: WorkerEventListener): void
```

Adds an event listener for the Worker thread. This API provides the same functionality as addEventListener9+.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event to listen for. |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | Yes | Callback to invoke when an event of the specified type occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

**Examples**

```TypeScript
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

## onAllErrors

```TypeScript
onAllErrors?: ErrorCallback
```

Called when an exception occurs within the lifecycle of the Worker thread. The event handler is executed in the host thread.

onerror can capture only exceptions generated by synchronous methods within the onmessage callback. It cannot capture exceptions from multithreaded callbacks or modularization-related exceptions. Once an exception is captured, the Worker thread will proceed to the destruction process and cannot be used.

onAllErrors can capture global exceptions generated during the onmessage callback, timer callback, and file execution of the Worker thread. After an exception is captured by onAllErrors, the Worker thread remains alive and can continue to be used. You are advised to use onAllErrors instead of onerror.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

## once

```TypeScript
once(type: string, listener: WorkerEventListener): void
```

Adds an event listener for the Worker thread and removes the event listener after it is invoked once.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event to listen for |
| listener | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | Yes | listener Callback to invoke when an event of the specified type occurs |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.once("alert", () => {
  console.info("alert listener callback");
})

workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.

// Event listeners added using once are automatically removed after being executed once and cannot be executed multiple times.
// workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.
```

## onerror

```TypeScript
onerror?: (err: ErrorEvent) => void
```

Called when an exception occurs during worker execution. The event handler is executed in the host thread. In the callback function, the err type is ErrorEvent, indicating the received abnormal data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| err | [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

## onexit

```TypeScript
onexit?: (code: number) => void
```

Called when the Worker thread exits. The event handler is executed in the host thread. In the callback function, the code value is of the number type, where the value 1 indicates abnormal exit and 0 indicates normal exit.The default value is undefined.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

## onmessage

```TypeScript
onmessage?: (event: MessageEvents) => void
```

Called when the host thread receives a message sent by the Worker thread through workerPort.postMessage. The event handler is executed in the host thread. In the callback function, the event type is MessageEvents, indicating the received message data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [MessageEvents](arkts-arkts-worker-messageevents-i.md) | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

## onmessageerror

```TypeScript
onmessageerror?: (event: MessageEvents) => void
```

Called when the Worker thread receives a message that cannot be serialized. The event handler is executed in the host thread. In the callback function, the event type is MessageEvents, indicating the received message data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [MessageEvents](arkts-arkts-worker-messageevents-i.md) | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-api-not-supported-in-the-worker-thread) | The called API is not supported in the worker thread. |

## postMessage

```TypeScript
postMessage(message: Object, transfer: ArrayBuffer[]): void
```

Sends a message from the host thread to the Worker thread by transferring object ownership.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | Object | Yes | Data to be sent to the Worker thread. The data object must be sequenceable. For details about the supported parameter types, see Sequenceable Data Types. |
| transfer | ArrayBuffer[] | Yes | ArrayBuffer instance holding an array of objects for which the ownership is transferred to the Worker thread. After the transfer, the objects are available only in the Worker thread. The array cannot be null. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization. |

**Examples**

```TypeScript
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

<a id="postmessage-1"></a>

## postMessage

```TypeScript
postMessage(message: Object, options?: PostMessageOptions): void
```

Sends a message from the host thread to the Worker thread by transferring object ownership or copying data.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | Object | Yes | Data to be sent to the Worker thread. The data object must be sequenceable. For details about the supported parameter types, see Sequenceable Data Types. |
| options | [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | No | If this parameter is specified, it functions the same as ArrayBuffer[]. Specifically, the ownership of the objects in the array is transferred to the Worker thread and becomes unavailable in the host thread. The objects are available only in the Worker thread. If this parameter is not specified, the default value undefined is used, and information is transferred to the Worker thread by copying data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization. |

**Examples**

```TypeScript
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.postMessage("hello world");

let buffer = new ArrayBuffer(8);

// When the options parameter is specified, the ownership of the buffer is transferred to the Worker thread and will no longer be accessible from the host thread.
workerInstance.postMessage(buffer, [buffer]);

// When the options parameter is not provided, it defaults to undefined, and the buffer is sent to the Worker thread by copying the data.
workerInstance.postMessage(buffer);
```

## postMessageWithSharedSendable

```TypeScript
postMessageWithSharedSendable(message: Object, transfer?: ArrayBuffer[]): void
```

Sends a message from the host thread to the Worker thread. In the message, a sendable object is passed by reference, and a non-sendable object is passed by serialization.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | Object | Yes | Data to be sent to the Worker thread. The data object must be sequenceable or sendable. For details about the supported sequenceable types, see Sequenceable Data Types. For details about the supported sendable types, see Sendable Data Types. |
| transfer | ArrayBuffer[] | No | ArrayBuffer instance holding an array of objects for which the ownership is transferred to the Worker thread. After the transfer, the objects are available only in the Worker thread. The array cannot be null. The default value is an empty array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization. |

**Examples**

```TypeScript
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

```TypeScript
// sendable.ets
// Define SendableObject.

@Sendable
export class SendableObject {
  a:number = 45;
}
```

```TypeScript
// The worker file path is entry/src/main/ets/workers/Worker.ets.
// Worker.ets
// Receive and access the data passed from the host thread to the Worker thread.

import { SendableObject } from '../pages/sendable';
import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (e: MessageEvents) => {
  let obj: SendableObject = e.data;
  console.info("sendable obj is: " + obj.a);
}
```

## registerGlobalCallObject

```TypeScript
registerGlobalCallObject(instanceName: string, globalCallObject: Object): void
```

Registers an object with the ThreadWorker instance of the host thread. In this way, the methods of the object can be called in the Worker thread through callGlobalCallObjectMethod.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceName | string | Yes | Key used for registration, based on which the registered object is identified during method calling. |
| globalCallObject | Object | Yes | Object to register. The ThreadWorker instance holds a strong reference to the object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |

**Examples**

```TypeScript
//Index.ets
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

```TypeScript
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
    console.info("worker:", res); //worker: this is a message from TestObj with input: hello there!
  } catch (error) {
    // Exception handling.
    console.error("worker: error code is " + error.code + " error message is " + error.message);
  }
}
```

## removeAllListener

```TypeScript
removeAllListener(): void
```

Removes all event listeners for the Worker thread.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |

**Examples**

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

Removes an event listener for the Worker thread. This API provides the same functionality as off9+.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Type of the event for which the event listener is to be removed. |
| callback | [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | No | Callback to invoke when the listener is removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |

**Examples**

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", () => {
  console.info("alert listener callback");
})

workerInstance.dispatchEvent({type: "alert", timeStamp: 0}); // timeStamp is not supported yet.

workerInstance.removeEventListener("alert");
```

## terminate

```TypeScript
terminate(): void
```

Terminates the Worker thread to stop it from receiving messages.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |

**Examples**

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

Unregisters an object with the ThreadWorker instance of the host thread. This API releases the strong reference between the ThreadWorker instance and the target object. No error is reported if no object is matched.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceName | string | No | Key used for registration. If this parameter is left blank, all registered objects registered in the ThreadWorker instance are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker-instance-is-not-running) | The Worker instance is not running. |

**Examples**

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
// Unregister the object.
workerInstance.unregisterGlobalCallObject("myObj");
// Unregister all objects from the ThreadWorker instance.
//workerInstance.unregisterGlobalCallObject();
workerInstance.postMessage("start worker");
```
