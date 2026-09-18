# oh_rdb_transaction.h

## Overview

Provides database transaction related functions and enumerations.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_RDB_TransOptions](capi-rdb-oh-rdb-transoptions.md) | OH_RDB_TransOptions | Define the OH_RDB_TransOptions structure type. |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) | OH_Rdb_Transaction | Define the OH_Rdb_Transaction structure type. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_RDB_TransType](#oh_rdb_transtype) | OH_RDB_TransType | Indicates relation database transaction type. |

### Function

| Name | Description |
| -- | -- |
| [OH_RDB_TransOptions *OH_RdbTrans_CreateOptions(void)](#oh_rdbtrans_createoptions) | Creates an OH_RDB_TransOptions instance object. |
| [int OH_RdbTrans_DestroyOptions(OH_RDB_TransOptions *options)](#oh_rdbtrans_destroyoptions) | Destroys an OH_RDB_TransOptions instance object. |
| [int OH_RdbTransOption_SetType(OH_RDB_TransOptions *options, OH_RDB_TransType type)](#oh_rdbtransoption_settype) | Sets integer data to the options object. |
| [int OH_RdbTrans_Commit(OH_Rdb_Transaction *trans)](#oh_rdbtrans_commit) | Commits a transaction of a relational database. |
| [int OH_RdbTrans_Rollback(OH_Rdb_Transaction *trans)](#oh_rdbtrans_rollback) | Roll back a transaction of a relational database. |
| [int OH_RdbTrans_Insert(OH_Rdb_Transaction *trans, const char *table, const OH_VBucket *row, int64_t *rowId)](#oh_rdbtrans_insert) | Inserts a row of data into the target table. |
| [int OH_RdbTrans_InsertWithConflictResolution(OH_Rdb_Transaction *trans, const char *table, const OH_VBucket *row, Rdb_ConflictResolution resolution, int64_t *rowId)](#oh_rdbtrans_insertwithconflictresolution) | Inserts a row of data into the target table and support conflict resolution. |
| [int OH_RdbTrans_BatchInsert(OH_Rdb_Transaction *trans, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, int64_t *changes)](#oh_rdbtrans_batchinsert) | Inserts a batch of data into the target table.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters. |
| [int OH_RdbTrans_Update(OH_Rdb_Transaction *trans, const OH_VBucket *row, const OH_Predicates *predicates, int64_t *changes)](#oh_rdbtrans_update) | Updates data in the database based on specified conditions. |
| [int OH_RdbTrans_UpdateWithConflictResolution(OH_Rdb_Transaction *trans, const OH_VBucket *row, const OH_Predicates *predicates, Rdb_ConflictResolution resolution, int64_t *changes)](#oh_rdbtrans_updatewithconflictresolution) | Updates data in the database based on specified conditions and support conflict resolution. |
| [int OH_RdbTrans_Delete(OH_Rdb_Transaction *trans, const OH_Predicates *predicates, int64_t *changes)](#oh_rdbtrans_delete) | Deletes data from the database based on specified conditions |
| [OH_Cursor *OH_RdbTrans_QueryWithoutRowCount(OH_Rdb_Transaction *trans, const OH_Predicates *predicates, const char * const columns[], int len)](#oh_rdbtrans_querywithoutrowcount) | Queries data in the database based on specified conditions without row count. |
| [OH_Cursor *OH_RdbTrans_Query(OH_Rdb_Transaction *trans, const OH_Predicates *predicates, const char *columns[], int len)](#oh_rdbtrans_query) | Queries data in the database based on specified conditions. |
| [OH_Cursor *OH_RdbTrans_QuerySql(OH_Rdb_Transaction *trans, const char *sql, const OH_Data_Values *args)](#oh_rdbtrans_querysql) | Queries data in the database based on SQL statement. |
| [OH_Cursor *OH_RdbTrans_QuerySqlWithoutRowCount(OH_Rdb_Transaction *trans, const char *sql, const OH_Data_Values *args)](#oh_rdbtrans_querysqlwithoutrowcount) | Queries data in the database based on SQL statement without row count. |
| [int OH_RdbTrans_Execute(OH_Rdb_Transaction *trans, const char *sql, const OH_Data_Values *args, OH_Data_Value **result)](#oh_rdbtrans_execute) | Executes an SQL statement that contains specified parameters. |
| [int OH_RdbTrans_Destroy(OH_Rdb_Transaction *trans)](#oh_rdbtrans_destroy) | Destroys an OH_Rdb_Transaction instance object. |
| [int OH_RdbTrans_BatchInsertWithReturning(OH_Rdb_Transaction *trans, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)](#oh_rdbtrans_batchinsertwithreturning) | Inserts a batch of data into the target table and output change info to context.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters. |
| [int OH_RdbTrans_UpdateWithReturning(OH_Rdb_Transaction *trans, OH_VBucket *row, OH_Predicates *predicates, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)](#oh_rdbtrans_updatewithreturning) | Updates data in the database based on specified conditions and output change info to context. |
| [int OH_RdbTrans_DeleteWithReturning(OH_Rdb_Transaction *trans, OH_Predicates *predicates, OH_RDB_ReturningContext *context)](#oh_rdbtrans_deletewithreturning) | Deletes data from the database based on specified conditions and output change info to context. |

## Enum type description

### OH_RDB_TransType

```c
enum OH_RDB_TransType
```

**Description**

Indicates relation database transaction type.

**Since**: 18

| Enum item | Description |
| -- | -- |
| RDB_TRANS_DEFERRED = 0 | Indicates the transaction does not actually start until the database is first accessed. It's a default. |
| RDB_TRANS_IMMEDIATE | Indicates the database connection to start a new write immediately, without waiting for a write statement. |
| RDB_TRANS_EXCLUSIVE | Indicates it is similar to RDB_TRANS_IMMEDIATE in that a write transaction is started immediately. RDB_TRANS_EXCLUSIVE and RDB_TRANS_IMMEDIATE are the same in WAL mode, but in other journaling modes, EXCLUSIVE prevents other database connections from reading the database while the transaction is underway. |
| RDB_TRANS_BUTT | The largest value for rdb transaction type. |


## Function description

### OH_RdbTrans_CreateOptions()

```c
OH_RDB_TransOptions *OH_RdbTrans_CreateOptions(void)
```

**Description**

Creates an OH_RDB_TransOptions instance object.

**Since**: 18

**Returns**:

| Type | Description |
| -- | -- |
| [OH_RDB_TransOptions *](capi-rdb-oh-rdb-transoptions.md) | Returns a pointer to OH_RDB_TransOptions instance when the execution is successful.  Otherwise, nullptr is returned. The memory must be released through the OH_RdbTrans_DestroyOptions  interface after the use is complete. |

**Reference**:

OH_RdbTrans_DestroyOptions


### OH_RdbTrans_DestroyOptions()

```c
int OH_RdbTrans_DestroyOptions(OH_RDB_TransOptions *options)
```

**Description**

Destroys an OH_RDB_TransOptions instance object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_RDB_TransOptions](capi-rdb-oh-rdb-transoptions.md) *options | Represents a pointer to an instance of OH_RDB_TransOptions. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_RdbTransOption_SetType()

```c
int OH_RdbTransOption_SetType(OH_RDB_TransOptions *options, OH_RDB_TransType type)
```

**Description**

Sets integer data to the options object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_RDB_TransOptions](capi-rdb-oh-rdb-transoptions.md) *options | Represents a pointer to an instance of OH_RDB_TransOptions. |
| [OH_RDB_TransType](capi-oh-rdb-transaction-h.md#oh_rdb_transtype) type | Represents relation database transaction type. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_RdbTrans_Commit()

```c
int OH_RdbTrans_Commit(OH_Rdb_Transaction *trans)
```

**Description**

Commits a transaction of a relational database.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred. |

### OH_RdbTrans_Rollback()

```c
int OH_RdbTrans_Rollback(OH_Rdb_Transaction *trans)
```

**Description**

Roll back a transaction of a relational database.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred. |

### OH_RdbTrans_Insert()

```c
int OH_RdbTrans_Insert(OH_Rdb_Transaction *trans, const char *table, const OH_VBucket *row, int64_t *rowId)
```

**Description**

Inserts a row of data into the target table.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const char *table | Represents the target table. |
| const OH_VBucket *row | Represents the row data to be inserted into the table. |
| int64_t *rowId | Represents row line number when insert successfully. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch. |

### OH_RdbTrans_InsertWithConflictResolution()

```c
int OH_RdbTrans_InsertWithConflictResolution(OH_Rdb_Transaction *trans, const char *table, const OH_VBucket *row, Rdb_ConflictResolution resolution, int64_t *rowId)
```

**Description**

Inserts a row of data into the target table and support conflict resolution.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const char *table | Represents the target table. |
| const OH_VBucket *row | Represents the row data to be inserted into the table. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| int64_t *rowId | Represents row line number when insert successfully. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

### OH_RdbTrans_BatchInsert()

```c
int OH_RdbTrans_BatchInsert(OH_Rdb_Transaction *trans, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, int64_t *changes)
```

**Description**

Inserts a batch of data into the target table.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const char *table | Represents the target table. |
| const OH_Data_VBuckets *rows | Represents the rows data to be inserted into the table. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| int64_t *changes | Represents the number of successful insertions. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

### OH_RdbTrans_Update()

```c
int OH_RdbTrans_Update(OH_Rdb_Transaction *trans, const OH_VBucket *row, const OH_Predicates *predicates, int64_t *changes)
```

**Description**

Updates data in the database based on specified conditions.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const OH_VBucket *row | Represents the row data to be updated into the table. |
| const OH_Predicates *predicates | Represents the specified update condition by the instance object of OH_Predicates. |
| int64_t *changes | Represents the number of successful insertions. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch. |

### OH_RdbTrans_UpdateWithConflictResolution()

```c
int OH_RdbTrans_UpdateWithConflictResolution(OH_Rdb_Transaction *trans, const OH_VBucket *row, const OH_Predicates *predicates, Rdb_ConflictResolution resolution, int64_t *changes)
```

**Description**

Updates data in the database based on specified conditions and support conflict resolution.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const OH_VBucket *row | Represents the row data to be updated into the table. |
| const OH_Predicates *predicates | Represents the specified update condition by the instance object of OH_Predicates. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| int64_t *changes | Represents the number of successful insertions. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

### OH_RdbTrans_Delete()

```c
int OH_RdbTrans_Delete(OH_Rdb_Transaction *trans, const OH_Predicates *predicates, int64_t *changes)
```

**Description**

Deletes data from the database based on specified conditions

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const OH_Predicates *predicates | Represents the specified update condition by the instance object of OH_Predicates. |
| int64_t *changes | Represents the number of successfully Deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch. |

### OH_RdbTrans_QueryWithoutRowCount()

```c
OH_Cursor *OH_RdbTrans_QueryWithoutRowCount(OH_Rdb_Transaction *trans, const OH_Predicates *predicates, const char * const columns[], int len)
```

**Description**

Queries data in the database based on specified conditions without row count.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const OH_Predicates *predicates | Represents the specified update condition by the instance object of OH_Predicates. |
| const char * const columns[] | Represents the columns to query. If the value is empty array, the query applies to all columns. |
| int len | Represents the number of columns elements. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the operation is successful, a pointer to the instance of the OH_Cursor structure is returned.  If database has closed or the database does not respond, nullptr is returned. |

### OH_RdbTrans_Query()

```c
OH_Cursor *OH_RdbTrans_Query(OH_Rdb_Transaction *trans, const OH_Predicates *predicates, const char *columns[], int len)
```

**Description**

Queries data in the database based on specified conditions.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const OH_Predicates *predicates | Represents the specified update condition by the instance object of OH_Predicates. |
| const char *columns[] | Represents the columns to query. If the value is empty array, the query applies to all columns. |
| int len | Represents the number of columns elements. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the operation is successful, a pointer to the instance of the OH_Cursor structure is returned.  If database has closed or the database does not respond, nullptr is returned. |

### OH_RdbTrans_QuerySql()

```c
OH_Cursor *OH_RdbTrans_QuerySql(OH_Rdb_Transaction *trans, const char *sql, const OH_Data_Values *args)
```

**Description**

Queries data in the database based on SQL statement.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const char *sql | Represents the SQL statement to execute. |
| const OH_Data_Values *args | Represents a pointer to an instance of OH_Data_Values and  it is the selection arguments. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the operation is successful, a pointer to the instance of the OH_Cursor structure is returned.  If database has closed or the database does not respond, nullptr is returned. |

### OH_RdbTrans_QuerySqlWithoutRowCount()

```c
OH_Cursor *OH_RdbTrans_QuerySqlWithoutRowCount(OH_Rdb_Transaction *trans, const char *sql, const OH_Data_Values *args)
```

**Description**

Queries data in the database based on SQL statement without row count.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const char *sql | Represents the SQL statement to execute. |
| const OH_Data_Values *args | Represents a pointer to an instance of OH_Data_Values and  it is the selection arguments. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the operation is successful, a pointer to the instance of the OH_Cursor structure is returned.  If database has closed or the database does not respond, nullptr is returned. |

### OH_RdbTrans_Execute()

```c
int OH_RdbTrans_Execute(OH_Rdb_Transaction *trans, const char *sql, const OH_Data_Values *args, OH_Data_Value **result)
```

**Description**

Executes an SQL statement that contains specified parameters.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const char *sql | Represents the SQL statement to execute. |
| const OH_Data_Values *args | Represents the values of the parameters in the SQL statement. |
| OH_Data_Value **result | Represents a pointer to OH_Data_Value instance when the execution is successful. The memory must be released through the OH_Value_Destroy interface after the use is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch. |

**Reference**:

OH_Value_Destroy


### OH_RdbTrans_Destroy()

```c
int OH_RdbTrans_Destroy(OH_Rdb_Transaction *trans)
```

**Description**

Destroys an OH_Rdb_Transaction instance object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_RdbTrans_BatchInsertWithReturning()

```c
int OH_RdbTrans_BatchInsertWithReturning(OH_Rdb_Transaction *trans, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)
```

**Description**

Inserts a batch of data into the target table and output change info to context.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| const char *table | Represents the target table. |
| const OH_Data_VBuckets *rows | Represents the rows data to be inserted into the table. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| OH_RDB_ReturningContext *context | Represents a pointer to a pointer to an {@link OH_RDB_ReturningContext} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_NOT_SUPPORTED} The error code for not support.<br>        Returns {@link RDB_E_DATABASE_BUSY} The error code for database busy.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation.<br>        Returns {@link RDB_E_SQLITE_ERROR} SQLite error.<br>            Possible causes: syntax error, such as a table or column not existing.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Transaction, OH_Data_VBuckets, OH_Rdb_ErrCode, OH_RDB_ReturningContext


### OH_RdbTrans_UpdateWithReturning()

```c
int OH_RdbTrans_UpdateWithReturning(OH_Rdb_Transaction *trans, OH_VBucket *row, OH_Predicates *predicates, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)
```

**Description**

Updates data in the database based on specified conditions and output change info to context.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| OH_VBucket *row | Represents the row data to be updated into the table. |
| OH_Predicates *predicates | Represents a pointer to an {link OH_Predicates} instance. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| OH_RDB_ReturningContext *context | Represents a pointer to a pointer to an {@link OH_RDB_ReturningContext} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_NOT_SUPPORTED} The error code for not support.<br>        Returns {@link RDB_E_EMPTY_VALUES_BUCKET} The error code for a values bucket is empty.<br>        Returns {@link RDB_E_DATABASE_BUSY} The error code for database busy.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation.<br>        Returns {@link RDB_E_SQLITE_ERROR} SQLite error.<br>            Possible causes: syntax error, such as a table or column not existing.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Transaction, OH_Data_VBuckets, OH_Predicates, OH_Rdb_ErrCode, OH_RDB_ReturningContext


### OH_RdbTrans_DeleteWithReturning()

```c
int OH_RdbTrans_DeleteWithReturning(OH_Rdb_Transaction *trans, OH_Predicates *predicates, OH_RDB_ReturningContext *context)
```

**Description**

Deletes data from the database based on specified conditions and output change info to context.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Transaction](capi-rdb-oh-rdb-transaction.md) *trans | Represents a pointer to an instance of OH_Rdb_Transaction. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. |
| OH_RDB_ReturningContext *context | Represents a pointer to a pointer to an {@link OH_RDB_ReturningContext} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_NOT_SUPPORTED} The error code for not support.<br>        Returns {@link RDB_E_DATABASE_BUSY} The error code for database busy.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_ERROR} SQLite error.<br>            Possible causes: syntax error, such as a table or column not existing.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Transaction, OH_Predicates, OH_Rdb_ErrCode, OH_RDB_ReturningContext



