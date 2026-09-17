# Task

Implements an upload or download task. Before using this API, you must obtain a **Task** object, from a promise through [request.agent.create](arkts-basicservices-agent-create-f.md) or from a callback through [request.agent.create](arkts-basicservices-agent-create-f.md).

> **NOTE:** 
> 
> The **Task** object and its mounting callback function are released and automatically reclaimed by the system
> after the **remove** method is called.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## off

```TypeScript
off(event: 'progress', callback?: (progress: Progress) => void): void
```

Unsubscribes from task progress events.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'progress' | Yes | Event type.<br>- **'progress'**: task progress. |
| callback | (progress: Progress) =&gt; void | No | Callback to be invoked when the specified event occurs. If this parameter is not specified, all callbacks of the task progress events are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | task mode error.<br>**Applicable version:** 10 |

## off

```TypeScript
off(event: 'completed', callback?: (progress: Progress) => void): void
```

Unsubscribes from task completion events.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'completed' | Yes | Event type.<br>- **'completed'**: task completion. |
| callback | (progress: Progress) =&gt; void | No | Callback to be invoked when the specified event occurs. If this parameter is not specified, all callbacks of the task completion events are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode.<br>**Applicable version:** 10 |

## off

```TypeScript
off(event: 'failed', callback?: (progress: Progress) => void): void
```

Unsubscribes from task failure events.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'failed' | Yes | Event type.<br>- **'failed'**: task failure. |
| callback | (progress: Progress) =&gt; void | No | Callback to be invoked when the specified event occurs. If this parameter is not specified, all callbacks of the task failure events are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode.<br>**Applicable version:** 10 |

## off

```TypeScript
off(event: 'pause', callback?: (progress: Progress) => void): void
```

Unsubscribes from the foreground task pause event.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'pause' | Yes | Event type.<br>- **'pause'**: task pause. |
| callback | (progress: Progress) =&gt; void | No | Callback to be invoked when the specified event occurs. If this parameter is not specified, all callbacks of the task pause events are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## off

```TypeScript
off(event: 'resume', callback?: (progress: Progress) => void): void
```

Unsubscribes from foreground task resume events.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'resume' | Yes | Event type.<br>- **'resume'**: task resume. |
| callback | (progress: Progress) =&gt; void | No | Callback to be invoked when the specified event occurs. If this parameter is not specified, all callbacks of the task resume events are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## off

```TypeScript
off(event: 'remove', callback?: (progress: Progress) => void): void
```

Unsubscribes from the task removal event.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'remove' | Yes | Event type.<br>- **'remove'**: task removal. |
| callback | (progress: Progress) =&gt; void | No | Callback to be invoked when the specified event occurs. If this parameter is not specified, all callbacks of the task removal events are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameter types. <br> 3. Parameter verification failed. |

## off

```TypeScript
off(event: 'response', callback?: Callback<HttpResponse>): void
```

Unsubscribes from task response headers.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'response' | Yes | Event type.<br>- **response**: task response. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[HttpResponse](arkts-basicservices-agent-httpresponse-i.md)&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## off

```TypeScript
off(event: 'faultOccur', callback?: Callback<Faults>): void
```

Unsubscribes from task failure events.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'faultOccur' | Yes | Event type.<br>- **'faultOccur'**: task failure. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[Faults](arkts-basicservices-agent-faults-e.md)&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## off

```TypeScript
off(event: 'wait', callback?: Callback<WaitingReason>): void
```

Unsubscribes from task waiting events.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'wait' | Yes | Event type.<br>- 'wait': The task is waiting. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[WaitingReason](arkts-basicservices-agent-waitingreason-e.md)&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks of the current type will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## on

```TypeScript
on(event: 'progress', callback: (progress: Progress) => void): void
```

Subscribes to task progress changes. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'progress' | Yes | Event type.<br>- **'progress'**: task progress. |
| callback | (progress: Progress) =&gt; void | Yes | Callback to be invoked when the specified event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | task mode error.<br>**Applicable version:** 10 |

## on

```TypeScript
on(event: 'completed', callback: (progress: Progress) => void): void
```

Subscribes to task completion events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'completed' | Yes | Event type.<br>- **'completed'**: task completion. |
| callback | (progress: Progress) =&gt; void | Yes | Callback to be invoked when the specified event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | task mode error.<br>**Applicable version:** 10 |

## on

```TypeScript
on(event: 'failed', callback: (progress: Progress) => void): void
```

