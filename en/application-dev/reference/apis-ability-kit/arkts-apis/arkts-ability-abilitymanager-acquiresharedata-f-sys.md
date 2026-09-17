# acquireShareData (System API)

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## acquireShareData

```TypeScript
function acquireShareData(missionId: number, callback: AsyncCallback<Record<string, Object>>): void
```

Called by a system dialog box to obtain shared data, which is set by the target UIAbility through [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare). This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID on the target application. The maximum value is 2&lt;sup&gt;31&lt;/sup&gt;-1. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Record&lt;string, Object&gt;&gt; | Yes | Callback used to return the result. If the API call is successful, **err** is **undefined** and **data** is the shared data obtained. Otherwise, **err** is an error object. You can perform error handling or other custom processing.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |


## acquireShareData

```TypeScript
function acquireShareData(missionId: number): Promise<Record<string, Object>>
```

Called by a system dialog box to obtain shared data, which is set by the target UIAbility through [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare). This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| missionId | number | Yes | Mission ID on the target application. The maximum value is 2&lt;sup&gt;31&lt;/sup&gt;-1. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{ [key: string]: Object }&gt; | The promise returned by the function.<br>**Since:** 10 |
| Promise&lt;Record&lt;string, Object&gt;&gt; | Promise used to return the API call result and the shared data. You can perform error handling or other custom processing.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
