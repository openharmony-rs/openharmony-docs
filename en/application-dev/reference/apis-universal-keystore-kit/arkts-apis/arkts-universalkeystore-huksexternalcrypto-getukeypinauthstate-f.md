# getUkeyPinAuthState

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## getUkeyPinAuthState

```TypeScript
function getUkeyPinAuthState(resourceId: string, params?: Array<HuksExternalCryptoParam>): Promise<HuksExternalPinAuthState>
```

Obtains the PIN authentication state. This API uses a promise to return the result.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | Resource ID, which can be obtained using [certificateManagerDialog.openAuthorizeDialog22+](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md). The result contains **resourceId**. |
| params | Array&lt;[HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; | No | Operation parameters. If a non-system application passes [HUKS_EXT_CRYPTO_TAG_UID](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md), the parameter is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksExternalPinAuthState](arkts-universalkeystore-huksexternalcrypto-huksexternalpinauthstate-e.md)&gt; | Promise used to return the authentication result.<br>**HUKS_EXT_CRYPTO_PIN_NO_AUTH**: The PIN authentication fails. **HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED**: The PIN authentication is successful. **HUKS_EXT_CRYPTO_PIN_LOCKED**: The PIN is locked. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | the UKey driver operation failed. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist. This may happen because the resource ID has not been opened. |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter is abnormal. This error may occur if the process function is not found, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the input parameter is invalid. |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | the provider operation failed. |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | the provider or UKey is busy. |

**Examples**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = "{\"providerName\":\"testProviderName\", \"bundleName\":\"com.example.cryptoapplication\", \"abilityName\":\"CryptoExtension\",\"index\":{\"key\":\"testKey\"}}";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
huksExternalCrypto.getUkeyPinAuthState(testResourceId, extProperties)
    .then((data) => {
      console.info(`promise: getUkeyPinAuthState success, data: ${data}`);
    });
```
