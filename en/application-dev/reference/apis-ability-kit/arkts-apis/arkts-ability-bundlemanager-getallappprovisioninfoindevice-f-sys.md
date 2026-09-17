# getAllAppProvisionInfoInDevice (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllAppProvisionInfoInDevice

```TypeScript
function getAllAppProvisionInfoInDevice(userId: number): Promise<Array<AppProvisionInfo>>
```

Obtains the provision configuration file information of all applications based in the device on the given user ID. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_INSTALLED_BUNDLE_LIST or (ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID on the device.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AppProvisionInfo](arkts-ability-bundlemanager-appprovisioninfo-t-sys.md)&gt;&gt; | Promise used to return the provision profile obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user id is not found. |
