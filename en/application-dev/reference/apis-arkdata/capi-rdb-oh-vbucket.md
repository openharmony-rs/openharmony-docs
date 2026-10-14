# OH_VBucket
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=17e4b320c8985512791b8b37fea849963e9ff387 translatedAt=2026-09-04T03:04:54.309Z pushedAt=2026-09-09T09:11:03.681Z -->

```c
typedef struct {...} OH_VBucket
```

## Overview

Defines a struct for the types of the key and value in a KV pair.

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

**Header file**: [oh_values_bucket.h](capi-oh-values-bucket-h.md)

### Member Variables

| Name               | Description                          |
| ------------------- | ------------------------------ |
| int64_t id          | Unique identifier of the **OH_VBucket** struct.|
| uint16_t capability | Capacity of the key-value pairs stored in the struct. |


### Member Functions

| Name                                                        | Description                                               |
| ------------------------------------------------------------ | --------------------------------------------------- |
| [int (*putText)(OH_VBucket *bucket, const char *field, const char *value)](#puttext) | Puts a char* value into the **OH_VBucket** object in the given column.          |
| [int (*putInt64)(OH_VBucket *bucket, const char *field, int64_t value)](#putint64) | Puts an int64_t value into the **OH_VBucket** object in the given column.        |
| [int (*putReal)(OH_VBucket *bucket, const char *field, double value)](#putreal) | Puts a double value into the **OH_VBucket** object in the given column.         |
| [int (*putBlob)(OH_VBucket *bucket, const char *field, const uint8_t *value, uint32_t size)](#putblob) | Puts a const uint8_t * value into the **OH_VBucket** object in the given column.|
| [int (*putNull)(OH_VBucket *bucket, const char *field)](#putnull) | Puts a null value into the **OH_VBucket** object in the given column.           |
| [int (*clear)(OH_VBucket *bucket)](#clear)                   | Clears an **OH_VBucket** object.                               |
| [int (*destroy)(OH_VBucket *bucket)](#destroy)               | Destroys an **OH_VBucket** object and reclaims the memory occupied.       |


## Member Function Description

### putText()

```c
int (*putText)(OH_VBucket *bucket, const char *field, const char *value)
```

**Description**

Puts a char* value into the **OH_VBucket** object in the given column.

**Since**: 10

**Parameters**

| Name            | Description                          |
| ------------------ | ------------------------------ |
| OH_VBucket *bucket | Pointer to the **OH_VBucket** instance.|
| const char *field  | Column name in the database table, which must not be a null pointer.               |
| const char *value  | Pointer to the value to put.  |

**Returns**

| Type| Description                                      |
| ---- | ------------------------------------------ |
| int  | Result code.<br>Returns **RDB_OK** if the operation is successful.<br>Returns **RDB_E_INVALID_ARGS** if the parameter is invalid. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### putInt64()

```c
int (*putInt64)(OH_VBucket *bucket, const char *field, int64_t value)
```

**Description**

Puts an int64_t value into the **OH_VBucket** object in the given column.

**Since**: 10

**Parameters**

| Name            | Description                          |
| ------------------ | ------------------------------ |
| OH_VBucket *bucket | Pointer to the **OH_VBucket** instance.|
| const char *field  | Column name in the database table, which must not be a null pointer.               |
| int64_t value      | Pointer to the value to put.  |

**Returns**

| Type| Description                                      |
| ---- | ------------------------------------------ |
| int  | Result code.<br>Returns **RDB_OK** if the operation is successful.<br>Returns **RDB_E_INVALID_ARGS** if the parameter is invalid. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### putReal()

```c
int (*putReal)(OH_VBucket *bucket, const char *field, double value)
```

**Description**

Puts a double value into the **OH_VBucket** object in the given column.

**Since**: 10

**Parameters**

| Name            | Description                          |
| ------------------ | ------------------------------ |
| OH_VBucket *bucket | Pointer to the **OH_VBucket** instance.|
| const char *field  | Column name in the database table, which must not be a null pointer.               |
| double value       | Pointer to the value to put.  |

**Returns**

| Type| Description                                      |
| ---- | ------------------------------------------ |
| int  | Result code.<br>Returns **RDB_OK** if the operation is successful.<br>Returns **RDB_E_INVALID_ARGS** if the parameter is invalid. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### putBlob()

```c
int (*putBlob)(OH_VBucket *bucket, const char *field, const uint8_t *value, uint32_t size)
```

**Description**

Puts a const uint8_t * value into the **OH_VBucket** object in the given column.

**Since**: 10

**Parameters**

| Name            | Description                          |
| ------------------ | ------------------------------ |
| OH_VBucket *bucket | Pointer to the **OH_VBucket** instance.|
| const char *field  | Column name in the database table, which must not be a null pointer.               |
| const uint8_t *value | Pointer to the value to put.|
| uint32_t size      | Byte length of value.              |

**Returns**

| Type| Description                                      |
| ---- | ------------------------------------------ |
| int  | Result code.<br>**RDB_OK**: success.<br>**RDB_E_INVALID_ARGS**: invalid parameter. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### putNull()

```c
int (*putNull)(OH_VBucket *bucket, const char *field)
```

**Description**

Puts a null value into the **OH_VBucket** object in the given column.

**Since**: 10

**Parameters**

| Name            | Description                          |
| ------------------ | ------------------------------ |
| OH_VBucket *bucket | Pointer to the **OH_VBucket** instance.|
| const char *field  | Column name in the database table, which must not be a null pointer.               |

**Returns**

| Type| Description                                      |
| ---- | ------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### clear()

```c
int (*clear)(OH_VBucket *bucket)
```

**Description**

Clears the OH_VBucket object.

**Since**: 10

**Parameters**

| Name            | Description                          |
| ------------------ | ------------------------------ |
| OH_VBucket *bucket | Pointer to the **OH_VBucket** instance.|

**Returns**

| Type| Description                                      |
| ---- | ------------------------------------------ |
| int  | Result code.<br>**RDB_OK**: success.<br>**RDB_E_INVALID_ARGS**: invalid parameter. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### destroy()

```c
int (*destroy)(OH_VBucket *bucket)
```

**Description**

Destroys the **OH_VBucket** object and reclaims the memory occupied by the object.

**Since**: 10

**Parameters**

| Name            | Description                          |
| ------------------ | ------------------------------ |
| OH_VBucket *bucket | Pointer to the **OH_VBucket** instance.|

**Returns**

| Type| Description                                      |
| ---- | ------------------------------------------ |
| int  | Whether the operation is successful. If an error occurs, returns the corresponding error code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

