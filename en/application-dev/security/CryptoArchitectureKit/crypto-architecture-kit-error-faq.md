# Encryption/Decryption Failure in Crypto Architecture Kit with Error Code 17630001

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=084bf627297e60b1f406ce34f5b473174466f7b3 translatedAt=2026-07-15T02:43:59.692Z pushedAt=2026-07-15T08:58:23.792Z -->

You may often encounter error 17630001 when using Crypto Architecture Kit. The following sections provide a detailed analysis of the failure causes.

## AES-GCM Algorithm

**Symptom**

When decrypting with AES-GCM, calling **doFinal** fails and returns error code 17630001.

> **NOTE**
>
> It is recommended that you use the update API to encrypt data and finally call the **doFinal** API to complete the current encryption and obtain the tag.
>
> It is recommended that you use the update API to decrypt data and finally call the **doFinal** API to complete the current decryption. The **doFinal** API will verify the tag internally, and if the verification fails, the API will throw an exception.

**Possible Causes**

**doFinal** failure indicates tag verification failure, meaning that the tag in the decryption input is inconsistent with the tag computed during decryption. An incorrect value in any of the parameters **key**, **iv**, **aad**, **tag**, and **ciphertext** may cause this error.

1. **key** is incorrect, the resulting plaintext from **update** is incorrect, and **doFinal** fails, indicating that tag verification fails.

2. **iv** is incorrect. The plaintext obtained by **update** is incorrect, and **doFinal** fails, indicating that tag verification fails.

3. **aad** is incorrect. The plaintext obtained by **update** is correct, but **doFinal** fails, indicating that tag verification fails.

4. **ciphertext** is incorrect. The plaintext obtained by **update** is incorrect, and **doFinal** fails, indicating that tag verification fails.

5. **tag** is incorrect. The plaintext obtained by **update** is correct, but **doFinal** fails, indicating that tag verification fails.

**Solution**

Ensure that the **key**, **iv**, and **aad** parameters are consistent between encryption and decryption, and verify that the **ciphertext** and **tag** used as decryption input are correct.

## AES-CBC Algorithm

**Symptom**

When **doFinal** is called during decryption, it fails and returns error code 17630001.

> **NOTE**
>
> AES-CBC is a block cipher algorithm, so the PKCS7 padding algorithm is required to pad the plaintext to an integer multiple of the block size.
>
> During decryption, the **doFinal** API validates the padding.

**Possible Causes**

A **doFinal** failure indicates that padding validation has failed. **doFinal** decrypts the last block of ciphertext data and checks whether the padding is valid. An incorrect value in any of the parameters **key**, **iv**, and **ciphertext** may cause this error.

1. **key** is incorrect: the plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning padding validation fails.

2. **iv** is incorrect. If the complete ciphertext length is 16 bytes, update produces no output and **doFinal** fails, meaning padding verification fails. If the complete ciphertext length is an integer multiple of 16 bytes (excluding 16 bytes), the plaintext obtained by **update** is partially correct and **doFinal** succeeds.

3. **ciphertext** is incorrect. If the last or second-to-last ciphertext block is erroneous, the plaintext obtained by **update** is partially correct (or there is no output) and **doFinal** fails, meaning padding verification fails. If any other ciphertext block is erroneous, the plaintext obtained by **update** is partially correct and **doFinal** succeeds.

**Solution**

Ensure that the key and **iv** parameters are consistent between encryption and decryption, and verify that the input **ciphertext** for decryption is correct.

## AES-CCM Algorithm

**Symptom**

When calling **doFinal** during AES-CCM decryption, the operation fails and error code 17630001 is returned.

> **NOTE**
>
> AES-CCM is an authenticated encryption mode. During encryption and decryption, you need to specify additional authentication data (**aad**, which must be at least 1 byte and at most 2048 bytes in length) and an authentication tag.
>
> You are advised to use the **update** API to encrypt data, and then call the **doFinal** API to complete the current encryption and obtain the tag.
>
> You are advised to use the **update** API to decrypt data, and then call the **doFinal** API to complete the current decryption. The **doFinal** API will verify the tag internally. If the verification fails, the API throws an exception.

**Possible Causes**

A **doFinal** failure indicates that tag verification has failed, meaning the tag provided as decryption input is inconsistent with the tag computed during the decryption process. Any incorrect value among the decryption input parameters **key**, **iv**, **aad**, **tag**, or **ciphertext** will cause this error.

