# Cipher

Encryption and decryption interface, defining methods for symmetric and asymmetric encryption and decryption. Before use, you must create a **Cipher** instance by using [createCipher(transformation: string): Cipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md). Call the [init()](#init-3), [update()](#update), and [doFinal()](#dofinal-1) APIs in this class as needed to complete encryption or decryption operations.

<br>For details about the complete encryption and decryption process, see [Encryption and Decryption Overview](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md).

<br>A complete symmetric encryption/decryption process is slightly different from the asymmetric encryption/decryption process.

- Symmetric encryption and decryption: **init()** and **doFinal()** are mandatory. **update()** is optional and can  
be called multiple times to encrypt or decrypt big data. After **doFinal()** is called to complete an encryption or decryption operation, **init()** can be called to start a new encryption or decryption operation.  
- RSA or SM2 asymmetric encryption and decryption: **init()** and **doFinal()** are mandatory, and **update()** is  
not supported. **doFinal()** can be called multiple times to encrypt or decrypt big data. **init()** cannot be called repeatedly. If the encryption/decryption mode or padding mode is changed, a new **Cipher** object must be created.

**Since:** 9

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## doFinal

```TypeScript
doFinal(data: DataBlob, callback: AsyncCallback<DataBlob>): void
```

Finishes the crypto operation, encrypts or decrypts the input data, and then feeds back the output data. Data cannot be updated after the crypto operation is finished. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Indicates the data to be finally encrypted or decrypted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the encrypted or decrypted data obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
For more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption).
```

```TypeScript
In addition, for more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption.
```

## doFinal

```TypeScript
doFinal(data: DataBlob | null, callback: AsyncCallback<DataBlob>): void
```

Finishes the crypto operation, encrypts or decrypts the input data, and then feeds back the output data. Data cannot be updated after the crypto operation is finished. This API uses an asynchronous callback to return the result.

<br>(1) Processes the remaining data and the data passed in this time, and completes the encryption or decryption operation for symmetric encryption and decryption. This API uses an asynchronous callback to return the encrypted or decrypted data. If a small amount of data needs to be encrypted or decrypted, you can use **doFinal()** to pass in all the data without using **update()**. If all the data has been passed in by [update()](#update), you can pass in **null** in **data** of **doFinal()**. The output of **doFinal()** varies with the symmetric block cipher mode in use. This API uses an asynchronous callback to return the result.

- In a single encryption process with GCM or CCM mode, concatenating the results of each **update()** and  
**doFinal()** produces the ciphertext and **authTag**. In GCM mode, **authTag** is the last 16 bytes. In CCM mode, **authTag** is the last 12 bytes. The rest part is the ciphertext. If **data** passed to **doFinal()** is **null**, the **doFinal()** result is only the **authTag**. During decryption, **authTag** must be set in [GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md) or [CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md), and the ciphertext must be set in **data**.  
- For other symmetric encryption and decryption modes and GCM and CCM decryption modes, concatenating the results  
of **update()** and **doFinal()** throughout the process will yield the complete plaintext or ciphertext.

(2) Encrypts or decrypts the data passed in this time in RSA and SM2 asymmetric encryption or decryption. This API uses an asynchronous callback to return the encrypted or decrypted data. If a large amount of data needs to be encrypted/decrypted, call **doFinal()** multiple times and concatenate the result of each **doFinal()** to obtain the complete plaintext/ciphertext.

> **NOTE:** 
> 
> 1. In symmetric encryption and decryption, after **doFinal** is called, the encryption and decryption process is complete and the [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance is cleared. When a new encryption and decryption process is started, **init()** must be called with a complete parameter list for initialization.Even if the same symmetric key is used to encrypt and decrypt the same **Cipher** instance, the **params**parameter must be set when **init** is called during decryption.
> 2. If a decryption fails, check whether the data to be encrypted and decrypted matches the parameters in
> **init()**. For the GCM mode, check whether the **authTag** obtained after encryption is obtained from the
> **GcmParamsSpec** for decryption.
> 3. The result of **doFinal()** may be **null**. To avoid exceptions, determine whether the result is **null**before using the **.data** field to access the **doFinal()** result.For encryption in CFB, OFB, or CTR mode, if **doFinal()** passes in **null**, the returned result is **null**.For decryption in GCM, CCM, CFB, OFB, or CTR mode, if **doFinal()** passes in **null**, the returned result is
> **null**. For decryption in other modes, if **update** is called to pass in all the plaintext, which is an
> integer multiple of the encryption block size, and **doFinal()** is called to pass in **null**, the returned
> result is **null**.
> 4. For details about the sample code for calling **doFinal** multiple times in asymmetric encryption and decryption, see [Encryption and Decryption by Segment with an RSA Asymmetric Key Pair](../../../security/CryptoArchitectureKit/crypto-rsa-asym-encrypt-decrypt.md).The operations are similar for SM2 and RSA.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) &#124; null | Yes | Data to encrypt or decrypt. In symmetric encryption and decryption, this parameter can be **null**, but **{data: Uint8Array (empty)}** cannot be passed in. Before API version 10, only **DataBlob** is supported. Since API version 10, **null** is also supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Yes | Callback used to return the result. If the encryption or decryption is successful, **err** is **undefined**, and **data** is the encryption or decryption result obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
For more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption).
```

