# oh_values_bucket.h

## Overview

Define the type of stored key value pairs.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) | OH_VBucket | Define the OH_VBucket structure type. |

### Function

| Name | Description |
| -- | -- |
| [int OH_VBucket_PutAsset(OH_VBucket *bucket, const char *field, Data_Asset *value)](#oh_vbucket_putasset) | Put the [Data_Asset](capi-rdb-data-asset.md) * value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name. |
| [int OH_VBucket_PutAssets(OH_VBucket *bucket, const char *field, Data_Asset **value, uint32_t count)](#oh_vbucket_putassets) | Put the [Data_Asset](capi-rdb-data-asset.md) * value of given count to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name. |
| [int OH_VBucket_PutFloatVector(OH_VBucket *bucket, const char *field, const float *vec, size_t len)](#oh_vbucket_putfloatvector) | Put the float vector to the OH_VBucket object. |
| [int OH_VBucket_PutUnlimitedInt(OH_VBucket *bucket, const char *field, int sign, const uint64_t *trueForm, size_t len)](#oh_vbucket_putunlimitedint) | Put the an integer of any length to the OH_VBucket object. |

## Function description

### OH_VBucket_PutAsset()

```c
int OH_VBucket_PutAsset(OH_VBucket *bucket, const char *field, Data_Asset *value)
```

**Description**

Put the [Data_Asset](capi-rdb-data-asset.md) * value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
| const char *field | Indicates the name of the column. |
| Data_Asset *value | Indicates the const [Data_Asset](capi-rdb-data-asset.md) * value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) - success.      [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) - The error code for common invalid args. |

**Reference**:

OH_VBucket


### OH_VBucket_PutAssets()

```c
int OH_VBucket_PutAssets(OH_VBucket *bucket, const char *field, Data_Asset **value, uint32_t count)
```

**Description**

Put the [Data_Asset](capi-rdb-data-asset.md) * value of given count to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
| const char *field | Indicates the name of the column. |
| Data_Asset **value | Indicates the [Data_Asset](capi-rdb-data-asset.md) value of given count. |
| uint32_t count | Indicates the count of value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) - success.      [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) - The error code for common invalid args. |

**Reference**:

OH_VBucket


### OH_VBucket_PutFloatVector()

```c
int OH_VBucket_PutFloatVector(OH_VBucket *bucket, const char *field, const float *vec, size_t len)
```

**Description**

Put the float vector to the OH_VBucket object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
| const char *field | Represents the name of the column. |
| const float *vec | Represents a pointer to float array. |
| size_t len | Represents the size of float array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) - success.      [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) - The error code for common invalid args. |

**Reference**:

OH_VBucket


### OH_VBucket_PutUnlimitedInt()

```c
int OH_VBucket_PutUnlimitedInt(OH_VBucket *bucket, const char *field, int sign, const uint64_t *trueForm, size_t len)
```

**Description**

Put the an integer of any length to the OH_VBucket object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
| const char *field | Represents the name of the column. |
| int sign | Represents 0 is positive integer, 1 is negative integer. |
| const uint64_t *trueForm | Represents a pointer to integer array. |
| size_t len | Represents the size of integer array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) - success.      [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) - The error code for common invalid args. |

**Reference**:

OH_VBucket



