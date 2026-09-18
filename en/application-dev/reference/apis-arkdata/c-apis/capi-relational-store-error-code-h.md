# relational_store_error_code.h

## Overview

Declaration error code information.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Rdb_ErrCode](#oh_rdb_errcode) | OH_Rdb_ErrCode | Indicates the error code information. |

## Enum type description

### OH_Rdb_ErrCode

```c
enum OH_Rdb_ErrCode
```

**Description**

Indicates the error code information.

**Since**: 10

| Enum item | Description |
| -- | -- |
| RDB_ERR = -1 | Indicates that the function execution exception. |
| RDB_OK = 0 | The error code in the correct case. |
| E_BASE = 14800000 | The base code of the exception error code. |
| RDB_E_NOT_SUPPORTED = 801 | The error when the capability not supported. |
| RDB_E_ERROR = E_BASE | The error code for common exceptions. |
| RDB_E_INVALID_ARGS = (E_BASE + 1) | The error code for common invalid args. |
| RDB_E_CANNOT_UPDATE_READONLY = (E_BASE + 2) | The error code for upgrade the read-only store. |
| RDB_E_REMOVE_FILE = (E_BASE + 3) | The error code when deleting a file fails. |
| RDB_E_EMPTY_TABLE_NAME = (E_BASE + 5) | The error code for a table name is empty. |
| RDB_E_EMPTY_VALUES_BUCKET = (E_BASE + 6) | The error code for a values bucket is empty. |
| RDB_E_EXECUTE_IN_STEP_QUERY = (E_BASE + 7) | The error code when the sql is not select. |
| RDB_E_INVALID_COLUMN_INDEX = (E_BASE + 8) | The error code for the column index is invalid. |
| RDB_E_INVALID_COLUMN_TYPE = (E_BASE + 9) | The error code for the column type is invalid. |
| RDB_E_EMPTY_FILE_NAME = (E_BASE + 10) | The error code for a file name is empty. |
| RDB_E_INVALID_FILE_PATH = (E_BASE + 11) | The error for the current file path is invalid. |
| RDB_E_TRANSACTION_IN_EXECUTE = (E_BASE + 12) | The error code when using transactions. |
| RDB_E_INVALID_STATEMENT = (E_BASE + 13) | The error code for the current status is invalid. |
| RDB_E_EXECUTE_WRITE_IN_READ_CONNECTION = (E_BASE + 14) | The error code when execute write operation in read connection. |
| RDB_E_BEGIN_TRANSACTION_IN_READ_CONNECTION = (E_BASE + 15) | The error code for execute begin transaction operation in read connection. |
| RDB_E_NO_TRANSACTION_IN_SESSION = (E_BASE + 16) | The error code for there are no transactions in this connection. |
| RDB_E_MORE_STEP_QUERY_IN_ONE_SESSION = (E_BASE + 17) | The error code when begin more step query in one session. |
| RDB_E_NO_ROW_IN_QUERY = (E_BASE + 18) | The error code when the current statement doesn't contains one row result data. |
| RDB_E_INVALID_BIND_ARGS_COUNT = (E_BASE + 19) | The error code for the bind arguments count is invalid. |
| RDB_E_INVALID_OBJECT_TYPE = (E_BASE + 20) | The error code for the object type is invalid. |
| RDB_E_INVALID_CONFLICT_FLAG = (E_BASE + 21) | The error code for the conflict flag is invalid. |
| RDB_E_HAVING_CLAUSE_NOT_IN_GROUP_BY = (E_BASE + 22) | The error code for having clause not in group. |
| RDB_E_NOT_SUPPORTED_BY_STEP_RESULT_SET = (E_BASE + 23) | The error code for not supported by step result set. |
| RDB_E_STEP_RESULT_SET_CROSS_THREADS = (E_BASE + 24) | The error code for step result current tid not equal to object's tid. |
| RDB_E_STEP_RESULT_QUERY_NOT_EXECUTED = (E_BASE + 25) | The error code when the result query was not executed. |
| RDB_E_STEP_RESULT_IS_AFTER_LAST = (E_BASE + 26) | The error code for the result set cursor is after the last row. |
| RDB_E_STEP_RESULT_QUERY_EXCEEDED = (E_BASE + 27) | The error code for the result set query exceeded. |
| RDB_E_STATEMENT_NOT_PREPARED = (E_BASE + 28) | The error code for the statement not prepared. |
| RDB_E_EXECUTE_RESULT_INCORRECT = (E_BASE + 29) | The error code for the result set is incorrect. |
| RDB_E_STEP_RESULT_CLOSED = (E_BASE + 30) | The error code when the result set is closed. |
| RDB_E_RELATIVE_PATH = (E_BASE + 31) | The error code when input relative path. |
| RDB_E_EMPTY_NEW_ENCRYPT_KEY = (E_BASE + 32) | The error code for the new encrypt key is empty. |
| RDB_E_CHANGE_UNENCRYPTED_TO_ENCRYPTED = (E_BASE + 33) | The error code for change unencrypted to encrypted. |
| RDB_E_CHANGE_ENCRYPT_KEY_IN_BUSY = (E_BASE + 34) | The error code for change encrypt in busy. |
| RDB_E_STEP_STATEMENT_NOT_INIT = (E_BASE + 35) | The error code when the statement not initialized. |
| RDB_E_NOT_SUPPORTED_ATTACH_IN_WAL_MODE = (E_BASE + 36) | The error code for the attach is not supported in WAL journal mode. |
| RDB_E_CREATE_FOLDER_FAIL = (E_BASE + 37) | The error code when create folder failed. |
| RDB_E_SQLITE_SQL_BUILDER_NORMALIZE_FAIL = (E_BASE + 38) | The error for SQL builder normalize failed. |
| RDB_E_STORE_SESSION_NOT_GIVE_CONNECTION_TEMPORARILY = (E_BASE + 39) | The error for store session not give connection temporarily. |
| RDB_E_STORE_SESSION_NO_CURRENT_TRANSACTION = (E_BASE + 40) | The error for store session not current transaction. |
| RDB_E_NOT_SUPPORT = (E_BASE + 41) | The error for not supported the current operation. |
| RDB_E_INVALID_PARCEL = (E_BASE + 42) | The error for the current parcel is invalid. |
| RDB_E_QUERY_IN_EXECUTE = (E_BASE + 43) | The error code when using sqlite3_step function failed. |
| RDB_E_SET_PERSIST_WAL = (E_BASE + 44) | The error for set persist WAL. |
| RDB_E_DB_NOT_EXIST = (E_BASE + 45) | The error when the database does not exist. |
| RDB_E_ARGS_READ_CON_OVERLOAD = (E_BASE + 46) | The error when the read connection count is overload. |
| RDB_E_WAL_SIZE_OVER_LIMIT = (E_BASE + 47) | The error when the wal file size over default limit. |
| RDB_E_CON_OVER_LIMIT = (E_BASE + 48) | The error when the connection count is used up. |
| RDB_E_ALREADY_CLOSED = (E_BASE + 50) | Database already closed.<br>**Since**: 18 |
| RDB_E_DATABASE_BUSY = (E_BASE + 51) | The database does not respond.<br>**Since**: 18 |
| RDB_E_SQLITE_CORRUPT = (E_BASE + 52) | Database corrupted.<br>**Since**: 18 |
| RDB_E_SQLITE_PERM = (E_BASE + 53) | SQLite: Access permission denied.<br>**Since**: 18 |
| RDB_E_SQLITE_BUSY = (E_BASE + 54) | SQLite: The database file is locked.<br>**Since**: 18 |
| RDB_E_SQLITE_LOCKED = (E_BASE + 55) | SQLite: A table in the database is locked.<br>**Since**: 18 |
| RDB_E_SQLITE_NOMEM = (E_BASE + 56) | SQLite: The database is out of memory.<br>**Since**: 18 |
| RDB_E_SQLITE_READONLY = (E_BASE + 57) | SQLite: Attempt to write a readonly database.<br>**Since**: 18 |
| RDB_E_SQLITE_IOERR = (E_BASE + 58) | SQLite: Some kind of disk I/O error occurred.<br>**Since**: 18 |
| RDB_E_SQLITE_FULL = (E_BASE + 59) | SQLite: The database is full.<br>**Since**: 18 |
| RDB_E_SQLITE_CANT_OPEN = (E_BASE + 60) | SQLite: Unable to open the database file.<br>**Since**: 18 |
| RDB_E_SQLITE_TOO_BIG = (E_BASE + 61) | SQLite: TEXT or BLOB exceeds size limit.<br>**Since**: 18 |
| RDB_E_SQLITE_MISMATCH = (E_BASE + 62) | SQLite: Data type mismatch.<br>**Since**: 18 |
| RDB_E_DATA_TYPE_NULL = (E_BASE + 63) | Data value type is null.<br>**Since**: 18 |
| RDB_E_TYPE_MISMATCH = (E_BASE + 64) | Data value type mismatch.<br>**Since**: 18 |
| RDB_E_SQLITE_CONSTRAINT = (E_BASE + 65) | SQLite: Abort due to constraint violation.<br>**Since**: 18 |
| RDB_E_SUB_LIMIT_REACHED = (E_BASE + 66) | The number of subscriptions exceeds the limit.<br>**Since**: 22 |
| RDB_E_SQLITE_ERROR = (E_BASE + 67) | SQLite error. Possible causes: syntax error, such as a table or column not existing.<br>**Since**: 23 |


