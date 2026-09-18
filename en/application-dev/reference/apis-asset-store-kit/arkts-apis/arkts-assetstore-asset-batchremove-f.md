# batchRemove

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## batchRemove

```TypeScript
function batchRemove(assetsToBeRemoved: Array<AssetMap>): Promise<void>
```

Removes assets in batches based on an alias list.

Only assets with the same [GROUP_ID](arkts-assetstore-asset-tag-e.md#group_id) and [REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tag-e.md#require_attr_encrypted) can be removed in batches.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetsToBeRemoved | Array&lt;[AssetMap](arkts-assetstore-asset-assetmap-t.md)&gt; | Yes | an array of attributes of the asset to remove, such as the asset alias, access control attributes, and custom data. <br>The [GROUP_ID](arkts-assetstore-asset-tag-e.md#group_id) and [REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tag-e.md#require_attr_encrypted) attributes of all data must be the same. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise object returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24000001](../errorcode-asset.md#24000001-asset-store-service-unavailable) | The ASSET service is unavailable. |
| [24000006](../errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000007](../errorcode-asset.md#24000007-asset-corrupted) | The asset is corrupted. |
| [24000008](../errorcode-asset.md#24000008-database-operation-failed) | The database operation failed. |
| [24000010](../errorcode-asset.md#24000010-ipc-failed) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-bundle-manager-service-abnormal) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-account-system-service-abnormal) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-access-token-service-abnormal) | Calling the Access Token service failed. |
| [24000015](../errorcode-asset.md#24000015-failed-to-obtain-the-system-time) | Getting the system time failed. |
| [24000019](../errorcode-asset.md#24000019-inconsistent-attribute-values) | Each value of [GROUP_ID](arkts-assetstore-asset-tag-e.md#group_id) and [REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tag-e.md#require_attr_encrypted) in the array is not consistent. |
