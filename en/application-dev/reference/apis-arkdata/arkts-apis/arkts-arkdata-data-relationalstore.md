# @ohos.data.relationalStore(RDB Store)

The relational database (RDB) manages data based on relational models. The **relationalStore** module provides a complete mechanism for managing local databases based on the underlying SQLite. You can use the APIs to perform operations such as adding, deleting, modifying, and querying data, and directly run SQL statements. In addition, you can obtain sendable data using [ResultSet.getSendableRow](arkts-arkdata-relationalstore-resultset-i.md#getsendablerow) and transfer the data across threads.

To ensure successful data access, limit the size of a data record to 2 MB. If a data record exceeds 2 MB, it can be inserted successfully but cannot be read.

Querying data from a large amount of data may take time or even cause application suspension. In this case, you can perform batch operations. For details, see [Batch Database Operations](../../../arkts-utils/batch-database-operations-guide.md). Moreover, observe the following:

- The number of data records to be queried at a time should not exceed 5000.  
- Use [TaskPool](../../apis-arkts/arkts-apis/arkts-arkts-taskpool.md) if there is a large amount of data needs to be queried.  
- Keep concatenated SQL statements as concise as possible.  
- Query data in batches.

The **relationalStore** module provides the following functionalities:

- [RdbPredicates](arkts-arkdata-data-relationalstore.md): provides predicates indicating the nature,  
feature, or relationship of a data entity in an RDB store. It is used to define the operation conditions for an RDB store.  
- [RdbStore](arkts-arkdata-data-relationalstore.md): provides APIs for managing data in an RDB store.  
- [ResultSet](arkts-arkdata-data-relationalstore.md): provides APIs for accessing the result set obtained  
from the RDB store.  
- [LiteResultSet](arkts-arkdata-data-relationalstore.md): provides APIs for accessing the result set  
obtained from the RDB store, such as [queryWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querywithoutrowcount) and [querySqlWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querysqlwithoutrowcount). Unlike [ResultSet](arkts-arkdata-data-relationalstore.md), **LiteResultSet** does not include the total number of rows in the query result.  
- [Transaction](arkts-arkdata-data-relationalstore.md): provides APIs for managing transaction objects.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleterdbstore) | Deletes the RDB store with the specified database file name. This API uses a promise to return the result. |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleterdbstore-1) | Deletes an RDB store. This API uses an asynchronous callback to return the result. |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleterdbstore-2) | Deletes an RDB store. This API uses a promise to return the result. |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleterdbstore-3) | Deletes an RDB store. This API uses a promise to return the result. |
| [getDeleteSqlInfo](arkts-arkdata-relationalstore-getdeletesqlinfo-f.md) | Obtains the SQL statement used to delete data. This API returns the result synchronously. |
| [getInsertSqlInfo](arkts-arkdata-relationalstore-getinsertsqlinfo-f.md) | Obtains the SQL statement used to insert data. This API returns the result synchronously. |
| [getQuerySqlInfo](arkts-arkdata-relationalstore-getquerysqlinfo-f.md) | Obtains the SQL statement used to query data. This API returns the result synchronously. |
| [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getrdbstore) | Obtains an RdbStore instance. You can set the **config** parameter as required and use **RdbStore** APIs to perform data operations. This API uses an asynchronous callback to return the result. |
| [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getrdbstore-1) | Obtains an RdbStore instance. You can set the **config** parameter as required and use **RdbStore** APIs to perform data operations. This API uses a promise to return the result. |
| [getRdbStoreSync](arkts-arkdata-relationalstore-getrdbstoresync-f.md) | Obtains a RDB store. You can set parameters of the RDB store as required. This is a synchronous method that blocks the thread until the RDB store is obtained. |
| [getUpdateSqlInfo](arkts-arkdata-relationalstore-getupdatesqlinfo-f.md) | Obtains the SQL statement used to update data. This API returns the result synchronously. |
| [isTokenizerSupported](arkts-arkdata-relationalstore-istokenizersupported-f.md) | Checks whether the specified tokenizer is supported. This API returns the result synchronously. |
| [isVectorSupported](arkts-arkdata-relationalstore-isvectorsupported-f.md) | Checks whether the system supports vector stores. |

