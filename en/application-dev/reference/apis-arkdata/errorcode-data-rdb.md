# RDB Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=03549490c8da5aa8e7aea81503480383b2dce6d7 translatedAt=2026-09-04T03:16:03.953Z pushedAt=2026-09-09T09:11:03.703Z -->

> **NOTE**
>
> The following describes only the error codes specific to this module. For details about common error codes, see [Universal Error Codes](../errorcode-universal.md).
>
> For details about how to obtain hilog system logs, see [Viewing HiLog Logs](../../dfx/hilog.md#viewing-logs).
>
> The searchable logs described below may vary with versions.

## 14800000 Internal Error

**Error Message**

Inner error.

**Error description**

This error code is reported if an internal error is thrown.

**Possible Causes**

1. Setting a distributed table does not support composite primary keys. Therefore, calling APIs such as [setDistributedTables](arkts-apis-data-relationalStore-RdbStore.md#setdistributedtables) to set a distributed table fails.
2. When multiple processes operate the database and one of them is frozen, the database lock is held by the frozen process until it is unfrozen. During this period, other processes fail to obtain the lock when calling APIs such as [getRdbStore](arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore) to open the database.
3. A read connection is used for write operations. A read connection cannot be used to perform write operations on the database; it can only be used to perform read operations.
4. When a transaction is not committed, APIs such as [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12) or [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql) are called to sequentially perform DDL operations such as deleting a trigger, deleting a table, and recreating a table. Subsequent similar operations fail.
5. The same batch of data is queried and deleted concurrently.
6. The root key fails to be generated. HUKS fails to generate the root key, so the key for the encrypted database cannot be further generated. Therefore, calling APIs such as [getRdbStore](arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore) to open an encrypted database fails.
7. No data is found during remote query. If the data to be queried does not exist in the peer database, calling the [remoteQuery](arkts-apis-data-relationalStore-RdbStore.md#remotequery) API to perform a remote query and then calling APIs such as [goToFirstRow](arkts-apis-data-relationalStore-ResultSet.md#gotofirstrow) to retrieve data after obtaining the result set will fail.
8. The data management service fails to start. When the data management service fails to start, a distributed table cannot be set. Therefore, calling APIs such as [setDistributedTables](arkts-apis-data-relationalStore-RdbStore.md#setdistributedtables) to set a distributed table fails.

**Solution**

1. Check whether the following log is printed near the time when the issue occurs: `Not support create distributed table with composite primary keys`.
   - Yes: Do not use composite primary keys when setting a distributed table.
   - No: Proceed to the next step.
2. Check whether logs related to process freezing, such as `Freeze pid: <process ID> success` or `PID <process ID> has been frozen`, and the log of database opening failure `ConnectionPool.*code:-15`, can be found by regular expression search near the time when the issue occurred.
   - Yes: Do not operate the database when the process moves to the background, to avoid concurrent database operations by multiple processes. Call [requestSuspendDelay](../apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerrequestsuspenddelay) to request a transient task, or call [startBackgroundRunning](../apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerstartbackgroundrunning) to request a continuous task, so that the database operation can finish before the process is frozen.
   - No: Proceed to the next step.
3. Check whether the business code uses a read connection to perform write operations.
   - Yes: When using a read connection, perform only read operations. Use a write connection for write operations.
   - No: Proceed to the next step.
4. Check whether the business code performs the following operations: after calling [beginTransaction](arkts-apis-data-relationalStore-RdbStore.md#begintransaction) to start a transaction, before the transaction is committed, it calls [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12) or [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql) to sequentially delete trigger a, delete table A, recreate table A, and then fails when deleting trigger a again.
   - Yes: Avoid sequentially performing operations such as deleting trigger a, deleting table A, recreating table A, and deleting trigger a again before the transaction is committed.
   - No: Proceed to next step.
5. Troubleshoot whether the business code has the following operation: after obtaining the result set, first call [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12), [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql), or [delete](arkts-apis-data-relationalStore-RdbStore.md#delete) to delete the data to be queried, and then call [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong) and other APIs to obtain the data, which fails.
   - Yes: The business needs to control the timing properly and avoid concurrently querying and deleting the same batch of data.
   - No: Proceed to next step.
6. Confirm whether the key log can be found via regular expression search near the time point of the issue: `01650.*Init.*retry.*error`, where error is not 0.
   - Yes: The root key may have failed to be generated, and the business needs to retry opening the encrypted database.
   - No: Proceed to next step.
7. Confirm whether the data to be queried exists in the database of the peer device.
   - Yes: Proceed to next step.
   - No: Ensure that the data to be queried exists before performing the remote query.
8. Confirm whether the key log `Get distributed data manager failed` can be found near the time point when the issue occurred.
   - Yes: The data management service failed to start. The business needs to retry setting the distributed table.
   - No: Provide the hilog system log and contact technical support personnel for locating the issue.

## 14800001 Invalid Parameter

**Error Message**

Invalid arguments. Possible causes: 1. Parameter is out of valid range; 2. Missing GROUP BY clause.

**Description**

This error code is reported if the arguments are invalid.

**Possible Causes**

The input arguments do not meet the API requirements, such as the value range, length, and format.

**Solution**

Modify the arguments according to the API reference.

## 14800010 Invalid Database Path

**Error Message**

Failed to open or delete the database by an invalid database path.

**Description**

This error code is reported if the database fails to be opened or deleted due to invalid database path.

**Possible Causes**

The RDB store path is invalid.

**Solution**

Check the RDB store path.

## 14800011 Database File Corrupted

**Error Message**

The current operation failed because the database is corrupted.

**Description**

The operation failed due to a database exception.

**Possible Causes**

1. When opening an encrypted database, the custom key does not match, so calling APIs such as [getRdbStore](arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore) to open the database fails.
2. The database file descriptor (fd) is misused, causing a database file exception. Therefore, calling CRUD operation APIs to operate the database fails.
3. A memory corruption issue exists in the business process, causing a database file exception. Therefore, calling CRUD operation APIs to operate the database fails.
4. The file copy or download process is interrupted, making the file content incomplete and causing a database file exception. Therefore, calling CRUD operation APIs to operate the database fails.
5. The database is directly operated using file APIs during database usage, causing a database file exception. Therefore, calling CRUD operation APIs to operate the database fails.
6. Database file mismatch: for example, the db file and the wal file do not belong to the same database, causing a database exception. Therefore, calling CRUD operation APIs to operate the database fails.

**Solution**

1. Check whether the custom key parameter is consistent with the key parameter used when the encrypted database was previously created.
   - Yes: proceed to the next step.
   - No: ensure that the custom key parameter is consistent each time the encrypted database is opened.
2. Search for logs near the time when the issue occurred: `fdsan`, or troubleshoot whether the business code contains scenarios that operate on file descriptors (fd).
   - Yes: Refer to [Using fdsan](../../napi/fdsan.md) to locate the issue, and synchronously process the database file anomaly. If data loss is acceptable, delete the existing database and recreate it; otherwise, complete the database backup first, and then perform the recovery operation. For details, see [Database Backup and Restore (ArkTS)](../../database/data-backup-and-restore.md).
   - No: Proceed to the next step.
3. Troubleshoot whether the business code contains memory corruption issues.
   - Yes: Resolve the memory corruption issue in the business code, and synchronously process the database file anomaly. If data loss is acceptable, delete the existing database and recreate it; otherwise, complete the database backup first, and then perform the recovery operation. For details, see [Database Backup and Restore (ArkTS)](../../database/data-backup-and-restore.md).
   - No: Proceed to the next step.
4. Troubleshoot whether the business contains scenarios where copying or downloading the database file is interrupted.
   - Yes: Avoid interrupting the process of copying or downloading the database file, and synchronously process the database file anomaly. If data loss is acceptable, delete the existing database and recreate it; otherwise, complete the database backup first, and then perform the recovery operation. For details, see [Database Backup and Restore (ArkTS)](../../database/data-backup-and-restore.md).
   - No: Proceed to the next step.
5. Troubleshoot whether the business code contains scenarios where file APIs are used to operate the database.
   - Yes: Do not use file APIs to operate the database, and synchronously process the database file anomaly. If data loss is acceptable, delete the existing database and recreate it; otherwise, complete the database backup first, and then perform the recovery operation. For details, see [Database Backup and Restore (ArkTS)](../../database/data-backup-and-restore.md).
   - No: Proceed to the next step.
6. Check whether the db file or wal file is overwritten or replaced in the business code.
   - Yes: Ensure that the db file and wal file correspond to each other, and synchronously process the database file anomaly. If data loss is acceptable, delete the existing database and recreate it; otherwise, complete the database backup first, and then perform the recovery operation. For details, see [Database Backup and Restore (ArkTS)](../../database/data-backup-and-restore.md).
   - No: Provide the hilog system log and contact technical support personnel for locating.

## 14800012 Result Set Is Empty or Pointer Index Is Out of Bounds

**Error Message**

ResultSet is empty or pointer index is out of bounds.

**Description**

The result set is empty or the pointer index is out of bounds.

**Possible Causes**

1. SQL spelling errors, failure to find a table or field, duplicate field addition, violation of SQLite system restrictions, database file exceptions, and so on (see the problem scenarios of error code 14800021). In these cases, calling APIs such as [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong) to obtain data fails.
2. The size of a single queried data record exceeds 2 MB. In this case, calling APIs such as [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong) to obtain data fails.
3. There is no data in the table. In this case, calling APIs such as [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong) to obtain data fails.
4. There is no data in the table that meets the query condition. In this case, calling APIs such as [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong) to obtain data fails.

**Solution**

1. Check whether the issue can be located by referring to the procedure of error code 14800021.
   - Yes: Refer to the procedure of error code 14800021.
   - No: Proceed to the next step.
2. Check whether the key log `ResetStatement.*over 2MB` can be found through regular expression search near the time when the issue occurred, or check whether the size of a single data record exceeds 2 MB.
   - Yes: Call the [queryWithoutRowCount](arkts-apis-data-relationalStore-RdbStore.md#querywithoutrowcount23) API to obtain the result set [LiteResultSet](arkts-apis-data-relationalStore-LiteResultSet.md), and then query the data whose single entry exceeds 2 MB.
   - No: Proceed to the next step.
3. Check whether data exists in the table.
   - Yes: Proceed to the next step.
   - No: Insert data and then query again.
4. Check whether data matching the query condition exists in the table.
   - Yes: Provide the HiLog system log and contact technical support personnel for locating the issue.
   - No: Ensure that the query condition meets expectations so that data can be queried.

## 14800013 Column Index Out of Range

**Error Message**

Column index is out of bounds.

**Description**

The column index is out of range.

**Possible Causes**

1. When [getColumnIndex](arkts-apis-data-relationalStore-ResultSet.md#getcolumnindex) is called with a column name that does not exist in the table, and its return value is then used as the input parameter of data retrieval APIs such as [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong) or [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring), the interface execution fails.
2. When the column index parameter passed in exceeds the valid range [0, number of table fields - 1], calling APIs such as [getColumnType](arkts-apis-data-relationalStore-ResultSet.md#getcolumntype18), [getColumnTypeSync](arkts-apis-data-relationalStore-ResultSet.md#getcolumntypesync18), [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong), and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) to retrieve data fails.

**Solution**

1. Confirm whether the key log `GetColumnIndex:Failed, columnName` can be found near the time when the issue occurred, and check whether the input parameter of [getColumnIndex](arkts-apis-data-relationalStore-ResultSet.md#getcolumnindex) is a column name that does not exist in the table.
   - Yes: Ensure that the input parameter meets expectations and is a column name that exists in the table.
   - No: Proceed to the next step.
2. Confirm whether the key log `column index.*out of range` can be found by regular expression search near the time when the issue occurred, and check whether the column index parameters of APIs such as [getColumnType](arkts-apis-data-relationalStore-ResultSet.md#getcolumntype18), [getColumnTypeSync](arkts-apis-data-relationalStore-ResultSet.md#getcolumntypesync18), [getLong](arkts-apis-data-relationalStore-ResultSet.md#getlong), and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) exceed the valid range.
   - Yes: Ensure that the value of the input parameter is within the valid range.
   - No: Provide the HiLog system log and contact technical support personnel for locating.

## 14800014 Target Instance Closed

**Error Message**

The target instance is already closed.

**Description**

The target instance is closed.

**Possible Causes**

The instance was not opened successfully, or the owning instance has been closed (for example, the **close** method has been called on a **ResultSet**/**RdbStore** object, or the **commit**/**rollback** method has been called on a **Transaction** object).

**Solution**

Open the RDB store or obtain the result set.

## 14800015 RDB Store Not Respond

**Error Message**

The database does not respond.

**Description**

This error code is reported if the RDB store does not respond.

**Possible Causes**

A read, write, attach, or detach operation is being performed, and cannot be complete within the specified time (2s by default).

**Solution**

1. Try again later.
2. If the [attach](arkts-apis-data-relationalStore-RdbStore.md#attach12) or [detach](arkts-apis-data-relationalStore-RdbStore.md#detach12) API is used, modify the value of **waitTime** to increase the waiting duration.

## 14800016 Duplicate RDB Alias

**Error Message**

The database alias already exists.

**Description**

This error code is reported if the RDB store alias already exists.

**Possible Causes**

The RDB store alias already exists.

**Solution**

Stop the attach operation or change the RDB store alias.

## 14800017 Key Configuration Changed

**Error Message**

StoreConfig is changed.

**Description**

This error code is reported if the key configuration of the RDB store has been modified.

**Possible Causes**

Key configurations of the database, such as **area**, **securityLevel**, and database read/write permissions, have changed.

**Solution**

Restore the original configuration if required. Otherwise, delete the old RDB store, use the new configuration to create a new RDB store, and import the data to the new RDB store.

Check whether the read/write permission on the database file is modified using chmod. Ensure that the current user has sufficient permissions to read and write the database file.

## 14800018 No Match

**Error Message**

No data meets the condition.

**Description**

No data matching the query conditions is found.

**Possible Causes**

The SQL statement used for query is incorrect, or the data does not exist.

**Solution**

Use the correct query statement or add data.

## 14800019 SQL Query Statement Required

**Error Message**

The SQL must be a query statement.

**Description**

This error code is reported if the SQL statement used is not a query statement.

**Possible Causes**

The SQL statement used for query does not meet specifications.

**Solution**

Use SQL statements that comply with specifications.

## 14800020 Key Damaged or Lost

**Error Message**

The secret key is corrupted or lost.

**Description**

The key is corrupted or lost.

**Possible Causes**

The root key is lost, the application does not have the permission to read the key file, or the key file is damaged.

**Solution**

1. Check the permission for accessing the key file and the content of the key file.
2. Rebuild or restore the database.

## 14800021 SQLite: Generic Error

**Error Message**

SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.

**Description**

This error code is reported if an SQLite generic error occurs.

**Possible Causes**

An error occurs during SQL statement execution, for example:
1. The SQL statement contains spelling errors or syntax issues. Calling APIs such as [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql), [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12), or [executeSync](arkts-apis-data-relationalStore-RdbStore.md#executesync12) to execute the SQL statement fails.
2. A table or a field in a table does not exist in the database. Calling APIs such as [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql), [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12), or [executeSync](arkts-apis-data-relationalStore-RdbStore.md#executesync12) to execute the SQL statement fails.
3. A field that already exists in a table is added repeatedly. Calling APIs such as [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql), [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12), or [executeSync](arkts-apis-data-relationalStore-RdbStore.md#executesync12) to execute the SQL statement fails.
4. SQLite system restrictions are violated (for example, the string or BLOB length exceeds the limit, there are too many columns, too many SQL variables, an overly deep expression tree, too many compound SELECT statements, or too many attached databases). Calling APIs such as [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql), [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12), or [executeSync](arkts-apis-data-relationalStore-RdbStore.md#executesync12) to execute the SQL statement fails.
5. The database file is abnormal. Calling APIs such as [executeSql](arkts-apis-data-relationalStore-RdbStore.md#executesql), [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12), or [executeSync](arkts-apis-data-relationalStore-RdbStore.md#executesync12) to execute the SQL statement fails.

**Solution**

1. Check whether the following key logs can be found through regular expression search near the time when the issue occurred: `Error.*unrecognized token|Error.*syntax error|Error.*incomplete input`.
   - Yes: The SQL statement must be complete. Do not use the `RETURN` keyword in a trigger statement. Do not include comments at the beginning of an SQL statement. When an SQL statement contains `in`, the matching values in the parentheses must be `?` placeholders or specific values, not empty values. Do not use special characters such as `{`, `}`, or `$` near table names or field names in SQL.
   - No: Proceed to the next step.
2. Check whether the following key log can be found through regular expression search near the time when the issue occurred: `Error.*no such table|Error.*no such column`.
   - Yes: Create the table or add the field before operating the database. Perform hardening and recreate the lost table or add the field.
   - No: Proceed to the next step.
3. Check whether the following key log can be found through regular expression search near the time when the issue occurred: `Error.*duplicate column name`.
   - Yes: Do not add a field that already exists in the table.
   - No: Proceed to the next step.
4. Check whether the following key log can be found through regular expression search near the time when the issue occurred: `too many SQL variables|string or blob too big|too many columns|expression tree too deep|too many terms in compound SELECT|too many attached databases`.
   - Yes: Ensure that SQL execution does not violate SQLite system restrictions. For details, see the official documentation: [Limits In SQLite](https://sqlite.org/limits.html).
   - No: proceed to the next step.
5. Confirm whether the key log can be found via regular expression search near the time point of the issue: `Error.*unsupported file format|Error.*database corruption|Error.*check hmac error`.
   - Yes: resolve the issue of the business process corrupting memory or mistakenly closing the fd; integrate backup and recovery; delete and recreate the database.
   - No: provide the HiLog system log and contact technical support personnel for locating the issue.

## 14800022 SQLite: Asynchronous Callback Request Aborted

**Error Message**

SQLite: Callback routine requested an abort.

**Description**

This error code is reported if the asynchronous callback request is aborted.

**Possible Causes**

1. The callback in a custom function in SQLite is aborted.
2. See SQLITE_ABORT.

**Solution**

Check that the hook functions (callbacks) of SQLite are implemented correctly.

## 14800023 SQLite: Access Denied

**Error Message**

SQLite: Access permission denied.

**Description**

This error code is reported if the SQLite access is denied.

**Possible Causes**

1. SQLite does not have the required permission to access or modify a file.
2. See SQLITE_PERM.

**Solution**

1. Ensure that the file is not read-only. If the file is read-only, remove the read-only property.
2. Check that the caller has the required permissions to access the file or folder.
3. Check whether the file system is read-only. If yes, change it to writable.
4. Check that the database file is not being used by another process. Terminate the process that is using the file.
5. When handling permission issues, ensure that you have the permission to change the permissions on the file or folder.

## 14800024 SQLite: Database File Locked

**Error Message**

SQLite: The database file is locked.

**Description**

This error code is reported if the SQLite database file is locked.

**Possible Causes**

1. Two processes of the same application, for example, **UIAbility** and **DataShareExtensionAbility**, perform addition, deletion, and modification operations in the same database, or processes in the same group of different applications perform addition, deletion, and modification operations in the same database via the group.
2. See SQLITE_BUSY.

**Solution**

1. Avoid concurrent database operations from processes.
2. Wait for a while and try again.

## 14800025 SQLite: Database Table Locked

**Error Message**

SQLite: A table in the database is locked.

**Description**

This error code is reported if an SQLite database table is locked.

**Possible Causes**

1. The database file to write has been locked by another process. A transaction is being performed in the RDB store, or the write attempt is blocked by a lock mechanism.
2. See **SQLITE_LOCKED**.

**Solution**

1. Check that the database file is not being written by another process or thread.
2. Check that no write operation is performed after a transaction is started and before the transaction is committed.
3. Check whether the write operation is blocked by other lock mechanisms (such as file locks).
4. Check that the database connection instance is closed after the database operation is complete.
5. In a multi-thread environment, ensure that synchronization mechanisms, such as locks, are used to prevent data races.

## 14800026 SQLite: Insufficient Database Memory

**Error Message**

SQLite: The database is out of memory.

**Description**

This error code is reported if the database memory is insufficient.

**Possible Causes**

The data volume is too large or the memory allocated is insufficient.

**Solution**

Reduce the data volume or increase the memory allocated.

## 14800027 SQLite: Attempt to Write a Read-only Database

**Error Message**

SQLite: Attempt to write a readonly database.

**Description**

This error code is reported if a write operation is invoked on a read-only database.

**Possible Causes**

1. An attempt is made to write an SQLite database file that is opened in read-only mode. The access is denied because the target file is in a read-only file system or the database is marked as read-only.
2. See SQLITE_READONLY.

**Solution**

1. Ensure that the caller has the permission to write data to the database file.
2. If the file system is read-only, change it to read/write.
3. Check that no read-only parameter is used when the database is opened.

## 14800028 SQLite: I/O Error

**Error Message**

SQLite: Some kind of disk I/O error occurred.

**Description**

This error code is reported if a disk I/O error occurs.

**Possible Causes**

The possible causes include the following:
1. The target file does not exist.
2. The target file is read-only.
3. The disk space is insufficient.
4. The target file is damaged.
5. See SQLITE_IOERR.

**Solution**

1. Check whether the file path is correct and whether the file exists.
2. Check that the file is not read-only.
3. Delete unnecessary files to ensure sufficient disk space.
4. Check that the caller has permissions to read and write the file.

## 14800029 SQLite: Database Is Full

**Error Message**

SQLite: The database is full.

**Description**

This error code is reported if the SQLite database is full.

**Possible Causes**

The data volume is too large or the disk space is insufficient.

**Solution**

Reduce the data volume or increase the disk space.

## 14800030 SQLite: Unable to Open the Database File

**Error Message**

SQLite: Unable to open the database file.

**Description**

This error code is reported if the database file fails to be opened.

**Possible Causes**

1. The file does not exist, and the RDB store fails to be created.
2. The file exists, but the database file is damaged.
3. The caller does not have the permission to access the file using SQLite.
4. The disk space is insufficient.
5. See SQLITE_CANTOPEN.

**Solution**

1. Check that the database file path is correct and the caller has the permission to read and write the file.
2. Check that the disk space is sufficient.

## 14800031 SQLite: TEXT or BLOB Exceeds the Limit

**Error Message**

SQLite: TEXT or BLOB exceeds size limit.

**Description**

This error code is reported if the size of the text or BLOB exceeds the limit.

**Possible Causes**

1. The result set returned exceeds the size limit that SQLite can process.
2. See SQLITE_TOOBIG.

**Solution**

Divide the query operation into multiple small queries, which process part of the data each time.

## 14800032 SQLite: Abort Due to Constraint Violation

**Error Message**

SQLite: Abort due to constraint violation.

**Description**

This error code is reported if the database operation violates the constraint rule and is aborted.

**Possible Causes**

1. The data write operation violates the constraints on the database integrity.
2. See SQLITE_CONSTRAINT.

**Solution**

Check whether the data to be inserted or updated violates the constraints.

## 14800033 SQLite: Data Types Mismatch

**Error Message**

SQLite: Data type mismatch.

**Description**

This error code is reported if the data types mismatch.

**Possible Causes**

1. The data type specified in an SQL statement does not match the type of the data stored in the database.
2. See SQLITE_MISMATCH.

**Solution**

Check the type of the data in the specified column in the SQL statement and ensure that the type of the data to be inserted, updated, or queried matches the data type of the column.

## 14800034 Incorrect Use of SQLite Library

**Error Message**

SQLite: Library used incorrectly.

**Description**

This error code is reported if the SQLite interface is used incorrectly.

**Possible Causes**

1. The database operation or context is incorrect. This error usually occurs in the following cases:
    - The next operation is performed before a database operation is complete.
    - A database operation is performed on a closed database connection.
    - A released or invalid database object is used to perform data operation.
2. See SQLITE_MISUSE.

**Solution**

1. Check that proper synchronization mechanisms like locks are used between database operations.
2. Check that a database connection is opened before use and closed after the operation is complete.
3. Check that all database objects are correctly released after being used.

## 14800041 Type Conversion Failure

**Error Message**

Type conversion failed.

**Description**

Type conversion failed.

**Possible Causes**

The data type of the specified column does not match the type of the data obtained from **resultSet**.

**Solution**

Ensure the data type of the specified column matches the type required by the corresponding API.

## 14800047 WAL File Size Exceeds the Default Limit

**Error Message**

The WAL file size exceeds the default limit.

**Description**

This error code is reported if the WAL file exceeds 512 MB, which is the default limit.

**Possible Causes**

Data is added, deleted, and modified continuously without closing the read transaction or result set.

**Solution**

Check for unclosed result sets or transactions.

Close all result sets or transactions.

## 14800050 Failed to Obtain the Subscription Service

**Error Message**

Failed to obtain the subscription service.

**Description**

The error code is reported if the subscription service failed to be obtained.

**Possible Causes**

The platform does not support service subscription.

**Solution**

Deploy the subscription service on the platform.

## 14801001 Stage Model Required

**Error Message**

The operation is supported in the stage model only.

**Description**

This error code is reported if this operation is not performed on the stage model.

**Possible Causes**

The context is not a stage model.

**Solution**

Perform the operation on the stage model.

## 14801002 Invalid dataGroupId in storeConfig

**Error Message**

Invalid data group ID.

**Description**

This error code is reported if the **dataGroupId** parameter is invalid.

**Possible Causes**

The **dataGroupId** is not obtained from the AppGallery.

**Solution**

Obtain **dataGroupId** from the AppGallery and pass it to **storeConfig** correctly.

## 14800051 Inconsistent Distributed Table Type

**Error Message**

The type of the distributed table does not match.

**Description**

This error code is reported if different distributed table types are set for the same database table.

**Possible Causes**

The same database table is set with different [DistributedType](arkts-apis-data-relationalStore-e.md#distributedtype10).

**Solution**

A database table can be synchronized either between devices or between device and cloud.