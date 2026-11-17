# setLaunchServicesEnabled (System API)

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## setLaunchServicesEnabled

```TypeScript
function setLaunchServicesEnabled(bundleName: string, userId: number, appIndex: number,
    enabled: boolean, token?: Uint8Array): Promise<void>
```

This method is used to set the enabling status of the LaunchService application.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function setLaunchServicesEnabled(bundleName: string, userId: int, appIndex: int,    enabled: boolean, token?: Uint8Array): Promise<void>--><!--Device-launchServiceManager-function setLaunchServicesEnabled(bundleName: string, userId: int, appIndex: int,    enabled: boolean, token?: Uint8Array): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Name of the target application package. |
| userId | number | Yes | ID of the target application user. <br>The value must be an integer. |
| appIndex | number | Yes | Indicates the twin index of the target application. <br>The value must be an integer. |
| enabled | boolean | Yes | Indicates the enabling status of the. The value true indicates that the function is enabled, and the value false indicates that the function is disabled. |
| token | Uint8Array | No | The authentication token used to approve the operation. If the token is transferred, the token is directly used for authentication. If this parameter is not transferred, the user authorization page is displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object. No result is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | System service connection failed. |
| 16000215 | The approval request was rejected. |
| [16300005](../errorcode-ability.md#16300005-bundle-information-does-not-exist) | The target bundle does not exist. |