### Classes

| Name | Description |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | Defines APIs to access the result set obtained by querying the RDB store. This result set is the collection of results returned with the **query()** method called. |
| [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Defines the predicates for an RDB store. This class determines whether the conditional expression for the RDB store is true or false. Multiple predicates statements can be concatenated by using **and()** by default. **RdbPredicates** cannot be passed across threads using Sendable. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c-sys.md) | Defines APIs to access the result set obtained by querying the RDB store. This result set is the collection of results returned with the **query()** method called. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [Asset](arkts-arkdata-relationalstore-asset-i.md) | Represents the asset (such as a document, image, or video). |
| [ChangeInfo](arkts-arkdata-relationalstore-changeinfo-i.md) | Defines a struct for the details about the device-cloud sync process. |
| [CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i.md) | Cloud sync configuration. |
| [CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md) | Represents the configuration of database encryption parameters. This configuration is valid only when **encrypt** of **StoreConfig** is set to **true** or the key is not empty. |
| [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md) | Defines a struct for distributed configuration of a table. |
| [ExceptionMessage](arkts-arkdata-relationalstore-exceptionmessage-i.md) | Represents an exception message about the SQL statement executed by the database. |
| [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) | Describes detail of the cloud sync `Progress`. |
| [RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md) | Provides APIs for managing data in an RDB store. |
| [Result](arkts-arkdata-relationalstore-result-i.md) | Records the number of affected data rows and the result set. |
| [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) | Provides APIs to access the result set obtained by querying the RDB store. This result set is the collection of results returned with the **query()** method called. |
| [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | Specifies the list of field names to return after returning-related APIs are called and the maximum number of records allowed in the result set. |
| [SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md) | Represents statistics about SQL statements executed by the database. |
| [SqlInfo](arkts-arkdata-relationalstore-sqlinfo-i.md) | Represents details about the SQL statement executed by the database. |
| [Statistic](arkts-arkdata-relationalstore-statistic-i.md) | Defines a struct for the device-cloud sync statistics of a database table. |
| [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) | Defines the RDB store configuration. |
| [SyncResult](arkts-arkdata-relationalstore-syncresult-i.md) | Indicates synchronization result. |
| [TableDetails](arkts-arkdata-relationalstore-tabledetails-i.md) | Defines a struct for statistics of device-cloud upload and download tasks of a database table. |
| [Transaction](arkts-arkdata-relationalstore-transaction-i.md) | Provides APIs for managing databases in transaction mode. A transaction object is created by using [createTransaction](arkts-arkdata-relationalstore-rdbstore-i.md#createtransaction). Operations on different transaction objects are isolated. For details about the transaction types, see [TransactionType](arkts-arkdata-relationalstore-transactiontype-e.md). |
| [TransactionOptions](arkts-arkdata-relationalstore-transactionoptions-i.md) | Represents the configuration of a transaction object. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i-sys.md) | Cloud sync configuration. |
| [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i-sys.md) | Defines a struct for distributed configuration of a table. |
| [DistributedInfo](arkts-arkdata-relationalstore-distributedinfo-i-sys.md) | Manages the distributed info of the table. |
| [RdbStore](arkts-arkdata-relationalstore-rdbstore-i-sys.md) | Provides APIs for managing data in an RDB store. |
| [Reference](arkts-arkdata-relationalstore-reference-i-sys.md) | Indicates the reference between tables. |
| [ResultSet](arkts-arkdata-relationalstore-resultset-i-sys.md) | Provides APIs to access the result set obtained by querying the RDB store. This result set is the collection of results returned with the **query()** method called. |
| [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i-sys.md) | Defines the RDB store configuration. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AssetConflictPolicy](arkts-arkdata-relationalstore-assetconflictpolicy-e.md) | Describes the asset conflict policy. |
| [AssetStatus](arkts-arkdata-relationalstore-assetstatus-e.md) | Enumerates the asset statuses. Use the enum name rather than the enum value. |
| [ChangeType](arkts-arkdata-relationalstore-changetype-e.md) | Enumerates data change types. Use the enum name rather than the enum value. |
| [ColumnType](arkts-arkdata-relationalstore-columntype-e.md) | Enumerates the types of the column data. Use the enum name rather than the enum value. |
| [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | Enumerates the resolutions used when a conflict occurs during data insertion or modification. Use the enum name rather than the enum value. |
| [DistributedTableType](arkts-arkdata-relationalstore-distributedtabletype-e.md) | Enumerates the distributed table types. Use the enum name rather than the enum value. This item is a database-level configuration. If a database contains multiple distributed tables, all tables must use the same distributed table type; switching the table type or upgrade tables is not supported. |
| [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | Enumerates the distributed database table types. Use the enum name rather than the enum value. |
| [EncryptionAlgo](arkts-arkdata-relationalstore-encryptionalgo-e.md) | Enumerates the encryption algorithms for the database. Use the enum name rather than the enum value. |
| [Field](arkts-arkdata-relationalstore-field-e.md) | Enumerates predicates used as query conditions. Use the enum name rather than the enum value. |
| [HmacAlgo](arkts-arkdata-relationalstore-hmacalgo-e.md) | Enumerates the HMAC algorithms for the database. Use the enum name rather than the enum value. |
| [KdfAlgo](arkts-arkdata-relationalstore-kdfalgo-e.md) | Enumerates the PBKDF2 algorithms for the database. Use the enum name rather than the enum value. |
| [Origin](arkts-arkdata-relationalstore-origin-e.md) | Enumerates the data sources. Use the enum name rather than the enum value. |
| [Progress](arkts-arkdata-relationalstore-progress-e.md) | Enumerates the stages in the device-cloud sync progress. Use the enum name rather than the enum value. |
| [ProgressCode](arkts-arkdata-relationalstore-progresscode-e.md) | Describes the status of `Progress`. |
| [RebuildType](arkts-arkdata-relationalstore-rebuildtype-e.md) | Enumerates the RDB store rebuild types. Use the enum name rather than the enum value. |
| [SecurityLevel](arkts-arkdata-relationalstore-securitylevel-e.md) | Enumerates the KV store security levels. Use the enum name rather than the enum value. You cannot change the security level of an RDB store from a higher level to a lower one. |
| [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md) | Enumerates the subscription types. Use the enum name rather than the enum value. |
| [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Defines the database synchronization mode. Use the enum name rather than the enum value. |
| [SyncResultCode](arkts-arkdata-relationalstore-syncresultcode-e.md) | Describes the status of device sync. |
| [Tokenizer](arkts-arkdata-relationalstore-tokenizer-e.md) | Enumerates tokenizers that can be used for FTS. Use the enum name rather than the enum value. |
| [TransactionType](arkts-arkdata-relationalstore-transactiontype-e.md) | Enumerates the types of transaction objects that can be created. Use the enum name rather than the enum value. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DistributedField](arkts-arkdata-relationalstore-distributedfield-e-sys.md) | Enumerates the DistributedField. |
| [DistributedOrigin](arkts-arkdata-relationalstore-distributedorigin-e-sys.md) | Describes the data origin sources. |
| [HAMode](arkts-arkdata-relationalstore-hamode-e-sys.md) | Enumerates the high availability modes of the RDB store. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [Assets](arkts-arkdata-relationalstore-assets-t.md) | Indicates several assets in one column |
| [ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md) | Indicates the primary key and UTC time of the modified rows. |
| [PRIKeyType](arkts-arkdata-relationalstore-prikeytype-t.md) | The type of the priority key can be number or string |
| [RowData](arkts-arkdata-relationalstore-rowdata-t.md) | Indicates a row of data with an array. |
| [RowsData](arkts-arkdata-relationalstore-rowsdata-t.md) | Indicates multiple rows of data with an array. |
| [UTCTime](arkts-arkdata-relationalstore-utctime-t.md) | The time is in UTC format. |
| [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Values in buckets are stored in key-value pairs, change {[key: string]: ValueType;} to Record&lt;string, ValueType&gt; |
| [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) | Indicates possible value types |
