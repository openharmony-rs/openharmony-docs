# oh_rdb_crypto_param.h

## Overview

Provides functions and enumerations related to cryptographic parameters of the relational database.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) | OH_Rdb_CryptoParam | Specifies the cryptographic parameters used when opening an encrypted database. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Rdb_EncryptionAlgo](#rdb_encryptionalgo) | Rdb_EncryptionAlgo | Enumerates the database encryption algorithms. |
| [Rdb_HmacAlgo](#rdb_hmacalgo) | Rdb_HmacAlgo | Enumerates the supported HMAC algorithm when opening a database. |
| [Rdb_KdfAlgo](#rdb_kdfalgo) | Rdb_KdfAlgo | Enumerates the supported KDF algorithm when opening a database. |

### Function

| Name | Description |
| -- | -- |
| [OH_Rdb_CryptoParam *OH_Rdb_CreateCryptoParam(void)](#oh_rdb_createcryptoparam) | Creates an OH_Rdb_CryptoParam instance object. |
| [int OH_Rdb_DestroyCryptoParam(OH_Rdb_CryptoParam *param)](#oh_rdb_destroycryptoparam) | Destroys an OH_Rdb_CryptoParam instance object. |
| [int OH_Crypto_SetEncryptionKey(OH_Rdb_CryptoParam *param, const uint8_t *key, int32_t length)](#oh_crypto_setencryptionkey) | Sets key data to the OH_Rdb_CryptoParam object. |
| [int OH_Crypto_SetIteration(OH_Rdb_CryptoParam *param, int64_t iteration)](#oh_crypto_setiteration) | Sets the number of KDF iterations used when opening an encrypted database. |
| [int OH_Crypto_SetEncryptionAlgo(OH_Rdb_CryptoParam *param, int32_t algo)](#oh_crypto_setencryptionalgo) | Sets the encryption algorithm when opening an encrypted database. |
| [int OH_Crypto_SetHmacAlgo(OH_Rdb_CryptoParam *param, int32_t algo)](#oh_crypto_sethmacalgo) | Sets the HMAC algorithm when opening an encrypted database. |
| [int OH_Crypto_SetKdfAlgo(OH_Rdb_CryptoParam *param, int32_t algo)](#oh_crypto_setkdfalgo) | Sets the KDF algorithm when opening an encrypted database. |
| [int OH_Crypto_SetCryptoPageSize(OH_Rdb_CryptoParam *param, int64_t size)](#oh_crypto_setcryptopagesize) | Sets the page size used when opening an encrypted database. |

## Enum type description

### Rdb_EncryptionAlgo

```c
enum Rdb_EncryptionAlgo
```

**Description**

Enumerates the database encryption algorithms.

**Since**: 20

| Enum item | Description |
| -- | -- |
| RDB_AES_256_GCM = 0 | Indicates the database is encrypted using RDB_AES_256_GCM. |
| RDB_AES_256_CBC | Indicates the database is encrypted using RDB_AES_256_CBC. |
| RDB_PLAIN_TEXT | Indicates the database is not encrypted.<br>**Since**: 22 |

### Rdb_HmacAlgo

```c
enum Rdb_HmacAlgo
```

**Description**

Enumerates the supported HMAC algorithm when opening a database.

**Since**: 20

| Enum item | Description |
| -- | -- |
| RDB_HMAC_SHA1 = 0 | RDB_HMAC_SHA1 algorithm. |
| RDB_HMAC_SHA256 | RDB_HMAC_SHA256 algorithm. |
| RDB_HMAC_SHA512 | RDB_HMAC_SHA512 algorithm. |

### Rdb_KdfAlgo

```c
enum Rdb_KdfAlgo
```

**Description**

Enumerates the supported KDF algorithm when opening a database.

**Since**: 20

| Enum item | Description |
| -- | -- |
| RDB_KDF_SHA1 = 0 | RDB_KDF_SHA1 algorithm. |
| RDB_KDF_SHA256 | RDB_KDF_SHA256 algorithm. |
| RDB_KDF_SHA512 | RDB_KDF_SHA512 algorithm. |


## Function description

### OH_Rdb_CreateCryptoParam()

```c
OH_Rdb_CryptoParam *OH_Rdb_CreateCryptoParam(void)
```

**Description**

Creates an OH_Rdb_CryptoParam instance object.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Rdb_CryptoParam *](capi-rdb-oh-rdb-cryptoparam.md) | Returns a pointer to OH_Rdb_CryptoParam instance when the execution is successful.  Otherwise, nullptr is returned. The memory must be released through the OH_Rdb_DestroyCryptoParam  interface after the use is complete. |

**Reference**:

OH_Rdb_DestroyCryptoParam


### OH_Rdb_DestroyCryptoParam()

```c
int OH_Rdb_DestroyCryptoParam(OH_Rdb_CryptoParam *param)
```

**Description**

Destroys an OH_Rdb_CryptoParam instance object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Crypto_SetEncryptionKey()

```c
int OH_Crypto_SetEncryptionKey(OH_Rdb_CryptoParam *param, const uint8_t *key, int32_t length)
```

**Description**

Sets key data to the OH_Rdb_CryptoParam object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |
| const uint8_t *key | Represents a pointer to array data. |
| int32_t length | Represents the size of key array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Crypto_SetIteration()

```c
int OH_Crypto_SetIteration(OH_Rdb_CryptoParam *param, int64_t iteration)
```

**Description**

Sets the number of KDF iterations used when opening an encrypted database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |
| int64_t iteration | Represents iterations times. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Crypto_SetEncryptionAlgo()

```c
int OH_Crypto_SetEncryptionAlgo(OH_Rdb_CryptoParam *param, int32_t algo)
```

**Description**

Sets the encryption algorithm when opening an encrypted database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |
| int32_t algo | Represents the encryption algorithm. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Crypto_SetHmacAlgo()

```c
int OH_Crypto_SetHmacAlgo(OH_Rdb_CryptoParam *param, int32_t algo)
```

**Description**

Sets the HMAC algorithm when opening an encrypted database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |
| int32_t algo | Represents the HMAC algorithm. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Crypto_SetKdfAlgo()

```c
int OH_Crypto_SetKdfAlgo(OH_Rdb_CryptoParam *param, int32_t algo)
```

**Description**

Sets the KDF algorithm when opening an encrypted database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |
| int32_t algo | Represents the KDF algorithm. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Crypto_SetCryptoPageSize()

```c
int OH_Crypto_SetCryptoPageSize(OH_Rdb_CryptoParam *param, int64_t size)
```

**Description**

Sets the page size used when opening an encrypted database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_CryptoParam](capi-rdb-oh-rdb-cryptoparam.md) *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |
| int64_t size | Represents the page size, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |


