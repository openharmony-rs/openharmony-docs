# crypto_common.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=8f9fd014fa77f1d5efa7ff2975ef2ded59df0585 translatedAt=2026-11-10T07:58:53.816Z pushedAt=2026-11-10T11:15:53.369Z nl=1 -->

## **Overview**

Defines the common data structures and error codes for encryption and decryption.

**Header file**: <CryptoArchitectureKit/crypto_common.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoCommonApi](capi-cryptocommonapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) | Crypto_DataBlob | Defines the data used for encryption and decryption.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Crypto_ErrCode](#oh_crypto_errcode) | OH_Crypto_ErrCode | Enumerates the error codes. |
| [Crypto_CipherMode](#crypto_ciphermode) | Crypto_CipherMode | Defines the cipher mode. |

### Functions

| Name| Description|
| -- | -- |
| [void OH_Crypto_FreeDataBlob(Crypto_DataBlob *dataBlob)](#oh_crypto_freedatablob) | Releases the memory of BLOB. |

## Enum Description

### OH_Crypto_ErrCode

```c
enum OH_Crypto_ErrCode
```

**Description**

Enumerates the error codes.

| Enum Item| Description|
| -- | -- |
| CRYPTO_SUCCESS = 0 | The operation succeeded.<br>**Since:** 12 |
| CRYPTO_INVALID_PARAMS = 401 | The input parameter is invalid.<br>**Since:** 12 |
| CRYPTO_NOT_SUPPORTED = 801 | The function or algorithm is not supported.<br>**Since:** 12 |
| CRYPTO_MEMORY_ERROR = 17620001 | The memory operation failed.<br>**Since:** 12 |
| CRYPTO_PARAMETER_CHECK_FAILED = 17620003 | Parameter verification failed.<br>**Since:** 20 |
| CRYPTO_INVALID_CALL = 17620004 | Invalid function call.<br>**Since**: 26.0.0|
| CRYPTO_OPERTION_ERROR = 17630001 | The encryption or decryption operation failed.<br>**Since:** 12 |

### Crypto_CipherMode

```c
enum Crypto_CipherMode
```

**Description**

Defines the cipher mode.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CRYPTO_ENCRYPT_MODE = 0 | Encryption operation. |
| CRYPTO_DECRYPT_MODE = 1 | Decryption operation. |


## Function Description

### OH_Crypto_FreeDataBlob()

```c
void OH_Crypto_FreeDataBlob(Crypto_DataBlob *dataBlob)
```

**Description**

Releases the memory of BLOB.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *dataBlob | [in] Pointer to the data blob to be released. |


