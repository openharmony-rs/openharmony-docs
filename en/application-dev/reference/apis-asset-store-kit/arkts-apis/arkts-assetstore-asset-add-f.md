# add

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## add

```TypeScript
function add(attributes: AssetMap): Promise<void>
```

Adds an asset. This API uses a promise to return the result.

To set [IS_PERSISTENT](arkts-assetstore-asset-tag-e.md#is_persistent), the application must have the ohos.permission.STORE_PERSISTENT_DATA permission.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attributes | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | Yes | Attributes of the asset to add, including the asset plaintext, access control attributes, and custom data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [24000001](../errorcode-asset.md#24000001-asset-store-service-unavailable) | The ASSET service is unavailable. |
| [24000003](../errorcode-asset.md#24000003-asset-already-exists) | The asset already exists. |
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

**Examples**

```TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

let attr: asset.AssetMap = new Map();
attr.set(asset.Tag.SECRET, stringToArray('demo_pwd'));
attr.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
attr.set(asset.Tag.ACCESSIBILITY, asset.Accessibility.DEVICE_FIRST_UNLOCKED);
attr.set(asset.Tag.DATA_LABEL_NORMAL_1, stringToArray('demo_label'));
asset.add(attr).then(() => {
  console.info(`Succeeded in adding Asset.`);
});
```