```TypeScript
In addition, for more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption.
```

## doFinal

```TypeScript
doFinal(data: DataBlob): Promise<DataBlob>
```

Finishes the crypto operation, encrypts or decrypts the input data, and then feeds back the output data. Data cannot be updated after the crypto operation is finished. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Indicates the data to be finally encrypted or decrypted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise used to return the encrypted or decrypted data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
For more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption).
```

```TypeScript
In addition, for more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption.
```

## doFinal

```TypeScript
doFinal(data: DataBlob | null): Promise<DataBlob>
```

Finishes the crypto operation, encrypts or decrypts the input data, and then feeds back the output data. Data cannot be updated after the crypto operation is finished. This API uses a promise to return the result.

<br>(1) Encrypts or decrypts the remaining data (generated by the block cipher mode) and the data passed in this time to finalize the symmetric encryption or decryption. This API uses a promise to return the result.

If a small amount of data needs to be encrypted or decrypted, you can use **doFinal()** to pass in data without using **update()**. If all the data has been passed in by **update()**, you can pass in **null** in **data** of **doFinal()**.

The output of **doFinal()** varies with the symmetric encryption/decryption mode in use.

- Symmetric encryption in GCM and CCM mode: The result consists of the ciphertext and **authTag** (the last 16  
bytes for GCM and the last 12 bytes for CCM). If **data** in **doFinal** is null, the result of **doFinal** is **authTag**.

During decryption, **authTag** must be set in [GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md) or [CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md), and the ciphertext must be set in **data**.

- For other symmetric encryption and decryption modes and GCM and CCM decryption modes, concatenating the results  
of **update()** and **doFinal()** throughout the process will yield the complete plaintext or ciphertext.

(2) Encrypts or decrypts the data passed in RSA and SM2 asymmetric encryption or decryption. This API uses a promise to return the encrypted or decrypted data. If a large amount of data is to be processed, call **doFinal()** multiple times and concatenate the results to obtain the complete plaintext or ciphertext.

> **NOTE:** 
> 
> 1. In symmetric encryption and decryption, after **doFinal** is called, the encryption and decryption process is complete and the [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance is cleared. When a new encryption and decryption process is started, **init()** must be called with a complete parameter list for initialization.Even if the same symmetric key is used to encrypt and decrypt the same **Cipher** instance, the **params**parameter must be set when **init** is called during decryption.
> 2. If a decryption fails, check whether the data to be encrypted and decrypted matches the parameters in
> **init()**. For the GCM mode, check whether the **authTag** obtained after encryption is obtained from the
> **GcmParamsSpec** for decryption.
> 3. The result of **doFinal()** may be **null**. To avoid exceptions, determine whether the result is **null**before using the **.data** field to access the **doFinal()** result.For encryption in CFB, OFB, or CTR mode, if **doFinal()** passes in **null**, the returned result is **null**.For decryption in GCM, CCM, CFB, OFB, or CTR mode, if **doFinal()** passes in **null**, the returned result is
> **null**. For decryption in other modes, if **update** is called to pass in all the plaintext, which is an
> integer multiple of the encryption block size, and **doFinal()** is called to pass in **null**, the returned
> result is **null**.
> 4. For details about the sample code for calling **doFinal** multiple times in asymmetric encryption and decryption, see [Encryption and Decryption by Segment with an RSA Asymmetric Key Pair](../../../security/CryptoArchitectureKit/crypto-rsa-asym-encrypt-decrypt.md).The operations are similar for SM2 and RSA.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) &#124; null | Yes | Data to encrypt or decrypt. It can be **null**, but cannot be {data:Uint8Array(empty)}. In versions earlier than API version 10, only **DataBlob** is supported. Since API version 10, **null** is also supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise used to return the **DataBlob**, which is the encryption or decryption result of the remaining data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
For more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption).
```

