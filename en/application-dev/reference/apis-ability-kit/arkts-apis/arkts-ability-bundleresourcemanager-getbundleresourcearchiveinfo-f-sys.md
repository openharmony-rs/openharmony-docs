# getBundleResourceArchiveInfo (System API)

## Modules to Import

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getBundleResourceArchiveInfo

```TypeScript
function getBundleResourceArchiveInfo(filePath: string, resourceFlags?: number): Promise<BundleResourceInfo>
```

Obtains the resource information based on the given file path and resource flags. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_BUNDLE_RESOURCES

**Model restriction:** This API can be used only in the stage model.

<!--Device-bundleResourceManager-function getBundleResourceArchiveInfo(filePath: string, resourceFlags?: int): Promise<BundleResourceInfo>--><!--Device-bundleResourceManager-function getBundleResourceArchiveInfo(filePath: string, resourceFlags?: int): Promise<BundleResourceInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Path where the file is stored. The path must be the relative path of the current bundle's data directory. |
| resourceFlags | number | No | Type of the resource information to obtain. For details. see [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BundleResourceInfo](arkts-ability-bundleresourcemanager-bundleresourceinfo-t-sys.md)&gt; | Promise used to return the BundleResourceInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system api. |
| [17700022](../errorcode-bundle.md#17700022-invalid-source-file) | The filePath is invalid. |
| [17700101](../errorcode-bundle.md#17700101-bundle-manager-service-abnormal) | Bundle manager service is excepted. |
