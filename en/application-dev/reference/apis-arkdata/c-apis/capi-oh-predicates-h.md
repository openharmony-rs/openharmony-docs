# oh_predicates.h

## Overview

Declared predicate related functions and enumerations.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Predicates](capi-rdb-oh-predicates.md) | OH_Predicates | Define the OH_Predicates structure type. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_OrderType](#oh_ordertype) | OH_OrderType | Result set sort type. |

### Function

| Name | Description |
| -- | -- |
| [int OH_Predicates_NotLike(OH_Predicates *predicates, const char *field, const char *pattern)](#oh_predicates_notlike) | Sets the OH_Predicates to match the field whose data type is string and value is not like the specified value. This method is similar to "Not like" of the SQL statement. |
| [int OH_Predicates_Glob(OH_Predicates *predicates, const char *field, const char *pattern)](#oh_predicates_glob) | Sets the OH_Predicates to match the specified field whose data type is string and the value contains a wildcard. Different from like, the input parameters of this method are case-sensitive. |
| [int OH_Predicates_NotGlob(OH_Predicates *predicates, const char *field, const char *pattern)](#oh_predicates_notglob) | Sets the OH_Predicates to not match the specified field whose data type is string and the value contains a wildcard. Different from not like, the input parameters of this method are case-sensitive. |
| [int OH_Predicates_Having(OH_Predicates *predicates, const char *conditions, const OH_Data_Values *values)](#oh_predicates_having) | Sets the OH_Predicates to specify conditions to filter grouped results that will appear in the final result. |

## Enum type description

### OH_OrderType

```c
enum OH_OrderType
```

**Description**

Result set sort type.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| ASC = 0 | Ascend order. |
| DESC = 1 | Descend order. |


## Function description

### OH_Predicates_NotLike()

```c
int OH_Predicates_NotLike(OH_Predicates *predicates, const char *field, const char *pattern)
```

**Description**

Sets the OH_Predicates to match the field whose data type is string and value is not like the specified value. This method is similar to "Not like" of the SQL statement.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates | Represents a pointer to an instance of OH_Predicates. |
| const char *field | Indicates the column name in the database table. |
| const char *pattern | Indicates the value to compare against. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Predicates_Glob()

```c
int OH_Predicates_Glob(OH_Predicates *predicates, const char *field, const char *pattern)
```

**Description**

Sets the OH_Predicates to match the specified field whose data type is string and the value contains a wildcard. Different from like, the input parameters of this method are case-sensitive.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates | Represents a pointer to an instance of OH_Predicates. |
| const char *field | Indicates the column name in the database table. |
| const char *pattern | Indicates the value to match with the predicate. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Predicates_NotGlob()

```c
int OH_Predicates_NotGlob(OH_Predicates *predicates, const char *field, const char *pattern)
```

**Description**

Sets the OH_Predicates to not match the specified field whose data type is string and the value contains a wildcard. Different from not like, the input parameters of this method are case-sensitive.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates | Represents a pointer to an instance of OH_Predicates. |
| const char *field | Indicates the column name in the database table. |
| const char *pattern | Indicates the value to compare against. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |

### OH_Predicates_Having()

```c
int OH_Predicates_Having(OH_Predicates *predicates, const char *conditions, const OH_Data_Values *values)
```

**Description**

Sets the OH_Predicates to specify conditions to filter grouped results that will appear in the final result.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates | Represents a pointer to an instance of OH_Predicates. |
| const char *conditions | Indicates filter conditions in the having clause. |
| const OH_Data_Values *values | Indicates a pointer to an instance of OH_Data_Values. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns [RDB_OK](capi-relational-store-error-code-h.md#oh_rdb_errcode) if the execution is successful.          Returns [RDB_E_INVALID_ARGS](capi-relational-store-error-code-h.md#oh_rdb_errcode) if invalid input parameter. |


