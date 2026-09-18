# getAllBundleInfoInstances (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllBundleInfoInstances

```TypeScript
function getAllBundleInfoInstances(bundleName: string, bundleFlags: number): Promise<Array<BundleInfo>>
```

Obtains all the bundle information in the system based on the given bundle name and bundle flags. This API uses a type of promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| bundleFlags | number | Yes | Type of the bundle information to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleInfo](arkts-ability-bundlemanager-bundleinfo-t.md)&gt;&gt; | Promise used to return an array of bundle information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
