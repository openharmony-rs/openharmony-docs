# relational_store.h

## Overview

Provides database related functions and enumerations.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Rdb_Config](capi-rdb-oh-rdb-config.md) | OH_Rdb_Config | Manages relational database configurations. |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) | OH_Rdb_Store | Define OH_Rdb_Store type. |
| [Rdb_DistributedConfig](capi-rdb-rdb-distributedconfig.md) | Rdb_DistributedConfig | Manages the distributed configuration of the table. |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) | Rdb_KeyInfo | Describes the primary keys or row-ids of changed rows. |
| [Rdb_ChangeInfo](capi-rdb-rdb-changeinfo.md) | Rdb_ChangeInfo | Describes the notify info of data change. |
| [Rdb_SubscribeCallback](capi-rdb-rdb-subscribecallback.md) | Rdb_SubscribeCallback | Indicates the callback functions. |
| [Rdb_DataObserver](capi-rdb-rdb-dataobserver.md) | Rdb_DataObserver | Indicates the observer of data. |
| [Rdb_Statistic](capi-rdb-rdb-statistic.md) | Rdb_Statistic | Describes the statistic of the cloud sync process. |
| [Rdb_TableDetails](capi-rdb-rdb-tabledetails.md) | Rdb_TableDetails | Describes the [Rdb_Statistic](capi-rdb-rdb-statistic.md) details of the table. |
| [Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md) | Rdb_ProgressDetails | Describes detail of the cloud sync progress. |
| [Rdb_ProgressObserver](capi-rdb-rdb-progressobserver.md) | Rdb_ProgressObserver | The observer of progress. |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) | OH_Rdb_ConfigV2 | Define OH_Rdb_ConfigV2 type. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Rdb_SecurityLevel](#oh_rdb_securitylevel) | OH_Rdb_SecurityLevel | Describe the security level of the database. |
| [Rdb_SecurityArea](#rdb_securityarea) | Rdb_SecurityArea | Describe the security area of the database. |
| [Rdb_DBType](#rdb_dbtype) | Rdb_DBType | Define Rdb_DBType type. |
| [Rdb_Tokenizer](#rdb_tokenizer) | Rdb_Tokenizer | Define Rdb_Tokenizer type. |
| [Rdb_DistributedType](#rdb_distributedtype) | Rdb_DistributedType | Describes the distribution type of the tables. |
| [Rdb_ChangeType](#rdb_changetype) | Rdb_ChangeType | Describes the change type. |
| [Rdb_SubscribeType](#rdb_subscribetype) | Rdb_SubscribeType | Indicates the subscribe type. |
| [Rdb_SyncMode](#rdb_syncmode) | Rdb_SyncMode | Indicates the database synchronization mode. |
| [Rdb_Progress](#rdb_progress) | Rdb_Progress |  |

### Macro

| Name | Description |
| -- | -- |
| RELATIONAL_STORE_H | Provides database related functions and enumerations.<br>**Since**: 10<br>**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core |
| DISTRIBUTED_CONFIG_VERSION 1 | Indicates version of [Rdb_DistributedConfig](capi-rdb-rdb-distributedconfig.md)<br>**Since**: 11 |
| DISTRIBUTED_CHANGE_INFO_VERSION 1 | Indicates version of [Rdb_ChangeInfo](capi-rdb-rdb-changeinfo.md)<br>**Since**: 11 |
| DISTRIBUTED_PROGRESS_DETAIL_VERSION 1 | Indicates version of [Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md)<br>**Since**: 11 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Rdb_ConfigV2 *OH_Rdb_CreateConfig()](#oh_rdb_createconfig) | - | Create OH_Rdb_ConfigV2 which is used to open store |
| [int OH_Rdb_DestroyConfig(OH_Rdb_ConfigV2 *config)](#oh_rdb_destroyconfig) | - | Destroy OH_Rdb_ConfigV2 which is created by OH_Rdb_CreateConfig |
| [int OH_Rdb_SetDatabaseDir(OH_Rdb_ConfigV2 *config, const char *databaseDir)](#oh_rdb_setdatabasedir) | - | Set property databaseDir into config |
| [int OH_Rdb_SetStoreName(OH_Rdb_ConfigV2 *config, const char *storeName)](#oh_rdb_setstorename) | - | Set property storeName into config |
| [int OH_Rdb_SetBundleName(OH_Rdb_ConfigV2 *config, const char *bundleName)](#oh_rdb_setbundlename) | - | Set property bundleName into config |
| [int OH_Rdb_SetModuleName(OH_Rdb_ConfigV2 *config, const char *moduleName)](#oh_rdb_setmodulename) | - | Set property moduleName into config |
| [int OH_Rdb_SetEncrypted(OH_Rdb_ConfigV2 *config, bool isEncrypted)](#oh_rdb_setencrypted) | - | Set property isEncrypted into config |
| [int OH_Rdb_SetSecurityLevel(OH_Rdb_ConfigV2 *config, int securityLevel)](#oh_rdb_setsecuritylevel) | - | Set property securityLevel into config |
| [int OH_Rdb_SetArea(OH_Rdb_ConfigV2 *config, int area)](#oh_rdb_setarea) | - | Set property area into config |
| [int OH_Rdb_SetDbType(OH_Rdb_ConfigV2 *config, int dbType)](#oh_rdb_setdbtype) | - | Set property dbType into config |
| [int OH_Rdb_SetCustomDir(OH_Rdb_ConfigV2 *config, const char *customDir)](#oh_rdb_setcustomdir) | - | Sets the customized directory relative to the database. |
| [int OH_Rdb_SetReadOnly(OH_Rdb_ConfigV2 *config, bool readOnly)](#oh_rdb_setreadonly) | - | Sets the relation database store is read-only mode. |
| [int OH_Rdb_SetPlugins(OH_Rdb_ConfigV2 *config, const char **plugins, int32_t length)](#oh_rdb_setplugins) | - | Sets the dynamic libraries with capabilities such as Full-Text Search (FTS). |
| [int OH_Rdb_SetCryptoParam(OH_Rdb_ConfigV2 *config, const OH_Rdb_CryptoParam *cryptoParam)](#oh_rdb_setcryptoparam) | - | Sets the custom encryption parameters. |
| [int OH_Rdb_SetTokenizer(OH_Rdb_ConfigV2 *config, Rdb_Tokenizer tokenizer)](#oh_rdb_settokenizer) | - | Set property tokenizer into config |
| [int OH_Rdb_SetPersistent(OH_Rdb_ConfigV2 *config, bool isPersistent)](#oh_rdb_setpersistent) | - | Set property persist into config |
| [int OH_Rdb_SetSemanticIndex(OH_Rdb_ConfigV2 *config, bool enableSemanticIndex)](#oh_rdb_setsemanticindex) | - | Set whether the database enable the capabilities for semantic indexing processing. |
| [int OH_Rdb_IsTokenizerSupported(Rdb_Tokenizer tokenizer, bool *isSupported)](#oh_rdb_istokenizersupported) | - | Check if a tokenizer is supported or not. |
| [const int *OH_Rdb_GetSupportedDbType(int *typeCount)](#oh_rdb_getsupporteddbtype) | - | Get support db type list |
| [OH_VObject *OH_Rdb_CreateValueObject()](#oh_rdb_createvalueobject) | - | Creates an {@link OH_VObject} instance. |
| [OH_VBucket *OH_Rdb_CreateValuesBucket()](#oh_rdb_createvaluesbucket) | - | Creates an {@link OH_VBucket} object. |
| [OH_Predicates *OH_Rdb_CreatePredicates(const char *table)](#oh_rdb_createpredicates) | - | Creates an {@link OH_Predicates} instance. |
| [OH_Rdb_Store *OH_Rdb_GetOrOpen(const OH_Rdb_Config *config, int *errCode)](#oh_rdb_getoropen) | - | Obtains an RDB store.<br> You can set parameters of the RDB store as required. In general, this method is recommended to obtain a rdb store. |
| [OH_Rdb_Store *OH_Rdb_CreateOrOpen(const OH_Rdb_ConfigV2 *config, int *errCode)](#oh_rdb_createoropen) | - | Obtains an RDB store with OH_Rdb_ConfigV2.<br> You can set parameters of the RDB store as required. In general, this method is recommended to obtain a rdb store. |
| [int OH_Rdb_CloseStore(OH_Rdb_Store *store)](#oh_rdb_closestore) | - | Close the [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) object and reclaim the memory occupied by the object. |
| [int OH_Rdb_DeleteStore(const OH_Rdb_Config *config)](#oh_rdb_deletestore) | - | Deletes the database with a specified path. |
| [int OH_Rdb_DeleteStoreV2(const OH_Rdb_ConfigV2 *config)](#oh_rdb_deletestorev2) | - | Deletes the database with a specified path. |
| [int OH_Rdb_Insert(OH_Rdb_Store *store, const char *table, OH_VBucket *valuesBucket)](#oh_rdb_insert) | - | Inserts a row of data into the target table. |
| [int OH_Rdb_InsertWithConflictResolution(OH_Rdb_Store *store, const char *table, OH_VBucket *row, Rdb_ConflictResolution resolution, int64_t *rowId)](#oh_rdb_insertwithconflictresolution) | - | Inserts a row of data into the target table and support conflict resolution. |
| [int OH_Rdb_BatchInsert(OH_Rdb_Store *store, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, int64_t *changes)](#oh_rdb_batchinsert) | - | Inserts a batch of data into the target table.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters. |
| [int OH_Rdb_Update(OH_Rdb_Store *store, OH_VBucket *valuesBucket, OH_Predicates *predicates)](#oh_rdb_update) | - | Updates data in the database based on specified conditions. |
| [int OH_Rdb_UpdateWithConflictResolution(OH_Rdb_Store *store, OH_VBucket *row, OH_Predicates *predicates, Rdb_ConflictResolution resolution, int64_t *changes)](#oh_rdb_updatewithconflictresolution) | - | Updates data in the database based on specified conditions and support conflict resolution. |
| [int OH_Rdb_Delete(OH_Rdb_Store *store, OH_Predicates *predicates)](#oh_rdb_delete) | - | Deletes data from the database based on specified conditions. |
| [OH_Cursor *OH_Rdb_Query(OH_Rdb_Store *store, OH_Predicates *predicates, const char *const *columnNames, int length)](#oh_rdb_query) | - | Queries data in the database based on specified conditions. |
| [OH_Cursor *OH_Rdb_QueryWithoutRowCount(OH_Rdb_Store *store, OH_Predicates *predicates, const char *const columns[], int length)](#oh_rdb_querywithoutrowcount) | - | Queries data in the database based on specified conditions without row count. |
| [OH_Cursor *OH_Rdb_QuerySqlWithoutRowCount(OH_Rdb_Store *store, const char *sql, const OH_Data_Values *args)](#oh_rdb_querysqlwithoutrowcount) | - | Queries data in the database based on an SQL statement without row count. |
| [int OH_Rdb_Execute(OH_Rdb_Store *store, const char *sql)](#oh_rdb_execute) | - | Executes an SQL statement. |
| [int OH_Rdb_ExecuteV2(OH_Rdb_Store *store, const char *sql, const OH_Data_Values *args, OH_Data_Value **result)](#oh_rdb_executev2) | - | Executes an SQL statement. |
| [int OH_Rdb_ExecuteByTrxId(OH_Rdb_Store *store, int64_t trxId, const char *sql)](#oh_rdb_executebytrxid) | - | Write operations are performed using the specified transaction represented by the transaction ID |
| [OH_Cursor *OH_Rdb_ExecuteQuery(OH_Rdb_Store *store, const char *sql)](#oh_rdb_executequery) | - | Queries data in the database based on an SQL statement. |
| [OH_Cursor *OH_Rdb_ExecuteQueryV2(OH_Rdb_Store *store, const char *sql, const OH_Data_Values *args)](#oh_rdb_executequeryv2) | - | Queries data in the database based on an SQL statement. |
| [int OH_Rdb_BeginTransaction(OH_Rdb_Store *store)](#oh_rdb_begintransaction) | - | Begins a transaction in EXCLUSIVE mode. |
| [int OH_Rdb_RollBack(OH_Rdb_Store *store)](#oh_rdb_rollback) | - | Rolls back a transaction in EXCLUSIVE mode. |
| [int OH_Rdb_Commit(OH_Rdb_Store *store)](#oh_rdb_commit) | - | Commits a transaction in EXCLUSIVE mode. |
| [int OH_Rdb_BeginTransWithTrxId(OH_Rdb_Store *store, int64_t *trxId)](#oh_rdb_begintranswithtrxid) | - | Begin a transaction and the transaction ID corresponding to the transaction. |
| [int OH_Rdb_RollBackByTrxId(OH_Rdb_Store *store, int64_t trxId)](#oh_rdb_rollbackbytrxid) | - | Roll back a transaction that is represented by a specified transaction ID |
| [int OH_Rdb_CommitByTrxId(OH_Rdb_Store *store, int64_t trxId)](#oh_rdb_commitbytrxid) | - | Commit a transaction that is represented by a specified transaction ID |
| [int OH_Rdb_Backup(OH_Rdb_Store *store, const char *databasePath)](#oh_rdb_backup) | - | Backs up a database on specified path. |
| [int OH_Rdb_Restore(OH_Rdb_Store *store, const char *databasePath)](#oh_rdb_restore) | - | Restores a database from a specified database file. |
| [int OH_Rdb_GetVersion(OH_Rdb_Store *store, int *version)](#oh_rdb_getversion) | - | Gets the version of a database. |
| [int OH_Rdb_SetVersion(OH_Rdb_Store *store, int version)](#oh_rdb_setversion) | - | Sets the version of a database. |
| [int OH_Rdb_SetDistributedTables(OH_Rdb_Store *store, const char *tables[], uint32_t count, Rdb_DistributedType type, const Rdb_DistributedConfig *config)](#oh_rdb_setdistributedtables) | - | Set table to be distributed table. |
| [OH_Cursor *OH_Rdb_FindModifyTime(OH_Rdb_Store *store, const char *tableName, const char *columnName, OH_VObject *values)](#oh_rdb_findmodifytime) | - | Set table to be distributed table. |
| [typedef void (\*Rdb_BriefObserver)(void *context, const char *values[], uint32_t count)](#rdb_briefobserver) | Rdb_BriefObserver | The callback function of cloud data change event. |
| [typedef void (\*Rdb_DetailsObserver)(void *context, const Rdb_ChangeInfo **changeInfo, uint32_t count)](#rdb_detailsobserver) | Rdb_DetailsObserver | The callback function of cloud data change details event. |
| [int OH_Rdb_Subscribe(OH_Rdb_Store *store, Rdb_SubscribeType type, const Rdb_DataObserver *observer)](#oh_rdb_subscribe) | - | Registers an observer for the database. When data in the distributed database or the local database changes, the callback will be invoked. |
| [int OH_Rdb_Unsubscribe(OH_Rdb_Store *store, Rdb_SubscribeType type, const Rdb_DataObserver *observer)](#oh_rdb_unsubscribe) | - | Remove specified observer of specified type from the database. |
| [Rdb_TableDetails *OH_Rdb_GetTableDetails(Rdb_ProgressDetails *progress, int32_t version)](#oh_rdb_gettabledetails) | - | Get table details from progress details. |
| [typedef void (\*Rdb_ProgressCallback)(void *context, Rdb_ProgressDetails *progressDetails)](#rdb_progresscallback) | Rdb_ProgressCallback | The callback function of progress. |
| [typedef void (\*Rdb_SyncCallback)(Rdb_ProgressDetails *progressDetails)](#rdb_synccallback) | Rdb_SyncCallback | The callback function of sync. |
| [int OH_Rdb_CloudSync(OH_Rdb_Store *store, Rdb_SyncMode mode, const char *tables[], uint32_t count, const Rdb_ProgressObserver *observer)](#oh_rdb_cloudsync) | - | Sync data to cloud. |
| [int OH_Rdb_SubscribeAutoSyncProgress(OH_Rdb_Store *store, const Rdb_ProgressObserver *observer)](#oh_rdb_subscribeautosyncprogress) | - | Subscribes to the automatic synchronization progress of an RDB store. A callback will be invoked when there is a notification of the automatic synchronization progress. |
| [int OH_Rdb_UnsubscribeAutoSyncProgress(OH_Rdb_Store *store, const Rdb_ProgressObserver *observer)](#oh_rdb_unsubscribeautosyncprogress) | - | Unsubscribes from the automatic synchronization progress of an RDB store. |
| [int OH_Rdb_LockRow(OH_Rdb_Store *store, OH_Predicates *predicates)](#oh_rdb_lockrow) | - | Lock data from the database based on specified conditions. |
| [int OH_Rdb_UnlockRow(OH_Rdb_Store *store, OH_Predicates *predicates)](#oh_rdb_unlockrow) | - | Unlock data from the database based on specified conditions. |
| [OH_Cursor *OH_Rdb_QueryLockedRow(OH_Rdb_Store *store, OH_Predicates *predicates, const char *const *columnNames, int length)](#oh_rdb_querylockedrow) | - | Queries locked data in the database based on specified conditions. |
| [int OH_Rdb_CreateTransaction(OH_Rdb_Store *store, const OH_RDB_TransOptions *options, OH_Rdb_Transaction **trans)](#oh_rdb_createtransaction) | - | Creates an OH_Rdb_Transaction instance object. |
| [int OH_Rdb_Attach(OH_Rdb_Store *store, const OH_Rdb_ConfigV2 *config, const char *attachName, int64_t waitTime, size_t *attachedNumber)](#oh_rdb_attach) | - | Attaches a database file to the currently linked database. |
| [int OH_Rdb_Detach(OH_Rdb_Store *store, const char *attachName, int64_t waitTime, size_t *attachedNumber)](#oh_rdb_detach) | - | Detaches a database from this database. |
| [int OH_Rdb_SetLocale(OH_Rdb_Store *store, const char *locale)](#oh_rdb_setlocale) | - | Support for collations in different languages. |
| [typedef void (\*Rdb_CorruptedHandler)(void *context, OH_Rdb_ConfigV2 *config, OH_Rdb_Store *store)](#rdb_corruptedhandler) | Rdb_CorruptedHandler | The callback function of database corruption handle. |
| [int OH_Rdb_RegisterCorruptedHandler(const OH_Rdb_ConfigV2 *config, void *context, const Rdb_CorruptedHandler handler)](#oh_rdb_registercorruptedhandler) | - | Registers corrupted handler for the database. |
| [int OH_Rdb_UnregisterCorruptedHandler(const OH_Rdb_ConfigV2 *config, void *context, const Rdb_CorruptedHandler handler)](#oh_rdb_unregistercorruptedhandler) | - | Unregisters corrupted handler for the database. |
| [int OH_Rdb_RekeyEx(OH_Rdb_Store *store, OH_Rdb_CryptoParam *param)](#oh_rdb_rekeyex) | - | Change the encrypted database key. |
| [int OH_Rdb_BatchInsertWithReturning(OH_Rdb_Store *store, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)](#oh_rdb_batchinsertwithreturning) | - | Inserts a batch of data into the target table and output change info to context.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters. |
| [int OH_Rdb_UpdateWithReturning(OH_Rdb_Store *store, OH_VBucket *row, OH_Predicates *predicates, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)](#oh_rdb_updatewithreturning) | - | Updates data in the database based on specified conditions and output change info to context. |
| [int OH_Rdb_DeleteWithReturning(OH_Rdb_Store *store, OH_Predicates *predicates, OH_RDB_ReturningContext *context)](#oh_rdb_deletewithreturning) | - | Deletes data from the database based on specified conditions and output change info to context. |

### Variable

| Name | Description |
| -- | -- |
| void (*Rdb_BriefObserver)(void *context, const char *values[], uint32_t count) | The callback function of cloud data change event.<br>**Since**: 11 |
| void (*Rdb_DetailsObserver)(void *context, const Rdb_ChangeInfo **changeInfo, uint32_t count) | The callback function of cloud data change details event.<br>**Since**: 11 |
| void (*Rdb_ProgressCallback)(void *context, Rdb_ProgressDetails *progressDetails) | The callback function of progress.<br>**Since**: 11 |
| void (*Rdb_SyncCallback)(Rdb_ProgressDetails *progressDetails) | The callback function of sync.<br>**Since**: 11 |
| void (*Rdb_CorruptedHandler)(void *context, OH_Rdb_ConfigV2 *config, OH_Rdb_Store *store) | The callback function of database corruption handle.<br>**Since**: 22 |

## Enum type description

### OH_Rdb_SecurityLevel

```c
enum OH_Rdb_SecurityLevel
```

**Description**

Describe the security level of the database.

**Since**: 10

| Enum item | Description |
| -- | -- |
| S1 = 1 | Low-level security. Data leaks have a minor impact. |
| S2 | Medium-level security. Data leaks have a major impact. |
| S3 | High-level security. Data leaks have a severe impact. |
| S4 | Critical-level security. Data leaks have a critical impact. |

### Rdb_SecurityArea

```c
enum Rdb_SecurityArea
```

**Description**

Describe the security area of the database.

**Since**: 11

| Enum item | Description |
| -- | -- |
| RDB_SECURITY_AREA_EL1 = 1 | Security Area 1. |
| RDB_SECURITY_AREA_EL2 | Security Area 2. |
| RDB_SECURITY_AREA_EL3 | Security Area 3. |
| RDB_SECURITY_AREA_EL4 | Security Area 4. |
| RDB_SECURITY_AREA_EL5 | Security Area 5.<br>**Since**: 12 |

### Rdb_DBType

```c
enum Rdb_DBType
```

**Description**

Define Rdb_DBType type.

**Since**: 14

| Enum item | Description |
| -- | -- |
| RDB_SQLITE = 1 | Means using SQLITE as the db kernel<br>**Since**: 14 |
| RDB_CAYLEY = 2 | Means using CAYLEY_DB as the db kernel<br>**Since**: 14 |
| DBTYPE_BUTT = 64 | Means largest value for Rdb_DBType<br>**Since**: 14 |

### Rdb_Tokenizer

```c
enum Rdb_Tokenizer
```

**Description**

Define Rdb_Tokenizer type.

**Since**: 17

| Enum item | Description |
| -- | -- |
| RDB_NONE_TOKENIZER = 1 | Means not using tokenizer. <br>**Since**: 17 |
| RDB_ICU_TOKENIZER = 2 | Means using native icu tokenizer. <br>**Since**: 17 |
| RDB_CUSTOM_TOKENIZER = 3 | Means using self-developed enhance tokenizer. <br>**Since**: 18 |

### Rdb_DistributedType

```c
enum Rdb_DistributedType
```

**Description**

Describes the distribution type of the tables.

**Since**: 11

| Enum item | Description |
| -- | -- |
| RDB_DISTRIBUTED_CLOUD | Indicates the table is distributed among the devices. |

### Rdb_ChangeType

```c
enum Rdb_ChangeType
```

**Description**

Describes the change type.

**Since**: 11

| Enum item | Description |
| -- | -- |
| RDB_DATA_CHANGE | Means the change type is data change. |
| RDB_ASSET_CHANGE | Means the change type is asset change. |

### Rdb_SubscribeType

```c
enum Rdb_SubscribeType
```

**Description**

Indicates the subscribe type.

**Since**: 11

| Enum item | Description |
| -- | -- |
| RDB_SUBSCRIBE_TYPE_CLOUD | Subscription to cloud data changes. |
| RDB_SUBSCRIBE_TYPE_CLOUD_DETAILS | Subscription to cloud data change details. |
| RDB_SUBSCRIBE_TYPE_LOCAL_DETAILS | Subscription to local data change details.<br>**Since**: 12 |

### Rdb_SyncMode

```c
enum Rdb_SyncMode
```

**Description**

Indicates the database synchronization mode.

**Since**: 11

| Enum item | Description |
| -- | -- |
| RDB_SYNC_MODE_TIME_FIRST | Indicates that data is synchronized from the end with the closest modification time to the end with a more distant modification time. |
| RDB_SYNC_MODE_NATIVE_FIRST | Indicates that data is synchronized from local to cloud. |
| RDB_SYNC_MODE_CLOUD_FIRST | Indicates that data is synchronized from cloud to local. |

### Rdb_Progress

```c
enum Rdb_Progress
```

**Description**

| Enum item | Description |
| -- | -- |
| RDB_SYNC_BEGIN | Means the sync process begin. |
| RDB_SYNC_IN_PROGRESS | Means the sync process is in progress |
| RDB_SYNC_FINISH | Means the sync process is finished |


## Function description

### OH_Rdb_CreateConfig()

```c
OH_Rdb_ConfigV2 *OH_Rdb_CreateConfig()
```

**Description**

Create OH_Rdb_ConfigV2 which is used to open store

**Since**: 14

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Rdb_ConfigV2 *](capi-rdb-oh-rdb-configv2.md) | Returns the newly created OH_Rdb_ConfigV2 object. If NULL is returned, the creation fails.  The possible cause is that the address space of the application is full, As a result, the space  cannot be allocated. |

**Reference**:

[OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md)


### OH_Rdb_DestroyConfig()

```c
int OH_Rdb_DestroyConfig(OH_Rdb_ConfigV2 *config)
```

**Description**

Destroy OH_Rdb_ConfigV2 which is created by OH_Rdb_CreateConfig

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetDatabaseDir()

```c
int OH_Rdb_SetDatabaseDir(OH_Rdb_ConfigV2 *config, const char *databaseDir)
```

**Description**

Set property databaseDir into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| const char *databaseDir | Indicates the directory of the database. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetStoreName()

```c
int OH_Rdb_SetStoreName(OH_Rdb_ConfigV2 *config, const char *storeName)
```

**Description**

Set property storeName into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| const char *storeName | Indicates the name of the database. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetBundleName()

```c
int OH_Rdb_SetBundleName(OH_Rdb_ConfigV2 *config, const char *bundleName)
```

**Description**

Set property bundleName into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| const char *bundleName | Indicates the bundle name of the application |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetModuleName()

```c
int OH_Rdb_SetModuleName(OH_Rdb_ConfigV2 *config, const char *moduleName)
```

**Description**

Set property moduleName into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| const char *moduleName | Indicates the module name of the application. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetEncrypted()

```c
int OH_Rdb_SetEncrypted(OH_Rdb_ConfigV2 *config, bool isEncrypted)
```

**Description**

Set property isEncrypted into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| bool isEncrypted | Indicates whether the database is encrypted. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetSecurityLevel()

```c
int OH_Rdb_SetSecurityLevel(OH_Rdb_ConfigV2 *config, int securityLevel)
```

**Description**

Set property securityLevel into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| int securityLevel | Indicates the security level [OH_Rdb_SecurityLevel](capi-relational-store-h.md#oh_rdb_securitylevel) of the database. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetArea()

```c
int OH_Rdb_SetArea(OH_Rdb_ConfigV2 *config, int area)
```

**Description**

Set property area into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store |
| int area | Represents the security area of the database. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetDbType()

```c
int OH_Rdb_SetDbType(OH_Rdb_ConfigV2 *config, int dbType)
```

**Description**

Set property dbType into config

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. |
| int dbType | Indicates the dbType [Rdb_DBType](capi-relational-store-h.md#rdb_dbtype) of the database |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    {@link RDB_E_NOT_SUPPORTED} - The error code for not support db types. |

### OH_Rdb_SetCustomDir()

```c
int OH_Rdb_SetCustomDir(OH_Rdb_ConfigV2 *config, const char *customDir)
```

**Description**

Sets the customized directory relative to the database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to a configuration of the database related to this relation database store. |
| const char *customDir | Represents the customized relative to the database directory, the value cannot exceed 128 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Rdb_SetReadOnly()

```c
int OH_Rdb_SetReadOnly(OH_Rdb_ConfigV2 *config, bool readOnly)
```

**Description**

Sets the relation database store is read-only mode.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to a configuration of the database related to this relation database store. |
| bool readOnly | Represents whether the relation database store is read-only. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Rdb_SetPlugins()

```c
int OH_Rdb_SetPlugins(OH_Rdb_ConfigV2 *config, const char **plugins, int32_t length)
```

**Description**

Sets the dynamic libraries with capabilities such as Full-Text Search (FTS).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to a configuration of the database related to this relation database store. |
| const char **plugins | Represents the dynamic libraries. |
| int32_t length | the size of plugins that the maximum value is 16. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Rdb_SetCryptoParam()

```c
int OH_Rdb_SetCryptoParam(OH_Rdb_ConfigV2 *config, const OH_Rdb_CryptoParam *cryptoParam)
```

**Description**

Sets the custom encryption parameters.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to a configuration of the database related to this relation database store. |
| const OH_Rdb_CryptoParam *cryptoParam | Represents the custom encryption parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter. |

### OH_Rdb_SetTokenizer()

```c
int OH_Rdb_SetTokenizer(OH_Rdb_ConfigV2 *config, Rdb_Tokenizer tokenizer)
```

**Description**

Set property tokenizer into config

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. |
| [Rdb_Tokenizer](capi-relational-store-h.md#rdb_tokenizer) tokenizer | Indicates the tokenizer [Rdb_Tokenizer](capi-relational-store-h.md#rdb_tokenizer) of the database |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    {@link RDB_E_NOT_SUPPORTED} - The error code for not support tokenizer. |

### OH_Rdb_SetPersistent()

```c
int OH_Rdb_SetPersistent(OH_Rdb_ConfigV2 *config, bool isPersistent)
```

**Description**

Set property persist into config

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| bool isPersistent | Indicates whether the database need persistence. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_SetSemanticIndex()

```c
int OH_Rdb_SetSemanticIndex(OH_Rdb_ConfigV2 *config, bool enableSemanticIndex)
```

**Description**

Set whether the database enable the capabilities for semantic indexing processing.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| bool enableSemanticIndex | Indicates whether the database enable the capabilities for semantic indexing processing. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

### OH_Rdb_IsTokenizerSupported()

```c
int OH_Rdb_IsTokenizerSupported(Rdb_Tokenizer tokenizer, bool *isSupported)
```

**Description**

Check if a tokenizer is supported or not.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Rdb_Tokenizer](capi-relational-store-h.md#rdb_tokenizer) tokenizer | the tokenizer type of [Rdb_Tokenizer](capi-relational-store-h.md#rdb_tokenizer). |
| bool *isSupported | Pointer to the Boolean value obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          {@link RDB_OK} indicates the operation is successful.<br>        {@link RDB_E_INVALID_ARGS} indicates invalid args are passed in. |

### OH_Rdb_GetSupportedDbType()

```c
const int *OH_Rdb_GetSupportedDbType(int *typeCount)
```

**Description**

Get support db type list

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| int *typeCount | The output parameter, which is used to receive the length of the support db type array. |

**Returns**:

| Type | Description |
| -- | -- |
| const int * | Return Rdb_DBType array contains supported db type, array length is number of support type |

### OH_Rdb_CreateValueObject()

```c
OH_VObject *OH_Rdb_CreateValueObject()
```

**Description**

Creates an {@link OH_VObject} instance.

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| OH_VObject * | If the creation is successful, a pointer to the instance of the @link OH_VObject} structure is returned,  otherwise NULL is returned. |

**Reference**:

OH_VObject


### OH_Rdb_CreateValuesBucket()

```c
OH_VBucket *OH_Rdb_CreateValuesBucket()
```

**Description**

Creates an {@link OH_VBucket} object.

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| OH_VBucket * | If the creation is successful, a pointer to the instance of the @link OH_VBucket} structure is returned,  otherwise NULL is returned. |

**Reference**:

OH_VBucket


### OH_Rdb_CreatePredicates()

```c
OH_Predicates *OH_Rdb_CreatePredicates(const char *table)
```

**Description**

Creates an {@link OH_Predicates} instance.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *table | Indicates the table name. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Predicates * | If the creation is successful, a pointer to the instance of the @link OH_Predicates} structure is returned.          If the table name is nullptr, Nullptr is returned. |

**Reference**:

OH_Predicates


### OH_Rdb_GetOrOpen()

```c
OH_Rdb_Store *OH_Rdb_GetOrOpen(const OH_Rdb_Config *config, int *errCode)
```

**Description**

Obtains an RDB store.<br> You can set parameters of the RDB store as required. In general, this method is recommended to obtain a rdb store.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Rdb_Config](capi-rdb-oh-rdb-config.md) *config | Represents a pointer to an [OH_Rdb_Config](capi-rdb-oh-rdb-config.md) instance. Indicates the configuration of the database related to this RDB store. |
| int *errCode | This parameter is the output parameter, and the execution status of a function is written to this variable. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Rdb_Store *](capi-rdb-oh-rdb-store.md) | If the creation is successful, a pointer to the instance of the @link OH_Rdb_Store} structure is returned.          If the Config is empty, config.size does not match, or errCode is empty.  Get database path failed.Get RDB Store fail. Nullptr is returned. |

**Reference**:

OH_Rdb_Config, OH_Rdb_Store


### OH_Rdb_CreateOrOpen()

```c
OH_Rdb_Store *OH_Rdb_CreateOrOpen(const OH_Rdb_ConfigV2 *config, int *errCode)
```

**Description**

Obtains an RDB store with OH_Rdb_ConfigV2.<br> You can set parameters of the RDB store as required. In general, this method is recommended to obtain a rdb store.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to an [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |
| int *errCode | This parameter is the output parameter, and the execution status of a function is written to this variable. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Rdb_Store *](capi-rdb-oh-rdb-store.md) | If the creation is successful, a pointer to the instance of the @link OH_Rdb_Store} structure is returned.          If the Config is empty, config.size does not match, or errCode is empty.  Get database path failed.Get RDB Store fail. Nullptr is returned. |

**Reference**:

OH_Rdb_ConfigV2, OH_Rdb_Store


### OH_Rdb_CloseStore()

```c
int OH_Rdb_CloseStore(OH_Rdb_Store *store)
```

**Description**

Close the [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) object and reclaim the memory occupied by the object.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>while failure returns a specific error code. Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store, OH_Rdb_ErrCode


### OH_Rdb_DeleteStore()

```c
int OH_Rdb_DeleteStore(const OH_Rdb_Config *config)
```

**Description**

Deletes the database with a specified path.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Rdb_Config](capi-rdb-oh-rdb-config.md) *config | Represents a pointer to an [OH_Rdb_Config](capi-rdb-oh-rdb-config.md) instance. Indicates the configuration of the database related to this RDB store. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>while failure returns a specific error code. Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_ErrCode


### OH_Rdb_DeleteStoreV2()

```c
int OH_Rdb_DeleteStoreV2(const OH_Rdb_ConfigV2 *config)
```

**Description**

Deletes the database with a specified path.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to an [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) instance. Indicates the configuration of the database related to this RDB store. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>while failure returns a specific error code. Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_ErrCode


### OH_Rdb_Insert()

```c
int OH_Rdb_Insert(OH_Rdb_Store *store, const char *table, OH_VBucket *valuesBucket)
```

**Description**

Inserts a row of data into the target table.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *table | Indicates the target table. |
| OH_VBucket *valuesBucket | Indicates the row of data {@link OH_VBucket} to be inserted into the table. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the rowId if success, returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store, OH_VBucket, OH_Rdb_ErrCode


### OH_Rdb_InsertWithConflictResolution()

```c
int OH_Rdb_InsertWithConflictResolution(OH_Rdb_Store *store, const char *table, OH_VBucket *row, Rdb_ConflictResolution resolution, int64_t *rowId)
```

**Description**

Inserts a row of data into the target table and support conflict resolution.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an OH_Rdb_Store instance. |
| const char *table | Represents the target table. |
| OH_VBucket *row | Represents the row data to be inserted into the table. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| int64_t *rowId | Represents the number of successful insertion. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

### OH_Rdb_BatchInsert()

```c
int OH_Rdb_BatchInsert(OH_Rdb_Store *store, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, int64_t *changes)
```

**Description**

Inserts a batch of data into the target table.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *table | Represents the target table. |
| const OH_Data_VBuckets *rows | Represents the rows data to be inserted into the table. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| int64_t *changes | Represents the number of successful insertions. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

### OH_Rdb_Update()

```c
int OH_Rdb_Update(OH_Rdb_Store *store, OH_VBucket *valuesBucket, OH_Predicates *predicates)
```

**Description**

Updates data in the database based on specified conditions.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_VBucket *valuesBucket | Indicates the row of data {@link OH_VBucket} to be updated in the database |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. Indicates the specified update condition. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the number of rows changed if success, otherwise, returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store, OH_Bucket, OH_Predicates, OH_Rdb_ErrCode


### OH_Rdb_UpdateWithConflictResolution()

```c
int OH_Rdb_UpdateWithConflictResolution(OH_Rdb_Store *store, OH_VBucket *row, OH_Predicates *predicates, Rdb_ConflictResolution resolution, int64_t *changes)
```

**Description**

Updates data in the database based on specified conditions and support conflict resolution.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an OH_Rdb_Store instance. |
| OH_VBucket *row | Represents the row data to be inserted into the table. |
| OH_Predicates *predicates | Represents  a pointer to an link OH_Predicates instance. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| int64_t *changes | Represents the number of successful update. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

### OH_Rdb_Delete()

```c
int OH_Rdb_Delete(OH_Rdb_Store *store, OH_Predicates *predicates)
```

**Description**

Deletes data from the database based on specified conditions.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. Indicates the specified delete condition. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the number of rows changed if success, otherwise, returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store, OH_Predicates, OH_Rdb_ErrCode


### OH_Rdb_Query()

```c
OH_Cursor *OH_Rdb_Query(OH_Rdb_Store *store, OH_Predicates *predicates, const char *const *columnNames, int length)
```

**Description**

Queries data in the database based on specified conditions.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. Indicates the specified query condition. |
| const char *const *columnNames | Indicates the columns to query. If the value is empty array, the query applies to all columns. |
| int length | Indicates the length of columnNames. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the query is successful, a pointer to the instance of the @link OH_Cursor} structure is returned.          If Get store failed or resultSet is nullptr, nullptr is returned. |

**Reference**:

OH_Rdb_Store, OH_Predicates, OH_Cursor


### OH_Rdb_QueryWithoutRowCount()

```c
OH_Cursor *OH_Rdb_QueryWithoutRowCount(OH_Rdb_Store *store, OH_Predicates *predicates, const char *const columns[], int length)
```

**Description**

Queries data in the database based on specified conditions without row count.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. Indicates the specified query condition. |
| const char *const columns[] | Indicates the columns to query. If the value is empty array, the query applies to all columns. |
| int length | Indicates the length of columns. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the query is successful, a pointer to the instance of the {@link OH_Cursor} structure is returned.          If Get store failed or resultSet is nullptr, nullptr is returned. |

**Reference**:

OH_Rdb_Store, OH_Predicates, OH_Cursor


### OH_Rdb_QuerySqlWithoutRowCount()

```c
OH_Cursor *OH_Rdb_QuerySqlWithoutRowCount(OH_Rdb_Store *store, const char *sql, const OH_Data_Values *args)
```

**Description**

Queries data in the database based on an SQL statement without row count.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *sql | Indicates the SQL statement to execute. |
| const OH_Data_Values *args | Represents a pointer to an instance of OH_Data_Values and  it is the selection arguments. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the query is successful, a pointer to the instance of the {@link OH_Cursor} structure is returned.          If sql statement is invalid or the memory allocate failed, nullptr is returned. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_Execute()

```c
int OH_Rdb_Execute(OH_Rdb_Store *store, const char *sql)
```

**Description**

Executes an SQL statement.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *sql | Indicates the SQL statement to execute. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_ExecuteV2()

```c
int OH_Rdb_ExecuteV2(OH_Rdb_Store *store, const char *sql, const OH_Data_Values *args, OH_Data_Value **result)
```

**Description**

Executes an SQL statement.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *sql | Indicates the SQL statement to execute. |
| const OH_Data_Values *args | Represents the values of the parameters in the SQL statement. |
| OH_Data_Value **result | Represents a pointer to OH_Data_Value instance when the execution is successful. The memory must be released through the OH_Value_Destroy interface after the use is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch. |

**Reference**:

OH_Value_Destroy


### OH_Rdb_ExecuteByTrxId()

```c
int OH_Rdb_ExecuteByTrxId(OH_Rdb_Store *store, int64_t trxId, const char *sql)
```

**Description**

Write operations are performed using the specified transaction represented by the transaction ID

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| int64_t trxId | The transaction ID of the specified transaction, must be greater than 0 |
| const char *sql | Indicates the SQL statement to execute. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    {@link RDB_E_NOT_SUPPORTED} - The error code for not support. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_ExecuteQuery()

```c
OH_Cursor *OH_Rdb_ExecuteQuery(OH_Rdb_Store *store, const char *sql)
```

**Description**

Queries data in the database based on an SQL statement.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *sql | Indicates the SQL statement to execute. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the query is successful, a pointer to the instance of the @link OH_Cursor} structure is returned.          If Get store failed,sql is nullptr or resultSet is nullptr, nullptr is returned. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_ExecuteQueryV2()

```c
OH_Cursor *OH_Rdb_ExecuteQueryV2(OH_Rdb_Store *store, const char *sql, const OH_Data_Values *args)
```

**Description**

Queries data in the database based on an SQL statement.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *sql | Indicates the SQL statement to execute. |
| const OH_Data_Values *args | Represents a pointer to an instance of OH_Data_Values and  it is the selection arguments. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the query is successful, a pointer to the instance of the @link OH_Cursor} structure is returned.          If sql statement is invalid or the memory allocate failed, nullptr is returned. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_BeginTransaction()

```c
int OH_Rdb_BeginTransaction(OH_Rdb_Store *store)
```

**Description**

Begins a transaction in EXCLUSIVE mode.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_RollBack()

```c
int OH_Rdb_RollBack(OH_Rdb_Store *store)
```

**Description**

Rolls back a transaction in EXCLUSIVE mode.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_Commit()

```c
int OH_Rdb_Commit(OH_Rdb_Store *store)
```

**Description**

Commits a transaction in EXCLUSIVE mode.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_BeginTransWithTrxId()

```c
int OH_Rdb_BeginTransWithTrxId(OH_Rdb_Store *store, int64_t *trxId)
```

**Description**

Begin a transaction and the transaction ID corresponding to the transaction.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| int64_t *trxId | The output parameter, which is used to receive the transaction ID corresponding to the transaction |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    {@link RDB_E_NOT_SUPPORTED} - The error code for not support. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_RollBackByTrxId()

```c
int OH_Rdb_RollBackByTrxId(OH_Rdb_Store *store, int64_t trxId)
```

**Description**

Roll back a transaction that is represented by a specified transaction ID

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| int64_t trxId | The transaction ID of the specified transaction, must be greater than 0 |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    {@link RDB_E_NOT_SUPPORTED} - The error code for not support. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_CommitByTrxId()

```c
int OH_Rdb_CommitByTrxId(OH_Rdb_Store *store, int64_t trxId)
```

**Description**

Commit a transaction that is represented by a specified transaction ID

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| int64_t trxId | The transaction ID of the specified transaction, must be greater than 0 |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    {@link RDB_E_NOT_SUPPORTED} - The error code for not support. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_Backup()

```c
int OH_Rdb_Backup(OH_Rdb_Store *store, const char *databasePath)
```

**Description**

Backs up a database on specified path.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *databasePath | Indicates the database file path. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_Restore()

```c
int OH_Rdb_Restore(OH_Rdb_Store *store, const char *databasePath)
```

**Description**

Restores a database from a specified database file.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *databasePath | Indicates the database file path. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_GetVersion()

```c
int OH_Rdb_GetVersion(OH_Rdb_Store *store, int *version)
```

**Description**

Gets the version of a database.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| int *version | Indicates the version number. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_SetVersion()

```c
int OH_Rdb_SetVersion(OH_Rdb_Store *store, int version)
```

**Description**

Sets the version of a database.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| int version | Indicates the version number. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store


### OH_Rdb_SetDistributedTables()

```c
int OH_Rdb_SetDistributedTables(OH_Rdb_Store *store, const char *tables[], uint32_t count, Rdb_DistributedType type, const Rdb_DistributedConfig *config)
```

**Description**

Set table to be distributed table.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *tables[] | Indicates the table names you want to set. |
| uint32_t count | Indicates the count of tables you want to set. |
| [Rdb_DistributedType](capi-relational-store-h.md#rdb_distributedtype) type | Indicates the distributed type [Rdb_DistributedType](capi-relational-store-h.md#rdb_distributedtype). |
| [const Rdb_DistributedConfig](capi-rdb-rdb-distributedconfig.md) *config | Indicates the distributed config of the tables. For details, see [Rdb_DistributedConfig](capi-rdb-rdb-distributedconfig.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store
Rdb_DistributedConfig


### OH_Rdb_FindModifyTime()

```c
OH_Cursor *OH_Rdb_FindModifyTime(OH_Rdb_Store *store, const char *tableName, const char *columnName, OH_VObject *values)
```

**Description**

Set table to be distributed table.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *tableName | Indicates the name of the table to check. |
| const char *columnName | Indicates the name of the column corresponding to the primary key. If the table has no primary key , please pass in "rowid". |
| OH_VObject *values | Indicates the primary keys of the rows to check. If the table has no primary key , please pass in the row-ids of the rows to check. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the operation is successful, a pointer to the instance of the @link OH_Cursor} structure is returned.          If Get store failed, NULL is returned.  There are two columns, "data_key" and "timestamp". Otherwise NULL is returned. |

**Reference**:

OH_Rdb_Store
OH_VObject
OH_Cursor


### Rdb_BriefObserver()

```c
typedef void (*Rdb_BriefObserver)(void *context, const char *values[], uint32_t count)
```

**Description**

The callback function of cloud data change event.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*context | Represents the context of data observer. |
| const char \*values[] | Indicates the cloud accounts that changed. |
| uint32_t count | The count of changed cloud accounts. |

### Rdb_DetailsObserver()

```c
typedef void (*Rdb_DetailsObserver)(void *context, const Rdb_ChangeInfo **changeInfo, uint32_t count)
```

**Description**

The callback function of cloud data change details event.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*context | Represents the context of data observer. |
| [const Rdb_ChangeInfo](capi-rdb-rdb-changeinfo.md) \*\*changeInfo | Indicates the [Rdb_ChangeInfo](capi-rdb-rdb-changeinfo.md) of changed tables. |
| uint32_t count | The count of changed tables. |

**Reference**:

Rdb_ChangeInfo


### OH_Rdb_Subscribe()

```c
int OH_Rdb_Subscribe(OH_Rdb_Store *store, Rdb_SubscribeType type, const Rdb_DataObserver *observer)
```

**Description**

Registers an observer for the database. When data in the distributed database or the local database changes, the callback will be invoked.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| [Rdb_SubscribeType](capi-relational-store-h.md#rdb_subscribetype) type | Indicates the subscription type, which is defined in [Rdb_SubscribeType](capi-relational-store-h.md#rdb_subscribetype). If its value is RDB_SUBSCRIBE_TYPE_LOCAL_DETAILS, the callback will be invoked for data changes in the local database. |
| [const Rdb_DataObserver](capi-rdb-rdb-dataobserver.md) *observer | The [Rdb_DataObserver](capi-rdb-rdb-dataobserver.md) of change events in the database. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store
Rdb_DataObserver


### OH_Rdb_Unsubscribe()

```c
int OH_Rdb_Unsubscribe(OH_Rdb_Store *store, Rdb_SubscribeType type, const Rdb_DataObserver *observer)
```

**Description**

Remove specified observer of specified type from the database.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| [Rdb_SubscribeType](capi-relational-store-h.md#rdb_subscribetype) type | Indicates the subscription type, which is defined in [Rdb_SubscribeType](capi-relational-store-h.md#rdb_subscribetype). |
| [const Rdb_DataObserver](capi-rdb-rdb-dataobserver.md) *observer | The [Rdb_DataObserver](capi-rdb-rdb-dataobserver.md) of change events in the database. If this is nullptr, remove all observers of the type. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store
Rdb_DataObserver


### OH_Rdb_GetTableDetails()

```c
Rdb_TableDetails *OH_Rdb_GetTableDetails(Rdb_ProgressDetails *progress, int32_t version)
```

**Description**

Get table details from progress details.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md) *progress | Represents a pointer to an [Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md) instance. |
| int32_t version | Indicates the version of current [Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [Rdb_TableDetails *](capi-rdb-rdb-tabledetails.md) | If the operation is successful, a pointer to the instance of the [Rdb_TableDetails](capi-rdb-rdb-tabledetails.md)  structure is returned.If get details is failed, nullptr is returned. |

**Reference**:

[Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md)
[Rdb_TableDetails](capi-rdb-rdb-tabledetails.md)


### Rdb_ProgressCallback()

```c
typedef void (*Rdb_ProgressCallback)(void *context, Rdb_ProgressDetails *progressDetails)
```

**Description**

The callback function of progress.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*context | Represents user-provided data context, which will be passed back into the function when invoked. |
| [Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md) \*progressDetails | The details of the sync progress. |

**Reference**:

Rdb_ProgressDetails


### Rdb_SyncCallback()

```c
typedef void (*Rdb_SyncCallback)(Rdb_ProgressDetails *progressDetails)
```

**Description**

The callback function of sync.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Rdb_ProgressDetails](capi-rdb-rdb-progressdetails.md) \*progressDetails | The details of the sync progress. |

**Reference**:

Rdb_ProgressDetails


### OH_Rdb_CloudSync()

```c
int OH_Rdb_CloudSync(OH_Rdb_Store *store, Rdb_SyncMode mode, const char *tables[], uint32_t count, const Rdb_ProgressObserver *observer)
```

**Description**

Sync data to cloud.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| [Rdb_SyncMode](capi-relational-store-h.md#rdb_syncmode) mode | Represents the [Rdb_SyncMode](capi-relational-store-h.md#rdb_syncmode) of sync progress. |
| const char *tables[] | Indicates the names of tables to sync. |
| uint32_t count | The count of tables to sync. If value equals 0, sync all tables of the store. |
| [const Rdb_ProgressObserver](capi-rdb-rdb-progressobserver.md) *observer | The [Rdb_ProgressObserver](capi-rdb-rdb-progressobserver.md) of cloud sync progress. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store
Rdb_ProgressObserver


### OH_Rdb_SubscribeAutoSyncProgress()

```c
int OH_Rdb_SubscribeAutoSyncProgress(OH_Rdb_Store *store, const Rdb_ProgressObserver *observer)
```

**Description**

Subscribes to the automatic synchronization progress of an RDB store. A callback will be invoked when there is a notification of the automatic synchronization progress.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Indicates the pointer to the target [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| [const Rdb_ProgressObserver](capi-rdb-rdb-progressobserver.md) *observer | The [Rdb_ProgressObserver](capi-rdb-rdb-progressobserver.md) for the automatic synchronization progress. Indicates the callback invoked to return the automatic synchronization progress. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store
Rdb_ProgressObserver


### OH_Rdb_UnsubscribeAutoSyncProgress()

```c
int OH_Rdb_UnsubscribeAutoSyncProgress(OH_Rdb_Store *store, const Rdb_ProgressObserver *observer)
```

**Description**

Unsubscribes from the automatic synchronization progress of an RDB store.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Indicates the pointer to the target [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| [const Rdb_ProgressObserver](capi-rdb-rdb-progressobserver.md) *observer | Indicates the [Rdb_ProgressObserver](capi-rdb-rdb-progressobserver.md) callback for the automatic synchronization progress. If it is a null pointer, all callbacks for the automatic synchronization progress will be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store
Rdb_ProgressObserver


### OH_Rdb_LockRow()

```c
int OH_Rdb_LockRow(OH_Rdb_Store *store, OH_Predicates *predicates)
```

**Description**

Lock data from the database based on specified conditions.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. Indicates the specified lock condition. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store, OH_Predicates, OH_Rdb_ErrCode


### OH_Rdb_UnlockRow()

```c
int OH_Rdb_UnlockRow(OH_Rdb_Store *store, OH_Predicates *predicates)
```

**Description**

Unlock data from the database based on specified conditions.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. Indicates the specified unlock condition. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. See {@link OH_Rdb_ErrCode}.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args. |

**Reference**:

OH_Rdb_Store, OH_Predicates, OH_Rdb_ErrCode


### OH_Rdb_QueryLockedRow()

```c
OH_Cursor *OH_Rdb_QueryLockedRow(OH_Rdb_Store *store, OH_Predicates *predicates, const char *const *columnNames, int length)
```

**Description**

Queries locked data in the database based on specified conditions.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. Indicates the specified query condition. |
| const char *const *columnNames | Indicates the columns to query. If the value is empty array, the query applies to all columns. |
| int length | Indicates the length of columnNames. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Cursor * | If the query is successful, a pointer to the instance of the @link OH_Cursor} structure is returned.          If Get store failed or resultSet is nullptr, nullptr is returned. |

**Reference**:

OH_Rdb_Store, OH_Predicates, OH_Cursor


### OH_Rdb_CreateTransaction()

```c
int OH_Rdb_CreateTransaction(OH_Rdb_Store *store, const OH_RDB_TransOptions *options, OH_Rdb_Transaction **trans)
```

**Description**

Creates an OH_Rdb_Transaction instance object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an instance of OH_Rdb_Store. |
| const OH_RDB_TransOptions *options | Represents a pointer to an instance of OH_RDB_TransOptions. |
| OH_Rdb_Transaction **trans | Represents a pointer to OH_Rdb_Transaction instance when the execution is successful. Otherwise, nullptr is returned. The memory must be released through the OH_RdbTrans_Destroy interface after the use is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the error code.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_DATABASE_BUSY} database does not respond.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_CANT_OPEN} SQLite: Unable to open the database file. |

**Reference**:

OH_RdbTrans_Destroy


### OH_Rdb_Attach()

```c
int OH_Rdb_Attach(OH_Rdb_Store *store, const OH_Rdb_ConfigV2 *config, const char *attachName, int64_t waitTime, size_t *attachedNumber)
```

**Description**

Attaches a database file to the currently linked database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an OH_Rdb_Store instance. |
| [const OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to an OH_Rdb_ConfigV2 configuration of the database related to this RDB store. |
| const char *attachName | Represents the alias of the database. |
| int64_t waitTime | Represents the maximum time allowed for attaching the database, in seconds, valid range is 1 to 300. |
| size_t *attachedNumber | Represents the number of attached databases, It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_NOT_SUPPORTED} - The error code for not support.<br>        Returns {@link RDB_E_DATABASE_BUSY} database does not respond.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

### OH_Rdb_Detach()

```c
int OH_Rdb_Detach(OH_Rdb_Store *store, const char *attachName, int64_t waitTime, size_t *attachedNumber)
```

**Description**

Detaches a database from this database.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an OH_Rdb_Store instance. |
| const char *attachName | Represents the alias of the database. |
| int64_t waitTime | Represents the maximum time allowed for detaching the database, in seconds, valid range is 1 to 300. |
| size_t *attachedNumber | Represents the number of attached databases, It is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_NOT_SUPPORTED} - The error code for not support.<br>        Returns {@link RDB_E_DATABASE_BUSY} database does not respond.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation. |

**Reference**:

OH_Rdb_Store, OH_Rdb_ErrCode


### OH_Rdb_SetLocale()

```c
int OH_Rdb_SetLocale(OH_Rdb_Store *store, const char *locale)
```

**Description**

Support for collations in different languages.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *locale | Language related to the locale, for example, zh. The value complies with the ISO 639 standard. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      <br>{@link RDB_OK} if the execution is successful.<br>    <br>{@link RDB_ERR} - Indicates that the function execution exception.<br>    <br>{@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    <br>{@link RDB_E_ALREADY_CLOSED} database already closed.<br>    <br>{@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>    <br>{@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>    <br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store


### Rdb_CorruptedHandler()

```c
typedef void (*Rdb_CorruptedHandler)(void *context, OH_Rdb_ConfigV2 *config, OH_Rdb_Store *store)
```

**Description**

The callback function of database corruption handle.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*context | Represents the context corruption handler. |
| [OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) \*config | Represents a pointer to an OH_Rdb_ConfigV2 configuration of the database related to this RDB store. |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) \*store | Represents a pointer to an OH_Rdb_Store instance. |

### OH_Rdb_RegisterCorruptedHandler()

```c
int OH_Rdb_RegisterCorruptedHandler(const OH_Rdb_ConfigV2 *config, void *context, const Rdb_CorruptedHandler handler)
```

**Description**

Registers corrupted handler for the database.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to an OH_Rdb_ConfigV2 configuration of the database related to this RDB store. |
| void *context | Represents the context corruption handle. |
| [const Rdb_CorruptedHandler](capi-relational-store-h.md#rdb_corruptedhandler) handler | The callback function of database corruption handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} if the execution is successful.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>    {@link RDB_E_SUB_OVER_LIMIT} - Indicates the number of subscriptions exceeds the limit.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_RegisterCorruptedHandler


### OH_Rdb_UnregisterCorruptedHandler()

```c
int OH_Rdb_UnregisterCorruptedHandler(const OH_Rdb_ConfigV2 *config, void *context, const Rdb_CorruptedHandler handler)
```

**Description**

Unregisters corrupted handler for the database.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Rdb_ConfigV2](capi-rdb-oh-rdb-configv2.md) *config | Represents a pointer to an OH_Rdb_ConfigV2 configuration of the database related to this RDB store. |
| void *context | Represents the context corruption handle. |
| [const Rdb_CorruptedHandler](capi-relational-store-h.md#rdb_corruptedhandler) handler | The callback function of database corruption handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} if the execution is successful.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_UnregisterCorruptedHandler


### OH_Rdb_RekeyEx()

```c
int OH_Rdb_RekeyEx(OH_Rdb_Store *store, OH_Rdb_CryptoParam *param)
```

**Description**

Change the encrypted database key.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Rdb_CryptoParam *param | Represents a pointer to an instance of OH_Rdb_CryptoParam. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_ERROR} database common error.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_ALREADY_CLOSED} database already closed.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_PERM} SQLite: Access permission denied.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_NOMEM} SQLite: The database is out of memory.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full. |

### OH_Rdb_BatchInsertWithReturning()

```c
int OH_Rdb_BatchInsertWithReturning(OH_Rdb_Store *store, const char *table, const OH_Data_VBuckets *rows, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)
```

**Description**

Inserts a batch of data into the target table and output change info to context.<br> A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code RDB_E_INVALID_ARGS is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| const char *table | Represents the target table. |
| const OH_Data_VBuckets *rows | Represents the rows data to be inserted into the table. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| OH_RDB_ReturningContext *context | Represents a pointer to a pointer to an {@link OH_RDB_ReturningContext} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_NOT_SUPPORTED} The error code for not support.<br>        Returns {@link RDB_E_DATABASE_BUSY} The error code for database busy.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation.<br>        Returns {@link RDB_E_SQLITE_ERROR} SQLite error.<br>            Possible causes: syntax error, such as a table or column not existing.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store, OH_Data_VBuckets, OH_Rdb_ErrCode, OH_RDB_ReturningContext


### OH_Rdb_UpdateWithReturning()

```c
int OH_Rdb_UpdateWithReturning(OH_Rdb_Store *store, OH_VBucket *row, OH_Predicates *predicates, Rdb_ConflictResolution resolution, OH_RDB_ReturningContext *context)
```

**Description**

Updates data in the database based on specified conditions and output change info to context.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_VBucket *row | Represents the row data to be updated into the table. |
| OH_Predicates *predicates | Represents  a pointer to an {link OH_Predicates} instance. |
| Rdb_ConflictResolution resolution | Represents the resolution when conflict occurs. |
| OH_RDB_ReturningContext *context | Represents a pointer to a pointer to an {@link OH_RDB_ReturningContext} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_NOT_SUPPORTED} The error code for not support.<br>        Returns {@link RDB_E_EMPTY_VALUES_BUCKET} The error code for a values bucket is empty.<br>        Returns {@link RDB_E_DATABASE_BUSY} The error code for database busy.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_CONSTRAINT} SQLite: Abort due to constraint violation.<br>        Returns {@link RDB_E_SQLITE_ERROR} SQLite error.<br>            Possible causes: syntax error, such as a table or column not existing.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store, OH_Data_VBuckets, OH_Predicates, OH_Rdb_ErrCode, OH_RDB_ReturningContext


### OH_Rdb_DeleteWithReturning()

```c
int OH_Rdb_DeleteWithReturning(OH_Rdb_Store *store, OH_Predicates *predicates, OH_RDB_ReturningContext *context)
```

**Description**

Deletes data from the database based on specified conditions and output change info to context.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) *store | Represents a pointer to an [OH_Rdb_Store](capi-rdb-oh-rdb-store.md) instance. |
| OH_Predicates *predicates | Represents a pointer to an {@link OH_Predicates} instance. |
| OH_RDB_ReturningContext *context | Represents a pointer to an {@link OH_RDB_ReturningContext} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution.          Returns {@link RDB_OK} if the execution is successful.<br>        Returns {@link RDB_E_INVALID_ARGS} if invalid input parameter.<br>        Returns {@link RDB_E_WAL_SIZE_OVER_LIMIT} the WAL file size over default limit.<br>        Returns {@link RDB_E_NOT_SUPPORTED} The error code for not support.<br>        Returns {@link RDB_E_DATABASE_BUSY} The error code for database busy.<br>        Returns {@link RDB_E_SQLITE_FULL} SQLite: The database is full.<br>        Returns {@link RDB_E_SQLITE_CORRUPT} database corrupted.<br>        Returns {@link RDB_E_SQLITE_BUSY} SQLite: The database file is locked.<br>        Returns {@link RDB_E_SQLITE_LOCKED} SQLite: A table in the database is locked.<br>        Returns {@link RDB_E_SQLITE_READONLY} SQLite: Attempt to write a readonly database.<br>        Returns {@link RDB_E_SQLITE_IOERR} SQLite: Some kind of disk I/O error occurred.<br>        Returns {@link RDB_E_SQLITE_TOO_BIG} SQLite: TEXT or BLOB exceeds size limit.<br>        Returns {@link RDB_E_SQLITE_MISMATCH} SQLite: Data type mismatch.<br>        Returns {@link RDB_E_SQLITE_ERROR} SQLite error.<br>            Possible causes: syntax error, such as a table or column not existing.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

OH_Rdb_Store, OH_Predicates, OH_Rdb_ErrCode, OH_RDB_ReturningContext



