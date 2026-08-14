# RdbStore

提供管理关系数据库（RDB）方法的接口。 在使用以下API前，请先通过[getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getRdbStore)方法获取RdbStore实例，并使用该实例调用对应接口方法。 在此基础上，建议优先使用[execute](arkts-arkdata-relationalstore-rdbstore-i.md#execute)方法完成数据库表结构和初始数据的 初始化，以确保相关接口调用的前置条件已满足。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-interface RdbStore--><!--Device-relationalStore-interface RdbStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## cleanDeviceDirtyData

```TypeScript
cleanDeviceDirtyData(table: string, cursor?: long): Promise<void>
```

本端手动清理对端删除后同步过来的数据。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-cleanDeviceDirtyData(table: string, cursor?: long): Promise<void>--><!--Device-RdbStore-cleanDeviceDirtyData(table: string, cursor?: long): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表示需要清理数据库表的名称。数据库表名只能由字母、数字和下划线组成，不能包含其他字符，长度为[1, 256]。 |
| cursor | long | 否 | 表示数据游标，不大于此游标的脏数据将被清理。整数类型，取值应大于0。当传入小于等于0的值时，会抛出异常，异常信息为无效的参数。当此参数不填时，清理当前表的所有脏数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| 14800043 | The database does not support this scenario. Possible causes: 1. The database type is not support;2. The table type is not supported; 3. This is a read-only database. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## cloudSync

```TypeScript
cloudSync(
      mode: SyncMode,
      predicates: RdbPredicates,
      progress: Callback<ProgressDetails>,
      callback: AsyncCallback<void>
    ): void
```

手动执行按条件进行端云同步，使用callback异步回调。使用该接口需要实现云同步功能。 > **说明：** > > 从API version 18开始，手动执行端云同步时，设置谓词条件时新增支持指定资产下载能力。此时，同步模式需要设置为`relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST`。 > > 谓词中支持使用主键（必填）和资产（可选）作为同步条件：选择资产作为同步条件时，谓词仅支持[equalTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#equalTo)；指定资产的数量较多时（最 > 多支持指定50个资产），建议谓词中仅使用主键作为同步条件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-cloudSync(      mode: SyncMode,      predicates: RdbPredicates,      progress: Callback<ProgressDetails>,      callback: AsyncCallback<void>    ): void--><!--Device-RdbStore-cloudSync(      mode: SyncMode,      predicates: RdbPredicates,      progress: Callback<ProgressDetails>,      callback: AsyncCallback<void>    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 表示数据库的同步模式。 |
| predicates | RdbPredicates | 是 | 表示同步数据的谓词条件。 |
| progress | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 用来处理数据库同步详细信息的回调函数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当同步成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The tablesNames must be not empty. 5. The progress must be a callback type. 6. The callback must be a function. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | if permission verification failed, application which is not a system application uses system API. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

## cloudSync

```TypeScript
cloudSync(mode: SyncMode, predicates: RdbPredicates, progress: Callback<ProgressDetails>): Promise<void>
```

手动执行按条件进行端云同步，使用Promise异步回调。使用该接口需要实现云同步功能。 > **说明：** > > 从API version 18开始，手动执行端云同步时，设置谓词条件时新增支持指定资产下载能力。此时，同步模式需要设置为`relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST`。 > > 谓词中支持使用主键（必填）和资产（可选）作为同步条件：选择资产作为同步条件时，谓词仅支持[equalTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#equalTo)；指定资产的数量较多时（最 > 多支持指定50个资产），建议谓词中仅使用主键作为同步条件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-cloudSync(mode: SyncMode, predicates: RdbPredicates, progress: Callback<ProgressDetails>): Promise<void>--><!--Device-RdbStore-cloudSync(mode: SyncMode, predicates: RdbPredicates, progress: Callback<ProgressDetails>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 表示数据库的同步模式。 |
| predicates | RdbPredicates | 是 | 表示同步数据的谓词条件。 |
| progress | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 用来处理数据库同步详细信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。返回同步结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The tablesNames must be not empty. 5. The progress must be a callback type. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | if permission verification failed, application which is not a system application uses system API. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

## delete

```TypeScript
delete(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<long>): void
```

根据DataSharePredicates的指定实例对象从数据库中删除数据，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-delete(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<long>): void--><!--Device-RdbStore-delete(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | DataSharePredicates的实例对象指定的删除条件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数。当删除数据成功，err为undefined，data为受影响的行数量；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## delete

```TypeScript
delete(table: string, predicates: dataSharePredicates.DataSharePredicates): Promise<long>
```

根据DataSharePredicates的指定实例对象从数据库中删除数据，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-delete(table: string, predicates: dataSharePredicates.DataSharePredicates): Promise<long>--><!--Device-RdbStore-delete(table: string, predicates: dataSharePredicates.DataSharePredicates): Promise<long>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | DataSharePredicates的实例对象指定的删除条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象。返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## lockCloudContainer

```TypeScript
lockCloudContainer(): Promise<int>
```

手动对应用云端数据库加锁，使用Promise异步回调。 > **说明：** > > 若手动加锁成功，则其他同账户设备的同应用禁止同步到云端。使用该接口需要实现云同步功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-lockCloudContainer(): Promise<int>--><!--Device-RdbStore-lockCloudContainer(): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象。如果加锁成功，返回锁的有效时长；如果加锁失败，返回0，单位：ms。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## query

```TypeScript
query(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<ResultSet>): void
```

根据指定条件查询数据库中的数据，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，使用此接口获取ResultSet后，调用 [getValue](arkts-arkdata-relationalstore-resultset-i.md#getValue)、[getString](arkts-arkdata-relationalstore-resultset-i.md#getString)等get方法 时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-query(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<ResultSet>): void--><!--Device-RdbStore-query(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | DataSharePredicates的实例对象指定的查询条件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ResultSet&gt; | 是 | 回调函数。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

## query

```TypeScript
query(
      table: string,
      predicates: dataSharePredicates.DataSharePredicates,
      columns: Array<string>,
      callback: AsyncCallback<ResultSet>
    ): void
```

根据指定条件查询数据库中的数据，支持指定要查询的列，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，使用此接口获取ResultSet后，调用 [getValue](arkts-arkdata-relationalstore-resultset-i.md#getValue)、[getString](arkts-arkdata-relationalstore-resultset-i.md#getString)等get方法 时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-query(      table: string,      predicates: dataSharePredicates.DataSharePredicates,      columns: Array<string>,      callback: AsyncCallback<ResultSet>    ): void--><!--Device-RdbStore-query(      table: string,      predicates: dataSharePredicates.DataSharePredicates,      columns: Array<string>,      callback: AsyncCallback<ResultSet>    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | DataSharePredicates的实例对象指定的查询条件。 |
| columns | Array&lt;string&gt; | 是 | 表示要查询的列。如果值为空，则查询应用于所有列。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ResultSet&gt; | 是 | 回调函数。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

## query

```TypeScript
query(
      table: string,
      predicates: dataSharePredicates.DataSharePredicates,
      columns?: Array<string>
    ): Promise<ResultSet>
```

根据指定条件查询数据库中的数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，使用此接口获取ResultSet后，调用 [getValue](arkts-arkdata-relationalstore-resultset-i.md#getValue)、[getString](arkts-arkdata-relationalstore-resultset-i.md#getString)等get方法 时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-query(      table: string,      predicates: dataSharePredicates.DataSharePredicates,      columns?: Array<string>    ): Promise<ResultSet>--><!--Device-RdbStore-query(      table: string,      predicates: dataSharePredicates.DataSharePredicates,      columns?: Array<string>    ): Promise<ResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | DataSharePredicates的实例对象指定的查询条件。 |
| columns | Array&lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResultSet&gt; | 返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

## querySharingResource

```TypeScript
querySharingResource(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

根据谓词条件匹配的数据记录查找对应记录的共享资源标识，返回查找的结果集。如果指定了列字段，则返回结果集中同时包含对应列的字段值，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-querySharingResource(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>--><!--Device-RdbStore-querySharingResource(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | 表示查询的谓词条件。 |
| columns | Array&lt;string&gt; | 否 | 表示要查找的列字段名。此参数不填时，返回的结果集中只包含共享资源标识字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResultSet&gt; | Promise对象。返回查询的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be not nullptr. 3. The predicates must be an RdbPredicates. 4. The columns must be a string array. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## querySharingResource

```TypeScript
querySharingResource(predicates: RdbPredicates, callback: AsyncCallback<ResultSet>): void
```

根据谓词条件匹配的数据记录查找对应记录的共享资源，返回查找的结果集，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-querySharingResource(predicates: RdbPredicates, callback: AsyncCallback<ResultSet>): void--><!--Device-RdbStore-querySharingResource(predicates: RdbPredicates, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | 表示查询的谓词条件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ResultSet&gt; | 是 | 回调函数。返回查询的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be not nullptr. 3. The predicates must be an RdbPredicates. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## querySharingResource

```TypeScript
querySharingResource(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void
```

根据谓词条件匹配的数据记录查找对应记录的共享资源，返回查找到的共享资源的结果集，同时在结果集中返回谓词条件匹配的指定列名的字段值，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-querySharingResource(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void--><!--Device-RdbStore-querySharingResource(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | 表示查询的谓词条件。 |
| columns | Array&lt;string&gt; | 是 | 表示要查找的列字段名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ResultSet&gt; | 是 | 回调函数。返回查询的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be not nullptr. 3. The predicates must be an RdbPredicates. 4. The columns must be a string array. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## restore

```TypeScript
restore(): Promise<void>
```

从副本关系型数据库文件恢复数据库，使用Promise异步回调。此接口仅供[HAMode](arkts-arkdata-relationalstore-hamode-e-sys.md#HAMode（系统接口）)为MAIN_REPLICA时使用，且不支持在事务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-restore(): Promise<void>--><!--Device-RdbStore-restore(): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## retainDeviceData

```TypeScript
retainDeviceData(retainDevices?: Record<string, Array<string>>): Promise<void>
```

保留对应[单版本表模式](../../../database/data-sync-of-rdb-store.md#数据同步存储机制)分布式数据表中对应设备同步过来的数据，删除其他设备同步过来的数据，使用Promise异步回 调。 不支持对[多设备协同表模式](../../../database/data-sync-of-rdb-store.md#数据同步存储机制)分布式数据表进行删除。 要删除数据越多，执行所需的时间越长。 > **说明：** > > 入参允许为空，数据库表名对应的设备id列表也允许为空，但是数据库表名和设备id不允许为空字符串。 > > 入参如果为空，则删除当前数据库所有单版本分布式表中所有其他设备同步过来的数据。 > > 入参中如果数据库表名对应的设备id列表为空，则删除该表下所有其他设备同步过来的数据。 > > 保留本地写入以及传入设备id同步过来的数据，其他设备id同步过来的数据会被删除。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-retainDeviceData(retainDevices?: Record<string, Array<string>>): Promise<void>--><!--Device-RdbStore-retainDeviceData(retainDevices?: Record<string, Array<string>>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| retainDevices | Record&lt;string, Array&lt;string&gt;&gt; | 否 | 指定要保留的分布式数据库表名和对应的设备id，无默认值，不传入则删除当前数据库中所有单版本分布式表中全量同步 数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| 14800043 | The database does not support this scenario. Possible causes: 1. The database type is not supported;2. The table type is not supported; 3. This is a read-only database. |
| 14800042 | The database does not exist. Possible causes: 1. The database is deleted; &lt;br&gt;2. The database is not created. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The RdbStore or ResultSet is already closed. |

## unlockCloudContainer

```TypeScript
unlockCloudContainer(): Promise<void>
```

手动对应用云端数据库解锁，使用Promise异步回调。使用该接口需要实现云同步功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RdbStore-unlockCloudContainer(): Promise<void>--><!--Device-RdbStore-unlockCloudContainer(): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## update

```TypeScript
update(
      table: string,
      values: ValuesBucket,
      predicates: dataSharePredicates.DataSharePredicates,
      callback: AsyncCallback<long>
    ): void
```

根据DataSharePredicates的指定实例对象更新数据库中的数据，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过 RdbStore的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querySql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getValue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getString)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-update(      table: string,      values: ValuesBucket,      predicates: dataSharePredicates.DataSharePredicates,      callback: AsyncCallback<long>    ): void--><!--Device-RdbStore-update(      table: string,      values: ValuesBucket,      predicates: dataSharePredicates.DataSharePredicates,      callback: AsyncCallback<long>    ): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | DataSharePredicates的实例对象指定的更新条件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数。返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## update

```TypeScript
update(table: string, values: ValuesBucket, predicates: dataSharePredicates.DataSharePredicates): Promise<long>
```

根据DataSharePredicates的指定实例对象更新数据库中的数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore 的 [query](arkts-arkdata-relationalstore-rdbstore-i.md#query) 或 [querySql](arkts-arkdata-relationalstore-rdbstore-i.md#querySql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getValue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getString)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-update(table: string, values: ValuesBucket, predicates: dataSharePredicates.DataSharePredicates): Promise<long>--><!--Device-RdbStore-update(table: string, values: ValuesBucket, predicates: dataSharePredicates.DataSharePredicates): Promise<long>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | dataSharePredicates.DataSharePredicates | 是 | DataSharePredicates的实例对象指定的更新条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象。返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## updateDistributedInfo

```TypeScript
updateDistributedInfo(info: DistributedInfo, predicates: RdbPredicates): Promise<long>
```

更新分布式信息，只支持单版本表模式，使用Promise异步回调。 不支持对多设备协同表模式分布式数据表进行更新。 要更新数据越多，执行所需的时间越长。 > **说明：** > > 入参info中若要传入设备id信息，则设备id必须是已与当前设备建立网络连接的设备id。 > > 入参predicates中若要传入[ORIGIN_ORIDEVICE](arkts-arkdata-relationalstore-distributedfield-e-sys.md#DistributedField（系统接口）)，则只允许使用等于空或不等于空。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbStore-updateDistributedInfo(info: DistributedInfo, predicates: RdbPredicates): Promise<long>--><!--Device-RdbStore-updateDistributedInfo(info: DistributedInfo, predicates: RdbPredicates): Promise<long>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | DistributedInfo | 是 | 指定要更新的分布式表的日志信息。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象。返回更新的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| 14800043 | The database does not support this scenario. Possible causes: 1. The database type is not supported;2. The table type is not supported; 3. This is a read-only database. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The RdbStore or ResultSet is already closed. |

