# oh_rdb_crypto_param.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=17e4b320c8985512791b8b37fea849963e9ff387 translatedAt=2026-09-04T02:51:25.897Z pushedAt=2026-09-09T09:11:03.648Z -->

## Overview

Defines functions and enums related to encryption parameters of the RDB store.

**File to include**: <database/rdb/oh_rdb_crypto_param.h>

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 20

**Related module**: [RDB](capi-rdb.md)

## Summary

### Structs

| Name                                            | typedef Keyword     | Description                                |
| ------------------------------------------------ | ------------------ | ------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) | OH_Rdb_CryptoParam | Defines the encryption parameters used to open an encrypted database.|

### Enums

| Name                                     | typedef Keyword     | Description                        |
| ----------------------------------------- | ------------------ | ---------------------------- |
| [Rdb_EncryptionAlgo](#rdb_encryptionalgo) | Rdb_EncryptionAlgo | Enumerates database encryption algorithms.            |
| [Rdb_HmacAlgo](#rdb_hmacalgo)             | Rdb_HmacAlgo       | Enumerates HMAC algorithms.|
| [Rdb_KdfAlgo](#rdb_kdfalgo)               | Rdb_KdfAlgo        | Enumerates KDF algorithms. |

### Functions

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam *OH_Rdb_CreateCryptoParam(void)](#oh_rdb_createcryptoparam) | Creates an [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| [int OH_Rdb_DestroyCryptoParam(OH_Rdb_CryptoParam *param)](#oh_rdb_destroycryptoparam) | Destroys an [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| [int OH_Crypto_SetEncryptionKey(OH_Rdb_CryptoParam *param, const uint8_t *key, int32_t length)](#oh_crypto_setencryptionkey) | Sets the key data of an [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| [int OH_Crypto_SetIteration(OH_Rdb_CryptoParam *param, int64_t iteration)](#oh_crypto_setiteration) | Sets the number of iterations of the KDF algorithm used when opening an encrypted database.                 |
| [int OH_Crypto_SetEncryptionAlgo(OH_Rdb_CryptoParam *param, int32_t algo)](#oh_crypto_setencryptionalgo) | Sets the encryption algorithm used when opening an encrypted database.                        |
| [int OH_Crypto_SetHmacAlgo(OH_Rdb_CryptoParam *param, int32_t algo)](#oh_crypto_sethmacalgo) | Sets the HMAC algorithm used when opening an encrypted database.                        |
| [int OH_Crypto_SetKdfAlgo(OH_Rdb_CryptoParam *param, int32_t algo)](#oh_crypto_setkdfalgo) | Sets the KDF algorithm used when opening an encrypted database.                         |
| [int OH_Crypto_SetCryptoPageSize(OH_Rdb_CryptoParam *param, int64_t size)](#oh_crypto_setcryptopagesize) | Sets the page size used when opening an encrypted database.                          |

## Enum Description

### Rdb_EncryptionAlgo

```c
enum Rdb_EncryptionAlgo
```

**Description**

Enumerates database encryption algorithms.

**Since**: 20

| Enum Item             | Description                               |
| ------------------- | ----------------------------------- |
| RDB_AES_256_GCM = 0 | RDB_AES_256_GCM.|
| RDB_AES_256_CBC     | RDB_AES_256_CBC.|
| RDB_PLAIN_TEXT | No encryption is required.<br>**Since**: 22|

### Rdb_HmacAlgo

```c
enum Rdb_HmacAlgo
```

**Description**

Enumerates HMAC algorithms.

**Since**: 20

| Enum Item           | Description                 |
| ----------------- | --------------------- |
| RDB_HMAC_SHA1 = 0 | RDB_HMAC_SHA1.  |
| RDB_HMAC_SHA256   | RDB_HMAC_SHA256.|
| RDB_HMAC_SHA512   | RDB_HMAC_SHA512.|

### Rdb_KdfAlgo

```c
enum Rdb_KdfAlgo
```

**Description**

Enumerates KDF algorithms.

**Since**: 20

| Enum Item          | Description                |
| ---------------- | -------------------- |
| RDB_KDF_SHA1 = 0 | RDB_KDF_SHA1.  |
| RDB_KDF_SHA256   | RDB_KDF_SHA256.|
| RDB_KDF_SHA512   | RDB_KDF_SHA512.|


## Function Description

### OH_Rdb_CreateCryptoParam()

```c
OH_Rdb_CryptoParam *OH_Rdb_CreateCryptoParam(void)
```

**Description**

Creates an [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.

**Since**: 20

**Returns**

| Type                                            | Description                                                        |
| ------------------------------------------------ | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) * | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance on success.<br>Otherwise, **nullptr** is returned. After use, the memory must be released through the [OH_Rdb_DestroyCryptoParam](capi-oh-rdb-crypto-param-h.md#oh_rdb_destroycryptoparam) API. |

### OH_Rdb_DestroyCryptoParam()

```c
int OH_Rdb_DestroyCryptoParam(OH_Rdb_CryptoParam *param)
```

**Description**

Destroys an [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.

**Since**: 20


**Parameters**

| Name                                                 | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Crypto_SetEncryptionKey()

```c
int OH_Crypto_SetEncryptionKey(OH_Rdb_CryptoParam *param, const uint8_t *key, int32_t length)
```

**Description**

Sets the key data of an [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.

**Since**: 20


**Parameters**

| Name                                                 | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| const uint8_t *key                                      | Pointer to the key data.                                     |
| int32_t length                                          | Size of the key array.                                        |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For detailed information, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Crypto_SetIteration()

```c
int OH_Crypto_SetIteration(OH_Rdb_CryptoParam *param, int64_t iteration)
```

**Description**

Sets the number of iterations of the KDF algorithm used when opening an encrypted database.

**Since**: 20


**Parameters**

| Name                                                 | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| int64_t iteration                                       | Number of iterations.                                              |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For detailed information, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Crypto_SetEncryptionAlgo()

```c
int OH_Crypto_SetEncryptionAlgo(OH_Rdb_CryptoParam *param, int32_t algo)
```

**Description**

Sets the encryption algorithm used when opening an encrypted database.

**Since**: 20


**Parameters**

| Name                                                 | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| int32_t algo                                            | Encryption algorithm. The value must be one of the enum values of [Rdb_EncryptionAlgo](#rdb_encryptionalgo). |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For detailed information, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Crypto_SetHmacAlgo()

```c
int OH_Crypto_SetHmacAlgo(OH_Rdb_CryptoParam *param, int32_t algo)
```

**Description**

Sets the HMAC algorithm used when opening an encrypted database.

**Since**: 20


**Parameters**

| Name                                                 | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| int32_t algo                                            | HMAC algorithm. The value must be one of the enum values of [Rdb_HmacAlgo](#rdb_hmacalgo). |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Crypto_SetKdfAlgo()

```c
int OH_Crypto_SetKdfAlgo(OH_Rdb_CryptoParam *param, int32_t algo)
```

**Description**

Sets the KDF algorithm used when opening an encrypted database.

**Since**: 20


**Parameters**

| Name                                                 | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| int32_t algo                                            | KDF algorithm. The value must be one of the enum values of [Rdb_KdfAlgo](#rdb_kdfalgo). |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For detailed information, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Crypto_SetCryptoPageSize()

```c
int OH_Crypto_SetCryptoPageSize(OH_Rdb_CryptoParam *param, int64_t size)
```

**Description**

Sets the page size used when opening an encrypted database.

**Since**: 20


**Parameters**

| Name                                                 | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Pointer to the [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) instance.|
| int64_t size                                            | Page size, in bytes. The value must be a power of 2, with a minimum value of 1024 and a maximum value of 65536. |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For detailed information, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

