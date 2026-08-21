# Crypto Framework Error Codes

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ee3aff3c192b61804c6eafd655527edff9eb980a translatedAt=2026-08-10T09:36:35.000Z pushedAt=2026-08-11T01:19:28.680Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 17620001 Memory Operation Failed

**Error Message**

Memory operation failed.

**Description**

The memory operation failed.

**Possible Causes**

The memory allocation failed.

**Solution**

1. Check whether the system is running properly.

2. Check whether the service data is too long. 

## 17620002 Failed to Obtain the Native Object or Convert Parameters

**Error Message**

Failed to obtain the native object or convert parameters.

**Description**

The Native object fails to be obtained or the parameter conversion fails.

**Possible Causes**

An unexpected error occurs.

**Solution**

Check whether the system is running properly.

## 17620003 Parameter Check Failed

**Error Message**

Parameter check failed.

**Description**

Parameter check failed.

**Possible Causes**

The entered parameter value exceeds the allowed range of a specification, for example, length or value.

**Solution**

Checks whether the entered parameter values are within the supported ranges.

## 17620004 Invalid Function Call

**Error Message**

Invalid function call.

**Description**

Invalid function call.

**Possible Causes**

This operation is not supported by the current function.

**Solution**

Check whether the function is properly called.

## 17630001 Cryptographic Operation Error

**Error Message**

Crypto operation error.

**Description**

A cryptographic operation error occurs.

**Possible Causes**

An error occurs when the cryptography framework interacts with a third-party algorithm library.

**Solution**

Check whether the input parameters of the API or associated APIs are correct.

Error 17630001 is often reported during decryption, which is analyzed in detail based on typical scenarios.

### Failed to Call doFinal During Decryption Using AES-GCM

**Symptom**

**doFinal** fails to be called during decryption using AES-GCM, and error code 17630001 is returned.

> **NOTE**
>
> - You are advised to use the **update** API to encrypt data and call the **doFinal** API to complete the encryption and obtain the tag.
> - You are advised to use the **update** API to decrypt data and then call the **doFinal** API to complete the decryption. The **doFinal** API verifies the tag. If the verification fails, an exception is thrown.

**Possible Causes**

If **doFinal** fails, the tag verification fails because the input value of **tag** for decryption is inconsistent with that of **tag** calculated during decryption. If any of the input values of **key**, **iv**, **aad**, **tag**, and **ciphertext** for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

2. If **iv** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

3. If **aad** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

4. If **ciphertext** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

5. If **tag** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

**Solution**

Ensure that the **key**, **iv**, and **aad** parameters for encryption and decryption are the same, and the **ciphertext** and **tag** input during decryption are correct.

### Failed to Call doFinal During Decryption Using AES-CBC

**Symptom**

**doFinal** fails to be called during decryption, and error code 17630001 is returned.

> **NOTE**
>
> AES-CBC is a block cipher algorithm, so it requires the padding algorithm PKCS #7 to pad the plaintext to an integer multiple of the block size.
>
> During decryption, the **doFinal** API verifies the padding.

**Possible Causes**

If **doFinal** fails, the padding fails to be verified. **doFinal** decrypts the last block of ciphertext data and verifies whether the padding is valid. If any of the input values of **key**, **iv**, and **ciphertext** for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the padding verification fails.

2. If **iv** is incorrect, the complete ciphertext length is 16 bytes, **update** has no output, and **doFinal** fails. That is, the padding verification fails. If the complete ciphertext length is an integer multiple of 16 bytes (excluding 16 bytes), the plaintext obtained by **update** is partially correct, and **doFinal** is successful.

3. If **ciphertext** is incorrect, the last or second-to-last ciphertext block is incorrect, the plaintext obtained by **update** is partially correct (or no output is generated), and **doFinal** fails. That is, the padding verification fails. If other ciphertext blocks are incorrect, the plaintext obtained by **update** is partially correct, and **doFinal** is successful.

**Solution**

Ensure that the **key** and **iv** parameters for encryption and decryption are the same, and the **ciphertext** input during decryption is correct.

### Failed to Call doFinal During Decryption Using AES-CCM

**Symptom**

**doFinal** fails to be called during decryption using AES-CCM, and error code 17630001 is returned.

