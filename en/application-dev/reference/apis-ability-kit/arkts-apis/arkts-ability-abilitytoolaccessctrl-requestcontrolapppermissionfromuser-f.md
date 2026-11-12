# requestControlAppPermissionFromUser

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## requestControlAppPermissionFromUser

```TypeScript
export function requestControlAppPermissionFromUser(context: Context, appInfo: AppInfo[]):
    Promise<ControlAppStatusResult[]>
```

Request the control permission of a specified application from a user. This function pops up a user dialog box to obtain the control authorization decision for each application. The returned result reflects the user's decision to allow or deny each application.

**Since:** 26.1.0

**Required permissions:** ohos.permission.CONTROL_DEVICE

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-abilityToolAccessCtrl-export function requestControlAppPermissionFromUser(context: Context, appInfo: AppInfo[]):    Promise<ControlAppStatusResult[]>--><!--Device-abilityToolAccessCtrl-export function requestControlAppPermissionFromUser(context: Context, appInfo: AppInfo[]):    Promise<ControlAppStatusResult[]>-End-->

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Context object for displaying the user dialog. |
| appInfo | [AppInfo](arkts-ability-abilitytoolaccessctrl-appinfo-i.md)[] | Yes | Application information list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ControlAppStatusResult](arkts-ability-abilitytoolaccessctrl-controlappstatusresult-i.md)[]&gt; | Promise object that returns ${ControlAppStatusResult[]}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. context is invalid, appInfo is empty, bundleName is invalid, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. possible cause: dependent service unavailable, resource access failure, etc. |
