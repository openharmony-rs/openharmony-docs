# on

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## on('applicationState')

```TypeScript
function on(type: 'applicationState', observer: ApplicationStateObserver): number
```

Registers an observer to listen for lifecycle changes of all applications.

**Since:** 14

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'applicationState' | Yes | Type of the API to call. It is fixed at **'applicationState'**. |
| observer | [ApplicationStateObserver](arkts-ability-appmanager-applicationstateobserver-t.md) | Yes | Application state observer, which is used to listen for applications lifecycle changes. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the observer registered. You can pass this ID to off('applicationState') to unregister the observer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |


## on('applicationState')

```TypeScript
function on(type: 'applicationState', observer: ApplicationStateObserver, bundleNameList: Array<string>): number
```

Registers an observer to listen for lifecycle changes of the specified application.

**Since:** 14

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'applicationState' | Yes | Type of the API to call. It is fixed at **'applicationState'**. |
| observer | [ApplicationStateObserver](arkts-ability-appmanager-applicationstateobserver-t.md) | Yes | Application state observer, which is used to listen for application lifecycle changes. |
| bundleNameList | Array&lt;string&gt; | Yes | **bundleName** array of the application. A maximum of 128 bundle names can be passed. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the observer registered. You can pass this ID to off('applicationState') to unregister the observer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