> **NOTE**
>
> - AES-CCM is an authentication and encryption mode. During encryption and decryption, the additional authentication data (AAD) and authentication tag must be specified. The length of AAD must be within the range of [1, 2048], in bytes.
> - You are advised to use the **update** API to encrypt data and call the **doFinal** API to complete the encryption and obtain the tag.
> - You are advised to use the **update** API to decrypt data and then call the **doFinal** API to complete the decryption. The **doFinal** API verifies the tag. If the verification fails, an exception is thrown.

**Possible Causes**

If **doFinal** fails, the tag verification fails because the input value of **tag** for decryption is inconsistent with that of **tag** calculated during decryption. If any of the input values of **key**, **iv**, **aad**, **tag**, and **ciphertext** for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

2. If **iv** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

3. If **aad** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

4. If **ciphertext** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

5. If **tag** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

**Solution**

Ensure that the **key**, **iv**, and **aad** parameters for encryption and decryption are the same, and the **ciphertext** and **tag** input during decryption are correct.

### Failed to Call doFinal During Decryption Using AES-ECB

**Symptom**

**doFinal** fails to be called during decryption using AES-ECB, and error code 17630001 is returned.

> **NOTE**
>
> AES-ECB is a block cipher algorithm with a block size of 128 bits (16 bytes). Therefore, it requires the padding algorithm PKCS #7 to pad the plaintext to an integer multiple of the block size.
>
> During decryption, the **doFinal** API verifies the padding.

**Possible Causes**

If **doFinal** fails, the padding fails to be verified. **doFinal** decrypts the last block of ciphertext data and verifies whether the padding is valid. If any of the input values of **key** and **ciphertext** for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the padding verification fails.

2. If **ciphertext** is incorrect, the last ciphertext block is incorrect, the plaintext obtained by **update** is partially correct, and **doFinal** fails. That is, the padding verification fails. If other ciphertext blocks are incorrect, the plaintext obtained by **update** is partially correct, and **doFinal** is successful.

3. If the length of **ciphertext** is not an integer multiple of 16 bytes (block size) when PKCS #7 is used for padding, **doFinal** fails.

**Solution**

Ensure that the **key** parameter for encryption and decryption is the same, the input value of **ciphertext** during decryption is correct, and the length of the ciphertext is an integer multiple of the block size (16 bytes).

### Failed to Call doFinal During Decryption Using DES/3DES

**Symptom**

**doFinal** fails to be called during decryption using DES or 3DES, and error code 17630001 is returned.

> **NOTE**
>
> DES and 3DES are block cipher algorithms, with a fixed block size of 64 bits (8 bytes). In ECB and CBC modes, the plaintext must be padded if its length is not an integer multiple of 64 bits.
>
> During decryption, the **doFinal** API verifies the padding.
>
> In **NoPadding** mode, if the **key**, **iv**, or ciphertext is incorrect, but the length meets the requirements, decryption can still succeed, but the obtained plaintext will be incorrect.

**Possible Causes**

If **doFinal** fails, the padding fails to be verified. This error may occur if the input value of **key** for decryption is incorrect (the length is correct but the key value is incorrect) or the **ciphertext** is incorrect.

1. If **key** is incorrect, and the plaintext obtained by **update** is incorrect, **doFinal** fails. The DES key should be of 8 bytes, and the 3DES key should be of 24 bytes.

2. If **iv** is incorrect, only the decryption of the first ciphertext block is affected in CBC or CFB mode, the plaintext obtained by **update** is incorrect, but **doFinal** is successful. OFB is a stream cipher algorithm. If **iv** is incorrect in OFB mode, all plaintexts are incorrect, but **doFinal** is still successful. In CBC, OFB, or CFB mode, **iv** should be of 8 bytes.

3. If **ciphertext** is incorrect, and the last ciphertext block is incorrect in ECB mode or the last or the second-to-last ciphertext block is incorrect in CBC mode, **doFinal** fails, that is, padding verification fails. If other ciphertext blocks are incorrect, **doFinal** is successful, but the obtained plaintext is incorrect.

4. If the length of **ciphertext** is not an integer multiple of 8 bytes (block size) when PKCS #7 is used for padding, **doFinal** fails.

