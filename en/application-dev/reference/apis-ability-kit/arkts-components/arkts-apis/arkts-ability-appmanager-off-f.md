# off

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## off('applicationState')

```TypeScript
function off(type: 'applicationState', observerId: number, callback: AsyncCallback<void>): void
```

Unregisters the observer used to listen for application state changes. This API uses an asynchronous callback to return the result.

**Since:** 15

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'applicationState' | Yes | Type of the API to call. It is fixed at **'applicationState'**. |
| observerId | number | Yes | ID of the observer registered, which is the listener ID returned by [on('applicationState')](arkts-ability-appmanager-on-f.md#onapplicationstate). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the application state observer is deregistered, **err** is undefined; otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |


## off('applicationState')

```TypeScript
function off(type: 'applicationState', observerId: number): Promise<void>
```

Unregisters the observer used to listen for application state changes. This API uses a promise to return the result.

**Since:** 14

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'applicationState' | Yes | Type of the API to call. It is fixed at **'applicationState'**. |
| observerId | number | Yes | ID of the observer registered, which is the listener ID returned by [on('applicationState')](arkts-ability-appmanager-on-f.md#onapplicationstate). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
