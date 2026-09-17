# setAdditionalInfoByIndex (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setAdditionalInfoByIndex

```TypeScript
function setAdditionalInfoByIndex(bundleName: string, additionalInfo: string, appIndex: number): void
```

Sets additional information for a specified application instance. This API can be called only by AppGallery.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| additionalInfo | string | Yes | Additional information to set. |
| appIndex | number | Yes | Index of the application mode.The value must be equal to 0 or 10000.<br>The value should be an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700053](../errorcode-bundle.md#17700053-not-invoked-by-appgallery) | The caller is not AppGallery. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range. |