**Solution**

Ensure that the **key** and **iv** parameters for encryption and decryption are the same, and the **ciphertext** input during decryption is correct. The DES key has a length of 8 bytes, and the 3DES key has a length of 24 bytes.

### Failed to Call doFinal During Decryption Using SM4-GCM

**Symptom**

**doFinal** fails to be called during decryption using SM4-GCM, and error code 17630001 is returned.

> **NOTE**
>
> - SM4-GCM is an authentication and encryption mode. During encryption and decryption, the additional authentication data (AAD) and authentication tag must be specified.
> - You are advised to use the **update** API to encrypt data and call the **doFinal** API to complete the encryption and obtain the tag.
> - You are advised to use the **update** API to decrypt data and then call the **doFinal** API to complete the decryption. The **doFinal** API verifies the tag. If the verification fails, an exception is thrown.

**Possible Causes**

If **doFinal** fails, the tag verification fails because the input value of **tag** for decryption is inconsistent with that of **tag** calculated during decryption. If any of the input values of **key**, **iv**, **aad**, **tag**, and **ciphertext** for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

2. If **iv** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

3. If **aad** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

4. If **ciphertext** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

5. If **tag** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

**Solution**

Ensure that the **key**, **iv**, and **aad** parameters for encryption and decryption are the same, and the **ciphertext** and **tag** input during decryption are correct.

### Failed to Call doFinal During Decryption Using SM4-ECB/CBC

**Symptom**

**doFinal** fails to be called during decryption using SM4-ECB or SM4-CBC, and error code 17630001 is returned.

> **NOTE**
>
> SM4 is a block cipher algorithm, with a fixed block size of 128 bits. In ECB and CBC modes, the plaintext must be padded if its length is not an integer multiple of 128 bits.
>
> During decryption, the **doFinal** API verifies the padding.

**Possible Causes**

If **doFinal** fails, the padding fails to be verified. If any of the input values of **key** and **ciphertext** for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the padding verification fails. The SM4 key should be of 16 bytes.

2. If **iv** is incorrect, only the decryption of the first ciphertext block is affected, the plaintext obtained by **update** is incorrect, but **doFinal** is successful. The **iv** value should be of 16 bytes in CBC mode.

3. If **ciphertext** is incorrect, and the last ciphertext block is incorrect in ECB mode or the last or the second-to-last ciphertext block is incorrect in CBC mode, **doFinal** fails, that is, padding verification fails. If other ciphertext blocks are incorrect, **doFinal** is successful, but the obtained plaintext is incorrect.

4. If the length of **ciphertext** is not an integer multiple of 16 bytes (block size) when PKCS #7 is used for padding, **doFinal** fails.

**Solution**

Ensure that the **key** and **iv** parameters for encryption and decryption are the same, and the **ciphertext** input during decryption is correct. The length of the SM4 key should be 16 bytes (128 bits).

### Failed to Call doFinal During Decryption Using ChaCha20-Poly1305

**Symptom**

**doFinal** fails to be called during decryption using ChaCha20-Poly1305, and error code 17630001 is returned.

> **NOTE**
>
> - ChaCha20-Poly1305 is an authentication and encryption mode. During encryption and decryption, the additional authentication data (AAD) and authentication tag must be specified.
> - You are advised to use the **update** API to encrypt data and call the **doFinal** API to complete the encryption and obtain the tag.
> - You are advised to use the **update** API to decrypt data and then call the **doFinal** API to complete the decryption. The **doFinal** API verifies the tag. If the verification fails, an exception is thrown.

**Possible Causes**

If **doFinal** fails, the tag verification fails because the input value of **tag** for decryption is inconsistent with that of **tag** calculated during decryption. If any of the input values of **key**, **nonce** (IV), **aad**, **tag**, and **ciphertext** for decryption is incorrect, this error is reported.

1. If **key** is incorrect (with correct length but incorrect value), the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

2. If **nonce** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails. The **nonce** value should be of 12 bytes.

3. If **aad** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

4. If **ciphertext** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

5. If **tag** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

**Solution**

Ensure that the **key**, **nonce**, and **aad** parameters for encryption and decryption are the same, and the **ciphertext** and **tag** input during decryption are correct.