```TypeScript
In addition, for more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption.
```

## doFinalSync

```TypeScript
doFinalSync(data: DataBlob | null): DataBlob
```

Finishes the crypto operation, encrypts or decrypts the input data, and then feeds back the output data. Data cannot be updated after the crypto operation is finished.

<br>(1) Processes the remaining data and the data passed in this time, and completes the encryption or decryption operation for symmetric encryption and decryption. This API returns the encrypted or decrypted data synchronously.

If a small amount of data is to be processed, you can pass in all the data at a time in **doFinalSync()** without using **updateSync()**. If data has been passed in by using [updateSync](#updatesync) in the current encryption and decryption process, you can pass in **null** to the **data** parameter of **doFinalSync()**.

The output of **doFinalSync()** varies with the symmetric block cipher mode in use.

- In a single encryption process with GCM or CCM mode, concatenating the results of each **updateSync()** and  
**doFinalSync()** produces the ciphertext and **authTag**. In GCM mode, **authTag** is the last 16 bytes. In CCM mode, **authTag** is the last 12 bytes. The rest part is the ciphertext. If **data** in **doFinalSync()** is **null**, the result of **doFinalSync()** is **authTag**.  
- During decryption, **authTag** must be set in [GcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-gcmparamsspec-i.md) or [CcmParamsSpec](arkts-cryptoarchitecture-cryptoframework-ccmparamsspec-i.md), and the ciphertext must be set in **data**.  
- For other symmetric encryption and decryption modes and GCM and CCM decryption modes, concatenating the results  
of **updateSync()** and **doFinalSync()** throughout the process will yield the complete plaintext or ciphertext.

(2) Encrypts or decrypts the input data for RSA or SM2 asymmetric encryption/decryption. This API returns the encrypted or decrypted data synchronously. If a large amount of data is to be processed, call **doFinalSync()** multiple times and concatenate the results to obtain the complete plaintext or ciphertext.

<br>See **NOTE:** in [doFinal()](#dofinal-1) for other precautions.

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, doFinal. Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) &#124; null | Yes | Data to encrypt or decrypt. It can be **null** in symmetric encryption or decryption, but cannot be {data:Uint8Array(empty)}. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Encrypted or decrypted data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
In addition, for more encryption and decryption examples, see Using an AES Symmetric Key (GCM Mode) for Encryption and Decryption.
```

## getCipherSpec

```TypeScript
getCipherSpec(itemType: CipherSpecItem): string | Uint8Array
```

Obtains cipher specifications. Currently, only RSA and SM2 (available since API version 11) are supported.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| itemType | [CipherSpecItem](arkts-cryptoarchitecture-cryptoframework-cipherspecitem-e.md) | Yes | Cipher parameter to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; Uint8Array | Returns the value of the cipher parameter obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Unsupported itemType.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testGetCipherSpec() {
  let cipher = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
  let mdName = cipher.getCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MD_NAME_STR);
  console.info('getCipherSpec: mdName =' + mdName);
}
```

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback<void>): void
```

Initializes the crypto operation with the given crypto mode, key and parameters. This API uses an asynchronous callback to return the result.

<br>**init**, **update**, and **doFinal** must be used together. **init** and **doFinal** are mandatory, and **update** is optional.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | Yes | Operation (encryption or decryption) to perform. |
| key | [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md) | Yes | Key for encryption or decryption. |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) | Yes | Indicates the algorithm parameters such as IV. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Invalid opMode value; <br>2. Invalid iv length; <br>3. Invalid key length.<br>**Applicable version:** 22 and later |

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec | null, callback: AsyncCallback<void>): void
```

Initializes the [cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) object for encryption and decryption. This API uses an asynchronous callback to return the result.

