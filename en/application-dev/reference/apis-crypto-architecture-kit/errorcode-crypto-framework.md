# Crypto Framework Error Codes

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=d21d1cbfb7ea850ec5b69c0f309f5ed8cc8aa9c3 translatedAt=2026-06-10T06:05:55.048Z pushedAt=2026-06-10T10:59:32.526Z -->

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

## 17620002 Parameter Conversion Between ArkTS and C Failed

**Error Message**

Failed to convert parameters between arkts and c.

**Description**

The parameter conversion between ArkTS and C failed.

**Possible Causes**

An unexpected error occurred.

**Solution**

Check whether the system is running properly.

## 17620003 Parameter Verification Failed

**Error Message**

Parameter check failed.

**Description**

Parameter verification failed.

**Possible Causes**

The input parameter is out of the specified range, such as the length or value.

**Solution**

Checks whether the entered parameter values are within the supported ranges.

## 17630001 Crypto Operation Error

**Error Message**

Crypto operation error.

**Description**

Failed to call the third-party cryptographic API.

**Possible Causes**

An error occurs when the cryptography framework interacts with a third-party algorithm library.

**Solution**

Check whether the input parameters of the API or associated APIs are correct.

For details about AES decryption failure, see [AES Decryption Failure Returning 17630001](../../security/CryptoArchitectureKit/crypto-aes-decryption-error-faq.md).