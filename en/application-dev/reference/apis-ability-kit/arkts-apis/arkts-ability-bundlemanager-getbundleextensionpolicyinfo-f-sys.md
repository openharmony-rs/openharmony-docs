# getBundleExtensionPolicyInfo (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getBundleExtensionPolicyInfo

```TypeScript
function getBundleExtensionPolicyInfo(bundleName: string, userId: number): BundleExtensionPolicyInfo
```

Obtains the bundle extension policy information of a specified application.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| userId | number | Yes | User ID, which can be obtained by calling getOsAccountLocalId. The value is greater than or equal to 0.<br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| [BundleExtensionPolicyInfo](arkts-ability-bundlemanager-bundleextensionpolicyinfo-t-sys.md) | The bundle extension policy information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Non-system APP calling system API. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