<br>**init**, **update**, and **doFinal** must be used together. **init** and **doFinal** are mandatory, and **update** is optional.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | Yes | Operation (encryption or decryption) to perform. |
| key | [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md) | Yes | Key for encryption or decryption. |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) &#124; null | Yes | Parameters for encryption or decryption. For algorithm modes without parameters (such as ECB), set this parameter to **null**. In versions earlier than API version 10, only **ParamsSpec** is supported. Since API version 10, **null** is also supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Invalid opMode value; <br>2. Invalid iv length; <br>3. Invalid key length.<br>**Applicable version:** 22 and later |

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise<void>
```

Initializes the crypto operation with the given crypto mode, key and parameters. This API uses a promise to return the result.

<br>**init**, **update**, and **doFinal** must be used together. **init** and **doFinal** are mandatory, and **update** is optional.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | Yes | Operation (encryption or decryption) to perform. |
| key | [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md) | Yes | Key for encryption or decryption. |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) | Yes | Indicates the algorithm parameters such as IV. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Invalid opMode value; <br>2. Invalid iv length; <br>3. Invalid key length.<br>**Applicable version:** 22 and later |

## init

```TypeScript
init(opMode: CryptoMode, key: Key, params: ParamsSpec | null): Promise<void>
```

Initializes the cipher object for encryption and decryption. This API uses a promise to return the result.

<br>**init**, **update**, and **doFinal** must be used together. **init** and **doFinal** are mandatory, and **update** is optional.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | Yes | Operation (encryption or decryption) to perform. |
| key | [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md) | Yes | Key for encryption or decryption. |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) &#124; null | Yes | Parameters for encryption or decryption. For algorithm modes without parameters (such as ECB), set this parameter to **null**. Before API version 10, only **ParamsSpec** is supported. Since API version 10, **null** is also supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Invalid opMode value; <br>2. Invalid iv length; <br>3. Invalid key length.<br>**Applicable version:** 22 and later |

## initSync

```TypeScript
initSync(opMode: CryptoMode, key: Key, params: ParamsSpec | null): void
```

Initializes a [cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance. This API returns the result synchronously.

<br>**initSync**, **updateSync**, and **doFinalSync** must be used together. **initSync** and **doFinalSync** are mandatory, and **updateSync** is optional.

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, init. Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opMode | [CryptoMode](arkts-cryptoarchitecture-cryptoframework-cryptomode-e.md) | Yes | Operation (encryption or decryption) to perform. |
| key | [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md) | Yes | Key for encryption or decryption. |
| params | [ParamsSpec](arkts-cryptoarchitecture-cryptoframework-paramsspec-i.md) &#124; null | Yes | Parameters for encryption or decryption. For algorithm modes without parameters (such as ECB), set this parameter to **null**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Invalid opMode value; <br>2. Invalid iv length; <br>3. Invalid key length.<br>**Applicable version:** 22 and later |

## setCipherSpec

```TypeScript
setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void
```

Sets cipher specifications. You can use this API to set cipher specifications that cannot be set by [createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md). Currently, only RSA is supported.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 10 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| itemType | [CipherSpecItem](arkts-cryptoarchitecture-cryptoframework-cipherspecitem-e.md) | Yes | Cipher parameter to set. |
| itemValue | Uint8Array | Yes | Value of the parameter to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. Unsupported itemType.<br>**Applicable version:** 22 and later |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testSetCipherSpec() {
  let cipher = cryptoFramework.createCipher('RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1');
  let pSource = new Uint8Array([1, 2, 3, 4]);
  cipher.setCipherSpec(cryptoFramework.CipherSpecItem.OAEP_MGF1_PSRC_UINT8ARR, pSource);
}
```

## update

```TypeScript
update(data: DataBlob, callback: AsyncCallback<DataBlob>): void
```

Updates the data to encrypt or decrypt by segment. This API uses an asynchronous callback to return the result.