Subscribes to task failure events. This API uses an asynchronous callback to return the result. You can call [request.agent.show](arkts-basicservices-agent-show-f.md) to view the error cause.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'failed' | Yes | Event type.<br>- **'failed'**: task failure. |
| callback | (progress: Progress) =&gt; void | Yes | Callback to be invoked when the specified event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode.<br>**Applicable version:** 10 |

## on

```TypeScript
on(event: 'pause', callback: (progress: Progress) => void): void
```

Subscribes to task pause events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'pause' | Yes | Event type.<br>- **'pause'**: task pause. |
| callback | (progress: Progress) =&gt; void | Yes | Callback to be invoked when the specified event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## on

```TypeScript
on(event: 'resume', callback: (progress: Progress) => void): void
```

Subscribes to task resume events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'resume' | Yes | Event type.<br>- **'resume'**: task resume. |
| callback | (progress: Progress) =&gt; void | Yes | Callback to be invoked when the specified event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## on

```TypeScript
on(event: 'remove', callback: (progress: Progress) => void): void
```

Subscribes to task removal events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'remove' | Yes | Event type.<br>- **'remove'**: task removal. |
| callback | (progress: Progress) =&gt; void | Yes | Callback to be invoked when the specified event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## on

```TypeScript
on(event: 'response', callback: Callback<HttpResponse>): void
```

Subscribes to task response headers. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'response' | Yes | Event type.<br>- **'response'**: task response. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[HttpResponse](arkts-basicservices-agent-httpresponse-i.md)&gt; | Yes | Callback used to return the data structure of the task response header. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## on

```TypeScript
on(event: 'faultOccur', callback: Callback<Faults>): void
```

Subscribes to task failure events. This API uses a callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'faultOccur' | Yes | Event type.<br>- **'faultOccur'**: task failure. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[Faults](arkts-basicservices-agent-faults-e.md)&gt; | Yes | Callback used to return the failure cause of the task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## on

```TypeScript
on(event: 'wait', callback: Callback<WaitingReason>): void
```

Subscribes to task wait events. This API uses a callback to return the result.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'wait' | Yes | Event type.<br>- 'wait': The task is waiting. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[WaitingReason](arkts-basicservices-agent-waitingreason-e.md)&gt; | Yes | Callback used to return the waiting reason of the task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

Pauses a task that is waiting, running, or retrying. A paused task can be resumed by [resume](#resume). This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode.<br>**Applicable version:** 10 |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## pause

```TypeScript
pause(): Promise<void>
```

Pauses a task that is waiting, running, or retrying. A paused task can be resumed by [resume](#resume). This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode.<br>**Applicable version:** 10 |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

Resumes a paused task. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode.<br>**Applicable version:** 10 |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## resume

```TypeScript
resume(): Promise<void>
```

Resumes a paused task. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Request.FileTransferAgent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900005](../errorcode-request.md#21900005-task-mode-error) | Operation with wrong task mode.<br>**Applicable version:** 10 |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## setMaxSpeed

```TypeScript
setMaxSpeed(speed: number): Promise<void>
```

Sets the maximum number of bytes that can be transmitted by a task per second. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | number | Yes | Maximum number of bytes that can be transmitted by a task per second, with a minimum of 16384 bytes. The value cannot be less than the minimum speed value specified by [MinSpeed](arkts-basicservices-agent-minspeed-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts a task. This API uses an asynchronous callback to return the result.

Tasks in the following states can be started:

1. Task created by **request.agent.create**.
2. Download tasks that are created by **request.agent.create** but have failed or paused.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## start

```TypeScript
start(): Promise<void>
```

Starts a task. This API uses a promise to return the result.

Tasks in the following states can be started:

1. Task created by **request.agent.create**.
2. Download tasks that are created by **request.agent.create** but have failed or paused.

> **NOTE:** 
> 
> For details about how to obtain the context in the example, see
> [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability)
> .

**Since:** 10

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops a task that is running, waiting, or retrying. A paused task can be resumed by [start](#start). This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## stop

```TypeScript
stop(): Promise<void>
```

Stops a task that is running, waiting, or retrying. A paused task can be resumed by [start](#start). This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [13400003](../errorcode-request.md#13400003-service-error) | Task service ability error. |
| [21900007](../errorcode-request.md#21900007-operation-not-supported-by-the-task-state) | Operation with wrong task state. |

## config

```TypeScript
config: Config
```

Task configuration.

**Type:** [Config](arkts-basicservices-agent-config-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## tid

```TypeScript
readonly tid: string
```

Task ID, which is unique and automatically generated by the system.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent
