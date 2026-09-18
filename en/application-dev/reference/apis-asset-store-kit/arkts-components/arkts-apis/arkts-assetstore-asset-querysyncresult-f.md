# querySyncResult

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## querySyncResult

```TypeScript
function querySyncResult(query: AssetMap): Promise<SyncResult>
```

Queries the result of the sync operation. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | Yes | Attributes of the sync result to query, such as the group to which the asset belongs and whether the custom attribute information is encrypted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SyncResult](arkts-assetstore-asset-syncresult-i.md)&gt; | Promise used to return the result obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [24000001](../errorcode-asset.md#24000001-asset-store-service-unavailable) | The ASSET service is unavailable. |
| [24000006](../errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000010](../errorcode-asset.md#24000010-ipc-failed) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-bundle-manager-service-abnormal) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-account-system-service-abnormal) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-access-token-service-abnormal) | Calling the Access Token service failed. |
| [24000014](../errorcode-asset.md#24000014-file-operation-failed) | The file operation failed. |
| [24000018](../errorcode-asset.md#24000018-parameter-check-failed) | Parameter verification failed. |

**Examples**

```TypeScript
import { asset } from '@kit.AssetStoreKit';

let query: asset.AssetMap = new Map();
asset.querySyncResult(query).then((res: asset.SyncResult) => {
  console.info(`Succeeded in querying sync result: ${JSON.stringify(res)}`);
});
```
