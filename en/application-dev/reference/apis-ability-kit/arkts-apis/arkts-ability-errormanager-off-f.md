# off

## Modules to Import

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## off('error')

```TypeScript
function off(type: 'error', observerId: number, callback: AsyncCallback<void>): void
```

Unregisters an error observer. This API uses an asynchronous callback to return the result.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. It is fixed at **'error'**. |
| observerId | number | Yes | Index of the observer returned by **on()**. There is no specific unit. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The specified ID does not exist. |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 100;

const unregisterErrorObserverCallback = (err: BusinessError) => {
  if (err) {
    console.error('------------ unregisterErrorObserverCallback ------------', err);
  }
};

try {
  errorManager.off('error', observerId, unregisterErrorObserverCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```


## off('error')

```TypeScript
function off(type: 'error', observerId: number): Promise<void>
```

Unregisters an error observer. This API uses a promise to return the result.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. It is fixed at **'error'**. |
| observerId | number | Yes | Index of the observer returned by **on()**. There is no specific unit. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The specified ID does not exist. |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 100;

try {
  errorManager.off('error', observerId)
    .then((data) => {
      console.info('----------- unregisterErrorObserver success ----------', data);
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to unregister error observer. Code: ${err.code}, message: ${err.message}`);
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```


## off('loopObserver')

```TypeScript
function off(type: 'loopObserver', observer?: LoopObserver): void
```

Unregisters an observer for the message processing duration of the main thread.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'loopObserver' | Yes | Event type. It is fixed at **'loopObserver'**, indicating an observer for the message processing duration of the main thread. |
| observer | [LoopObserver](arkts-ability-errormanager-loopobserver-t.md) | No | Observer to unregister. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) |  |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  errorManager.off('loopObserver');
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```


## off('unhandledRejection')

```TypeScript
function off(type: 'unhandledRejection', observer?: UnhandledRejectionObserver): void
```

Unregisters an observer for the promise rejection.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'unhandledRejection' | Yes | Event type. It is fixed at **'unhandledRejection'**, indicating an observer for the promise rejection. |
| observer | [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | No | Observer to unregister. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | If the caller is invalid. |
| [16300004](../errorcode-ability.md#16300004-observer-does-not-exist) | If the observer does not exist |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    console.info('promise1 is rejected');
  }
  console.info('reason.name: ', reason.name);
  console.info('reason.message: ', reason.message);
  if (reason.stack) {
    console.info('reason.stack: ', reason.stack);
  }
};

errorManager.on('unhandledRejection', observer);

let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error('uncaught error')
})

errorManager.off('unhandledRejection');
```

Or:

```TypeScript
import { errorManager } from '@kit.AbilityKit';

let observer: errorManager.UnhandledRejectionObserver = (reason: Error, promise: Promise<void>) => {
  if (promise === promise1) {
    console.info('promise1 is rejected');
  }
  console.info('reason.name: ', reason.name);
  console.info('reason.message: ', reason.message);
  if (reason.stack) {
    console.info('reason.stack: ', reason.stack);
  }
};

errorManager.on('unhandledRejection', observer);

let promise1 = new Promise<void>(() => {}).then(() => {
  throw new Error('uncaught error')
})

errorManager.off('unhandledRejection', observer);
```


## off('globalUnhandledRejectionDetected')

```TypeScript
function off(type: 'globalUnhandledRejectionDetected', observer?: GlobalObserver): void
```

Unregisters a rejected promise observer. After the deregistration, promise exceptions in the process cannot be listened for.

If the observer passed in is not in the observer queue registered via the **on** API, error code 16300004 is thrown. Therefore, you are advised to handle this using **try-catch** logic.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'globalUnhandledRejectionDetected' | Yes | Event type. It is fixed at **'globalUnhandledRejectionDetected'**, indicating an observer for the promise rejection. |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | No | Observer registered by the **on** API. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | If the caller is invalid. |
| [16300004](../errorcode-ability.md#16300004-observer-does-not-exist) | If the observer does not exist |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';

const promiseFunc = (observer: errorManager.GlobalError) => {
  console.info('result name :' + observer.name);
  console.info('result message :' + observer.message);
  console.info('result stack :' + observer.stack);
  console.info('result instanceName :' + observer.instanceName);
  console.info('result instanceType :' + observer.instanceType);
};

errorManager.on('globalUnhandledRejectionDetected', promiseFunc);

const throwError = async () => {
  throw new Error('uncaught error');
};

let promise1 = new Promise<void>(() => {}).then(() => {
  throwError();
});

errorManager.off('globalUnhandledRejectionDetected', promiseFunc);
```


## off('freeze')

```TypeScript
function off(type: 'freeze', observer?: FreezeObserver): void
```

Unregisters an observer for the main thread freeze event of the application.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

If the observer passed in does not match the observer registered via the **on** API, error code 16300004 is thrown. Therefore, you are advised to handle this using **try-catch** logic.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'freeze' | Yes | Event type. It is fixed at **'freeze'**, indicating an observer for the freeze event of the main thread. |
| observer | [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | No | Observer to unregister. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300004](../errorcode-ability.md#16300004-observer-does-not-exist) | If the observer does not exist |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const freezeCallback = () => {
  console.info('freezecallback');
};
try {
  errorManager.on('freeze', freezeCallback);
  errorManager.off('freeze', freezeCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```


## off('globalErrorOccurred')

```TypeScript
function off(type: 'globalErrorOccurred', observer?: GlobalObserver): void
```

Unregisters a global error observer. Once unregistered, global listening cannot be implemented.

If the observer passed in is not in the observer queue registered via the **on** API, error code 16300004 is thrown. Therefore, you are advised to handle this using **try-catch** logic.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'globalErrorOccurred' | Yes | Event type. It is fixed at **'globalErrorOccurred'**. |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | No | Observer registered by the **on** API. You are advised to use this parameter. If omitted, all observers registered with the same environment through **on** are unregistered by default. Otherwise, the specified observer is unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | If the caller is invalid. |
| [16300004](../errorcode-ability.md#16300004-observer-does-not-exist) | If the observer does not exist |

**Examples**

```TypeScript
import { errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const errorFunc = (observer: errorManager.GlobalError) => {
  console.info('result name :' + observer.name);
  console.info('result message :' + observer.message);
  console.info('result stack :' + observer.stack);
  console.info('result instanceName :' + observer.instanceName);
  console.info('result instanceType :' + observer.instanceType);
}

try {
  errorManager.off('globalErrorOccurred', errorFunc)
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message}`);
}
```
