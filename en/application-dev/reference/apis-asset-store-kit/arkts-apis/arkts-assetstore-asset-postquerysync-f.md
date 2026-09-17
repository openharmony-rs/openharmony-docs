# postQuerySync

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## postQuerySync

```TypeScript
function postQuerySync(handle: AssetMap): void
```

Performs postprocessing for the asset query. This API is used when user authentication is required for the access to the asset. This API must be used with [asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md) together. This API returns the result synchronously.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | Yes | Handle of the query operation, including the challenge value returned by [asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [24000001](../errorcode-asset.md#24000001-asset-store-service-unavailable) | The ASSET service is unavailable. |
| [24000006](../errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000010](../errorcode-asset.md#24000010-ipc-failed) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-bundle-manager-service-abnormal) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-account-system-service-abnormal) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-access-token-service-abnormal) | Calling the Access Token service failed. |

**Examples**

```TypeScript
import { asset } from '@kit.AssetStoreKit';

let handle: asset.AssetMap = new Map();
// The new Uint8Array(32) is only an example. Pass in the challenge value returned by asset.preQuerySync.
handle.set(asset.Tag.AUTH_CHALLENGE, new Uint8Array(32));
asset.postQuerySync(handle)
```
