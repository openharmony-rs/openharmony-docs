# tee_crypto_hal.h

## Overview

Provides APIs for cryptographic operations.<br> You can use these APIs to implement encryption and decryption.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Enum

| Name | Description |
| -- | -- |
| [CRYPTO_ENGINE](#crypto_engine) | Enumerates the types of the crypto engine. |

### Function

| Name | Description |
| -- | -- |
| [TEE_Result TEE_SetCryptoFlag(TEE_OperationHandle operation, uint32_t crypto)](#tee_setcryptoflag) | Sets the encryption and decryption engines to an operation. |
| [TEE_Result TEE_SetObjectFlag(TEE_ObjectHandle object, uint32_t crypto)](#tee_setobjectflag) | Sets the encryption and decryption engines to an object. |

## Enum type description

### CRYPTO_ENGINE

```c
enum CRYPTO_ENGINE
```

**Description**

Enumerates the types of the crypto engine.

**Since**: 20

| Enum item | Description |
| -- | -- |
| DX_CRYPTO = 0 | The hardware-based DX crypto engine. |
| EPS_CRYPTO = 1 | The hardware-based MSPE crypto engine. |
| SOFT_CRYPTO = 2 | The software-based crypto engine, such as OpenSSL. |
| SEC_CRYPTO = 3 | The SEC crypto engine, commonly employed in vehicle platforms. |
| CRYPTO_ENGINE_MAX = 1024 | The maximum value of the crypto engine. |


## Function description

### TEE_SetCryptoFlag()

```c
TEE_Result TEE_SetCryptoFlag(TEE_OperationHandle operation, uint32_t crypto)
```

**Description**

Sets the encryption and decryption engines to an operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the handle of the operation to set. |
| uint32_t crypto | Indicates the engines to set. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if <b>operation</b> is null or <b>crypto</b> is invalid. |

### TEE_SetObjectFlag()

```c
TEE_Result TEE_SetObjectFlag(TEE_ObjectHandle object, uint32_t crypto)
```

**Description**

Sets the encryption and decryption engines to an object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_ObjectHandle object | Indicates the handle of the object to set. |
| uint32_t crypto | Indicates the engines to set. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if <b>object</b> is null or <b>crypto</b> is invalid. |


