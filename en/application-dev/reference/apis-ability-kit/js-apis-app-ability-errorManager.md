# @ohos.app.ability.errorManager (Error Management Module)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @rr_cn-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

The ErrorManager module provides capabilities for registering and unregistering error observers, which are primarily used to listen for errors such as JavaScript crashes and application freezes.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import
```ts
import { errorManager } from '@kit.AbilityKit';
```

## errorManager.on('error')

on(type: 'error', observer: ErrorObserver): number

Registers an error observer. Once registered, it can capture JavaScript crashes occurring within the application, which are a type of application crash. When the observer captures such an exception, the application will not exit automatically. You are advised to add a synchronous exit operation after the callback function completes.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'error'**.|
| observer | [ErrorObserver](js-apis-inner-application-errorObserver.md) | Yes| Error observer instance.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | number | Unique index of the observer, which corresponds one-to-one with the observer. This value can be used as the **observerId** parameter in the **errorManager.off** function.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16000003 | The specified ID does not exist. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.info('onUnhandledException, errorMsg: ', errorMsg);
  },
  onException(errorObj) {
    console.info('onException, name: ', errorObj.name);
    console.info('onException, message: ', errorObj.message);
    if (typeof(errorObj.stack) === 'string') {
      console.info('onException, stack: ', errorObj.stack);
    }
  }
};
let observerId = -1;

