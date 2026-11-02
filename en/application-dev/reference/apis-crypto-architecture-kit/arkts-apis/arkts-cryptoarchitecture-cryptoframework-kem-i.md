# Kem

```TypeScript
interface Kem
```

Defines an API for key encapsulation and decapsulation based on the key encapsulation mechanism (KEM). Before calling this API, you must use the [createKem](arkts-cryptoarchitecture-cryptoframework-createkem-f.md) method to create a Kem instance.

**Since:** 26.0.0

<!--Device-cryptoFramework-interface Kem--><!--Device-cryptoFramework-interface Kem-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## decapsulate

```TypeScript
decapsulate(priKey: PriKey, wrappedKey: Uint8Array): Promise<Uint8Array>
```

Decapsulates a key based on the given private key and wrapped key. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-Kem-decapsulate(priKey: PriKey, wrappedKey: Uint8Array): Promise<Uint8Array>--><!--Device-Kem-decapsulate(priKey: PriKey, wrappedKey: Uint8Array): Promise<Uint8Array>-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | Yes | Private key used for key decapsulation. |
| wrappedKey | Uint8Array | Yes | Wrapped key generated during key encapsulation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the shared key obtained through key decapsulation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function kemDecapsulate() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = await asyKeyGenerator.generateKeyPair();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = await kem.encapsulate(keyPair.pubKey, null);
    let sharedSecret = await kem.decapsulate(keyPair.priKey, encapResult.wrappedKey);
    console.info('decapsulate success');
    console.info('sharedSecret length: ' + sharedSecret.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`decapsulate failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## decapsulateSync

```TypeScript
decapsulateSync(priKey: PriKey, wrappedKey: Uint8Array): Uint8Array
```

Decapsulates a key based on the given private key and wrapped key. This API returns the result synchronously.

<br><br>**NOTE:** <br>You are advised to preferentially use the asynchronous API <br>[decapsulate](#decapsulate) in a child thread. A synchronous API may block the main thread due to long execution time caused by the busy system or a high load.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-Kem-decapsulateSync(priKey: PriKey, wrappedKey: Uint8Array): Uint8Array--><!--Device-Kem-decapsulateSync(priKey: PriKey, wrappedKey: Uint8Array): Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | Yes | Private key used for key decapsulation. |
| wrappedKey | Uint8Array | Yes | Wrapped key generated during key encapsulation. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Shared key obtained through key decapsulation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function kemDecapsulateSync() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = asyKeyGenerator.generateKeyPairSync();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = kem.encapsulateSync(keyPair.pubKey, null);
    let sharedSecret = kem.decapsulateSync(keyPair.priKey, encapResult.wrappedKey);
    console.info('decapsulateSync success');
    console.info('sharedSecret length: ' + sharedSecret.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`decapsulateSync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## encapsulate

```TypeScript
encapsulate(pubKey: PubKey, ikme: Uint8Array | null): Promise<KemEncapResult>
```

Encapsulates a key based on the given public key. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-Kem-encapsulate(pubKey: PubKey, ikme: Uint8Array | null): Promise<KemEncapResult>--><!--Device-Kem-encapsulate(pubKey: PubKey, ikme: Uint8Array | null): Promise<KemEncapResult>-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pubKey | [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | Yes | Public key used for key encapsulation. |
| ikme | Uint8Array &#124; null | Yes | Random number seed, used to replace the random number within the algorithm. For the ML-KEM algorithm, the random number seed is 32 bytes. It is recommended to pass null. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KemEncapResult](arkts-cryptoarchitecture-cryptoframework-kemencapresult-i.md)&gt; | Promise used to return the KemEncapResult. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function kemEncapsulate() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = await asyKeyGenerator.generateKeyPair();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = await kem.encapsulate(keyPair.pubKey, null);
    console.info('encapsulate success');
    console.info('sharedSecret length: ' + encapResult.sharedSecret.length);
    console.info('wrappedKey length: ' + encapResult.wrappedKey.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`encapsulate failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## encapsulateSync

```TypeScript
encapsulateSync(pubKey: PubKey, ikme: Uint8Array | null): KemEncapResult
```

Encapsulates a key based on the given public key. This API returns the result synchronously.

<br><br>**NOTE:** <br>You are advised to preferentially use the asynchronous API <br>[encapsulate](#encapsulate) in a child thread. A synchronous API may block the main thread due to long execution time caused by the busy system or a high load.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-Kem-encapsulateSync(pubKey: PubKey, ikme: Uint8Array | null): KemEncapResult--><!--Device-Kem-encapsulateSync(pubKey: PubKey, ikme: Uint8Array | null): KemEncapResult-End-->

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pubKey | [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | Yes | Public key used for key encapsulation. |
| ikme | Uint8Array &#124; null | Yes | Random number seed, used to replace the random number within the algorithm. For the ML-KEM algorithm, the random number seed is 32 bytes. It is recommended to pass null. |

**Return value:**

| Type | Description |
| --- | --- |
| [KemEncapResult](arkts-cryptoarchitecture-cryptoframework-kemencapresult-i.md) | The encapsulation result of the KEM. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function kemEncapsulateSync() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = asyKeyGenerator.generateKeyPairSync();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = kem.encapsulateSync(keyPair.pubKey, null);
    console.info('encapsulateSync success');
    console.info('sharedSecret length: ' + encapResult.sharedSecret.length);
    console.info('wrappedKey length: ' + encapResult.wrappedKey.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`encapsulateSync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```
