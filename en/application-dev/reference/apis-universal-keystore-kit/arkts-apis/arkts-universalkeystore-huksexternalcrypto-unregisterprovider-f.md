# unregisterProvider

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## unregisterProvider

```TypeScript
function unregisterProvider(providerName: string, params?: Array<HuksExternalCryptoParam>): Promise<void>
```

Unregisters a specified external Provider. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.CRYPTO_EXTENSION_REGISTER

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| providerName | string | Yes | Provider name, which contains a maximum of 128 characters. It is recommended that the value contain the vendor information, be globally unique, and not contain sensitive data such as personal contact information. If a provider has registered multiple extension capabilities, all the extension capabilities of the provider will be unregistered. |
| params | Array&lt;[HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; | No | Parameters to be passed during the operation.<br>You can specify [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md) in the **params** parameter to unregister the corresponding **cryptoExtensionAbility** based on the bundle name, **providerName**, and **abilityName**.<br>If [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md) is not specified in the **params** parameter or the **params** parameter is not passed, all providers under the corresponding **providerName** are unregistered. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the unregisterProvider API, missing Permission: ohos.permission.CRYPTO_EXTENSION_REGISTER. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | the provider is not found. |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter is abnormal. This may happen for several reasons, such as the model already being unloaded. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the input parameter is invalid. |

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

const providerName = "testProviderName";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: StringToUint8Array("CryptoExtension")
  }
];
huksExternalCrypto.unregisterProvider(providerName, extProperties)
    .then((data) => {
        console.info('promise: unregisterProvider success.');
    });
```
