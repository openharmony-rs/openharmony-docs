# on

## Modules to Import

```TypeScript
import { errorManager } from '@kit.AbilityKit';
```

## on('error')

```TypeScript
function on(type: 'error', observer: ErrorObserver): number
```

Registers an error observer. Once registered, it can capture JavaScript crashes occurring within the application, which are a type of application crash. When the observer captures such an exception, the application will not exit automatically. You are advised to add a synchronous exit operation after the callback function completes.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. It is fixed at **'error'**. |
| observer | [ErrorObserver](arkts-ability-errormanager-errorobserver-t.md) | Yes | Error observer instance. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Unique index of the observer, which corresponds one-to-one with the observer. This value can be used as the **observerId** parameter in the **errorManager.off** function. There is no specific unit. the returned result is observerId. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The specified ID does not exist. |


## on('loopObserver')

```TypeScript
function on(type: 'loopObserver', timeout: number, observer: LoopObserver): void
```

Registers an observer for the message processing duration of the main thread. After the registration, the execution time of a message processed by the main thread of the application can be captured.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'loopObserver' | Yes | Event type. It is fixed at **'loopObserver'**, indicating an observer for the message processing duration of the main thread. |
| timeout | number | Yes | Event execution threshold, in milliseconds. The value must be greater than **0**.The unit is milliseconds(ms). |
| observer | [LoopObserver](arkts-ability-errormanager-loopobserver-t.md) | Yes | Observer to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## on('unhandledRejection')

```TypeScript
function on(type: 'unhandledRejection', observer: UnhandledRejectionObserver): void
```

Registers an observer for the promise rejection. After the registration, a rejected promise that is not captured in the current thread of the application can be captured.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'unhandledRejection' | Yes | Event type. It is fixed at **'unhandledRejection'**, indicating an observer for the promise rejection. |
| observer | [UnhandledRejectionObserver](arkts-ability-errormanager-unhandledrejectionobserver-t.md) | Yes | Observer to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | If the caller is invalid. |


## on('globalUnhandledRejectionDetected')

```TypeScript
function on(type: 'globalUnhandledRejectionDetected', observer: GlobalObserver): void
```

Registers a rejected promise observer with any thread in the process. Once registered, it can capture a rejected promise that is not captured in the current thread of the application.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'globalUnhandledRejectionDetected' | Yes | Event type. It is fixed at **'globalUnhandledRejectionDetected'**, indicating an observer for the promise rejection. |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | Yes | Observer to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | If the caller is invalid. |


## on('freeze')

```TypeScript
function on(type: 'freeze', observer: FreezeObserver): void
```

Registers an observer for the main thread freeze event of the application. If the observer is registered multiple times, only the last one takes effect.

This API can only be used in the main thread. If a thread error occurs, an error code is thrown. You are advised to handle it with try-catch logic.

> **NOTE:** 
> 
> If the callback function runs for more than 1 second, the
> [AppRecovery](arkts-ability-app-ability-apprecovery.md) feature may not work. The execution duration can
> be calculated by parsing the time difference between **begin** and **Freeze callback execution completed** in
> HiLogs. If the execution duration exceeds 1 second, you can optimize the callback logic by using methods such as
> asynchronous processing, reducing operations that block other tasks, and optimizing the data structures to reduce
> the execution duration.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'freeze' | Yes | Event type. It is fixed at **'freeze'**, indicating an observer for the freeze event of the main thread. |
| observer | [FreezeObserver](arkts-ability-errormanager-freezeobserver-t.md) | Yes | Observer to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## on('globalErrorOccurred')

```TypeScript
function on(type: 'globalErrorOccurred', observer: GlobalObserver): void
```

Registers a global error observer via the **errorManager.on** API within any thread of a process. Once registered, it can capture exceptions occurring in any thread across the entire process. When the observer captures such an exception, the application will not exit automatically. You are advised to add a synchronous exit operation after the callback function completes.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'globalErrorOccurred' | Yes | Event type. It is fixed at **'globalErrorOccurred'**. |
| observer | [GlobalObserver](arkts-ability-errormanager-globalobserver-t.md) | Yes | Customized callback function for exception handling. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | If the caller is invalid. |
