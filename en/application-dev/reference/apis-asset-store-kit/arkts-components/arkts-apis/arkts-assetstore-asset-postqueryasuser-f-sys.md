# postQueryAsUser (System API)

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## postQueryAsUser

```TypeScript
function postQueryAsUser(userId:number, handle: AssetMap): Promise<void>
```

Performs postprocessing for the asset query in the specified user space. This API is used when user authentication is required for the access to an asset. This API must be used with [asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md) together. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | the user identifier to post-query one or more assets. The value must be greater than or equal to 100. |
| handle | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | Yes | Handle of the query operation, including the challenge value returned by [asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
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

let userId: number = 100;
let handle: asset.AssetMap = new Map();
// The new Uint8Array(32) is only an example. Pass in the challenge value returned by asset.preQueryAsUser.
handle.set(asset.Tag.AUTH_CHALLENGE, new Uint8Array(32));
asset.postQueryAsUser(userId, handle).then(() => {
  console.info(`Succeeded in post-querying Asset from user space.`);
});
```
