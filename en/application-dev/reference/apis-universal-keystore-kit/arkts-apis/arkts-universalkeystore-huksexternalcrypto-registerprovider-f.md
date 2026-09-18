# registerProvider

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## registerProvider

```TypeScript
function registerProvider(providerName: string, params: Array<HuksExternalCryptoParam>): Promise<void>
```

Registers a specified external Provider. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.CRYPTO_EXTENSION_REGISTER

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| providerName | string | Yes | Provider name, which contains a maximum of 128 characters. It is recommended that the value contain the vendor information, be globally unique, and not contain sensitive data such as personal contact information.<br>A maximum of 10 providers can be registered. |
| params | Array&lt;[HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; | Yes | Parameters to be passed during the operation. The mandatory tag is [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md), indicating the ability name. Set this parameter based on the actual service requirements. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the registerProvider API, missing Permission: ohos.permission.CRYPTO_EXTENSION_REGISTER. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | the ability name param is missing. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the input parameter is invalid. |
| [12000019](../errorcode-huks.md#12000019-provider-name-already-registered) | the provider is already registered. |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | an error occurred in the dependent module. |
| [12000025](../errorcode-huks.md#12000025-resource-limit-exceeded) | the number of providers exceeds the limit. |

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
huksExternalCrypto.registerProvider(providerName, extProperties)
    .then((data) => {
        console.info('promise: registerProvider success.');
    });
```