**key** is incorrect: The plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning tag verification fails.

**iv** is incorrect: The plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning tag verification fails.

**aad** is incorrect: The plaintext obtained from **update** is correct, but **doFinal** fails, meaning tag verification fails.

**ciphertext** is incorrect: The plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning tag verification fails.

**tag** is incorrect: The plaintext obtained from **update** is correct, but **doFinal** fails, meaning tag verification fails.

**Solution**

Ensure that the **key**, **iv**, and **aad** parameters are consistent between encryption and decryption, and verify that the **ciphertext** and **tag** input during decryption are correct.

## AES-ECB Algorithm

**Symptom**

When AES-ECB decryption calls **doFinal**, it fails and returns error code 17630001.

> **NOTE**
>
> AES-ECB is a block cipher algorithm with a block length of 128 bits (16 bytes). Therefore, the PKCS7 padding algorithm is required to pad the plaintext to an integer multiple of the block size.
>
> During decryption, the **doFinal** API verifies the padding.

**Possible Causes**

A **doFinal** failure indicates that padding verification has failed. **doFinal** decrypts the last block of ciphertext data and checks whether the padding is valid. If either **key** or **ciphertext** in the decryption input is incorrect, this error may occur.

**key** is incorrect: The plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning padding verification fails.

**ciphertext** is incorrect: If the last ciphertext block is erroneous, the plaintext obtained from **update** is partially correct, and **doFinal** fails, meaning padding verification fails. If other ciphertext blocks are erroneous, the plaintext obtained from **update** is partially correct, and **doFinal** succeeds.

**ciphertext** length is not an integer multiple of 16 bytes (block size) (when PKCS7 padding is used), and **doFinal** fails.

**Solution**

Ensure that the key parameters for encryption and decryption are consistent, the **ciphertext** input during decryption is correct, and the ciphertext length is an integer multiple of the block size (16 bytes).

## DES/3DES Algorithm

**Symptom**

When decrypting with DES or 3DES, calling **doFinal** fails and returns error code 17630001.

> **NOTE**
>
> DES/3DES is a block cipher with a block length of 64 bits (8 bytes). In ECB and CBC modes, if the plaintext length is not an integer multiple of 64 bits, a padding method must be used to fill the gap.
>
> During decryption, the **doFinal** API verifies the padding.
>
> If **NoPadding** mode is used and the **key**, **iv**, or ciphertext is incorrect (while all lengths meet the requirements), decryption can still succeed, but the resulting plaintext will be incorrect.

**Possible Causes**

A **doFinal** failure indicates that **padding** verification fails. An incorrect key content in the decryption input (the key length is correct but the key value is wrong) or an incorrect **ciphertext** may both cause this error.

1. The key content is incorrect (a DES key should be 8 bytes, and a 3DES key should be 24 bytes): The plaintext obtained from update is incorrect, and **doFinal** fails.

2. Incorrect **iv** (the **iv** is 8 bytes in CBC/OFB/CFB modes): In CBC and CFB modes, only the decryption of the first ciphertext block is affected, the plaintext obtained from update is partially incorrect, and **doFinal** succeeds. OFB is a stream cipher, so an incorrect **iv** will cause all plaintext to be incorrect, but **doFinal** still succeeds.

3. Incorrect ciphertext: If the last ciphertext block in ECB mode is erroneous, or the last and second-to-last ciphertext block in CBC mode is erroneous, **doFinal** fails, meaning padding verification fails. If other ciphertext blocks are erroneous, **doFinal** succeeds, but the resulting plaintext is incorrect.

4. The ciphertext length is not an integer multiple of 8 bytes (the block size) when PKCS7 padding is used, causing **doFinal** to fail.

**Solution**

Ensure that the **key** and **iv** parameters are consistent between encryption and decryption, and verify that the ciphertext input for decryption is correct. The DES key length is 8 bytes, and the 3DES key length is 24 bytes.

## SM4-GCM Algorithm

**Symptom**

When SM4-GCM decryption calls **doFinal**, it fails and returns error code 17630001.

> **NOTE**
>
> SM4-GCM is an authenticated encryption mode. During encryption/decryption, you need to specify the additional authentication data (**aad**) and authentication **tag**.
>
> You are advised to use the update API to encrypt data and finally call the **doFinal** API to complete the current encryption and obtain the tag.
>
> You are advised to use the **update** API to decrypt data and finally call the **doFinal** API to complete the current decryption. The **doFinal** API will verify the tag internally, and if verification fails, the API will throw an exception.