try {
  observerId = errorManager.on('error', observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

## errorManager.on('globalErrorOccurred')<sup>18+</sup>

on(type: 'globalErrorOccurred', observer: GlobalObserver): void

Registers a global error observer via the **errorManager.on** API within any thread of a process. Once registered, it can capture exceptions occurring in any thread across the entire process. When the observer captures such an exception, the application will not exit automatically. You are advised to add a synchronous exit operation after the callback function completes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'globalErrorOccurred'**.|
| observer | [GlobalObserver](#globalobserver18) | Yes| Customized callback function for exception handling.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16200001 | The caller has been released. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function errorFunc(observer: errorManager.GlobalError) {
    console.info("result name :" + observer.name);
    console.info("result message :" + observer.message);
    console.info("result stack :" + observer.stack);
    console.info("result instanceName :" + observer.instanceName);
    console.info("result instanceType :" + observer.instanceType);
}

try {
  errorManager.on('globalErrorOccurred', errorFunc);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

## errorManager.off('globalErrorOccurred')<sup>18+</sup>

off(type: 'globalErrorOccurred', observer?: GlobalObserver): void

Unregisters a global error observer. Once unregistered, global listening cannot be implemented.

If the observer passed in is not in the observer queue registered via the **on** API, error code 16300004 is thrown. Therefore, you are advised to handle this using **try-catch** logic.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'globalErrorOccurred'**.|
| observer | [GlobalObserver](#globalobserver18) | No| Observer registered by the **on** API. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16200001 | The caller has been released. |
| 16300004 | The observer does not exist. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function errorFunc(observer: errorManager.GlobalError) {
    console.info("result name :" + observer.name);
    console.info("result message :" + observer.message);
    console.info("result stack :" + observer.stack);
    console.info("result instanceName :" + observer.instanceName);
    console.info("result instanceType :" + observer.instanceType);
}

try {
  errorManager.off('globalErrorOccurred', errorFunc)
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

## errorManager.off('error')

off(type: 'error', observerId: number,  callback: AsyncCallback\<void>): void

Unregisters an error observer. This API uses an asynchronous callback to return the result.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'error'**.|
| observerId | number | Yes| Index of the observer returned by **on()**.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16000003 | The specified ID does not exist. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 100;

function unregisterErrorObserverCallback(err: BusinessError) {
  if (err) {
    console.error('------------ unregisterErrorObserverCallback ------------', err);
  }
}

try {
  errorManager.off('error', observerId, unregisterErrorObserverCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

## errorManager.off('error')

off(type: 'error', observerId: number): Promise\<void>

Unregisters an error observer. This API uses a promise to return the result.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'error'**.|
| observerId | number | Yes| Index of the observer returned by **on()**.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16000003 | The specified ID does not exist. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 100;

try {
  errorManager.off('error', observerId)
    .then((data) => {
      console.info('----------- unregisterErrorObserver success ----------', data);
    })
    .catch((err: BusinessError) => {
      console.error('----------- unregisterErrorObserver fail ----------', err);
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```

## errorManager.on('loopObserver')<sup>12+</sup>

on(type: 'loopObserver', timeout: number, observer: LoopObserver): void

Registers an observer for the message processing duration of the main thread. After the registration, the execution time of a message processed by the main thread of the application can be captured.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'loopObserver'**, indicating an observer for the message processing duration of the main thread.|
| timeout | number | Yes|  Event execution threshold, in milliseconds. The value must be greater than **0**.|
| observer | [LoopObserver](js-apis-inner-application-loopObserver.md) | Yes| Observer to register.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.LoopObserver = {
  onLoopTimeOut(timeout: number) {
    console.info('Duration timeout: ' + timeout);
  }
};

errorManager.on("loopObserver", 1, observer);
```

## errorManager.on('globalUnhandledRejectionDetected')<sup>18+</sup>

on(type: 'globalUnhandledRejectionDetected', observer: GlobalObserver): void

Registers a rejected promise observer with any thread in the process. Once registered, it can capture a rejected promise that is not captured in the current thread of the application.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name                  | Type                                                         | Mandatory| Description                                      |
|-----------------------|-------------------------------------------------------------| -------- |------------------------------------------|
| type                  | string                                                      | Yes| Event type. It is fixed at **'globalUnhandledRejectionDetected'**, indicating an observer for the promise rejection.|
| observer              | [GlobalObserver](#globalobserver18) | Yes| Observer to register.                         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16200001 | The caller has been released. |

**Example**

```ts
import { errorManager } from '@kit.AbilityKit';

function promiseFunc(observer: errorManager.GlobalError) {
  console.info("result name :" + observer.name);
  console.info("result message :" + observer.message);
  console.info("result stack :" + observer.stack);
  console.info("result instanceName :" + observer.instanceName);
  console.info("result instanceType :" + observer.instanceType);
}

errorManager.on("globalUnhandledRejectionDetected", promiseFunc);
// You are advised to use async to throw a promise exception.
async function throwError() {
  throw new Error("uncaught error");
}

let promise1 = new Promise<void>(() => {}).then(() => {
  throwError();
});
```

## errorManager.on('unhandledRejection')<sup>12+</sup>

on(type: 'unhandledRejection', observer: UnhandledRejectionObserver): void

Registers an observer for the promise rejection. After the registration, a rejected promise that is not captured in the current thread of the application can be captured.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name                  | Type                                                         | Mandatory| Description                                      |
|-----------------------|-------------------------------------------------------------| -------- |------------------------------------------|
| type                  | string                                                      | Yes| Event type. It is fixed at **'unhandledRejection'**, indicating an observer for the promise rejection.|
| observer              | [UnhandledRejectionObserver](#unhandledrejectionobserver12) | Yes| Observer to register.                         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16200001 | The caller has been released. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    console.info("promise1 is rejected");
  }
  console.info("reason.name: ", reason.name);
  console.info("reason.message: ", reason.message);
  if (reason.stack) {
    console.info("reason.stack: ", reason.stack);
  }
};

errorManager.on("unhandledRejection", observer);

let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error("uncaught error");
});
```
## errorManager.on('freeze')<sup>18+</sup>

on(type: 'freeze', observer: FreezeObserver): void

Registers an observer for the main thread freeze event of the application. If the observer is registered multiple times, only the last one takes effect.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

> **NOTE**
>
> If the callback function runs for more than 1 second, the [AppRecovery](./js-apis-app-ability-appRecovery.md) feature may not work. The execution duration can be calculated by parsing the time difference between **begin** and **Freeze callback execution completed** in HiLogs. If the execution duration exceeds 1 second, you can optimize the callback logic by using methods such as asynchronous processing, reducing operations that block other tasks, and optimizing the data structures to reduce the execution duration.
> 

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'freeze'**, indicating an observer for the freeze event of the main thread.|
| observer | [FreezeObserver](#freezeobserver18) | Yes| Observer to register.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.   |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';

function freezeCallback() {
    console.info("freezecallback");
}
errorManager.on("freeze", freezeCallback);
```

## errorManager.off('loopObserver')<sup>12+</sup>

off(type: 'loopObserver', observer?: LoopObserver): void

Unregisters an observer for the message processing duration of the main thread.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'loopObserver'**, indicating an observer for the message processing duration of the main thread.|
| observer | [LoopObserver](js-apis-inner-application-loopObserver.md) | No| Observer to unregister.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';

errorManager.off("loopObserver");
```

## errorManager.off('globalUnhandledRejectionDetected')<sup>18+</sup>

off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void

Unregisters a rejected promise observer. After the deregistration, promise exceptions in the process cannot be listened for.

If the observer passed in is not in the observer queue registered via the **on** API, error code 16300004 is thrown. Therefore, you are advised to handle this using **try-catch** logic.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name                  | Type                             | Mandatory| Description                                          |
|-----------------------|---------------------------------|----|----------------------------------------------|
| type                  | string                          | Yes | Event type. It is fixed at **'globalUnhandledRejectionDetected'**, indicating an observer for the promise rejection.|
| observer              | [GlobalObserver](#globalobserver18) | No | Observer registered by the **on** API. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16200001 | The caller has been released. |
| 16300004 | The observer does not exist. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';

function promiseFunc(observer: errorManager.GlobalError) {
  console.info("result name :" + observer.name);
  console.info("result message :" + observer.message);
  console.info("result stack :" + observer.stack);
  console.info("result instanceName :" + observer.instanceName);
  console.info("result instanceType :" + observer.instanceType);
}

errorManager.on("globalUnhandledRejectionDetected", promiseFunc);

async function throwError() {
  throw new Error("uncaught error");
}

let promise1 = new Promise<void>(() => {}).then(() => {
  throwError();
});

errorManager.off("globalUnhandledRejectionDetected", promiseFunc);
```

## errorManager.off('unhandledRejection')<sup>12+</sup>

off(type: 'unhandledRejection', observer?: UnhandledRejectionObserver): void

Unregisters an observer for the promise rejection.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name                  | Type                             | Mandatory| Description                                          |
|-----------------------|---------------------------------|----|----------------------------------------------|
| type                  | string                          | Yes | Event type. It is fixed at **'unhandledRejection'**, indicating an observer for the promise rejection.|
| observer              | [UnhandledRejectionObserver](#unhandledrejectionobserver12) | No | Observer to unregister. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered.                       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |
| 16200001 | The caller has been released. |
| 16300004 | The observer does not exist. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    console.info("promise1 is rejected");
  }
  console.info("reason.name: ", reason.name);
  console.info("reason.message: ", reason.message);
  if (reason.stack) {
    console.info("reason.stack: ", reason.stack);
  }
};

errorManager.on("unhandledRejection", observer);

let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error("uncaught error")
})

errorManager.off("unhandledRejection");
```
Or:
```ts
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    console.info("promise1 is rejected");
  }
  console.info("reason.name: ", reason.name);
  console.info("reason.message: ", reason.message);
  if (reason.stack) {
    console.info("reason.stack: ", reason.stack);
  }
};

errorManager.on("unhandledRejection", observer);

let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error("uncaught error")
})

errorManager.off("unhandledRejection", observer);
```

## errorManager.off('freeze')<sup>18+</sup>

off(type: 'freeze', observer?: FreezeObserver): void

Unregisters an observer for the main thread freeze event of the application.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

If the observer passed in does not match the observer registered via the **on** API, error code 16300004 is thrown. Therefore, you are advised to handle this using **try-catch** logic.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'freeze'**, indicating an observer for the freeze event of the main thread.|
| observer | [FreezeObserver](#freezeobserver18) | No| Observer to unregister. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.|
| 16300004 | The observer does not exist. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';

function freezeCallback() {
    console.info("freezecallback");
}
errorManager.on("freeze", freezeCallback);
errorManager.off("freeze", freezeCallback);
```

## errorManager.setDefaultErrorHandler<sup>21+</sup>

setDefaultErrorHandler(defaultHandler?: ErrorHandler): ErrorHandler

Returns the previously registered handler when a JavaScript crash exception occurs. It can only be used in the main thread.

If an invalid parameter is passed or the API is called from a child thread, an error code is thrown and **undefined** is returned. You are advised to handle it with try-catch logic.

If the API parameter is empty, subsequently registered handlers are not able to establish a connection with previously registered handlers, thereby breaking the chain call mechanism.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
 
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| defaultHandler | [ErrorHandler](#errorhandler21) | No| Newly registered error handler. The default value is empty.|

**Return value**

| Type| Description|
| -------- | -------- |
| [ErrorHandler](#errorhandler21) | Previously registered error handler.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000205      | The API is not called in the main thread. |

**Example**
    
```ts
import { errorManager } from '@kit.AbilityKit';
import { process } from '@kit.ArkTS';

let oldHandler: errorManager.ErrorHandler;
const errorHandler: errorManager.ErrorHandler = (reason: Error) => {
    // Customize the errorHandler logic.
    console.info('[Handler]  Uncaught exception handler invoked.');
    if (oldHandler) {
        oldHandler(reason);
    } else {
        // You are advised to add a null check. If the value is null, use a synchronous exit approach.
        const processManager = new process.ProcessManager();
        processManager.exit(0);
    }
};
oldHandler = errorManager.setDefaultErrorHandler(errorHandler);
```

## ErrorObserver

type ErrorObserver = _ErrorObserver.default

Defines the ErrorObserver module.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_ErrorObserver.default](js-apis-inner-application-errorObserver.md) | ErrorObserver module.|

## LoopObserver<sup>12+</sup>

type LoopObserver = _LoopObserver

Defines the LoopObserver module. It can be used as a parameter of **errormanager.on** to listen for and handle main thread timeout events in the current application.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_LoopObserver](js-apis-inner-application-loopObserver.md) | LoopObserver module.|

## UnhandledRejectionObserver<sup>12+</sup>

type UnhandledRejectionObserver = (reason: Error | any, promise: Promise\<any>) => void

Defines an observer to capture the cause of a rejected promise.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name   | Type           | Mandatory| Description|
|--------|---------------|---| -------- |
| reason | Error \| any  | Yes| Generally, the value is of the **Error** type, indicating the reason for rejection.|
| promise | Promise\<any> | Yes| Rejected promise.|

## FreezeObserver<sup>18+</sup>

type FreezeObserver = () => void

Defines an observer for the main thread freeze event of the application. It is used by the application to customize freeze information.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

## GlobalObserver<sup>18+</sup>

type GlobalObserver = (reason: GlobalError) => void

Defines an exception observer, which can be used as the input parameter of [errorManager.on('globalErrorOccurred')](#errormanageronglobalerroroccurred18) and [errorManager.on('globalUnhandledRejectionDetected')](#errormanageronglobalunhandledrejectiondetected18) to listen for event processing events of the main thread of the current application.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type         | Mandatory| Description|
|--------| ------------- | ---- | --- |
| reason | [GlobalError](#globalerror18)   | Yes  | Object related to the exception event name, message, error stack information, exception thread name, and exception thread type.|


## GlobalError<sup>18+</sup>

Describes the object related to the exception event name, message, error stack information, exception thread name, and exception thread type.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read Only | Optional | Description |
| ---- | ----- | ---- | ----- | ------ |
| instanceName | string | No| No| Name of a VM instance.|
| instanceType | [InstanceType](#instancetype18) | No| No| Type of the VM instance.|

## InstanceType<sup>18+</sup>

Enumerates the VM instance types.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

| Name | Value | Description  |
| ---- | --- | ------ |
| MAIN     | 0   | Main VM instance.|
| WORKER   | 1   | Worker VM instance.|
| TASKPOOL | 2   | TaskPool VM instance.|
| CUSTOM   | 3   | VM instance created from the local code using [napi_create_ark_runtime](../native-lib/napi.md#napi_create_ark_runtime).|


## ErrorHandler<sup>21+</sup>

type ErrorHandler = (errObject: Error) => void

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type         | Mandatory| Description|
|--------| ------------- | ---- | --- |
| errObject | Error   | Yes  | Event name, message, and error stack of the exception.|
