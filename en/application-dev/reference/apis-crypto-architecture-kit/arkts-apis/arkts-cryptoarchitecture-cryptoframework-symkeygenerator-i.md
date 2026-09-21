# SymKeyGenerator

```TypeScript
interface SymKeyGenerator
```

Symmetric key generator interface, defining methods for generating symmetric keys. Before use, you must create a **SymKeyGenerator** instance by using [createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md).

**Since:** 9

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.SymKey
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## convertKey

```TypeScript
convertKey(key: DataBlob, callback: AsyncCallback<SymKey>): void
```

Converts specified data into a symmetric key. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For symmetric keys used in the HMAC algorithm, if a hash algorithm (for example, **HMAC|SHA256**) is specified
> when the symmetric key generator is created, the binary key data passed in must match the hash length (for
> example, a 256-bit key for SHA256).

If no hash algorithm is specified when the symmetric key generator is created (for example, only **HMAC** is specified), any binary key data with a length of 1 to 4,096 bytes is supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.SymKey
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to convert. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the symmetric key obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function genKeyMaterialBlob(): cryptoFramework.DataBlob {
  let arr = [
    0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56,
    0xad, 0x47, 0xfc, 0x5a, 0x46, 0x39, 0xee, 0x7c,
    0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72]; // keyLen = 192 (24 bytes)
  let keyMaterial = new Uint8Array(arr);
  return { data: keyMaterial };
}

function testConvertKey() {
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
  let keyMaterialBlob = genKeyMaterialBlob();
  symKeyGenerator.convertKey(keyMaterialBlob, (err, symKey) => {
    console.info('Convert symKey result: success, algName: ' + symKey.algName);
  });
}
```

<a id="convertkey-1"></a>

## convertKey

```TypeScript
convertKey(key: DataBlob): Promise<SymKey>
```

Converts specified data into a symmetric key. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.SymKey
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to convert. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md)&gt; | Promise used to return the symmetric key generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 26.2.0 and later |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function genKeyMaterialBlob(): cryptoFramework.DataBlob {
  let arr = [
    0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56,
    0xad, 0x47, 0xfc, 0x5a, 0x46, 0x39, 0xee, 0x7c,
    0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72]; // keyLen = 192 (24 bytes)
  let keyMaterial = new Uint8Array(arr);
  return { data: keyMaterial };
}

function testConvertKey() {
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
  let keyMaterialBlob = genKeyMaterialBlob();
  symKeyGenerator.convertKey(keyMaterialBlob)
    .then(symKey => {
      console.info('Convert symKey result: success, algName: ' + symKey.algName);
    }).catch((error: BusinessError) => {
      console.error(`Convert symKey failed, ${error.code}, ${error.message}`);
    });
}
```

## convertKeySync

```TypeScript
convertKeySync(key: DataBlob): SymKey
```

Converts specified data into a symmetric key.

> **NOTE:** 
> 
> For symmetric keys used in the HMAC algorithm, if a hash algorithm (for example, **HMAC|SHA256**) is specified
> when the symmetric key generator is created, the binary key data passed in must match the hash length (for
> example, a 256-bit key for SHA256). If no hash algorithm is specified when the symmetric key generator is
> created (for example, only **HMAC** is specified), any binary key data with a length of 1 to 4,096 bytes is
> supported.

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, convertKey. Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.Key.SymKey

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to convert. |

**Return value:**

| Type | Description |
| --- | --- |
| [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | Symmetric key obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function testConvertKeySync() {
  // The symmetric key length is 64 bytes (512 bits).
  let keyMessage = '87654321abcdefgh87654321abcdefgh87654321abcdefgh87654321abcdefgh';
  let keyBlob: cryptoFramework.DataBlob = {
    data : new Uint8Array(buffer.from(keyMessage, 'utf-8').buffer)
  }
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('HMAC');
  let key = symKeyGenerator.convertKeySync(keyBlob);
  let encodedKey = key.getEncoded();
  console.info('key encoded data: ' + encodedKey.data);
}
```

## generateSymKey

```TypeScript
generateSymKey(callback: AsyncCallback<SymKey>): void
```

Generates a random key using this symmetric key generator. This API uses an asynchronous callback to return the result. <br>OpenSSL RAND_priv_bytes() is currently used to generate random keys.

> **NOTE:** 
> 
> For symmetric keys used in the HMAC algorithm, if a hash algorithm (for example, **HMAC|SHA256**) is specified
> when the symmetric key generator is created, a binary key matching the hash length (for example, a 256-bit key)
> will be randomly generated. If no hash algorithm is specified, for example, only **HMAC** is specified, random
> symmetric key generation is not supported. You can generate symmetric key data using
> [convertKey](#convertkey).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.SymKey
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the symmetric key obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 26.2.0 and later |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
  symKeyGenerator.generateSymKey((err, symKey) => {
    console.info('Generate symKey result: success, algName: ' + symKey.algName);
  });
```

<a id="generatesymkey-1"></a>

## generateSymKey

```TypeScript
generateSymKey(): Promise<SymKey>
```

Generates a random key using this symmetric key generator. This API uses a promise to return the result. <br>OpenSSL RAND_priv_bytes() is currently used to generate random keys.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.SymKey
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md)&gt; | Promise used to return the symmetric key generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 26.2.0 and later |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  symKeyGenerator.generateSymKey()
    .then(symKey => {
      console.info('Generate symKey result: success, algName: ' + symKey.algName);
    }).catch((error: BusinessError) => {
      console.error(`Generate symKey failed, ${error.code}, ${error.message}`);
    });
```

## generateSymKeySync

```TypeScript
generateSymKeySync(): SymKey
```

Generates a random key using this symmetric key generator. This API returns the result synchronously. <br>OpenSSL RAND_priv_bytes() is currently used to generate random keys.

> **NOTE:** 
> 
> For symmetric keys used in the HMAC algorithm, if a hash algorithm (for example, **HMAC|SHA256**) is specified
> when the symmetric key generator is created, a binary key matching the hash length (for example, a 256-bit key)
> will be randomly generated.

If no hash algorithm is specified, for example, only **HMAC** is specified, random symmetric key generation is not supported. You can generate symmetric key data using [convertKeySync](#convertkeysync).

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, [generateSymKey](#generatesymkey). Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.Key.SymKey

**Return value:**

| Type | Description |
| --- | --- |
| [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | Symmetric key generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 26.2.0 and later |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620004](../errorcode-crypto-framework.md#17620004-invalid-function-call) | Invalid function call.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testGenerateSymKeySync() {
  // Create a SymKeyGenerator instance.
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES256');
  // Use SymKeyGenerator to randomly generate a symmetric key.
  let key = symKeyGenerator.generateSymKeySync();
  let encodedKey = key.getEncoded();
  console.info('key hex:' + encodedKey.data);
}
```

## algName

```TypeScript
readonly algName: string
```

Indicates the algorithm name of the SymKeyGenerator object.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.SymKey
- API versions 9 to 11: SystemCapability.Security.CryptoFramework
