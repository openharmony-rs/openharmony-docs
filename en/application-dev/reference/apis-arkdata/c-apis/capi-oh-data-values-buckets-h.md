# oh_data_values_buckets.h

## Overview

Provides functions and enumerations related to the data value buckets.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Data_VBuckets](capi-rdb-oh-data-vbuckets.md) | OH_Data_VBuckets | Define the OH_Data_VBuckets structure type. |

### Function

| Name | Description |
| -- | -- |
| [OH_Data_VBuckets *OH_VBuckets_Create(void)](#oh_vbuckets_create) | Creates an OH_Data_VBuckets instance object. |
| [int OH_VBuckets_Destroy(OH_Data_VBuckets *buckets)](#oh_vbuckets_destroy) | Destroys an OH_Data_VBuckets instance object. |
| [int OH_VBuckets_PutRow(OH_Data_VBuckets *buckets, const OH_VBucket *row)](#oh_vbuckets_putrow) | Add an OH_VBucket to OH_Data_VBuckets object. |
| [int OH_VBuckets_PutRows(OH_Data_VBuckets *buckets, const OH_Data_VBuckets *rows)](#oh_vbuckets_putrows) | Add an OH_Data_VBuckets to OH_Data_VBuckets object. |
| [int OH_VBuckets_RowCount(OH_Data_VBuckets *buckets, size_t *count)](#oh_vbuckets_rowcount) | Gets the number of rows in OH_Data_VBuckets object. |

## Function description

### OH_VBuckets_Create()

```c
OH_Data_VBuckets *OH_VBuckets_Create(void)
```

**Description**

Creates an OH_Data_VBuckets instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Data_VBuckets *](capi-rdb-oh-data-vbuckets.md) | Returns a pointer to OH_Data_VBuckets instance when the execution is successful.  Otherwise, nullptr is returned. The memory must be released through the OH_VBuckets_Destroy  interface after the use is complete. |

**Reference**:

OH_VBuckets_Destroy


### OH_VBuckets_Destroy()

```c
int OH_VBuckets_Destroy(OH_Data_VBuckets *buckets)
```

**Description**

Destroys an OH_Data_VBuckets instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_VBuckets](capi-rdb-oh-data-vbuckets.md) *buckets | Represents a pointer to an instance of OH_Data_VBuckets. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_VBuckets_PutRow()

```c
int OH_VBuckets_PutRow(OH_Data_VBuckets *buckets, const OH_VBucket *row)
```

**Description**

Add an OH_VBucket to OH_Data_VBuckets object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_VBuckets](capi-rdb-oh-data-vbuckets.md) *buckets | Represents a pointer to an instance of OH_Data_VBuckets. |
| const OH_VBucket *row | Represents a pointer to an instance of OH_VBucket. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_VBuckets_PutRows()

```c
int OH_VBuckets_PutRows(OH_Data_VBuckets *buckets, const OH_Data_VBuckets *rows)
```

**Description**

Add an OH_Data_VBuckets to OH_Data_VBuckets object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_VBuckets](capi-rdb-oh-data-vbuckets.md) *buckets | Represents a pointer to an instance of OH_Data_VBuckets. |
| [const OH_Data_VBuckets](capi-rdb-oh-data-vbuckets.md) *rows | Represents a pointer to an instance of OH_Data_VBuckets. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_VBuckets_RowCount()

```c
int OH_VBuckets_RowCount(OH_Data_VBuckets *buckets, size_t *count)
```

**Description**

Gets the number of rows in OH_Data_VBuckets object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Data_VBuckets](capi-rdb-oh-data-vbuckets.md) *buckets | Represents a pointer to an instance of OH_Data_VBuckets. |
| size_t *count | Represents the count of OH_VBucket in OH_Data_VBuckets. It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |


