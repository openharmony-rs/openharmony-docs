# authUkeyPin (System API)

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## authUkeyPin

```TypeScript
function authUkeyPin(resourceId: string, params: Array<HuksExternalCryptoParam>): Promise<void>
```

Authenticates a UKey PIN. This API uses a promise to return the result.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | Resource ID of a container in the UKey, which can be obtained using [certificateManagerDialog.openAuthorizeDialog22+](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openauthorizedialog-1). The result contains **resourceId**. |
| params | Array&lt;[HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; | Yes | Parameters to be passed during the operation. The mandatory tag is [HUKS_EXT_CRYPTO_TAG_UKEY_PIN](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application and is not allowed to use system applications. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | the UKey driver operation failed. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist. |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal. This error may occur if the process function is not found, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the input parameter is invalid. |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | the provider operation failed. |
| [12000021](../errorcode-huks.md#12000021-ukey-pin-locked) | the UKey PIN is locked. |
| [12000022](../errorcode-huks.md#12000022-incorrect-ukey-pin) | the UKey PIN is incorrect. |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | the provider or UKey is busy. |

**Examples**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

let uid: number = 3511;
const testResourceId = "{\"providerName\":\"testProviderName\", \"bundleName\":\"com.example.cryptoapplication\", \"abilityName\":\"CryptoExtension\",\"index\":{\"key\":\"testKey\"}}";
const pin = "123456";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID,
    value: uid
  }, {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
    value: StringToUint8Array(pin)
  }
];
huksExternalCrypto.authUkeyPin(testResourceId, extProperties)
    .then((data) => {
        console.info(`promise: authUkeyPin success`);
    });
```
