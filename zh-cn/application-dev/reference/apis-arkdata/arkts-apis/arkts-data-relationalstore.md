# @ohos.data.relationalStore

关系型数据库（Relational Database，RDB）是一种基于关系模型来管理数据的数据库。关系型数据库基于SQLite组件提供了一套完整的对本地数据库进行管理的机制，对外提供了一系列的增、删、改、查等接口，也可以直接运行用户 输入的SQL语句来满足复杂的场景需要。支持通过[ResultSet.getSendableRow](arkts-arkdata-relationalstore-resultset-i.md#getSendableRow)方法获取Sendable数据，进行跨线程 传递。 为保证插入并读取数据成功，建议一条数据不超过2MB。如果数据超过2MB，插入操作将成功，读取操作将失败。 大数据量场景下查询数据可能会导致耗时长甚至应用卡死，如有相关操作可参考文档[批量数据写数据库场景](../../../arkts-utils/batch-database-operations-guide.md)，且有建议如下： - 单次查询数据量不超过5000条。 - 在[TaskPool](../../apis-arkts/arkts-apis/arkts-taskpool.md#@ohos.taskpool)中查询。 - 拼接SQL语句尽量简洁。 - 合理地分批次查询。 该模块提供以下关系型数据库相关的常用功能： - [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md#RdbPredicates)：数据库中用来代表数据实体的性质、特征或者数据实体之间关系的谓词，主要用来定义数据库的操作条件。 - [RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md#RdbStore)：提供管理关系数据库（RDB）方法的接口。 - [ResultSet](arkts-arkdata-relationalstore-resultset-i.md#ResultSet)：提供用户调用关系型数据库查询接口之后返回的结果集合。 - [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md#LiteResultSet)：提供用户调用关系型数据库 [queryWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#queryWithoutRowCount)、 [querySqlWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querySqlWithoutRowCount)等查询接口之后返回的结果集合。与 [ResultSet](arkts-arkdata-relationalstore-resultset-i.md#ResultSet)相比，LiteResultSet不包含查询结果的总行数信息。 - [Transaction](arkts-arkdata-relationalstore-transaction-i.md#Transaction)：提供管理事务对象的接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace relationalStore--><!--Device-unnamed-declare namespace relationalStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleteRdbStore) | 删除数据库文件，使用callback异步回调。 删除成功后，建议将数据库对象置为null。建立数据库时，若在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)中配置了自定义路径，则调用此接口进行删库无效，必须使用 [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleteRdbStore) 接口进行删库。 当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。 |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleteRdbStore) | 使用指定的数据库文件配置删除数据库，使用callback异步回调。 删除成功后，建议将数据库对象置为null。若数据库文件处于公共沙箱目录下，则删除数据库时必须使用该接口，当存在多个进程操作同一个数据库的情况，建议向其他进程发送数据库删除通知使其感知并处理。建立数据库时，若在 [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)中配置了自定义路径，则必须调用此接口进行删库。 当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。 |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleteRdbStore) | 删除数据库文件，使用Promise异步回调。 删除成功后，建议将数据库对象置为null。建立数据库时，若在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)中配置了自定义路径，则调用此接口进行删库无效，必须使用 [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleteRdbStore) 接口进行删库。 当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。 |
| [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md#deleteRdbStore) | 使用指定的数据库文件配置删除数据库，使用Promise异步回调。 删除成功后，建议将数据库对象置为null。若数据库文件处于公共沙箱目录下，则删除数据库时必须使用该接口，当存在多个进程操作同一个数据库的情况，建议向其他进程发送数据库删除通知使其感知并处理。建立数据库时，若在 [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)中配置了自定义路径，则必须调用此接口进行删库。 当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。 |
| [getDeleteSqlInfo](arkts-arkdata-relationalstore-getdeletesqlinfo-f.md#getDeleteSqlInfo) | 获取用于删除数据的SQL语句，此为同步接口。 |
| [getInsertSqlInfo](arkts-arkdata-relationalstore-getinsertsqlinfo-f.md#getInsertSqlInfo) | 获取用于插入数据的SQL语句，此为同步接口。 |
| [getQuerySqlInfo](arkts-arkdata-relationalstore-getquerysqlinfo-f.md#getQuerySqlInfo) | 获取用于查询数据的SQL语句，此为同步接口。 |
| [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getRdbStore) | 创建或打开已有的关系型数据库，开发者可以根据自己的需求配置config参数，然后通过RdbStore调用相关接口执行数据操作。使用callback异步回调。 对应沙箱路径下无数据库文件时，将创建数据库文件，文件创建位置详见[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)。对应路径下已有数据库文件时，将打开已有数据库文件。 开发者在创建数据库时，应谨慎配置是否进行数据库加密的参数[encrypt](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)，数据库创建后，禁止对该参数进行修改。 \| 当前打开数据库时配置的加密类型 \| 本设备上创建该数据库时的加密类型 \| 结果 \| \| ------- \| -------------------------------- \| ---- \| \| 非加密 \| 加密 \| 使用加密配置（encrypt=true）打开数据库。 \| \| 加密 \| 非加密 \| 使用非加密配置（encrypt=false）打开数据库。 \| getRdbStore支持多线程并发操作。 |
| [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getRdbStore) | 创建或打开已有的关系型数据库，开发者可以根据自己的需求配置config参数，然后通过RdbStore调用相关接口执行数据操作。使用Promise异步回调。 对应沙箱路径下无数据库文件时，将创建数据库文件，文件创建位置详见[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)。对应路径下已有数据库文件时，将打开已有数据库文件。 开发者在创建数据库时，应谨慎配置是否进行数据库加密的参数[encrypt](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)，数据库创建后，禁止对该参数进行修改。 \| 当前打开数据库时配置的加密类型 \| 本设备上创建该数据库时的加密类型 \| 结果 \| \| ------- \| -------------------------------- \| ---- \| \| 非加密 \| 加密 \| 使用加密配置（encrypt=true）打开数据库。 \| \| 加密 \| 非加密 \| 使用非加密配置（encrypt=false）打开数据库。 \| getRdbStore支持多线程并发操作。 |
| [getRdbStoreSync](arkts-arkdata-relationalstore-getrdbstoresync-f.md#getRdbStoreSync) | 创建或打开已有的关系型数据库。开发者可以根据自己的需求配置config参数，然后通过RdbStore调用相关接口执行数据操作。这是一个同步方法，会阻塞线程直到获取到RdbStore。 对应沙箱路径下无数据库文件时，将创建数据库文件，文件创建位置详见[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)。对应路径下已有数据库文件时，将打开已有数据库文件。 开发者在创建数据库时，应谨慎配置是否进行数据库加密的参数[encrypt](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)，数据库创建后，禁止对该参数进行修改。如果有修改参数，则会报错误码。 \| 当前打开数据库时配置的加密类型 \| 本设备上创建该数据库时的加密类型 \| 结果 \| \| ------- \| -------------------------------- \| ---- \| \| 非加密 \| 加密 \| 使用加密配置（encrypt=true）打开数据库。 \| \| 加密 \| 非加密 \| 使用非加密配置（encrypt=false）打开数据库。 \| getRdbStoreSync支持多线程并发操作。 |
| [getUpdateSqlInfo](arkts-arkdata-relationalstore-getupdatesqlinfo-f.md#getUpdateSqlInfo) | 获取用于更新数据的SQL语句，此为同步接口。 |
| [isTokenizerSupported](arkts-arkdata-relationalstore-istokenizersupported-f.md#isTokenizerSupported) | 判断当前平台是否支持传入的分词器，此为同步接口。 如果当前平台支持传入的分词器时，此接口返回值为true；反之，返回值为false。 |
| [isVectorSupported](arkts-arkdata-relationalstore-isvectorsupported-f.md#isVectorSupported) | 判断系统是否提供向量数据库能力。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | 提供查询数据库后生成的结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。 LiteResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。 下列API示例中，都需先使用[queryWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#queryWithoutRowCount)、 [querySqlWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querySqlWithoutRowCount)等query类方法中任一方法获取到LiteResultSet实例，再 通过此实例调用对应方法。 |
| [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | 表示关系型数据库（RDB）的谓词。该类确定RDB中条件表达式的值是true还是false。谓词间支持多语句拼接，拼接时默认使用and()连接。不支持Sendable跨线程传递。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c-sys.md) | 提供查询数据库后生成的结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。 LiteResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。 下列API示例中，都需先使用[queryWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#queryWithoutRowCount)、 [querySqlWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querySqlWithoutRowCount)等query类方法中任一方法获取到LiteResultSet实例，再 通过此实例调用对应方法。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Asset](arkts-arkdata-relationalstore-asset-i.md) | 记录资产附件（文件、图片、视频等类型文件）的相关信息。 |
| [ChangeInfo](arkts-arkdata-relationalstore-changeinfo-i.md) | 记录端云同步过程详情。 |
| [CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i.md) | 云同步配置信息。 |
| [CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md) | 数据库加密参数配置。此配置只有在StoreConfig的encrypt选项设置为true或密钥非空时有效。 |
| [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md) | 记录表的分布式配置信息。 |
| [ExceptionMessage](arkts-arkdata-relationalstore-exceptionmessage-i.md) | 描述数据库执行的SQL语句的错误信息。 |
| [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) | 描述数据库整体执行端云同步任务上传和下载的统计信息。 |
| [RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md) | 提供管理关系数据库（RDB）方法的接口。 在使用以下API前，请先通过[getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getRdbStore)方法获取RdbStore实例，并使用该实例调用对应接口方法。 在此基础上，建议优先使用[execute](arkts-arkdata-relationalstore-rdbstore-i.md#execute)方法完成数据库表结构和初始数据的 初始化，以确保相关接口调用的前置条件已满足。 |
| [Result](arkts-arkdata-relationalstore-result-i.md) | 记录受影响的数据行数量和结果集。 |
| [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) | 提供通过查询数据库生成的数据库结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。 ResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。 下列API示例中，都需先使用 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 、 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querySql) 、 [remoteQuery](arkts-arkdata-relationalstore-rdbstore-i.md#remoteQuery) 、[queryLockedRow](arkts-arkdata-relationalstore-rdbstore-i.md#queryLockedRow)等query类方法中任一方法获取到ResultSet实例，再通过此实例调用对应方法。 |
| [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 指定returning相关接口操作后需要返回的字段名列表和结果集中允许包含的最大记录数。 |
| [SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md) | 描述数据库执行的SQL语句的统计信息。 |
| [SqlInfo](arkts-arkdata-relationalstore-sqlinfo-i.md) | 描述数据库执行的SQL语句的详细信息。 |
| [Statistic](arkts-arkdata-relationalstore-statistic-i.md) | 描述数据库表的端云同步过程的统计信息。 |
| [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) | 管理关系数据库配置。 |
| [SyncResult](arkts-arkdata-relationalstore-syncresult-i.md) | 表示设备同步结果。 |
| [TableDetails](arkts-arkdata-relationalstore-tabledetails-i.md) | 描述数据库表执行端云同步任务上传和下载的统计信息。 |
| [Transaction](arkts-arkdata-relationalstore-transaction-i.md) | 提供以事务方式管理数据库的方法。事务对象是通过[createTransaction](arkts-arkdata-relationalstore-rdbstore-i.md#createTransaction)接口创建的，不同事务对象之间的操作是隔离的，不 同类型事务的区别见[TransactionType](arkts-arkdata-relationalstore-transactiontype-e.md#TransactionType) 。 当前关系型数据库同一时刻仅支持一个写事务，所以如果当前[RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md#RdbStore)存在写事务未释放，创建IMMEDIATE或EXCLUSIVE事务会返回14800024错误 码。如果是创建的DEFERRED事务，则可能在首次使用DEFERRED事务调用写操作时返回14800024错误码。通过IMMEDIATE或EXCLUSIVE创建写事务或者DEFERRED事务升级到写事务之后， [RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md#RdbStore)的写操作也会返回14800024错误码。 当事务并发量较高且写事务持续时间较长时，返回14800024错误码的次数可能会变多，开发者可以通过减少事务占用时长减少14800024出现的次数，也可以通过重试的方式处理14800024错误码。 在使用以下API前，请先通过[createTransaction](arkts-arkdata-relationalstore-rdbstore-i.md#createTransaction)方法获取Transaction实例，再通过此实例调用对应方法。 |
| [TransactionOptions](arkts-arkdata-relationalstore-transactionoptions-i.md) | 事务对象的配置信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i-sys.md) | 云同步配置信息。 |
| [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i-sys.md) | 记录表的分布式配置信息。 |
| [DistributedInfo](arkts-arkdata-relationalstore-distributedinfo-i-sys.md) | 记录分布式信息。 |
| [RdbStore](arkts-arkdata-relationalstore-rdbstore-i-sys.md) | 提供管理关系数据库（RDB）方法的接口。 在使用以下API前，请先通过[getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getRdbStore)方法获取RdbStore实例，并使用该实例调用对应接口方法。 在此基础上，建议优先使用[execute](arkts-arkdata-relationalstore-rdbstore-i.md#execute)方法完成数据库表结构和初始数据的 初始化，以确保相关接口调用的前置条件已满足。 |
| [Reference](arkts-arkdata-relationalstore-reference-i-sys.md) | 记录表之间通过表字段指定的关联关系。其中表a关联到表b，称a为b关联的子表，b为a关联的父表。 |
| [ResultSet](arkts-arkdata-relationalstore-resultset-i-sys.md) | 提供通过查询数据库生成的数据库结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。 ResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。 下列API示例中，都需先使用 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 、 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querySql) 、 [remoteQuery](arkts-arkdata-relationalstore-rdbstore-i.md#remoteQuery) 、[queryLockedRow](arkts-arkdata-relationalstore-rdbstore-i.md#queryLockedRow)等query类方法中任一方法获取到ResultSet实例，再通过此实例调用对应方法。 |
| [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i-sys.md) | 管理关系数据库配置。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AssetConflictPolicy](arkts-arkdata-relationalstore-assetconflictpolicy-e.md) | 资产冲突策略枚举。请使用枚举名称而非枚举值。 |
| [AssetStatus](arkts-arkdata-relationalstore-assetstatus-e.md) | 描述资产附件的状态枚举。请使用枚举名称而非枚举值。 |
| [ChangeType](arkts-arkdata-relationalstore-changetype-e.md) | 描述数据变更类型的枚举。请使用枚举名称而非枚举值。 |
| [ColumnType](arkts-arkdata-relationalstore-columntype-e.md) | 描述数据库列存储类型的枚举。请使用枚举名称而非枚举值。 |
| [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | 插入和修改接口的冲突解决模式。请使用枚举名称而非枚举值。 |
| [DistributedTableType](arkts-arkdata-relationalstore-distributedtabletype-e.md) | 分布式表类型的枚举。请使用枚举名称而非枚举值。此配置项为数据库级配置，如果数据库中有多张分布式表，则所有表必须使用相同的分布式表类型，且不支持切换升级。 |
| [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | 描述表的分布式类型的枚举。请使用枚举名称而非枚举值。 |
| [EncryptionAlgo](arkts-arkdata-relationalstore-encryptionalgo-e.md) | 数据库的加密方式枚举。请使用枚举名称而非枚举值。 |
| [Field](arkts-arkdata-relationalstore-field-e.md) | 用于谓词查询条件的特殊字段。请使用枚举名称而非枚举值。 |
| [HmacAlgo](arkts-arkdata-relationalstore-hmacalgo-e.md) | 数据库的HMAC算法枚举。请使用枚举名称而非枚举值。 |
| [KdfAlgo](arkts-arkdata-relationalstore-kdfalgo-e.md) | 数据库的PBKDF2算法枚举。请使用枚举名称而非枚举值。 |
| [Origin](arkts-arkdata-relationalstore-origin-e.md) | 表示数据来源。请使用枚举名称而非枚举值。 |
| [Progress](arkts-arkdata-relationalstore-progress-e.md) | 描述端云同步过程的枚举。请使用枚举名称而非枚举值。 |
| [ProgressCode](arkts-arkdata-relationalstore-progresscode-e.md) | 表示端云同步过程的状态码。请使用枚举名称而非枚举值。 |
| [RebuildType](arkts-arkdata-relationalstore-rebuildtype-e.md) | 描述数据库重建类型的枚举。请使用枚举名称而非枚举值。 |
| [SecurityLevel](arkts-arkdata-relationalstore-securitylevel-e.md) | 数据库的安全级别枚举。请使用枚举名称而非枚举值。数据库的安全级别仅支持由低向高设置，不支持由高向低设置。 |
| [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md) | 描述订阅类型。请使用枚举名称而非枚举值。 |
| [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | 指数据库同步模式。请使用枚举名称而非枚举值。 |
| [SyncResultCode](arkts-arkdata-relationalstore-syncresultcode-e.md) | 描述设备同步状态的枚举。请使用枚举名称而非枚举值。 |
| [Tokenizer](arkts-arkdata-relationalstore-tokenizer-e.md) | 描述fts（全文搜索）场景下使用的分词器枚举。请使用枚举名称而非枚举值。 在使用不同的分词器时，使用的建表语句会有所区别。 示例代码中this.context定义见Stage模型的应用Context。 使用ICU_TOKENIZER分词器时，创建表的示例： 使用CUSTOM_TOKENIZER分词器时，创建表的示例： 使用CUSTOM_TOKENIZER分词器，并指定分词模式时，创建表的示例： |
| [TransactionType](arkts-arkdata-relationalstore-transactiontype-e.md) | 描述创建事务对象的枚举。请使用枚举名称而非枚举值。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DistributedField](arkts-arkdata-relationalstore-distributedfield-e-sys.md) | 用于谓词查询条件的特殊字段。请使用枚举名称而非枚举值。 |
| [DistributedOrigin](arkts-arkdata-relationalstore-distributedorigin-e-sys.md) | 表示数据来源。请使用枚举名称而非枚举值。 |
| [HAMode](arkts-arkdata-relationalstore-hamode-e-sys.md) | 描述关系型数据库存储的高可用性模式的枚举。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [Assets](arkts-arkdata-relationalstore-assets-t.md) | 表示[Asset](arkts-arkdata-relationalstore-asset-i.md#Asset)类型的数组。 |
| [ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md) | 用于存储数据库表的主键和修改时间的数据类型。 |
| [PRIKeyType](arkts-arkdata-relationalstore-prikeytype-t.md) | 用于表示数据库表某一行主键的数据类型。 |
| [RowData](arkts-arkdata-relationalstore-rowdata-t.md) | 用于表示数据库表中的某一行数据。 |
| [RowsData](arkts-arkdata-relationalstore-rowsdata-t.md) | 用于表示数据库表中的多行数据。 |
| [UTCTime](arkts-arkdata-relationalstore-utctime-t.md) | 用于表示UTC时间的数据类型。 |
| [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) | 用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。 |
| [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | 用于存储键值对的类型。不支持Sendable跨线程传递。 |

