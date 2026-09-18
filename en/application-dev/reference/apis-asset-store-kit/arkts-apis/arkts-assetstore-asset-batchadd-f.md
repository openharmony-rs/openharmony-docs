# batchAdd

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## batchAdd

```TypeScript
function batchAdd(attributesArray: Array<AssetMap>): Promise<BatchResult>
```

Adds assets in batches based on an attributes array. To set [IS_PERSISTENT](arkts-assetstore-asset-tag-e.md#is_persistent), the application must have the ohos.permission.STORE_PERSISTENT_DATA permission.

Only assets with the same [GROUP_ID](arkts-assetstore-asset-tag-e.md#group_id) and [REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tag-e.md#require_attr_encrypted) can be added in batches.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attributesArray | Array&lt;[AssetMap](arkts-assetstore-asset-assetmap-t.md)&gt; | Yes | an array of assets to be added. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[BatchResult](arkts-assetstore-asset-batchresult-i.md)&gt; | The result of the batch operation, including error information for adding failed assets, if there are any failures. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24000001](../errorcode-asset.md#24000001-asset-store-service-unavailable) | The ASSET service is unavailable. |
| [24000005](../errorcode-asset.md#24000005-incorrect-screen-lock-status) | The screen lock status does not match. |
| [24000006](../errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000007](../errorcode-asset.md#24000007-asset-corrupted) | The asset is corrupted. |
| [24000008](../errorcode-asset.md#24000008-database-operation-failed) | The database operation failed. |
| [24000009](../errorcode-asset.md#24000009-cryptographic-operation-failed) | The cryptography operation failed. |
| [24000010](../errorcode-asset.md#24000010-ipc-failed) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-bundle-manager-service-abnormal) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-account-system-service-abnormal) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-access-token-service-abnormal) | Calling the Access Token service failed. |
| [24000014](../errorcode-asset.md#24000014-file-operation-failed) | The file operation failed. |
| [24000015](../errorcode-asset.md#24000015-failed-to-obtain-the-system-time) | Getting the system time failed. |
| [24000019](../errorcode-asset.md#24000019-inconsistent-attribute-values) | Each value of [GROUP_ID](arkts-assetstore-asset-tag-e.md#group_id) and [REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tag-e.md#require_attr_encrypted) in the array is not consistent. |
