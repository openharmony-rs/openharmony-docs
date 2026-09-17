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
