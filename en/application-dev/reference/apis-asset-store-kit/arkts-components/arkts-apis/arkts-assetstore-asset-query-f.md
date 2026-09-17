# query

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## query

```TypeScript
function query(query: AssetMap): Promise<Array<AssetMap>>
```

Queries one or more assets. If user authentication is required for the access to the asset, call [asset.preQuery](arkts-assetstore-asset-prequery-f.md) before this API and call [asset.postQuery](arkts-assetstore-asset-postquery-f.md) after this API. For details about the development procedure, see [Development Guidance](../../../security/AssetStoreKit/asset-js-query-auth.md). This API uses a promise to return the result.

If no asset is found, an exception indicating that no asset is found is thrown instead of returning an empty query result list.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | Yes | Attributes of the asset to query, such as the asset alias, access control attributes, and custom data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AssetMap](arkts-assetstore-asset-assetmap-t.md)&gt;&gt; | Promise used to return the result obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [24000001](../errorcode-asset.md#24000001-asset-store-service-unavailable) | The ASSET service is unavailable. |
| [24000002](../errorcode-asset.md#24000002-asset-not-found) | The asset is not found. |
| [24000004](../errorcode-asset.md#24000004-access-denied) | Access denied. |
| [24000005](../errorcode-asset.md#24000005-incorrect-screen-lock-status) | The screen lock status does not match. |
| [24000006](../errorcode-asset.md#24000006-insufficient-memory) | Insufficient memory. |
| [24000007](../errorcode-asset.md#24000007-asset-corrupted) | The asset is corrupted. |
| [24000008](../errorcode-asset.md#24000008-database-operation-failed) | The database operation failed. |
| [24000009](../errorcode-asset.md#24000009-cryptographic-operation-failed) | The cryptography operation failed. |
| [24000010](../errorcode-asset.md#24000010-ipc-failed) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-bundle-manager-service-abnormal) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-account-system-service-abnormal) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-access-token-service-abnormal) | Calling the Access Token service failed. |
| [24000017](../errorcode-asset.md#24000017-function-not-supported) | The capability is not supported. |

**Examples**

```TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

let query: asset.AssetMap = new Map();
query.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
// If only the asset attributes need to be returned, set RETURN_TYPE to ATTRIBUTES. The attributes do not need to be decrypted, so the query takes a short time.
query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ALL); // Return all asset information, including the attributes and asset plaintext. The plaintext needs to be decrypted, so the query takes a long time.
asset.query(query).then((res: Array<asset.AssetMap>) => {
  for (let i = 0; i < res.length; i++) {
    // Parse the attributes.
    let accessibility: number = res[i].get(asset.Tag.ACCESSIBILITY) as number;
    console.info(`Succeeded in getting accessibility, which is: ${accessibility}.`);
  }
  console.info(`Succeeded in querying Asset.`);
});
```
