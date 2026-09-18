# crypto_common.h

## Overview

Defines common data structures and error codes for crypto operations.

**Include**: <CryptoArchitectureKit/crypto_common.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoCommonApi](capi-cryptocommonapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) | Crypto_DataBlob | Crypto data structure. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Crypto_ErrCode](#oh_crypto_errcode) | OH_Crypto_ErrCode | Enumerates the error codes. |
| [Crypto_CipherMode](#crypto_ciphermode) | Crypto_CipherMode | Defines the cipher mode. |

### Function

| Name | Description |
| -- | -- |
| [void OH_Crypto_FreeDataBlob(Crypto_DataBlob *dataBlob)](#oh_crypto_freedatablob) | Frees the memory of a data blob. |

## Enum type description

### OH_Crypto_ErrCode

```c
enum OH_Crypto_ErrCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| CRYPTO_SUCCESS = 0 | Operation succeeded.<br>**Since**: 12 |
| CRYPTO_INVALID_PARAMS = 401 | Invalid input parameters.<br>**Since**: 12 |
| CRYPTO_NOT_SUPPORTED = 801 | Unsupported feature or algorithm.<br>**Since**: 12 |
| CRYPTO_MEMORY_ERROR = 17620001 | Memory operation failed.<br>**Since**: 12 |
| CRYPTO_PARAMETER_CHECK_FAILED = 17620003 | Parameter check failed.<br>**Since**: 20 |
| CRYPTO_INVALID_CALL = 17620004 | Invalid function call.<br>**Since**: 26.0.0 |
| CRYPTO_OPERTION_ERROR = 17630001 | Crypto operation error.<br>**Since**: 12 |

### Crypto_CipherMode

```c
enum Crypto_CipherMode
```

**Description**

Defines the cipher mode.

**Since**: 12

| Enum item | Description |
| -- | -- |
| CRYPTO_ENCRYPT_MODE = 0 | Encryption operation.<br>**Since**: 12 |
| CRYPTO_DECRYPT_MODE = 1 | Decryption operation.<br>**Since**: 12 |


## Function description

### OH_Crypto_FreeDataBlob()

```c
void OH_Crypto_FreeDataBlob(Crypto_DataBlob *dataBlob)
```

**Description**

Frees the memory of a data blob.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *dataBlob | [in] Data blob to free. |


