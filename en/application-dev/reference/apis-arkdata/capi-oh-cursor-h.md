# oh_cursor.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=34d468971c598bfa559c4eeed468969214f84dc6 translatedAt=2026-09-04T02:40:55.579Z pushedAt=2026-09-09T09:11:03.631Z -->

## Overview

Provides APIs to access the result set obtained by querying the RDB store. A result set is a set of results returned by **query()**.

**File to include**: <database/rdb/oh_cursor.h>

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Structs

| Name                          | typedef Keyword| Description                                                        |
| ------------------------------ | ------------- | ------------------------------------------------------------ |
| [OH_Cursor](capi-rdb-oh-cursor.md) | OH_Cursor     | Provides APIs to access the result set obtained by querying the RDB store. A result set is a set of results returned by **query()**.|

### Functions

| Name                                                        | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------ |
| [int OH_Cursor_GetFloatVectorCount(OH_Cursor *cursor, int32_t columnIndex, size_t *length)](#oh_cursor_getfloatvectorcount) | Obtains the length of a floating-point array in the specified column of the current row.      |
| [int OH_Cursor_GetFloatVector(OH_Cursor *cursor, int32_t columnIndex, float *val, size_t inLen, size_t *outLen)](#oh_cursor_getfloatvector) | Obtains the value in the specified column of the current row in the form of a floating-point array.|

## Function Description

### OH_Cursor_GetFloatVectorCount()

```c
int OH_Cursor_GetFloatVectorCount(OH_Cursor *cursor, int32_t columnIndex, size_t *length)
```

**Description**

Obtains the length of a floating-point array in the specified column of the current row.

**Since**: 18


**Parameters**

| Parameter                                | Description                                                        |
| -------------------------------------- | ------------------------------------------------------------ |
| [OH_Cursor](capi-rdb-oh-cursor.md) *cursor | Pointer to the [OH_Cursor](capi-rdb-oh-cursor.md) instance.          |
| int32_t columnIndex                    | Index of the column, which starts from **0**.                   |
| size_t *length                         | Pointer to the length of the float array obtained.|

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>Returns **RDB_OK** if the operation is successful.<br>Returns **RDB_E_ERROR** if a common database error occurs.<br>Returns **RDB_E_INVALID_ARGS** if the parameter is invalid.<br>Returns **RDB_E_SQLITE_CORRUPT** if the database is corrupted.<br>Returns **RDB_E_STEP_RESULT_CLOSED** if the queried result set is closed.<br>Returns **RDB_E_ALREADY_CLOSED** if the database is already closed.<br>Returns **RDB_E_SQLITE_PERM** if an SQLite error occurs: access permission denied.<br>Returns **RDB_E_SQLITE_BUSY** if an SQLite error occurs: the database file is locked.<br>Returns **RDB_E_SQLITE_LOCKED** if an SQLite error occurs: a table in the database is locked.<br>Returns **RDB_E_SQLITE_NOMEM** if an SQLite error occurs: the database is out of memory.<br>Returns **RDB_E_SQLITE_IOERR** if an SQLite error occurs: a disk I/O error occurs.<br>Returns **RDB_E_SQLITE_TOO_BIG** if an SQLite error occurs: the TEXT or BLOB exceeds the size limit.<br>Returns **RDB_E_SQLITE_MISMATCH** if an SQLite error occurs: the data type does not match. |

### OH_Cursor_GetFloatVector()

```c
int OH_Cursor_GetFloatVector(OH_Cursor *cursor, int32_t columnIndex, float *val, size_t inLen, size_t *outLen)
```

**Description**

Obtains the value in the specified column of the current row in the form of a floating-point array.

**Since**: 18


**Parameters**

| Parameter                                | Description                                                        |
| -------------------------------------- | ------------------------------------------------------------ |
| [OH_Cursor](capi-rdb-oh-cursor.md) *cursor | Pointer to the [OH_Cursor](capi-rdb-oh-cursor.md) instance.          |
| int32_t columnIndex                    | Index of the column, which starts from **0**.                   |
| float *val                             | Ponter to the value obtained, in a float array. The caller needs to apply for the memory.|
| size_t inLen                           | Length of the float array requested.                                  |
| size_t *outLen                         | Pointer to the actual length of the float array.                |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| int  | Result code.<br>Returns **RDB_OK** if the operation is successful.<br>Returns **RDB_E_ERROR** if a common database error occurs.<br>Returns **RDB_E_INVALID_ARGS** if the parameter is invalid.<br>Returns **RDB_E_SQLITE_CORRUPT** if the database is corrupted.<br>Returns **RDB_E_STEP_RESULT_CLOSED** if the result set obtained by the query is closed.<br>Returns **RDB_E_ALREADY_CLOSED** if the database is already closed.<br>Returns **RDB_E_SQLITE_PERM** if an SQLite error occurs: access permission denied.<br>Returns **RDB_E_SQLITE_BUSY** if an SQLite error occurs: the database file is locked.<br>Returns **RDB_E_SQLITE_LOCKED** if an SQLite error occurs: a table in the database is locked.<br>Returns **RDB_E_SQLITE_NOMEM** if an SQLite error occurs: the database is out of memory.<br>Returns **RDB_E_SQLITE_IOERR** if an SQLite error occurs: a disk I/O error occurs.<br>Returns **RDB_E_SQLITE_TOO_BIG** if an SQLite error occurs: the TEXT or BLOB exceeds the size limit.<br>Returns **RDB_E_SQLITE_MISMATCH** if an SQLite error occurs: the data type does not match. |