<br>This API can be called only after the [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance is initialized by using [init()](#init-3).

> **NOTE:** 
> 
> 1. The results of **update()** and **doFinal()** may vary with the block mode used. If you are not familiar with the block modes, you are advised to check each **update()** and **doFinal()** result to ensure that the results are not **null**. When a valid result is returned, extract and concatenate the data to form a complete ciphertext or plaintext.<br>For example, in ECB and CBC modes, encryption and decryption are performed by block regardless of whether the data input by **update()** is an integer multiple of the block size, and **update()** returns the newly processed block data.<br>That is, data is returned as long as the data passed in by **update()** reaches the size of a block. Otherwise,
> **null** is returned and the data will be retained until a block is formed in the next **update()** or
> **doFinal()**.
> <br>In the final **doFinal()** operation, the remaining unprocessed data is padded based on the padding mode set in
> [createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md) to the integer multiple of the block size to produce the
> final encrypted or decrypted data.
> <br>For block cipher modes that can be converted to stream mode, the ciphertext length may be the same as the
> plaintext length.
> 2. You can call **update()** multiple times or skip calling **update()** (call **doFinal()** directly after
> **init()**), depending on the data volume.
> <br>The amount of the data to be passed in by **update()** (one-time or accumulative) is not limited. If there is a
> large amount of data, you are advised to pass data in multiple **update()** calls rather than processing it all
> at once.
> <br>For details about the sample code for passing data in multiple **update()** calls, see
> [Encryption and Decryption by Segment with an AES Symmetric Key (GCM Mode)](../../../security/CryptoArchitectureKit/crypto-aes-sym-encrypt-decrypt.md).
> 3. RSA or SM2 asymmetric encryption and decryption do not support **update()**.
> 4. If CCM is used in symmetric encryption or decryption, **update()** can be called only once. In the encryption process, you can either use **update()** to encrypt data and use **doFinal()** to obtain **authTag**or use **doFinal()** without using **update()**. In the decryption process, you can either use **update()** or
> **doFinal()** once to decrypt data and verify the tag.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to be encrypted or decrypted. It cannot be null. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Yes | Callback used to return the result. If the data is updated successfully, **err** is **undefined**, and **data** is the encryption or decryption result obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

## update

```TypeScript
update(data: DataBlob): Promise<DataBlob>
```

Updates the data to encrypt or decrypt by segment. This API uses a promise to return the result.

<br>This API can be called only after the [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance is initialized by using [init()](#init-3).

> **NOTE:** 
> 
> 1. The results of **update()** and **doFinal()** may vary with the block mode used. If you are not familiar with the block modes, you are advised to check each **update()** and **doFinal()** result to ensure that the results are not **null**. When a valid result is returned, extract and concatenate the data to form a complete ciphertext or plaintext.<br>For example, in ECB and CBC modes, encryption and decryption are performed by block regardless of whether the data input by **update()** is an integer multiple of the block size, and **update()** returns the newly processed block data.<br>That is, data is returned as long as the data passed in by **update()** reaches the size of a block. Otherwise,
> **null** is returned and the data will be retained until a block is formed in the next **update()** or
> **doFinal()**.
> <br>In the final **doFinal()** operation, the remaining unprocessed data is padded based on the padding mode set in
> [createCipher](arkts-cryptoarchitecture-cryptoframework-createcipher-f.md) to the integer multiple of the block size to produce the
> final encrypted or decrypted data.
> <br>For block cipher modes that can be converted to stream mode, the ciphertext length may be the same as the
> plaintext length.
> 2. You can call **update()** multiple times or skip calling **update()** (call **doFinal()** directly after
> **init()**), depending on the data volume.
> <br>The amount of the data to be passed in by **update()** (one-time or accumulative) is not limited. If there is a
> large amount of data, you are advised to pass data in multiple **update()** calls rather than processing it all
> at once.
> <br>For details about the sample code for passing data in multiple **update()** calls, see
> [Encryption and Decryption by Segment with an AES Symmetric Key (GCM Mode)](../../../security/CryptoArchitectureKit/crypto-aes-sym-encrypt-decrypt.md).
> 3. RSA or SM2 asymmetric encryption and decryption do not support **update()**.
> 4. If CCM is used in symmetric encryption or decryption, **update()** can be called only once. In the encryption process, you can either use **update()** to encrypt data and use **doFinal()** to obtain **authTag**or use **doFinal()** without using **update()**. In the decryption process, you can either use **update()** or
> **doFinal()** once to decrypt data and verify the tag.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to encrypt or decrypt. It cannot be null. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise used to return the **DataBlob** (containing the encrypted or decrypted data). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

## updateSync

```TypeScript
updateSync(data: DataBlob): DataBlob
```

Updates the data to encrypt or decrypt by segment.

<br>This API can be called only after the [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md) instance is initialized by using [initSync()](#initsync).

<br>See **NOTE:** in **update()** for other precautions.

<br><br>**NOTE:** <br>It is recommended to prioritize the use of asynchronous API, update. Synchronous API may take a long time and block the main thread due to system busyness, high load, and other reasons. Therefore, it is advised to invoke synchronous API within a child thread to avoid blocking the main thread.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Yes | Data to encrypt or decrypt. It cannot be null. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | Encryption/decryption result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-failed-to-obtain-the-native-object-or-convert-parameters) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-parameter-check-failed) | Parameter check failed. Possible causes:<br>1. The data is too long.<br>**Applicable version:** 22 and later |

## algName

```TypeScript
readonly algName: string
```

Indicates the algorithm name of the cipher object.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Cipher
- API versions 9 to 11: SystemCapability.Security.CryptoFramework
