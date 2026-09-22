# oh_data_values.h

## Overview

Provides functions and enumerations related to the data values.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) | OH_Data_Values | Define the OH_Data_Values structure type. |

### Function

| Name | Description |
| -- | -- |
| [OH_Data_Values *OH_Values_Create(void)](#oh_values_create) | Creates an OH_Data_Values instance object. |
| [int OH_Values_Destroy(OH_Data_Values *values)](#oh_values_destroy) | Destroys an OH_Data_Values instance object. |
| [int OH_Values_Put(OH_Data_Values *values, const OH_Data_Value *val)](#oh_values_put) | Add OH_Data_Value data to the OH_Data_Values object. |
| [int OH_Values_PutNull(OH_Data_Values *values)](#oh_values_putnull) | Add empty data to the OH_Data_Values object. |
| [int OH_Values_PutInt(OH_Data_Values *values, int64_t val)](#oh_values_putint) | Add integer data to the OH_Data_Values object. |
| [int OH_Values_PutReal(OH_Data_Values *values, double val)](#oh_values_putreal) | Add decimal data to the OH_Data_Values object. |
| [int OH_Values_PutText(OH_Data_Values *values, const char *val)](#oh_values_puttext) | Add string data to the OH_Data_Values object. |
| [int OH_Values_PutBlob(OH_Data_Values *values, const unsigned char *val, size_t length)](#oh_values_putblob) | Add binary data to the OH_Data_Values object. |
| [int OH_Values_PutAsset(OH_Data_Values *values, const Data_Asset *val)](#oh_values_putasset) | Add Data_Asset data to the OH_Data_Values object. |
| [int OH_Values_PutAssets(OH_Data_Values *values, const Data_Asset * const * val, size_t length)](#oh_values_putassets) | Add multiple Data_Asset data to the OH_Data_Values object. |
| [int OH_Values_PutFloatVector(OH_Data_Values *values, const float *val, size_t length)](#oh_values_putfloatvector) | Add float array data to the OH_Data_Values object. |
| [int OH_Values_PutUnlimitedInt(OH_Data_Values *values, int sign, const uint64_t *trueForm, size_t length)](#oh_values_putunlimitedint) | Add an integer of any length data to the OH_Data_Values object. |
| [int OH_Values_Count(OH_Data_Values *values, size_t *count)](#oh_values_count) | Get data count from OH_Data_Values object. |
| [int OH_Values_GetType(OH_Data_Values *values, int index, OH_ColumnType *type)](#oh_values_gettype) | Get data type from OH_Data_Values object. |
| [int OH_Values_Get(OH_Data_Values *values, int index, OH_Data_Value **val)](#oh_values_get) | Get OH_Data_Value data from OH_Data_Values object. |
| [int OH_Values_IsNull(OH_Data_Values *values, int index, bool *val)](#oh_values_isnull) | Check whether the data is empty from OH_Data_Values object. |
| [int OH_Values_GetInt(OH_Data_Values *values, int index, int64_t *val)](#oh_values_getint) | Get integer data from OH_Data_Values object. |
| [int OH_Values_GetReal(OH_Data_Values *values, int index, double *val)](#oh_values_getreal) | Get decimal data from OH_Data_Values object. |
| [int OH_Values_GetText(OH_Data_Values *values, int index, const char **val)](#oh_values_gettext) | Get string data from OH_Data_Values object. |
| [int OH_Values_GetBlob(OH_Data_Values *values, int index, const uint8_t **val, size_t *length)](#oh_values_getblob) | Get binary data from OH_Data_Values object. |
| [int OH_Values_GetAsset(OH_Data_Values *values, int index, Data_Asset *val)](#oh_values_getasset) | Get Data_Asset data from OH_Data_Values object. |
| [int OH_Values_GetAssetsCount(OH_Data_Values *values, int index, size_t *length)](#oh_values_getassetscount) | Get multiple Data_Asset size from OH_Data_Values object. |
| [int OH_Values_GetAssets(OH_Data_Values *values, int index, Data_Asset **val, size_t inLen, size_t *outLen)](#oh_values_getassets) | Get multiple Data_Asset data from OH_Data_Values object. |
| [int OH_Values_GetFloatVectorCount(OH_Data_Values *values, int index, size_t *length)](#oh_values_getfloatvectorcount) | Get float array data size from OH_Data_Values object. |
| [int OH_Values_GetFloatVector(OH_Data_Values *values, int index, float *val, size_t inLen, size_t *outLen)](#oh_values_getfloatvector) | Get float array from OH_Data_Values object. |
| [int OH_Values_GetUnlimitedIntBand(OH_Data_Values *values, int index, size_t *length)](#oh_values_getunlimitedintband) | Get an integer of any length data size from OH_Data_Values object. |
| [int OH_Values_GetUnlimitedInt(OH_Data_Values *values, int index, int *sign, uint64_t *trueForm, size_t inLen, size_t *outLen)](#oh_values_getunlimitedint) | Get an integer of any length data from OH_Data_Values object. |

## Function description

### OH_Values_Create()

```c
OH_Data_Values *OH_Values_Create(void)
```

**Description**

Creates an OH_Data_Values instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Data_Values *](capi-rdb-oh-data-values.md) | Returns a pointer to OH_Data_Values instance when the execution is successful.  Otherwise, nullptr is returned. The memory must be released through the OH_Values_Destroy  interface after the use is complete. |

**Reference**:

OH_Values_Destroy


### OH_Values_Destroy()

```c
int OH_Values_Destroy(OH_Data_Values *values)
```

**Description**

Destroys an OH_Data_Values instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_Put()

```c
int OH_Values_Put(OH_Data_Values *values, const OH_Data_Value *val)
```

**Description**

Add OH_Data_Value data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| const OH_Data_Value *val | Represents a pointer to an instance of OH_Data_Value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutNull()

```c
int OH_Values_PutNull(OH_Data_Values *values)
```

**Description**

Add empty data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutInt()

```c
int OH_Values_PutInt(OH_Data_Values *values, int64_t val)
```

**Description**

Add integer data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int64_t val | Represents a integer data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutReal()

```c
int OH_Values_PutReal(OH_Data_Values *values, double val)
```

**Description**

Add decimal data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| double val | Represents a decimal data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutText()

```c
int OH_Values_PutText(OH_Data_Values *values, const char *val)
```

**Description**

Add string data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| const char *val | Represents a string data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutBlob()

```c
int OH_Values_PutBlob(OH_Data_Values *values, const unsigned char *val, size_t length)
```

**Description**

Add binary data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| const unsigned char *val | Represents a binary data. |
| size_t length | Represents the size of binary data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutAsset()

```c
int OH_Values_PutAsset(OH_Data_Values *values, const Data_Asset *val)
```

**Description**

Add Data_Asset data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| const Data_Asset *val | Represents a pointer to an instance of Data_Asset. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutAssets()

```c
int OH_Values_PutAssets(OH_Data_Values *values, const Data_Asset * const * val, size_t length)
```

**Description**

Add multiple Data_Asset data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| const Data_Asset * const * val | Represents a pointer to multiple Data_Asset. |
| size_t length | Represents the count of multiple data. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutFloatVector()

```c
int OH_Values_PutFloatVector(OH_Data_Values *values, const float *val, size_t length)
```

**Description**

Add float array data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| const float *val | Represents a pointer to float array. |
| size_t length | Represents the size of float array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_PutUnlimitedInt()

```c
int OH_Values_PutUnlimitedInt(OH_Data_Values *values, int sign, const uint64_t *trueForm, size_t length)
```

**Description**

Add an integer of any length data to the OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int sign | Represents 0 is positive integer, 1 is negative integer. |
| const uint64_t *trueForm | Represents a pointer to integer array. |
| size_t length | Represents the size of integer array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_Count()

```c
int OH_Values_Count(OH_Data_Values *values, size_t *count)
```

**Description**

Get data count from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| size_t *count | Represents the count of data in values. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_GetType()

```c
int OH_Values_GetType(OH_Data_Values *values, int index, OH_ColumnType *type)
```

**Description**

Get data type from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| OH_ColumnType *type | Represents the parameter of the data type. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_Get()

```c
int OH_Values_Get(OH_Data_Values *values, int index, OH_Data_Value **val)
```

**Description**

Get OH_Data_Value data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| OH_Data_Value **val | Represents a pointer to an instance of OH_Data_Value. It is an output parameter. The caller does not need to apply for memory and release memory. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_IsNull()

```c
int OH_Values_IsNull(OH_Data_Values *values, int index, bool *val)
```

**Description**

Check whether the data is empty from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| bool *val | Represents empty data flag. It is an output parameter. The value true means that the data is empty, and false means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Values_GetInt()

```c
int OH_Values_GetInt(OH_Data_Values *values, int index, int64_t *val)
```

**Description**

Get integer data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| int64_t *val | Represents a pointer to an integer data. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetReal()

```c
int OH_Values_GetReal(OH_Data_Values *values, int index, double *val)
```

**Description**

Get decimal data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| double *val | Represents a pointer to an decimal data. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetText()

```c
int OH_Values_GetText(OH_Data_Values *values, int index, const char **val)
```

**Description**

Get string data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| const char **val | Represents a pointer to a string data. It is an output parameter. The caller does not need to apply for memory and release memory. The life cycle of val follows the value of index in values. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetBlob()

```c
int OH_Values_GetBlob(OH_Data_Values *values, int index, const uint8_t **val, size_t *length)
```

**Description**

Get binary data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| const uint8_t **val | Represents a pointer to a binary data. It is an output parameter. The caller does not need to apply for memory and release memory. The life cycle of val follows the value of index in values. |
| size_t *length | Represents the size of binary array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetAsset()

```c
int OH_Values_GetAsset(OH_Data_Values *values, int index, Data_Asset *val)
```

**Description**

Get Data_Asset data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| Data_Asset *val | Represents a pointer to an instance of Data_Asset. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetAssetsCount()

```c
int OH_Values_GetAssetsCount(OH_Data_Values *values, int index, size_t *length)
```

**Description**

Get multiple Data_Asset size from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| size_t *length | Represents the size of Data_Asset array. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetAssets()

```c
int OH_Values_GetAssets(OH_Data_Values *values, int index, Data_Asset **val, size_t inLen, size_t *outLen)
```

**Description**

Get multiple Data_Asset data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| Data_Asset **val | Represents a pointer to Data_Asset array. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |
| size_t inLen | Represents the size of val. It can be obtained through the OH_Values_GetAssetsCount function. |
| size_t *outLen | Represents the actual amount of data obtained. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

**Reference**:

OH_Values_GetAssetsCount


### OH_Values_GetFloatVectorCount()

```c
int OH_Values_GetFloatVectorCount(OH_Data_Values *values, int index, size_t *length)
```

**Description**

Get float array data size from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| size_t *length | Represents the size of float array. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetFloatVector()

```c
int OH_Values_GetFloatVector(OH_Data_Values *values, int index, float *val, size_t inLen, size_t *outLen)
```

**Description**

Get float array from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| float *val | Represents a pointer to float array. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |
| size_t inLen | Represents the size of val. It can be obtained through the OH_Values_GetFloatVectorCount function. |
| size_t *outLen | Represents the actual amount of data obtained. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

**Reference**:

OH_Values_GetFloatVectorCount


### OH_Values_GetUnlimitedIntBand()

```c
int OH_Values_GetUnlimitedIntBand(OH_Data_Values *values, int index, size_t *length)
```

**Description**

Get an integer of any length data size from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| size_t *length | Represents the size of integer array. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

### OH_Values_GetUnlimitedInt()

```c
int OH_Values_GetUnlimitedInt(OH_Data_Values *values, int index, int *sign, uint64_t *trueForm, size_t inLen, size_t *outLen)
```

**Description**

Get an integer of any length data from OH_Data_Values object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Represents a pointer to an instance of OH_Data_Values. |
| int index | Represents the zero-based index of target data in values. |
| int *sign | Represents 0 is positive integer, 1 is negative integer. It is an output parameter. |
| uint64_t *trueForm | Represents a pointer to integer array. The caller needs to apply for data memory. This function only fills data. Otherwise, the execution fails. |
| size_t inLen | Represents the size of trueForm. It can be obtained through the OH_Values_GetUnlimitedIntBand function. |
| size_t *outLen | Represents the actual amount of data obtained. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter.          Returns [RDB_E_DATA_TYPE_NULL](capi-relational-store-error-code-h.md#oh_rdb_errcode) the content stored in parameter value is null.          Returns [RDB_E_TYPE_MISMATCH](capi-relational-store-error-code-h.md#oh_rdb_errcode) storage data type mismatch. |

**Reference**:

OH_Values_GetUnlimitedIntBand



