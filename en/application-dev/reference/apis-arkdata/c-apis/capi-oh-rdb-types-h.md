# oh_rdb_types.h

## Overview

Provides type define related to the data value.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) | OH_RDB_ReturningContext | Define the OH_RDB_ReturningContext structure type. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Rdb_ConflictResolution](#rdb_conflictresolution) | Rdb_ConflictResolution | Describe the security area of the database. |

### Function

| Name | Description |
| -- | -- |
| [OH_RDB_ReturningContext *OH_RDB_CreateReturningContext(void)](#oh_rdb_createreturningcontext) | Creates an OH_RDB_ReturningContext instance object. |
| [void OH_RDB_DestroyReturningContext(OH_RDB_ReturningContext *context)](#oh_rdb_destroyreturningcontext) | Destroys an OH_RDB_ReturningContext instance object. |
| [int OH_RDB_SetReturningFields(OH_RDB_ReturningContext *context, const char *const fields[], int32_t len)](#oh_rdb_setreturningfields) | Set the returning fields. |
| [int OH_RDB_SetMaxReturningCount(OH_RDB_ReturningContext *context, int32_t count)](#oh_rdb_setmaxreturningcount) | Set the maximum returning value. |
| [OH_Cursor *OH_RDB_GetReturningValues(OH_RDB_ReturningContext *context)](#oh_rdb_getreturningvalues) | Get the cursor of data changes, includes 1024 by default. |
| [int64_t OH_RDB_GetChangedCount(OH_RDB_ReturningContext *context)](#oh_rdb_getchangedcount) | Get the number of rows affected by this operation. |

## Enum type description

### Rdb_ConflictResolution

```c
enum Rdb_ConflictResolution
```

**Description**

Describe the security area of the database.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 18

| Enum item | Description |
| -- | -- |
| RDB_CONFLICT_NONE = 1 | Implements no operation when conflict occurs. |
| RDB_CONFLICT_ROLLBACK | Implements rollback operation when conflict occurs. |
| RDB_CONFLICT_ABORT | Implements abort operation when conflict occurs. |
| RDB_CONFLICT_FAIL | Implements fail operation when conflict occurs. |
| RDB_CONFLICT_IGNORE | Implements ignore operation when conflict occurs. |
| RDB_CONFLICT_REPLACE | Implements replace operation when conflict occurs. |


## Function description

### OH_RDB_CreateReturningContext()

```c
OH_RDB_ReturningContext *OH_RDB_CreateReturningContext(void)
```

**Description**

Creates an OH_RDB_ReturningContext instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| [OH_RDB_ReturningContext *](capi-rdb-oh-rdb-returningcontext.md) | Returns a pointer to OH_RDB_ReturningContext instance when the execution is successful.      Otherwise, nullptr is returned. The memory must be released through the OH_RDB_DestroyReturningContext      interface after the use is complete. |

**Reference**:

OH_RDB_DestroyReturningContext


### OH_RDB_DestroyReturningContext()

```c
void OH_RDB_DestroyReturningContext(OH_RDB_ReturningContext *context)
```

**Description**

Destroys an OH_RDB_ReturningContext instance object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) *context | Represents a pointer to [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) instance. |

### OH_RDB_SetReturningFields()

```c
int OH_RDB_SetReturningFields(OH_RDB_ReturningContext *context, const char *const fields[], int32_t len)
```

**Description**

Set the returning fields.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) *context | Represents a pointer to [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) instance. |
| const char *const fields[] | Indicates the columnNames to returning. |
| int32_t len | Indicates the length of fields. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_RDB_SetMaxReturningCount()

```c
int OH_RDB_SetMaxReturningCount(OH_RDB_ReturningContext *context, int32_t count)
```

**Description**

Set the maximum returning value.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) *context | Represents a pointer to [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) instance. |
| int32_t count | Indicates the maximum entry of the returned result set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_RDB_GetReturningValues()

```c
OH_Cursor *OH_RDB_GetReturningValues(OH_RDB_ReturningContext *context)
```

**Description**

Get the cursor of data changes, includes 1024 by default.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) *context | Represents a pointer to [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | a pointer to the instance of the [OH_Cursor](capi-rdb-oh-cursor.md) structure is returned.      If Get Cursor failed, nullptr is returned. |

### OH_RDB_GetChangedCount()

```c
int64_t OH_RDB_GetChangedCount(OH_RDB_ReturningContext *context)
```

**Description**

Get the number of rows affected by this operation.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) *context | Represents a pointer to [OH_RDB_ReturningContext](capi-rdb-oh-rdb-returningcontext.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | the number of entries that have changed, it will return -1 if get the change fails. |


