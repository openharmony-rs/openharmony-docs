# preQueryAsUser (System API)

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## preQueryAsUser

```TypeScript
function preQueryAsUser(userId: number, query: AssetMap): Promise<Uint8Array>
```

Performs preprocessing for the asset query in the specified user space. This API is used when user authentication is required for the access to an asset. After the user authentication is successful, call [asset.queryAsUser](arkts-assetstore-asset-queryasuser-f-sys.md) and [asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md). This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | the user identifier to pre-query one or more Assets. The value must be greater than or equal to 100. |
| query | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | Yes | Conditions for querying the asset, such as the asset aliases, access control attributes, and custom data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return a challenge value.<br>**NOTE:**  The challenge value is used for subsequent user authentication. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [24000001](../errorcode-asset.md#24000001-asset-store-service-unavailable) | The ASSET service is unavailable. |
| [24000002](../errorcode-asset.md#24000002-asset-not-found) | The asset is not found. |
| [24000005](../errorcode-asset.md#24000005-incorrect-screen-lock-status) | The screen lock status does not match. |
| [24000006](../errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000007](../errorcode-asset.md#24000007-asset-corrupted) | The asset is corrupted. |
| [24000008](../errorcode-asset.md#24000008-database-operation-failed) | The database operation failed. |
| [24000009](../errorcode-asset.md#24000009-cryptographic-operation-failed) | The cryptography operation failed. |
| [24000010](../errorcode-asset.md#24000010-ipc-failed) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-bundle-manager-service-abnormal) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-account-system-service-abnormal) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-access-token-service-abnormal) | Calling the Access Token service failed. |
| [24000016](../errorcode-asset.md#24000016-cached-assets-reaches-the-limit) | The cache exceeds the limit. |
| [24000017](../errorcode-asset.md#24000017-function-not-supported) | The capability is not supported. |

**Examples**

```TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

let userId: number = 100;
let query: asset.AssetMap = new Map();
query.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
asset.preQueryAsUser(userId, query).then((challenge: Uint8Array) => {
  console.info(`Succeeded in pre-querying Asset from user space.`);
});
```