**Possible Causes**

**doFinal** failure indicates that tag verification has failed, meaning the tag in the decryption input is inconsistent with the tag computed during decryption. An incorrect value in any of the parameters **key**, **iv**, **aad**, **tag**, and **ciphertext** may cause this error.

1. The key is incorrect, the resulting plaintext from update is incorrect, and doFinal fails, meaning tag verification fails.

2. The iv is incorrect, the resulting plaintext from update is incorrect, and doFinal fails, that is, tag verification fails.

3. The aad is incorrect, the resulting plaintext from update is correct, but doFinal fails, that is, tag verification fails.

4. The ciphertext is incorrect, the resulting plaintext from update is incorrect, and doFinal fails, that is, tag verification fails.

5. The tag is incorrect, the resulting plaintext from update is correct, but doFinal fails, that is, tag verification fails.

**Solution**

Ensure that the **key**, **iv**, and **aad** parameters are consistent between encryption and decryption, and verify that the ciphertext and tag input during decryption are correct.

## SM4-ECB/CBC Algorithm

**Symptom**

When calling **doFinal** for SM4-ECB or SM4-CBC decryption, it fails and returns error code 17630001.

> **NOTE**
>
> SM4 is a block cipher algorithm with a block length of 128 bits. In ECB and CBC modes, when the plaintext length is not an integer multiple of 128 bits, a padding method must be used to fill the gap.
>
> During decryption, the **doFinal** API verifies the padding.

**Possible Causes**

A **doFinal** failure indicates that **padding** verification has failed. An incorrect value in any of the parameters **key** or **ciphertext** may cause this error.

**key** is incorrect (an SM4 key should be 16 bytes): the plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning padding verification fails.

**iv** is incorrect (the iv is 16 bytes in CBC mode): it only affects the decryption of the first ciphertext block. The plaintext obtained from **update** is partially incorrect, and **doFinal** succeeds.

**ciphertext** is incorrect. In ECB mode, if the last ciphertext block is erroneous, or in CBC mode, if the second-to-last or last ciphertext block is erroneous, **doFinal** fails, meaning padding verification fails. If other ciphertext blocks are erroneous, **doFinal** succeeds, but the plaintext obtained from **update** is incorrect.

**ciphertext** length is not an integer multiple of 16 bytes (block size) (when PKCS7 padding is used), and **doFinal** fails.

**Solution**

Ensure that the **key** and **iv** parameters are consistent between encryption and decryption, and verify that the **ciphertext** input during decryption is correct. The SM4 key length is 16 bytes (128 bits).

## ChaCha20-Poly1305 Algorithm

**Symptom**

When decrypting with ChaCha20-Poly1305, calling **doFinal** fails and returns error code 17630001.

> **NOTE**
>
> ChaCha20-Poly1305 is an authenticated encryption mode. During encryption and decryption, you need to specify the additional authentication data (aad) and the authentication tag.
>
> You are advised to use the update API to encrypt data, and finally call the **doFinal** API to complete the current encryption and obtain the tag.
>
> You are advised to use the update API to decrypt data, and finally call the **doFinal** API to complete the current decryption. The **doFinal** API will verify the tag internally. If the verification fails, the API will throw an exception.

**Possible Causes**

A **doFinal** failure indicates that tag verification has failed, meaning the tag provided as decryption input does not match the tag computed during decryption. An incorrect value in any of the parameters **key**, **nonce (IV)**, **aad**, **tag**, and **ciphertext** may cause this error.

**key** is incorrect (the key length is correct, but the key content is wrong): The plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning tag verification fails.

**nonce** is incorrect (**nonce** is 12 bytes): The plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning tag verification fails.

**aad** is incorrect: The plaintext obtained from **update** is correct, but **doFinal** fails, meaning tag verification fails.

**ciphertext** is incorrect: The plaintext obtained from **update** is incorrect, and **doFinal** fails, meaning tag verification fails.

**tag** is incorrect: The plaintext obtained from **update** is correct, but **doFinal** fails, meaning tag verification fails.

**Solution**

Ensure that the **key**, **nonce**, and **aad** parameters are consistent between encryption and decryption, and verify that the ciphertext and tag input during decryption are correct.