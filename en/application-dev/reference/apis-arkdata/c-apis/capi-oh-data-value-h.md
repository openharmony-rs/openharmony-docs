# oh_data_value.h

## Overview

Provides functions and enumerations related to the data value.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) | OH_Data_Value | Define the OH_Data_Value structure type. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ColumnType](#oh_columntype) | OH_ColumnType | Indicates the column type. |

### Function

| Name | Description |
| -- | -- |
| [OH_Data_Value *OH_Value_Create(void)](#oh_value_create) | Creates an OH_Data_Value instance object. |
| [int OH_Value_Destroy(OH_Data_Value *value)](#oh_value_destroy) | Destroys an OH_Data_Value instance object. |
| [int OH_Value_PutNull(OH_Data_Value *value)](#oh_value_putnull) | Set empty data to the OH_Data_Value object. |
| [int OH_Value_PutInt(OH_Data_Value *value, int64_t val)](#oh_value_putint) | Set integer data to the OH_Data_Value object. |
| [int OH_Value_PutReal(OH_Data_Value *value, double val)](#oh_value_putreal) | Set decimal data to the OH_Data_Value object. |
| [int OH_Value_PutText(OH_Data_Value *value, const char *val)](#oh_value_puttext) | Set string data to the OH_Data_Value object. |
| [int OH_Value_PutBlob(OH_Data_Value *value, const unsigned char *val, size_t length)](#oh_value_putblob) | Set binary data to the OH_Data_Value object. |
| [int OH_Value_PutAsset(OH_Data_Value *value, const Data_Asset *val)](#oh_value_putasset) | Set Data_Asset data to the OH_Data_Value object. |
| [int OH_Value_PutAssets(OH_Data_Value *value, const Data_Asset * const * val, size_t length)](#oh_value_putassets) | Set multiple Data_Asset data to the OH_Data_Value object. |
| [int OH_Value_PutFloatVector(OH_Data_Value *value, const float *val, size_t length)](#oh_value_putfloatvector) | Set float array data to the OH_Data_Value object. |
| [int OH_Value_PutUnlimitedInt(OH_Data_Value *value, int sign, const uint64_t *trueForm, size_t length)](#oh_value_putunlimitedint) | Set an integer of any length data to the OH_Data_Value object. |
| [int OH_Value_GetType(OH_Data_Value *value, OH_ColumnType *type)](#oh_value_gettype) | Get data type from OH_Data_Value object. |
| [int OH_Value_IsNull(OH_Data_Value *value, bool *val)](#oh_value_isnull) | Check whether the data is empty from OH_Data_Value object. |
| [int OH_Value_GetInt(OH_Data_Value *value, int64_t *val)](#oh_value_getint) | Get integer data from OH_Data_Value object. |
| [int OH_Value_GetReal(OH_Data_Value *value, double *val)](#oh_value_getreal) | Get decimal data from OH_Data_Value object. |
| [int OH_Value_GetText(OH_Data_Value *value, const char **val)](#oh_value_gettext) | Get string data from OH_Data_Value object. |
| [int OH_Value_GetBlob(OH_Data_Value *value, const uint8_t **val, size_t *length)](#oh_value_getblob) | Get binary data from OH_Data_Value object. |
| [int OH_Value_GetAsset(OH_Data_Value *value, Data_Asset *val)](#oh_value_getasset) | Get Data_Asset data from OH_Data_Value object. |
| [int OH_Value_GetAssetsCount(OH_Data_Value *value, size_t *length)](#oh_value_getassetscount) | Get multiple Data_Asset size from OH_Data_Value object. |
| [int OH_Value_GetAssets(OH_Data_Value *value, Data_Asset **val, size_t inLen, size_t *outLen)](#oh_value_getassets) | Get multiple Data_Asset data from OH_Data_Value object. |
| [int OH_Value_GetFloatVectorCount(OH_Data_Value *value, size_t *length)](#oh_value_getfloatvectorcount) | Get float array data size from OH_Data_Value object. |
| [int OH_Value_GetFloatVector(OH_Data_Value *value, float *val, size_t inLen, size_t *outLen)](#oh_value_getfloatvector) | Get float array from OH_Data_Value object. |
| [int OH_Value_GetUnlimitedIntBand(OH_Data_Value *value, size_t *length)](#oh_value_getunlimitedintband) | Get an integer of any length data size from OH_Data_Value object. |
| [int OH_Value_GetUnlimitedInt(OH_Data_Value *value, int *sign, uint64_t *trueForm, size_t inLen, size_t *outLen)](#oh_value_getunlimitedint) | Get an integer of any length data from OH_Data_Value object. |

## Enum type description

### OH_ColumnType

```c
enum OH_ColumnType
```

**Description**

Indicates the column type.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| TYPE_NULL = 0 | Indicates the column type is NULL. Moved from oh_cursor.h file.<br>**Since**: 10 |
| TYPE_INT64 | Indicates the column type is INT64. Moved from oh_cursor.h file.<br>**Since**: 10 |
| TYPE_REAL | Indicates the column type is REAL. Moved from oh_cursor.h file.<br>**Since**: 10 |
| TYPE_TEXT | Indicates the column type is TEXT. Moved from oh_cursor.h file.<br>**Since**: 10 |
| TYPE_BLOB | Indicates the column type is BLOB. Moved from oh_cursor.h file.<br>**Since**: 10 |
| TYPE_ASSET | Indicates the column type is [Data_Asset](capi-rdb-data-asset.md). Moved from oh_cursor.h file.<br>**Since**: 11 |
| TYPE_ASSETS | Indicates the column type is array of [Data_Asset](capi-rdb-data-asset.md). Moved from oh_cursor.h file.<br>**Since**: 11 |
| TYPE_FLOAT_VECTOR | Indicates the column type is FLOAT VECTOR.<br>**Since**: 18 |
| TYPE_UNLIMITED_INT | Indicates that the column type is a number whose length is greater than 64 bits.<br>**Since**: 18 |


## Function description

### OH_Value_Create()

```c
OH_Data_Value *OH_Value_Create(void)
```

**Description**

Creates an OH_Data_Value instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Data_Value *](capi-rdb-oh-data-value.md) | Returns a pointer to OH_Data_Value instance when the execution is successful.  Otherwise, nullptr is returned. The memory must be released through the OH_Value_Destroy  interface after the use is complete. |

**Reference**:

OH_Value_Destroy


### OH_Value_Destroy()

```c
int OH_Value_Destroy(OH_Data_Value *value)
```

**Description**

Destroys an OH_Data_Value instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutNull()

```c
int OH_Value_PutNull(OH_Data_Value *value)
```

**Description**

Set empty data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutInt()

```c
int OH_Value_PutInt(OH_Data_Value *value, int64_t val)
```

**Description**

Set integer data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| int64_t val | Represents a integer data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutReal()

```c
int OH_Value_PutReal(OH_Data_Value *value, double val)
```

**Description**

Set decimal data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| double val | Represents a decimal data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutText()

```c
int OH_Value_PutText(OH_Data_Value *value, const char *val)
```

**Description**

Set string data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| const char *val | Represents a string data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutBlob()

```c
int OH_Value_PutBlob(OH_Data_Value *value, const unsigned char *val, size_t length)
```

**Description**

Set binary data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| const unsigned char *val | Represents a binary data. |
| size_t length | Represents the size of binary data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutAsset()

```c
int OH_Value_PutAsset(OH_Data_Value *value, const Data_Asset *val)
```

**Description**

Set Data_Asset data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| const Data_Asset *val | Represents a pointer to an instance of Data_Asset. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutAssets()

```c
int OH_Value_PutAssets(OH_Data_Value *value, const Data_Asset * const * val, size_t length)
```

**Description**

Set multiple Data_Asset data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| const Data_Asset * const * val | Represents a pointer to multiple Data_Asset. |
| size_t length | Represents the count of multiple data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutFloatVector()

```c
int OH_Value_PutFloatVector(OH_Data_Value *value, const float *val, size_t length)
```

**Description**

Set float array data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| const float *val | Represents a pointer to float array. |
| size_t length | Represents the size of float array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_PutUnlimitedInt()

```c
int OH_Value_PutUnlimitedInt(OH_Data_Value *value, int sign, const uint64_t *trueForm, size_t length)
```

**Description**

Set an integer of any length data to the OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| int sign | Represents 0 is positive integer, 1 is negative integer. |
| const uint64_t *trueForm | Represents a pointer to integer array. |
| size_t length | Represents the size of integer array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_GetType()

```c
int OH_Value_GetType(OH_Data_Value *value, OH_ColumnType *type)
```

**Description**

Get data type from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| [OH_ColumnType](capi-oh-data-value-h.md#oh_columntype) *type | Represents the parameter of the data type. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_IsNull()

```c
int OH_Value_IsNull(OH_Data_Value *value, bool *val)
```

**Description**

Check whether the data is empty from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| bool *val | Represents empty data flag. It is an output parameter. The value true means that the data is empty, and false means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Value_GetInt()

```c
int OH_Value_GetInt(OH_Data_Value *value, int64_t *val)
```

**Description**

Get integer data from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| int64_t *val | Represents a pointer to an integer data. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetReal()

```c
int OH_Value_GetReal(OH_Data_Value *value, double *val)
```

**Description**

Get decimal data from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| double *val | Represents a pointer to an decimal data. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetText()

```c
int OH_Value_GetText(OH_Data_Value *value, const char **val)
```

**Description**

Get string data from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| const char **val | Represents a pointer to a string data. It is an output parameter. The caller does not need to apply for memory and release memory. The life cycle of val follows value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetBlob()

```c
int OH_Value_GetBlob(OH_Data_Value *value, const uint8_t **val, size_t *length)
```

**Description**

Get binary data from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| const uint8_t **val | Represents a pointer to a binary data. It is an output parameter. The caller does not need to apply for memory and release memory. The life cycle of val follows value. |
| size_t *length | Represents the size of binary array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetAsset()

```c
int OH_Value_GetAsset(OH_Data_Value *value, Data_Asset *val)
```

**Description**

Get Data_Asset data from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| Data_Asset *val | Represents a pointer to an instance of Data_Asset. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetAssetsCount()

```c
int OH_Value_GetAssetsCount(OH_Data_Value *value, size_t *length)
```

**Description**

Get multiple Data_Asset size from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| size_t *length | Represents the size of Data_Asset array. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetAssets()

```c
int OH_Value_GetAssets(OH_Data_Value *value, Data_Asset **val, size_t inLen, size_t *outLen)
```

**Description**

Get multiple Data_Asset data from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| Data_Asset **val | Represents a pointer to Data_Asset array. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |
| size_t inLen | Represents the size of val. It can be obtained through the OH_Value_GetAssetsCount function. |
| size_t *outLen | Represents the actual amount of data obtained. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

**Reference**:

OH_Value_GetAssetsCount


### OH_Value_GetFloatVectorCount()

```c
int OH_Value_GetFloatVectorCount(OH_Data_Value *value, size_t *length)
```

**Description**

Get float array data size from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| size_t *length | Represents the size of float array. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetFloatVector()

```c
int OH_Value_GetFloatVector(OH_Data_Value *value, float *val, size_t inLen, size_t *outLen)
```

**Description**

Get float array from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| float *val | Represents a pointer to float array. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |
| size_t inLen | Represents the size of val. It can be obtained through the OH_Value_GetFloatVectorCount function. |
| size_t *outLen | Represents the actual amount of data obtained. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

**Reference**:

OH_Value_GetFloatVectorCount


### OH_Value_GetUnlimitedIntBand()

```c
int OH_Value_GetUnlimitedIntBand(OH_Data_Value *value, size_t *length)
```

**Description**

Get an integer of any length data size from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| size_t *length | Represents the size of integer array. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Value_GetUnlimitedInt()

```c
int OH_Value_GetUnlimitedInt(OH_Data_Value *value, int *sign, uint64_t *trueForm, size_t inLen, size_t *outLen)
```

**Description**

Get an integer of any length data from OH_Data_Value object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Value](capi-rdb-oh-data-value.md) *value | Represents a pointer to an instance of OH_Data_Value. |
| int *sign | Represents 0 is positive integer, 1 is negative integer. It is an output parameter. |
| uint64_t *trueForm | Represents a pointer to integer array. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |
| size_t inLen | Represents the size of trueForm. It can be obtained through the OH_Value_GetUnlimitedIntBand function. |
| size_t *outLen | Represents the actual amount of data obtained. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

**Reference**:

OH_Value_GetUnlimitedIntBand



