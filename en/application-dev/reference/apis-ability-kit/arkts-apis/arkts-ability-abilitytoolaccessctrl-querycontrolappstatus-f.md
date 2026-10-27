# queryControlAppStatus

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## queryControlAppStatus

```TypeScript
export function queryControlAppStatus(appInfo: AppInfo[]): Promise<ControlAppStatusResult[]>
```

Queries the control permission status for the specified applications. This function checks whether each application in the input list is allowed or denied to be controlled by external tools. The result list corresponds to the input order.

**Since:** 26.1.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-abilityToolAccessCtrl-export function queryControlAppStatus(appInfo: AppInfo[]): Promise<ControlAppStatusResult[]>--><!--Device-abilityToolAccessCtrl-export function queryControlAppStatus(appInfo: AppInfo[]): Promise<ControlAppStatusResult[]>-End-->

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appInfo | [AppInfo](arkts-ability-abilitytoolaccessctrl-appinfo-i.md)[] | Yes | Application information list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ControlAppStatusResult](arkts-ability-abilitytoolaccessctrl-controlappstatusresult-i.md)[]&gt; | Promise used to return ${ControlAppStatusResult[]}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. appInfo is empty, bundleName is invalid, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. possible cause: dependent service unavailable, resource access failure, etc. |
