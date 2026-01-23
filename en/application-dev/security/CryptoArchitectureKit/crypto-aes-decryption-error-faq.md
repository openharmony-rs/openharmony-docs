# AES Decryption Failure Returning 17630001

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

When using the encryption and decryption algorithm library, developers often encounter symmetric algorithm decryption error 17630001. The following describes the failure causes in detail.

## AES-GCM Algorithm

**Symptom**

During AES decryption, **doFinal** fails to be called, and error code 17630001 is returned. As a result, the correct plaintext cannot be obtained.

> **NOTE**
>
> You are advised to use the **update** API to encrypt data and call the **doFinal** API to complete the encryption and obtain the tag.
>
> You are advised to use the **update** API to decrypt data and then call the **doFinal** API to complete the decryption. The **doFinal** API verifies the tag. If the verification fails, an exception is thrown.

**Possible Causes**

If **doFinal** fails, the tag verification fails because the **tag** input for decryption is inconsistent with the tag calculated during decryption. If any of the **key**, **iv**, **aad**, **tag**, and **ciphertext** input for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

2. If **iv** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

3. If **aad** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

4. If **ciphertext** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the tag verification fails.

5. If **tag** is incorrect, the plaintext obtained by **update** is correct, and **doFinal** fails. That is, the tag verification fails.

**Solution**

Ensure that the **key**, **iv**, and **aad** parameters for encryption and decryption are the same, and the **ciphertext** and **tag** input during decryption are correct.

## AES-CBC Algorithm

**Symptom**

During decryption, **doFinal** fails to be called, and error code 17630001 is returned. As a result, the correct plaintext cannot be obtained.

> **NOTE**
>
> AES-CBC is a block cipher algorithm, so it requires the padding algorithm PKCS7 padding to pad the plaintext to an integer multiple of the block size.
>
> During decryption, the **doFinal** API verifies the padding.

**Possible Causes**

If **doFinal** fails, the padding fails to be verified. **doFinal** decrypts the last block of ciphertext data and verifies whether the padding is valid. If any of the **key**, **iv**, and **ciphertext** input for decryption is incorrect, this error is reported.

1. If **key** is incorrect, the plaintext obtained by **update** is incorrect, and **doFinal** fails. That is, the padding verification fails.

2. If **iv** is incorrect, the complete ciphertext length is 16 bytes, **update** has no output, and **doFinal** fails. That is, the padding verification fails. If the complete ciphertext length is not 16 bytes (multiple of 16), the plaintext obtained by **update** is partially correct, and **doFinal** is successful.

3. If **ciphertext** is incorrect, the last or second-to-last ciphertext block is incorrect, the plaintext obtained by **update** is partially correct (or no output is generated), and **doFinal** fails. That is, the padding verification fails. If other ciphertext blocks are incorrect, the plaintext obtained by **update** is partially correct, and **doFinal** is successful.

**Solution**

Ensure that the **key** and **iv** parameters for encryption and decryption are the same, and the **ciphertext** input during decryption is correct.
