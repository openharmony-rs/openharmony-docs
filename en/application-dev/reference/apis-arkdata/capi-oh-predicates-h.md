# oh_predicates.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=03549490c8da5aa8e7aea81503480383b2dce6d7 translatedAt=2026-09-04T02:45:00.946Z pushedAt=2026-09-09T09:11:03.644Z -->

## Overview

Defines the predicates for an RDB store.

**File to include**: <database/rdb/oh_predicates.h>

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Structs

| Name                                  | typedef Keyword| Description      |
| -------------------------------------- | ------------- | ---------- |
| [OH_Predicates](capi-rdb-oh-predicates.md) | OH_Predicates | Defines a **predicates** object.|

### Enums

| Name                         | typedef Keyword| Description      |
| ----------------------------- | ------------- | ---------- |
| [OH_OrderType](#oh_ordertype) | OH_OrderType  | Enumerates the sorting types.|

### Functions

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [int OH_Predicates_NotLike(OH_Predicates *predicates, const char *field, const char *pattern)](#oh_predicates_notlike) | Sets **OH_Predicates** to match fields whose data type is string and whose value is not similar to the specified value.<br>This method is similar to "Not Like" in SQL statements. |
| [int OH_Predicates_Glob(OH_Predicates *predicates, const char *field, const char *pattern)](#oh_predicates_glob) | Sets **OH_Predicates** to match the specified field (whose data type is string) whose value contains a wildcard.<br>Unlike the "Like" method, the input parameters of this method are case-sensitive. |
| [int OH_Predicates_NotGlob(OH_Predicates *predicates, const char *field, const char *pattern)](#oh_predicates_notglob) | Sets **OH_Predicates** to not match the specified field (whose data type is string) whose value contains a wildcard.<br>Unlike the "Not Like" method, the input parameters of this method are case-sensitive. |
| [int OH_Predicates_Having(OH_Predicates *predicates, const char *conditions, const OH_Data_Values *values)](#oh_predicates_having) | Sets an **OH_Predicates** object to filter grouped results by specified conditions.|

## Enum Description

### OH_OrderType

```c
enum OH_OrderType
```

**Description**

Enumerates the sorting types.

**Since**: 10

| Enum Item  | Description      |
| -------- | ---------- |
| ASC = 0  | Ascending order.|
| DESC = 1 | Descending order.|


## Function Description

### OH_Predicates_NotLike()

```c
int OH_Predicates_NotLike(OH_Predicates *predicates, const char *field, const char *pattern)
```

**Description**

Sets the **OH_Predicates** to match fields whose data type is string and whose value is not similar to the specified value.<br>This method is similar to "Not Like" in SQL statements.

**Since**: 20


**Parameters**

| Name                                            | Description                                                      |
| -------------------------------------------------- | ---------------------------------------------------------- |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates | Pointer to the [OH_Predicates](capi-rdb-oh-predicates.md) instance. Must not be null. |
| const char *field                                  | Column name in the database table. Must not be null.                                     |
| const char *pattern                                | Specified value to be compared. Must not be null.                                     |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK**: success.<br>**RDB_E_INVALID_ARGS**: invalid parameter. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Predicates_Glob()

```c
int OH_Predicates_Glob(OH_Predicates *predicates, const char *field, const char *pattern)
```

**Description**

Sets the **OH_Predicates** to match the specified field (of the string type) whose value contains wildcards.<br>Unlike the "Like" method, the input parameters of this method are case-sensitive.

**Since**: 20


**Parameters**

| Name                                            | Description                                                      |
| -------------------------------------------------- | ---------------------------------------------------------- |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates | Pointer to an [OH_Predicates](capi-rdb-oh-predicates.md) instance. It must not be null. |
| const char *field                                  | Column name in the database table. It must not be null.                                     |
| const char *pattern                                | Value to match against the predicate. It must not be null.                                       |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int | Result code indicating whether the operation is successful.<br>**RDB_OK**: success.<br>**RDB_E_INVALID_ARGS**: invalid parameter. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Predicates_NotGlob()

```c
int OH_Predicates_NotGlob(OH_Predicates *predicates, const char *field, const char *pattern)
```

**Description**

Sets the **OH_Predicates** to not match the specified field (of the string type) whose value contains wildcards.<br>Unlike the "Not Like" method, the input parameters of this method are case-sensitive.

**Since**: 20


**Parameters**

| Name                                            | Description                                                      |
| -------------------------------------------------- | ---------------------------------------------------------- |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates | Pointer to the [OH_Predicates](capi-rdb-oh-predicates.md) instance. Must not be null. |
| const char *field                                  | Column name in the database table. Must not be null.                                     |
| const char *pattern                                | Specified value to be compared. Must not be null.                                     |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK** indicates success.<br>**RDB_E_INVALID_ARGS** indicates invalid parameters. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

### OH_Predicates_Having()

```c
int OH_Predicates_Having(OH_Predicates *predicates, const char *conditions, const OH_Data_Values *values)
```

**Description**

Sets an **OH_Predicates** object to filter grouped results by specified conditions.

**Since**: 20


**Parameters**

| Name                                                | Description                                                        |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_Predicates](capi-rdb-oh-predicates.md) *predicates     | Pointer to the [OH_Predicates](capi-rdb-oh-predicates.md) instance. Must not be null.   |
| const char *conditions                                 | Filter condition in the HAVING clause. Must not be null or an empty string.                                 |
| const [OH_Data_Values](capi-rdb-oh-data-values.md) *values | Pointer to the [OH_Data_Values](capi-rdb-oh-data-values.md) instance. Must not be null. |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>**RDB_OK**: success.<br>**RDB_E_INVALID_ARGS**: invalid parameter. For details, see [OH_Rdb_ErrCode](capi-relational-store-error-code-h.md#oh_rdb_errcode). |

