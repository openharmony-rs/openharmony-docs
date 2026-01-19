# Crypto Framework Error Codes

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 17620001 Memory Error

**Error Message**

Memory error.

**Description**

A memory error occurs.

**Possible Causes**

The memory allocation failed.

**Solution**

1. Check whether the system is running properly.
2. Check whether the service data is too long.

## 17620002 Runtime Error

**Error Message**

Runtime error.

**Description**

An external error occurs during running.

**Possible Causes**

An unexpected error occurs.

**Solution**

Check whether the system is running properly.

## 17630001 Crypto Operation Error

**Error Message**

Crypto operation error.

**Description**

Failed to invoke the third-party cryptographic API.

**Possible Causes**

An error occurs when the cryptography framework interacts with a third-party algorithm library.

**Solution**

Check whether the input parameters of the API or associated APIs are correct.

For details about AES decryption failure, see [AES Decryption Failure Returning 17630001](../../security/CryptoArchitectureKit/crypto-aes-decryption-error-faq.md).
<!--no_check-->