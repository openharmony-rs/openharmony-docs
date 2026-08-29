# RdbStore

提供管理关系数据库（RDB）方法的接口。在使用以下API前，请先通过[getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md)方法获取RdbStore实例，并使用该实例调用对应接口方法。在此基础上，建议优先使用[execute](#execute)方法完成数据库表结构和初始数据的 初始化，以确保相关接口调用的前置条件已满足。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## attach

```TypeScript
attach(fullPath: string, attachName: string, waitTime?: number) : Promise<number>
```

将一个数据库文件附加到当前数据库中，以便在SQL语句中可以直接访问附加数据库中的数据，使用Promise异步回调。数据库文件来自文件，且此API不支持附加加密数据库。调用attach接口后，数据库切换为非WAL模式，性能会存在一定的劣化。attach时，数据库会切换为非WAL模式，切换模式需要确保所有的ResultSet都已经Close，所有的写操作已经结束，否则会报错14800015。attach不能并发调用，否则可能出现未响应情况并报错14800015，需要重试。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullPath | string | 是 | 表示要附加的数据库的路径，不能为空字符串，路径长度不超过1024字节。 |
| attachName | string | 是 | 表示附加后的数据库的别名，不能为空字符串。 |
| waitTime | number | 否 | 表示附加数据库文件的等待时长，单位：s。默认值2s，最小值1s，最大值300s。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回附加数据库的数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800016](../errorcode-data-rdb.md#14800016-数据库别名已被使用) | The database alias already exists. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
// 非加密数据库附加非加密数据库。
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).attach("/path/rdbstore1.db", "attachDB").then((number: number) => {
    console.info('attach succeeded');
  }).catch((err: BusinessError) => {
    console.error(`attach failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## attach

```TypeScript
attach(context: Context, config: StoreConfig, attachName: string, waitTime?: number) : Promise<number>
```

将一个当前应用的数据库附加到当前数据库中，以便在SQL语句中可以直接访问附加数据库中的数据，使用Promise异步回调。此API不支持加密数据库附加非加密数据库。调用attach接口后，数据库切换为非WAL模式，性能会存在一定的劣化。attach时，数据库会切换为非WAL模式，切换模式需要确保所有的ResultSet都已经Close，所有的写操作已经结束，否则会报错14800015。attach不能并发调用，否则可能出现未响应情况并报错14800015，需要重试。除此之外，attach附加加密数据库时，可能受到并发的影响，出现解密失败的情况，报错14800011，需要显式指定加密参数并重试。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 FA模型的应用Context定义见Context。 Stage模型的应用Context定义见Context。 |
| config | StoreConfig | 是 | 与此RDB存储相关的数据库配置。 |
| attachName | string | 是 | 表示附加后的数据库的别名，不能为空字符串。 |
| waitTime | number | 否 | 表示附加数据库文件的等待时长，单位：s。默认值2s，最小值1s，最大值300s。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回附加数据库的数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800016](../errorcode-data-rdb.md#14800016-数据库别名已被使用) | The database alias already exists. |
| [14801001](../errorcode-data-rdb.md#14801001-上下文环境非stage模型) | The operation is supported in the stage model only. |
| [14801002](../errorcode-data-rdb.md#14801002-storeconfig中传入的datagroupid参数非法) | Invalid data group ID. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

参见 [attach](#attach)

## backup

```TypeScript
backup(destName: string, callback: AsyncCallback<void>): void
```

以指定名称备份数据库，使用callback异步回调。该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| destName | string | 是 | 指定数据库的备份文件名，不能为空字符串。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当备份成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path.<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).backup("dbBackup.db", (err) => {
    if (err) {
      console.error(`Backup failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Backup success.');
  });
}
```

## backup

```TypeScript
backup(destName: string): Promise<void>
```

以指定名称备份数据库，使用Promise异步回调。该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| destName | string | 是 | 指定数据库的备份文件名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  let promiseBackup = (store as relationalStore.RdbStore).backup("dbBackup.db");
  promiseBackup.then(() => {
    console.info('Backup success.');
  }).catch((err: BusinessError) => {
    console.error(`Backup failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void
```

向目标表中插入一组数据，使用callback异步回调。接口报错，表示插入数据失败；接口没有报错但返回值为-1时，也表示插入数据失败。按每批32766个参数，分批以[ConflictResolution.ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md)策略写入，参数数量计算方式为插入 数据条数乘以插入数据的所有字段的并集大小，中途失败则立即返回。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。从API version 20开始，支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array &lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当批量插入成功，err为undefined，data为插入的数据个数；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).batchInsert("EMPLOYEE", valueBuckets, (err, insertNum) => {
    if (err || insertNum == -1) {
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  })
}
```

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>): Promise<number>
```

向目标表中插入一组数据，使用Promise异步回调。接口报错，表示插入数据失败；接口没有报错但返回值为-1时，也表示插入数据失败。按每批32766个参数，分批以[ConflictResolution.ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md)策略写入，参数数量计算方式为插入 数据条数乘以插入数据的所有字段的并集大小，中途失败则立即返回。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。从API version 20开始，该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array &lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

关系型数据库：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).batchInsert("EMPLOYEE", valueBuckets).then((insertNum: number) => {
    if (insertNum == -1) {
      console.error(`batchInsert is failed`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  }).catch((err: BusinessError) => {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  })
}
```

向量数据库：

```TypeScript
let createSql = "CREATE TABLE IF NOT EXISTS test (id INTEGER PRIMARY KEY AUTOINCREMENT, data1 floatvector(2));";
await store!.execute(createSql, 0, undefined); // 创建关系表，第二个参数0表示不开启显式事务，第三个参数undefined表示sql未使用绑定参数化
let floatVector = Float32Array.from([1.2, 2.3]);
let valueBucketArray = new Array<relationalStore.ValuesBucket>();
for (let i = 0; i < 100; i++) { // 构造一个BucketArray用于写入
  const row : relationalStore.ValuesBucket = {
    "id" : i,
    "data1" : floatVector,
  }
  valueBucketArray.push(row);
}
await store!.batchInsert("test", valueBucketArray); // 执行批量写入
```

```TypeScript
const valueBucket3: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucket4: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucket5: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets = new Array(valueBucket3, valueBucket4, valueBucket5);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = await transaction.batchInsert('EMPLOYEE', valueBuckets);
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertSync

```TypeScript
batchInsertSync(table: string, values: Array<ValuesBucket>): number
```

向目标表中插入一组数据。接口报错，表示插入数据失败；接口没有报错但返回值为-1时，也表示插入数据失败。按每批32766个参数，分批以[ConflictResolution.ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md)策略写入，参数数量计算方式为插入 数据条数乘以插入数据的所有字段的并集大小，中途失败则立即返回。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array &lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  try {
    let insertNum: number = (store as relationalStore.RdbStore).batchInsertSync("EMPLOYEE", valueBuckets);
    if (insertNum == -1) {
      console.error(`batchInsertSync is failed`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  } catch (err) {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
const valueBucket6: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucket7: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucket8: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets2 = new Array(valueBucket6, valueBucket7, valueBucket8);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let insertNum: number = (transaction as relationalStore.Transaction).batchInsertSync('EMPLOYEE', valueBuckets2);
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithConflictResolution

```TypeScript
batchInsertWithConflictResolution(
        table: string,
        values: Array<ValuesBucket>, 
        conflict: ConflictResolution
    ): Promise<number>
```

向目标表中插入一组数据，可以通过conflict参数指定冲突解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)。使用Promise异步回调。单次插入参数的最大数量限制为32766，超出上限会返回14800000错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array &lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).batchInsertWithConflictResolution("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then((insertNum: number) => {
    console.info(`batchInsert is successful, insertNum = ${insertNum}`);
  }).catch((err: BusinessError) => {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  });
}
```

```TypeScript
const valueBucket9: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucketA: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucketB: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets3 = new Array(valueBucket9, valueBucketA, valueBucketB);

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = await transaction.batchInsertWithConflictResolution(
        'EMPLOYEE',
        valueBuckets3,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithConflictResolutionSync

```TypeScript
batchInsertWithConflictResolutionSync(
        table: string,
        values: Array<ValuesBucket>,
        conflict: ConflictResolution
    ): number
```

向目标表中插入一组数据，可以通过conflict参数指定冲突解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)。单次插入参数的最大数量限制为32766，超出上限会返回14800000错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | Array &lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回批量插入的数据个数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  try {
    let insertNum: number = (store as relationalStore.RdbStore).batchInsertWithConflictResolutionSync("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  } catch (err) {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
const valueBucketC: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucketD: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucketE: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets4 = new Array(valueBucketC, valueBucketD, valueBucketE);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = transaction.batchInsertWithConflictResolutionSync(
        'EMPLOYEE',
        valueBuckets4,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithReturning

```TypeScript
batchInsertWithReturning(table: string, values: Array<ValuesBucket>, config: ReturningConfig,
      conflict?: ConflictResolution): Promise<Result>
```

向目标表中插入一组数据，可以通过conflict参数指定当发生数据冲突时的解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回 [Result](arkts-arkdata-relationalstore-result-i.md)。使用Promise异步回调。单次插入参数的最大数量限制为32766，超出上限会返回14800001错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 要插入的目标表名。注意：正确的表名不应包含空格、逗号和星号，不能以点开头和结尾等，否则会抛出参数错误。 |
| values | Array &lt;ValuesBucket&gt; | 是 | 要插入到表中的一组数据。注意：空数组、含有重复资产数据会抛出参数错误。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Result&gt; | Promise对象。返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
async function batchInsertWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = await rdbStore.batchInsertWithReturning("EMPLOYEE", valueBuckets, config);
    console.info(`batchInsertWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`batchInsertWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`batchInsertWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
async function transBatchInsertWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = await trans.batchInsertWithReturning("EMPLOYEE", valueBuckets, config);
    console.info(`transBatchInsertWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transBatchInsertWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transBatchInsertWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## batchInsertWithReturningSync

```TypeScript
batchInsertWithReturningSync(table: string, values: Array<ValuesBucket>, config: ReturningConfig,
      conflict?: ConflictResolution): Result
```

向目标表中插入一组数据，可以通过conflict参数指定当发生数据冲突时的解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回 [Result](arkts-arkdata-relationalstore-result-i.md)。单次插入参数的最大数量限制为32766，超出上限会返回14800001错误码。参数数量计算方式为插入数据条数乘以插入数据的所有字段的并集大小。例如：插入数据的所有字段的并集大小为10，则最多可以插入3276条数据（3276*10=32760）。请确保在调用接口时遵守此限制，以避免因参数数量过多而导致错误。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 要插入的目标表名。注意：正确的表名不应包含空格、逗号和星号，不能以点开头和结尾等，否则会抛出参数错误。 |
| values | Array &lt;ValuesBucket&gt; | 是 | 表示要插入到表中的一组数据。注意：空数组、含有重复资产数据会抛出参数错误。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Result | 返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
function batchInsertWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = rdbStore.batchInsertWithReturningSync("EMPLOYEE", valueBuckets, config);
    console.info(`batchInsertWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`batchInsertWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`batchInsertWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
function transBatchInsertWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = trans.batchInsertWithReturningSync("EMPLOYEE", valueBuckets, config);
    console.info(`transBatchInsertWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transBatchInsertWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transBatchInsertWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## beginTrans

```TypeScript
beginTrans(): Promise<number>
```

在开始执行SQL语句之前，开始事务，使用Promise异步回调。与[beginTransaction](#begintransaction)的区别在于：该接口会返回事务ID， [execute](#execute)可以指定不同事务ID达到事务 隔离目的。该接口仅支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象，返回事务ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: The RdbStore verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## beginTransaction

```TypeScript
beginTransaction(): void
```

在开始执行SQL语句之前，开始事务。此接口不允许嵌套事务，且不支持在多进程或多线程中使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

if (store != undefined) {
  (store as relationalStore.RdbStore).beginTransaction();
  const valueBucket: relationalStore.ValuesBucket = {
    'NAME': value1,
    'AGE': value2,
    'SALARY': value3,
    'CODES': value4
  };
  (store as relationalStore.RdbStore).insert("test", valueBucket);
  (store as relationalStore.RdbStore).commit();
}
```

## cleanDirtyData

```TypeScript
cleanDirtyData(table: string, cursor: number, callback: AsyncCallback<void>): void
```

清理云端删除的数据同步到本地后，未自动清理的，且数据的游标（cursor）小于指定游标的数据。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表示当前数据库的表的名称。 |
| cursor | number | 是 | 整数类型，表示数据游标，小于此游标的脏数据将被清理。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当清理成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The cursor must be valid cursor. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).cleanDirtyData('test_table', 100, (err) => {
    if (err) {
      console.error(`clean dirty data failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('clean dirty data succeeded');
  });
}
```

## cleanDirtyData

```TypeScript
cleanDirtyData(table: string, callback: AsyncCallback<void>): void
```

清理云端删除的数据同步到本地后，未自动清理的所有数据。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表示当前数据库的表的名称。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当清理成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s). 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).cleanDirtyData('test_table', (err) => {
    if (err) {
      console.error(`clean dirty data failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('clean dirty data succeeded');
  });
}
```

## cleanDirtyData

```TypeScript
cleanDirtyData(table: string, cursor?: number): Promise<void>
```

清理云端删除的数据同步到本地后，未自动清理的，且数据的游标（cursor）小于指定游标的数据，使用Promise异步回调。若无cursor参数，将全部清理。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表示当前数据库的表的名称。 |
| cursor | number | 否 | 整数类型，表示数据游标，小于此游标的脏数据将被清理。当此参数不填时，清理当前表的所有脏数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The cursor must be valid cursor. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).cleanDirtyData('test_table', 100).then(() => {
    console.info('clean dirty data  succeeded');
  }).catch((err: BusinessError) => {
    console.error(`clean dirty data failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## close

```TypeScript
close(): Promise<void>
```

关闭数据库，使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).close().then(() => {
    console.info(`close succeeded`);
  }).catch((err: BusinessError) => {
    console.error(`close failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## cloudSync

```TypeScript
cloudSync(mode: SyncMode, progress: Callback<ProgressDetails>, callback: AsyncCallback<void>): void
```

主动执行对所有分布式表的端云同步，使用callback异步回调。使用该接口需要实现云服务功能。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 表示数据库的同步模式。 |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 用来处理数据库同步详细信息的回调函数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当同步成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The progress must be a callback type. 5. The callback must be a function. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, (progressDetails) => {
    console.info(`Progress: ${progressDetails}`);
  }, (err) => {
    if (err) {
      console.error(`Cloud sync failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Cloud sync succeeded');
  });
}
```

## cloudSync

```TypeScript
cloudSync(mode: SyncMode, progress: Callback<ProgressDetails>): Promise<void>
```

主动执行对所有分布式表的端云同步，使用Promise异步回调。使用该接口需要实现云服务功能。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 表示数据库的同步模式。 |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 用来处理数据库同步详细信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The progress must be a callback type. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail}`);
  }).then(() => {
    console.info('Cloud sync succeeded');
  }).catch((err: BusinessError) => {
    console.error(`cloudSync failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## cloudSync

```TypeScript
cloudSync(
      mode: SyncMode,
      tables: string[],
      progress: Callback<ProgressDetails>,
      callback: AsyncCallback<void>
    ): void
```

主动执行对指定表的端云同步，使用callback异步回调。使用该接口需要实现云服务功能。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 表示数据库的同步模式。 |
| tables | string[] | 是 | 指定同步的表名。 |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 用来处理数据库同步详细信息的回调函数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当同步成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameter types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
const tables = ["table1", "table2"];

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, tables, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`Progress: ${progressDetail}`);
  }, (err) => {
    if (err) {
      console.error(`Cloud sync failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Cloud sync succeeded');
  });
};
```

## cloudSync

```TypeScript
cloudSync(mode: SyncMode, tables: string[], progress: Callback<ProgressDetails>): Promise<void>
```

主动执行对指定表的端云同步，使用Promise异步回调。使用该接口需要实现云服务功能。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 表示数据库的同步模式。 |
| tables | string[] | 是 | 指定同步的表名。 |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 用来处理数据库同步详细信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The tablesNames must be not empty. 5. The progress must be a callback type. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const tables = ["table1", "table2"];

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, tables, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail}`);
  }).then(() => {
    console.info('Cloud sync succeeded');
  }).catch((err: BusinessError) => {
    console.error(`cloudSync failed, code is ${err.code},message is ${err.message}`);
  });
};
```

## cloudSyncEx

```TypeScript
cloudSyncEx(config: CloudSyncConfig, progress: Callback<ProgressDetails>): Promise<void>
```

主动执行端云同步，根据云同步配置信息进行同步，使用Promise异步回调。使用该接口需要实现云服务功能。

> **说明：**
> 
> [CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i.md)中仅支持以下谓词：
> 
> - [beginWrap](arkts-arkdata-relationalstore-rdbpredicates-c.md#beginwrap)
> 
> - [endWrap](arkts-arkdata-relationalstore-rdbpredicates-c.md#endwrap)
> 
> - [or](arkts-arkdata-relationalstore-rdbpredicates-c.md#or)
> 
> - [and](arkts-arkdata-relationalstore-rdbpredicates-c.md#and)
> 
> - 以下谓词的数据字段类型[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)仅支持number类型的整数和string：
> 
> - [equalTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#equalto)
> 
> - [notEqualTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#notequalto)
> 
> - [in](arkts-arkdata-relationalstore-rdbpredicates-c.md#in)
> 
> - [notIn](arkts-arkdata-relationalstore-rdbpredicates-c.md#notin)
> 
> - 以下谓词的数据字段类型[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)仅支持number类型的整数：
> 
> - [greaterThan](arkts-arkdata-relationalstore-rdbpredicates-c.md#greaterthan)
> 
> - [lessThan](arkts-arkdata-relationalstore-rdbpredicates-c.md#lessthan)
> 
> - [greaterThanOrEqualTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#greaterthanorequalto)
> 
> - [lessThanOrEqualTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#lessthanorequalto)
> 
> 谓词中支持使用主键（必填）和资产（可选）作为同步条件：当选择资产作为同步条件时，同步模式需要设置为relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST；指定资产的数量较多时（最多支持
> 指定50个资产），建议谓词中仅使用主键作为同步条件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i.md) | 是 | 云同步配置。 |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 进度回调函数，返回ProgressDetails实例对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.in("id", ["id1", "id2"]);

let config: relationalStore.CloudSyncConfig = {
  mode: relationalStore.SyncMode.SYNC_MODE_TIME_FIRST,
  enablePredicate: true,
  predicate: predicates
};
if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSyncEx(config, (progressDetails: relationalStore.ProgressDetails) => {
      console.info(`progress: ${progressDetails.schedule}`);
  }).then(() => {
      console.info('cloud sync succeeded');
  }).catch((err: BusinessError) => {
      console.error(`cloud sync failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

## commit

```TypeScript
commit(): void
```

提交已执行的SQL语句，跟[beginTransaction](#begintransaction)配合使用。此接口不允许嵌套事务，且不支持在多进程或多线程中使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error.<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

if (store != undefined) {
  (store as relationalStore.RdbStore).beginTransaction();
  const valueBucket: relationalStore.ValuesBucket = {
    'NAME': value1,
    'AGE': value2,
    'SALARY': value3,
    'CODES': value4
  };
  (store as relationalStore.RdbStore).insert("test", valueBucket);
  (store as relationalStore.RdbStore).commit();
}
```

## commit

```TypeScript
commit(txId : number): Promise<void>
```

提交已执行的SQL语句，跟[beginTrans](#begintrans)配合使用，使用Promise异步回调。该接口仅支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| txId | number | 是 | 通过[beginTrans](#begintrans)获取的事务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## createTransaction

```TypeScript
createTransaction(options?: TransactionOptions): Promise<Transaction>
```

创建一个事务对象并开始事务，使用Promise异步回调。与[beginTransaction](#begintransaction)的区别在于：createTransaction接口会返回一个事务对象，不同事务对象之间是隔 离的。使用事务对象进行插入、删除或更新数据等操作，无法被注册数据变更通知[on('dataChange')](#on)监听到。一个store最多支持同时存在四个事务对象，超过后会返回14800015错误码，此时需要检查是否持有事务对象时间过长或并发事务过多，若确认无法通过上述优化解决问题，建议等待现有事务释放后，再尝试新建事务对象。优先使用createTransaction，不再推荐使用beginTransaction。

**起始版本：** 14

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TransactionOptions](arkts-arkdata-relationalstore-transactionoptions-i.md) | 否 | 表示事务对象的配置信息，默认值为DEFERRED。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Transaction](arkts-arkdata-relationalstore-transaction-i.md)&gt; | Promise对象，返回事务对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database is busy. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then(async (transaction: relationalStore.Transaction) => {
    transaction.execute("DELETE FROM test WHERE age = ? OR age = ?", [21, 20]).then(() => {
      transaction.commit();
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`execute sql failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    (store as relationalStore.RdbStore).close();
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## delete

```TypeScript
delete(predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

根据RdbPredicates的指定实例对象从数据库中删除数据，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当删除数据成功，err为undefined，data为受影响的行数量；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).delete(predicates, (err, rows) => {
    if (err) {
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Delete rows: ${rows}`);
  });
}
```

## delete

```TypeScript
delete(predicates: RdbPredicates): Promise<number>
```

根据RdbPredicates的指定实例对象从数据库中删除数据，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回受影响的行数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).delete(predicates).then((rows: number) => {
    console.info(`Delete rows: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
  });
}
```

```TypeScript
let predicates2 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates2.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const rows = await transaction.delete(predicates2);
      await transaction.commit();
      console.info(`Delete rows: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## deleteSync

```TypeScript
deleteSync(predicates: RdbPredicates): number
```

根据RdbPredicates的指定实例对象从数据库中删除数据。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回受影响的行数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  try {
    let rows: number = (store as relationalStore.RdbStore).deleteSync(predicates);
    console.info(`Delete rows: ${rows}`);
  } catch (err) {
    console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
let predicates3 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates3.equalTo('NAME', 'Lisa');
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rows = transaction.deleteSync(predicates3);
      await transaction.commit();
      console.info(`Delete rows: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## deleteWithReturning

```TypeScript
deleteWithReturning(predicates: RdbPredicates, config: ReturningConfig): Promise<Result>
```

根据RdbPredicates的实例对象从数据库中删除数据，返回[Result](arkts-arkdata-relationalstore-result-i.md)，使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Result&gt; | Promise对象。返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
async function deleteWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = await rdbStore.deleteWithReturning(predicates, config);
    console.info(`deleteWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`deleteWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`deleteWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
async function transDeleteWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = await trans.deleteWithReturning(predicates, config);
    console.info(`transDeleteWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transDeleteWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transDeleteWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## deleteWithReturningSync

```TypeScript
deleteWithReturningSync(predicates: RdbPredicates, config: ReturningConfig): Result
```

根据RdbPredicates的实例对象从数据库中删除数据，返回[Result](arkts-arkdata-relationalstore-result-i.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的删除条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Result | 返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
function deleteWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = rdbStore.deleteWithReturningSync(predicates, config);
    console.info(`deleteWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`deleteWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`deleteWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
function transDeleteWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = trans.deleteWithReturningSync(predicates, config);
    console.info(`transDeleteWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transDeleteWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transDeleteWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## detach

```TypeScript
detach(attachName: string, waitTime?: number) : Promise<number>
```

将附加的数据库从当前数据库中分离，使用Promise异步回调。当所有的附加的数据库被分离后，数据库会重新切换为WAL模式。在detach之前，所有的数据库操作要确保已经结束，所有的ResultSet已经Close。并且不能并发调用，可能出现未响应情况，需要重试。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attachName | string | 是 | 表示附加后的数据库的别名，不能为空字符串。 |
| waitTime | number | 否 | 表示分离数据库的等待时长，单位：s。默认值2s，最小值1s，最大值300s。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回分离后剩余附加的数据库的数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).detach("attachDB").then((number: number) => {
    console.info(`detach succeeded, number is ${number}`);
  }).catch((err: BusinessError) => {
    console.error(`detach failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## emit

```TypeScript
emit(event: string): void
```

通知通过[on](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#on10)注册的进程间或者进程内监听事件。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 通知订阅事件的名称，可自定义事件名称，不能与系统已有事件[dataChange](#on)， [autoSyncProgress](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#onautosyncprogress11)， [statistics](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#onstatistics12)名称重 复。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800050](../errorcode-data-rdb.md#14800050-获取订阅服务失败) | Failed to obtain the subscription service. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).emit('storeObserver');
}
```

## execute

```TypeScript
execute(sql: string, args?: Array<ValueType>): Promise<ValueType>
```

执行包含指定参数的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，返回值类型为ValueType，使用Promise异步回调。该接口支持执行增删改操作，支持执行PRAGMA语法的sql，支持对表的操作（建表、删表、修改表），返回结果类型由执行具体sql的结果决定。此接口不支持执行查询、附加数据库和事务操作，可以使用 [querySql](#querysql)、 [query](#query)、 [attach](#attach)、 [beginTransaction](#begintransaction)、 [commit](#commit)等接口代替。向量数据库使用该接口执行插入操作，数据来源于子查询时，支持全字段插入，暂不支持部分字段插入。不支持分号分隔的多条语句。不支持开头包含注释的语句。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| args | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ValueType&gt; | Promise对象，返回SQL执行后的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

关系型数据库：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 校验数据库完整性
if (store != undefined) {
  const SQL_CHECK_INTEGRITY = 'PRAGMA integrity_check';
  (store as relationalStore.RdbStore).execute(SQL_CHECK_INTEGRITY).then((data) => {
    console.info(`check result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`check failed, code is ${err.code}, message is ${err.message}`);
  });
}

// 删除表中所有数据
if (store != undefined) {
  const SQL_DELETE_TABLE = 'DELETE FROM test';
  (store as relationalStore.RdbStore).execute(SQL_DELETE_TABLE).then((data) => {
    console.info(`delete result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
  });
}

// 删表
if (store != undefined) {
  const SQL_DROP_TABLE = 'DROP TABLE test';
  (store as relationalStore.RdbStore).execute(SQL_DROP_TABLE).then((data) => {
    console.info(`drop result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`drop failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

向量数据库：

```TypeScript
// FLOATVECTOR(2)是维度为2的向量属性，后续操作repr需依照该维度进行。
let createSql = "CREATE TABLE test (ID INTEGER PRIMARY KEY,REPR FLOATVECTOR(2));";
// 建表
await store!.execute(createSql);
// 使用参数绑定插入数据
let insertSql = "insert into test VALUES(?, ?);";
const vectorValue: Float32Array = Float32Array.from([1.5, 6.6]);
await store!.execute(insertSql, [0, vectorValue]);
// 不使用绑定参数直接执行
await store!.execute("insert into test values(1, '[3.5, 1.8]');");
```

```TypeScript
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      // 删除表中所有数据
      const SQL_DELETE_TABLE = 'DELETE FROM EMPLOYEE';
      const data = await transaction.execute(SQL_DELETE_TABLE);
      await transaction.commit();
      console.info(`delete result: ${data}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## execute

```TypeScript
execute(sql: string, txId: number, args?: Array<ValueType>): Promise<ValueType>
```

执行包含指定参数的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用Promise异步回调。该接口仅支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。使用该接口执行插入操作，数据来源于子查询时，支持全字段插入，暂不支持 部分字段插入。此接口不支持执行查询，可以使用 [querySql](#querysql)接口代替。不支持分号分隔的多条语句。不支持开头包含注释的语句。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| txId | number | 是 | 通过[beginTrans](#begintrans)获取的事务ID，如果传0，该语句默认在单独事务内。 |
| args | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ValueType&gt; | Promise对象，返回SQL执行后的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## executeSql

```TypeScript
executeSql(sql: string, callback: AsyncCallback<void>): void
```

执行指定的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用callback异步回调。此接口不支持执行查询、附加数据库和事务操作，可以使用 [querySql](#querysql)、 [query](#query)、 [attach](#attach)、 [beginTransaction](#begintransaction)、 [commit](#commit)等接口代替。不支持分号分隔的多条语句。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当执行SQL成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.).<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = 'zhangsan'";
if (store != undefined) {
  (store as relationalStore.RdbStore).executeSql(SQL_DELETE_TABLE, (err) => {
    if (err) {
      console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Delete table done.');
  });
}
```

## executeSql

```TypeScript
executeSql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<void>): void
```

执行指定的SQL语句，支持传入SQL语句中参数的值，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用callback异步回调。此接口不支持执行查询、附加数据库和事务操作，可以使用 [querySql](#querysql)、 [query](#query)、 [attach](#attach)、 [beginTransaction](#begintransaction)、 [commit](#commit)等接口代替。不支持分号分隔的多条语句。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array &lt;ValueType&gt; | 是 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当执行SQL成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.).<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = ?";
if (store != undefined) {
  (store as relationalStore.RdbStore).executeSql(SQL_DELETE_TABLE, ['zhangsan'], (err) => {
    if (err) {
      console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Delete table done.');
  });
}
```

## executeSql

```TypeScript
executeSql(sql: string, bindArgs?: Array<ValueType>): Promise<void>
```

执行指定的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用Promise异步回调。此接口不支持执行查询、附加数据库和事务操作，可以使用 [querySql](#querysql)、 [query](#query)、 [attach](#attach)、 [beginTransaction](#begintransaction)、 [commit](#commit)等接口代替。不支持分号分隔的多条语句。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported the sql(attach,begin,commit,rollback etc.).<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = 'zhangsan'";
if (store != undefined) {
  (store as relationalStore.RdbStore).executeSql(SQL_DELETE_TABLE).then(() => {
    console.info('Delete table done.');
  }).catch((err: BusinessError) => {
    console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## executeSync

```TypeScript
executeSync(sql: string, args?: Array<ValueType>): ValueType
```

执行包含指定参数的SQL语句，语句中的各种表达式和操作符之间的关系操作符号不超过1000个，返回值类型为ValueType。该接口支持执行增删改操作，支持执行PRAGMA语法的sql，支持对表的操作（建表、删表、修改表），返回结果类型由执行具体sql的结果决定。此接口不支持执行查询、附加数据库和事务操作，可以使用 [querySql](#querysql)、 [query](#query)、 [attach](#attach)、 [beginTransaction](#begintransaction)、 [commit](#commit)等接口代替。不支持分号分隔的多条语句。不支持开头包含注释的语句。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| args | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。该参数不填，或者填null或undefined，都认为是sql参数语句完整，默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValueType | 返回SQL执行后的结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
// 校验数据库完整性
if (store != undefined) {
  const SQL_CHECK_INTEGRITY = 'PRAGMA integrity_check';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_CHECK_INTEGRITY);
    console.info(`check result: ${data}`);
  } catch (err) {
    console.error(`check failed, code is ${err.code}, message is ${err.message}`);
  }
}

// 删除表中所有数据
if (store != undefined) {
  const SQL_DELETE_TABLE = 'DELETE FROM test';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_DELETE_TABLE);
    console.info(`delete result: ${data}`);
  } catch (err) {
    console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
  }
}

// 删表
if (store != undefined) {
  const SQL_DROP_TABLE = 'DROP TABLE test';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_DROP_TABLE);
    console.info(`drop result: ${data}`);
  } catch (err) {
    console.error(`drop failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

```TypeScript
// 删除表中所有数据
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const SQL_DELETE_TABLE = 'DELETE FROM EMPLOYEE';
      let data = transaction.executeSync(SQL_DELETE_TABLE);
      await transaction.commit();
      console.info(`delete result: ${data}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## getModifyTime

```TypeScript
getModifyTime(table: string, columnName: string, primaryKeys: PRIKeyType[]): Promise<ModifyTime>
```

获取数据库表中数据的最后修改时间，使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定要查询的数据库表的表名。 |
| columnName | string | 是 | 指定要查询的数据库表的列名。 |
| primaryKeys | [PRIKeyType](arkts-arkdata-relationalstore-prikeytype-t.md)[] | 是 | 指定要查询的行的主键。 如果数据库表无主键，参数columnName需传入"rowid"，此时primaryKeys为要查询的数据库表的行号。 如果数据库表无主键，参数columnName传入不为"rowid"，返回对应的错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md)&gt; | 返回ModifyTime类型的Promise对象，表示数据最后的修改时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 3 - 4 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The columnName must be not empty string. 5. The PRIKey must be number or string. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let PRIKey = [1, 2, 3];
if (store != undefined) {
  (store as relationalStore.RdbStore).getModifyTime("EMPLOYEE", "NAME", PRIKey)
    .then((modifyTime: relationalStore.ModifyTime) => {
      let size = modifyTime.size;
    })
    .catch((err: BusinessError) => {
      console.error(`getModifyTime failed, code is ${err.code},message is ${err.message}`);
    });
}
```

## getModifyTime

```TypeScript
getModifyTime(
      table: string,
      columnName: string,
      primaryKeys: PRIKeyType[],
      callback: AsyncCallback<ModifyTime>
    ): void
```

获取数据库表中数据的最后修改时间，使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定要查询的数据库表的表名。 |
| columnName | string | 是 | 指定要查询的数据库表的列名。 |
| primaryKeys | [PRIKeyType](arkts-arkdata-relationalstore-prikeytype-t.md)[] | 是 | 指定要查询的行的主键。 如果数据库表无主键，参数columnName需传入"rowid"，此时primaryKeys为要查询的数据库表的行号。 如果数据库表无主键，参数columnName传入不为"rowid"，返回对应的错误码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md)&gt; | 是 | 回调函数。当获取修改时间成功，err为undefined，data为ModifyTime对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 3 - 4 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The columnName must be not empty string. 5. The PRIKey must be number or string. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let PRIKey = [1, 4, 2, 3];
if (store != undefined) {
  (store as relationalStore.RdbStore).getModifyTime("EMPLOYEE", "NAME", PRIKey, (err, modifyTime: relationalStore.ModifyTime) => {
    if (err) {
      console.error(`getModifyTime failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    let size = modifyTime.size;
  });
}
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket, callback: AsyncCallback<number>): void
```

向目标表中插入一行数据，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当插入数据成功，err为undefined，data为行ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1, (err: BusinessError, rowId: number) => {
    if (err) {
      console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Insert is successful, rowId = ${rowId}`);
  });
}
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket, conflict: ConflictResolution, callback: AsyncCallback<number>): void
```

向目标表中插入一行数据，可以通过conflict参数指定冲突解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当插入数据成功，err为undefined，data为行ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE,
    (err: BusinessError, rowId: number) => {
      if (err) {
        console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
        return;
      }
      console.info(`Insert is successful, rowId = ${rowId}`);
    });
}
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket): Promise<number>
```

向目标表中插入一行数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回插入数据的行ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1).then((rowId: number) => {
    console.info(`Insert is successful, rowId = ${rowId}`);
  }).catch((err: BusinessError) => {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket, conflict: ConflictResolution): Promise<number>
```

向目标表中插入一行数据，可以通过conflict参数指定冲突解决模式[ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回插入数据的行ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then((rowId: number) => {
    console.info(`Insert is successful, rowId = ${rowId}`);
  }).catch((err: BusinessError) => {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## insertSync

```TypeScript
insertSync(table: string, values: ValuesBucket, conflict?: ConflictResolution): number
```

向目标表中插入一行数据。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | ValuesBucket | 是 | 表示要插入到表中的数据行。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回插入数据的行ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  try {
    let rowId: number = (store as relationalStore.RdbStore).insertSync("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`Insert is successful, rowId = ${rowId}`);
  } catch (err) {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## insertSync

```TypeScript
insertSync(table: string, values: sendableRelationalStore.ValuesBucket, conflict?: ConflictResolution): number
```

传入Sendable数据，向目标表中插入一行数据。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| values | sendableRelationalStore.ValuesBucket | 是 | 表示要插入到表中的可跨线程传递数据。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回插入数据的行ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
import { sendableRelationalStore } from '@kit.ArkData';

const valuesBucket: relationalStore.ValuesBucket = {
  "NAME": 'hangman',
  "AGE": 18,
  "SALARY": 100.5,
  "CODES": new Uint8Array([1, 2, 3])
};
const sendableValuesBucket = sendableRelationalStore.toSendableValuesBucket(valuesBucket);

if (store != undefined) {
  try {
    let rowId: number = (store as relationalStore.RdbStore).insertSync("EMPLOYEE", sendableValuesBucket, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`Insert is successful, rowId = ${rowId}`);
  } catch (err) {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## lockRow

```TypeScript
lockRow(predicates: RdbPredicates): Promise<void>
```

根据RdbPredicates的指定实例对象从数据库中锁定数据，锁定数据不执行端云同步，使用Promise异步回调。该接口只支持主键为基本类型的表、不支持共享表、无主键表和复合类型主键表。该接口不支持依赖关系表之间的锁传递，如果表存在依赖关系，需要根据依赖关系手动调用该接口。该接口不支持对已删除数据的操作。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的锁定条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800018](../errorcode-data-rdb.md#14800018-查询结果没有数据符合条件) | No data meets the condition. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).lockRow(predicates).then(() => {
    console.info(`Lock success`);
  }).catch((err: BusinessError) => {
    console.error(`Lock failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string, callback: AsyncCallback<string>): void
```

根据远程设备的本地表名获取指定远程设备的分布式表名。在查询远程设备数据库时，需要使用分布式表名，使用callback异步回调。

> **说明：**
> 
> 其中device通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> 方法得到。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 远程设备ID，不能为空字符串。 |
| table | string | 是 | 远程设备的本地表名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当获取分布式表名成功，err为undefined，data为远程设备的分布式表名；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).obtainDistributedTableName(deviceId, "EMPLOYEE", (err, tableName) => {
    if (err) {
      console.error(`ObtainDistributedTableName failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ObtainDistributedTableName successfully, tableName= ${tableName}`);
  });
}
```

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string): Promise<string>
```

根据远程设备的本地表名获取指定远程设备的分布式表名。在查询远程设备数据库时，需要使用分布式表名，使用Promise异步回调。

> **说明：**
> 
> 其中device通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> 方法得到。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 远程设备ID，不能为空字符串。 |
| table | string | 是 | 远程设备的本地表名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象。返回远程设备的分布式表名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).obtainDistributedTableName(deviceId, "EMPLOYEE").then((tableName: string) => {
    console.info(`ObtainDistributedTableName successfully, tableName= ${tableName}`);
  }).catch((err: BusinessError) => {
    console.error(`ObtainDistributedTableName failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## off

```TypeScript
off(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

取消数据变更的事件监听。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取值为'dataChange'，表示数据更改。 |
| type | SubscribeType | 是 | 订阅类型。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 指已注册的数据更改观察者。Array &lt;string&gt;为数据库中的数据发生改变的对端设备ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storeObserver = () => {
  console.info(`storeObserver`);
};

try {
  if (store != undefined) {
    (store as relationalStore.RdbStore).on('storeObserver', false, storeObserver);
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Register observer failed, code is ${code},message is ${message}`);
}

try {
  if (store != undefined) {
    (store as relationalStore.RdbStore).off('storeObserver', false, storeObserver);
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Unregister observer failed, code is ${code},message is ${message}`);
}
```

## off

```TypeScript
off(
      event: 'dataChange',
      type: SubscribeType,
      observer?: Callback<Array<string>> | Callback<Array<ChangeInfo>>
    ): void
```

取消数据变更的事件监听。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取值为'dataChange'，表示数据更改。 |
| type | SubscribeType | 是 | 订阅类型。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; \| [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;ChangeInfo&gt;&gt; | 否 | 回调函数。当type为 SUBSCRIBE_TYPE_REMOTE，observer类型需为Callback &lt;Array\<string>&gt;，其中Array &lt;string&gt;为数据库中的数据发生改变的对端设备ID。当type为 SUBSCRIBE_TYPE_CLOUD，observer类型需为Callback &lt;Array\<string>&gt;，其中Array &lt;string&gt;为数据库中的数据发生改变的云端账号。当type为 SUBSCRIBE_TYPE_CLOUD_DETAILS，observer类型需为Callback &lt;Array\<ChangeInfo>&gt;，其中Array &lt;ChangeInfo&gt;为数据库端云同步过程的详情。 当type为SUBSCRIBE_TYPE_LOCAL_DETAILS，observer类型需为Callback &lt;Array\<ChangeInfo>&gt;，其中Array &lt;ChangeInfo&gt;为本地数据库中的数据更 改的详情。 当observer没有传入时，表示取消当前type类型下所有数据变更的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

参见 [off](#off)

## off

```TypeScript
off(event: string, interProcess: boolean, observer?: Callback<void>): void
```

取消数据库的进程内或者进程间事件监听。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 取消订阅事件名称。事件名称与on接口调用时订阅事件的名称一致。 |
| interProcess | boolean | 是 | 指定是进程间还是本进程取消订阅。true：进程间。false：本进程。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 该参数存在，则取消指定Callback监听回调，否则取消该event事件的所有监听回调。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800050](../errorcode-data-rdb.md#14800050-获取订阅服务失败) | Failed to obtain the subscription service. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

参见 [off](#off)

## off

```TypeScript
off(event: 'autoSyncProgress', progress?: Callback<ProgressDetails>): void
```

取消订阅自动同步进度的通知。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'autoSyncProgress' | 是 | 取值为'autoSyncProgress'，表示自动同步进度通知。 |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 否 | 指已注册的自动同步进度观察者。该参数存在，则取消订阅指定回调，该参数为null或undefined或不存在，则取消订阅所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be valid. 3. The event must be a not empty string. 4. The progress must be function. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

参见 [off](#off)

## off

```TypeScript
off(event: 'statistics', observer?: Callback<SqlExecutionInfo> ): void
```

取消订阅SQL统计信息。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'statistics' | 是 | 取消订阅事件名称。取值为'statistics'，表示sql执行时间的统计。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | 否 | 回调函数。该参数存在，则取消指定Callback监听回调，否则取消该event事件的所有监听回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

参见 [off](#off)

## off

```TypeScript
off(event: 'perfStat', observer?: Callback<SqlExecutionInfo>): void
```

取消订阅SQL统计信息。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'perfStat' | 是 | 取消订阅事件名称。取值为'perfStat'，统计执行SQL的时间。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | 否 | 回调函数，表示订阅时的回调函数。该参数存在，则取消指定Callback监听回调，否则取消该event事件的所有监听回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

参见 [off](#off)

## off

```TypeScript
off(event: 'sqliteErrorOccurred', observer?: Callback<ExceptionMessage>): void
```

停止记录SQL执行过程中的异常日志。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'sqliteErrorOccurred' | 是 | 取消订阅事件名称，取值为'sqliteErrorOccurred'，记录SQL语句执行过程中的错误信息。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExceptionMessage](arkts-arkdata-relationalstore-exceptionmessage-i.md)&gt; | 否 | 回调函数。该参数存在，则取消指定Callback监听回调，否则取消该event事件的所有监听回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

参见 [off](#off)

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

注册数据库的数据变更的事件监听。当分布式数据库中的数据发生更改时，将调用回调。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取值为'dataChange'，表示数据更改。 |
| type | SubscribeType | 是 | 订阅类型。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 指分布式数据库中数据更改事件的观察者。Array &lt;string&gt;为数据库中的数据发生改变的对端设备ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storeObserver = () => {
  console.info(`storeObserver`);
};

try {
  if (store != undefined) {
    (store as relationalStore.RdbStore).on('storeObserver', false, storeObserver);
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Register observer failed, code is ${code},message is ${message}`);
}
```

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>> | Callback<Array<ChangeInfo>>): void
```

注册数据库的数据变更的事件监听。当分布式数据库或本地数据库中的数据发生更改时，将调用回调。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取值为'dataChange'，表示数据更改。 |
| type | SubscribeType | 是 | 订阅类型。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; \| [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;ChangeInfo&gt;&gt; | 是 | 回调函数。 当type为SUBSCRIBE_TYPE_REMOTE，observer类型需为Callback &lt;Array\<string>&gt;，其中Array &lt;string&gt;为数据库中的数据发生改变的对端设备ID。 当type为SUBSCRIBE_TYPE_CLOUD，observer类型需为Callback &lt;Array\<string>&gt;，其中Array &lt;string&gt;为数据库中的数据发生改变的云端账号。 当type为SUBSCRIBE_TYPE_CLOUD_DETAILS，observer类型需为Callback &lt;Array\<ChangeInfo>&gt;，其中Array &lt;ChangeInfo&gt;为数据库端云同步过程的 详情。 当type为SUBSCRIBE_TYPE_LOCAL_DETAILS，observer类型需为Callback &lt;Array\<ChangeInfo>&gt;，其中Array &lt;ChangeInfo&gt;为本地数据库中的数据更 改的详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

参见 [on](#on)

## on

```TypeScript
on(event: string, interProcess: boolean, observer: Callback<void>): void
```

注册数据库的进程内或者进程间事件监听。当调用emit接口时，将调用回调。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 订阅事件名称，与emit接口触发事件时的名称一致。 |
| interProcess | boolean | 是 | 指定是进程间还是本进程订阅。true：进程间。false：本进程。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。当进程间或本进程数据变更时触发回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800050](../errorcode-data-rdb.md#14800050-获取订阅服务失败) | Failed to obtain the subscription service. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

参见 [on](#on)

## on

```TypeScript
on(event: 'autoSyncProgress', progress: Callback<ProgressDetails>): void
```

在已打开端云同步，并且网络状态正常的条件下，注册自动同步进度通知，自动同步进行时调用回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'autoSyncProgress' | 是 | 取值为'autoSyncProgress'，表示自动同步进度通知。 |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | 是 | 用于返回[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)结果的回调 函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed;  4. The event must be a not empty string; 5. The progress must be function. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

参见 [on](#on)

## on

```TypeScript
on(event: 'statistics', observer: Callback<SqlExecutionInfo> ): void
```

订阅SQL统计信息。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'statistics' | 是 | 订阅事件名称，取值为'statistics'，表示sql执行时间的统计。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | 是 | 回调函数。用于返回数据库中SQL执行时间的统计信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

参见 [on](#on)

## on

```TypeScript
on(event: 'perfStat', observer: Callback<SqlExecutionInfo>): void
```

订阅SQL统计信息。使用[createTransaction](#createtransaction)创建的事务进行相关操作（ [Transaction](arkts-arkdata-relationalstore-transaction-i.md)），只会在事务结束（COMMIT/ROLLBACK）时通知一次统计信息。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'perfStat' | 是 | 订阅事件名称，取值为'perfStat'，统计执行SQL的时间。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | 是 | 回调函数。用于返回数据库执行SQL的时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

参见 [on](#on)

## on

```TypeScript
on(event: 'sqliteErrorOccurred', observer: Callback<ExceptionMessage>): void
```

记录执行SQL语句时的异常日志。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'sqliteErrorOccurred' | 是 | 订阅事件名称，取值为'sqliteErrorOccurred'，记录SQL语句执行过程中的错误信息。 |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExceptionMessage](arkts-arkdata-relationalstore-exceptionmessage-i.md)&gt; | 是 | 回调函数。用于返回SQL执行时出现的异常信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

参见 [on](#on)

## query

```TypeScript
query(predicates: RdbPredicates, callback: AsyncCallback<ResultSet>): void
```

根据指定条件查询数据库中的数据，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，使用此接口获取ResultSet后，调用 [getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、[getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法 时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数。当查询成功，err为undefined，data为ResultSet对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query(predicates, async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  });
}
```

## query

```TypeScript
query(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void
```

根据指定条件查询数据库中的数据，支持指定要查询的列，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，使用此接口获取ResultSet后，调用 [getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、[getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法 时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array &lt;string&gt; | 是 | 表示要查询的列。如果值为空，则查询应用于所有列。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数。当查询成功，err为undefined，data为ResultSet对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"], async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  });
}
```

## query

```TypeScript
query(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

根据指定条件查询数据库中的数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，使用此接口获取ResultSet后，调用 [getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、[getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法 时将无法成功获取数据，并可能导致操作失败或抛出异常。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array &lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ResultSet&gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  });
}
```

```TypeScript
let predicates4 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates4.equalTo('NAME', 'Rose');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const resultSet = await transaction.query(predicates4, ['ID', 'NAME', 'AGE', 'SALARY', 'CODES']);
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## queryByStep

```TypeScript
queryByStep(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>
```

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符不超过1000个，使用Promise异步回调。该接口按行逐步获取结果，不存在2MB的单条数据大小限制。聚合函数不支持嵌套使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 必须使用有效的SQL语句。否则在使用ResultSet时可能会抛出错误码。 |
| bindArgs | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ResultSet&gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).queryByStep("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'").then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起文件描述符泄漏与内存泄漏。
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

## queryByStep

```TypeScript
queryByStep(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

根据指定条件查询数据库中的数据，使用Promise异步回调。该接口按行逐步获取结果，不存在2MB的单条数据大小限制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array &lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ResultSet&gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).queryByStep(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起文件描述符泄漏与内存泄漏。
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

## queryLockedRow

```TypeScript
queryLockedRow(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

根据指定条件查询数据库中锁定的数据，使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array &lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ResultSet&gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).queryLockedRow(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## querySql

```TypeScript
querySql(sql: string, callback: AsyncCallback<ResultSet>): void
```

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此 限制，使用此接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用，当前支持的语法见 [规格限制](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/database/data-persistence-by-vector-store.md#规格限制)。聚合函数不支持嵌套使用。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数。当查询成功，err为undefined，data为ResultSet对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |

**示例**

关系型数据库：

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'", async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  });
}
```

向量数据库：

```TypeScript
// 相似度的计算符号是<->，余弦距离的计算符号是<=>
const querySql = "select id, repr <-> '[1.5,5.6]' as distance from test ORDER BY repr <-> '[1.5,5.6]' limit 10 offset 1;";
let resultSet = await store.querySql(querySql);

// 聚合查询，其中group by支持多列
const querySql1 = "select id, repr from test group by id, repr having max(repr<=>'[1.5,5.6]');";
let resultSet1 = await store.querySql(querySql1);

// 子查询，最大支持嵌套32层
const querySql2 = "select * from test where id in (select id from test1)";
let resultSet2 = await store.querySql(querySql2);
```

## querySql

```TypeScript
querySql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<ResultSet>): void
```

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个，支持传入SQL语句中参数的值，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格 小于2MB。如果单条数据超过此限制，使用此接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用，当前支持的语法见 [规格限制](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/database/data-persistence-by-vector-store.md#规格限制)。聚合函数不支持嵌套使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array &lt;ValueType&gt; | 是 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数。当查询成功，err为undefined，data为ResultSet对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = ?", ['sanguo'], async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  });
}
```

## querySql

```TypeScript
querySql(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>
```

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限 制，使用此接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用，当前支持的语法见 [规格限制](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/database/data-persistence-by-vector-store.md#规格限制)。聚合函数不支持嵌套使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ResultSet&gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |

**示例**

关系型数据库：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'").then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  });
}
```

向量数据库：

```TypeScript
// 查询id为1，与[1.5, 2.5]相似度小于0.5，且以相似度进行升序排序的前10条数据
const querySql = "select id, repr <-> ? as distance from test where id = ? and repr <-> ? < 0.5 ORDER BY repr <-> ? limit 10;";
const vectorValue: Float32Array = new Float32Array([1.5, 2.5]);
let resultSet = await store.querySql(querySql, [vectorValue, 1, vectorValue, vectorValue]);
```

## querySqlSync

```TypeScript
querySqlSync(sql: string, bindArgs?: Array<ValueType>): ResultSet
```

根据指定SQL语句查询数据库中的数据，SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个。对query同步接口获得的resultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤 放到[taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ResultSet | 返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |

**示例**

```TypeScript
if (store != undefined) {
  let resultSet: relationalStore.ResultSet | undefined;
  try {
    resultSet = store.querySqlSync("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'");
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  } finally {
    // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
    if (resultSet) {
      resultSet.close();
    }
  }
}
```

## querySqlWithoutRowCount

```TypeScript
querySqlWithoutRowCount(sql: string, bindArgs?: Array<ValueType>): Promise<LiteResultSet>
```

根据指定条件查询数据库中的数据，查询时不计算行数。使用Promise异步回调。性能优于 [querySql](#querysql)接口。SQL语句中的各种表达式和操作符之 间的关系操作符号不超过1000个。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md)&gt; | Promise对象。返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
async function querySqlWithoutRowCountEmployee(store : relationalStore.RdbStore) {
  if (store != undefined) {
    let resultSet: relationalStore.LiteResultSet | undefined;
    try {
      resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
      if (resultSet != undefined) {
        // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
        while (resultSet.goToNextRow()) {
          const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
          const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
          const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
          const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
          console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
        }
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      if (resultSet != undefined) {
        resultSet.close();
      }
    }
  }
}
```

```TypeScript
async function querySqlWithoutRowCountExample(store : relationalStore.RdbStore) {
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = await transaction.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## querySqlWithoutRowCountSync

```TypeScript
querySqlWithoutRowCountSync(sql: string, bindArgs?: Array<ValueType>): LiteResultSet
```

根据指定SQL语句查询数据库中的数据，查询时不计算行数。SQL语句中的各种表达式和操作符之间的关系操作符号不超过1000个。对querySqlWithoutRowCountSync同步接口获得的LiteResultSet进行操 作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到[taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句，不能为空字符串。 |
| bindArgs | Array &lt;ValueType&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | 返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
if (store != undefined) {
  let resultSet: relationalStore.LiteResultSet | undefined;
  try {
    resultSet = store.querySqlWithoutRowCountSync('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
    if (resultSet != undefined) {
      resultSet.close();
    }
  }
}
```

```TypeScript
async function querySqlWithoutRowCountSyncExample(store : relationalStore.RdbStore) {
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = transaction.querySqlWithoutRowCountSync('select * from EMPLOYEE where name = ?', ["Rose"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## querySync

```TypeScript
querySync(predicates: RdbPredicates, columns?: Array<string>): ResultSet
```

根据指定条件查询数据库中的数据。对query同步接口获得的resultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到 [taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array &lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ResultSet | 返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  let resultSet: relationalStore.ResultSet | undefined;
  try {
    resultSet = store.querySync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
    if (resultSet) {
      resultSet.close();
    }
  }
}
```

```TypeScript
let predicates5 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates5.equalTo('NAME', 'Rose');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let resultSet = transaction.querySync(predicates5, ['ID', 'NAME', 'AGE', 'SALARY', 'CODES']);
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## queryWithoutRowCount

```TypeScript
queryWithoutRowCount(predicates: RdbPredicates, columns?: Array<string>): Promise<LiteResultSet>
```

根据指定条件查询数据库中的数据，查询时不计算行数，性能优于 [query](#query)接口。使用Promise异步回 调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array &lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询该表的所有列。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md)&gt; | 返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
async function queryWithoutRowCountEmployee(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    let resultSet: relationalStore.LiteResultSet | undefined;
    try {
      resultSet = await store.queryWithoutRowCount(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
      if (resultSet != undefined) {
        // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
        while (resultSet.goToNextRow()) {
          const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
          const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
          const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
          const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
          console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
        }
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      if (resultSet != undefined) {
        resultSet.close();
      }
    }
  }
}
```

```TypeScript
async function queryWithoutRowCountExample(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = await transaction.queryWithoutRowCount(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## queryWithoutRowCountSync

```TypeScript
queryWithoutRowCountSync(predicates: RdbPredicates, columns?: Array<string>): LiteResultSet
```

根据指定条件查询数据库中的数据，查询时不计算行数。对queryWithoutRowCountSync同步接口获得的LiteResultSet进行操作时，若逻辑复杂且循环次数过多，可能造成freeze问题，建议将此步骤放到 [taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)线程中执行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array &lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | 返回LiteResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  let resultSet: relationalStore.LiteResultSet | undefined;
  try {
    resultSet = store.queryWithoutRowCountSync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
    if (resultSet != undefined) {
      // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
    if (resultSet != undefined) {
      resultSet.close();
    }
  }
}
```

```TypeScript
async function queryWithoutRowCountSyncExample(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = transaction.queryWithoutRowCountSync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
        if (resultSet != undefined) {
          // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## rekey

```TypeScript
rekey(cryptoParam?: CryptoParam): Promise<void>
```

手动更新加密数据库的密钥。使用Promise异步回调。从API版本26.0.0开始，支持使用该接口更新向量数据库（创建数据库时配置StoreConfig的vector字段为true）的密钥。仅支持加密数据库进行密钥更新，不支持非加密数据库变加密数据库及加密数据库变非加密数据库，且需要保持加密参数和密钥生成方式与建库时一致。不支持对非WAL模式的数据库进行密钥更新。手动更新密钥时需要独占访问数据库，此时若存在任何未释放的结果集（ResultSet）、事务（Transaction）或其他进程打开的数据库均会引发失败。数据库越大，密钥更新所需的时间越长。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cryptoParam | [CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md) | 否 | 指定用户自定义的加密参数。当此参数不填时，使用默认的加密参数，见CryptoParam。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |

**示例**

示例代码中this.context定义见Stage模型的应用[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 示例1：使用默认的加密参数
export default class EntryAbility extends UIAbility {
  onCreate() {
    let store: relationalStore.RdbStore | undefined = undefined;
    const STORE_CONFIG1: relationalStore.StoreConfig = {
      name: 'rdbstore1.db',
      securityLevel: relationalStore.SecurityLevel.S3,
      encrypt: true
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG1).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');

      let cryptoParam1: relationalStore.CryptoParam = {
        encryptionKey: new Uint8Array()
      };

      if (store != undefined) {
        try {
          await (store as relationalStore.RdbStore).rekey(cryptoParam1);
          console.info('rekey successful');
        } catch (err) {
          let e = err as BusinessError;
          console.error(`rekey failed, code is ${err.code}, message is ${err.message}`);
        }
      }
    }).catch((err: Error) => {
      let e = err as BusinessError;
      console.error(`Get RdbStore failed, code is ${e.code}, message is ${e.message}`);
    });
  }
}
```

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 示例2：使用自定义的加密参数
export default class EntryAbility extends UIAbility {
  onCreate() {
    let store: relationalStore.RdbStore | undefined = undefined;
    let cryptoParam: relationalStore.CryptoParam = {
      encryptionKey: new Uint8Array([1, 2, 3, 4, 5, 6]),
      iterationCount: 1000,
      encryptionAlgo: relationalStore.EncryptionAlgo.AES_256_GCM,
      hmacAlgo: relationalStore.HmacAlgo.SHA256,
      kdfAlgo: relationalStore.KdfAlgo.KDF_SHA256,
      cryptoPageSize: 1024
    };

    const STORE_CONFIG2: relationalStore.StoreConfig = {
      name: 'rdbstore2.db',
      securityLevel: relationalStore.SecurityLevel.S3,
      encrypt: true,
      cryptoParam: cryptoParam
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG2).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');
      let cryptoParam2: relationalStore.CryptoParam = {
        encryptionKey: new Uint8Array([6, 5, 4, 3, 2, 1]),
        iterationCount: 1000,
        encryptionAlgo: relationalStore.EncryptionAlgo.AES_256_GCM,
        hmacAlgo: relationalStore.HmacAlgo.SHA256,
        kdfAlgo: relationalStore.KdfAlgo.KDF_SHA256,
        cryptoPageSize: 1024
      };

      if (store != undefined) {
        try {
          await (store as relationalStore.RdbStore).rekey(cryptoParam2);
          console.info('rekey successful');
        } catch (err) {
          let e = err as BusinessError;
          console.error(`rekey failed, code is ${err.code}, message is ${err.message}`);
        }
      }
    }).catch((err: Error) => {
      let e = err as BusinessError;
      console.error(`Get RdbStore failed, code is ${e.code}, message is ${e.message}`);
    });
  }
}
```

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 示例3：更新向量数据库密钥
export default class EntryAbility extends UIAbility {
  onCreate() {
    let store: relationalStore.RdbStore | undefined = undefined;
    let cryptoParam: relationalStore.CryptoParam = {
      encryptionKey: new Uint8Array([1, 2, 3, 4, 5, 6]),
    };
    const STORE_CONFIG1: relationalStore.StoreConfig = {
      name: 'test.db',
      securityLevel: relationalStore.SecurityLevel.S2,
      encrypt: true,
      vector: true,
      cryptoParam: cryptoParam,
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG1).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');

      let newCryptoParam: relationalStore.CryptoParam = {
        encryptionKey: new Uint8Array([6, 5, 4, 3, 2, 1]),
      };

      if (store != undefined) {
        try {
          await (store as relationalStore.RdbStore).rekey(newCryptoParam);
          console.info('rekey successful');
        } catch (err) {
          let e = err as BusinessError;
          console.error(`rekey failed, code is ${err.code}, message is ${err.message}`);
        }
      }
    }).catch((err: Error) => {
      let e = err as BusinessError;
      console.error(`Get RdbStore failed, code is ${e.code}, message is ${e.message}`);
    });
  }
}
```

## rekeyEx

```TypeScript
rekeyEx(cryptoParam: CryptoParam): Promise<void>
```

手动更新数据库的密钥或加密参数，使用Promise异步回调。不支持对非WAL模式的数据库进行密钥更新。手动更新时需要独占访问数据库，此时若存在任何未释放的结果集（ResultSet）、事务（Transaction）或其他进程打开的数据库均会导致更新失败。支持加密数据库的参数更新，以及加密数据库与非加密数据库之间的相互转换。数据库越大，执行更新所需的时间越长。

> **说明：**
> 
> 加密参数变更需谨慎，在完成rekeyEx操作后，getRdbStore时必须使用新的参数来打开数据库，否则可能会导致开库失败。
> 
> 如果rekey过程因设备断电等原因中断，操作可能成功也可能失败。因此，建议业务方做好兜底保障（使用RekeyEx前后的参数进行冗余重试），确保不会错误地判断数据库的状态，从而避免出现数据库无法打开的问题。
> 
> 如果有加密参数变更，不建议getRdbStore时使用AllowedRebuild参数，防止因为传入的错误加密参数导致数据库发生重建。

**起始版本：** 22

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cryptoParam | [CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md) | 是 | 指定用户自定义的加密参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |

## remoteQuery

```TypeScript
remoteQuery(
      device: string,
      table: string,
      predicates: RdbPredicates,
      columns: Array<string>,
      callback: AsyncCallback<ResultSet>
    ): void
```

根据指定条件查询远程设备数据库中的数据。使用callback异步回调。

> **说明：**
> 
> 其中device通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> 方法得到。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 指定的远程设备ID，不能为空字符串。 |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象，指定查询的条件。 |
| columns | Array &lt;string&gt; | 是 | 表示要查询的列。如果值为空，则查询应用于所有列。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数。当查询成功，err为undefined，data为ResultSet对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.greaterThan("id", 0);
if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).remoteQuery(deviceId, "EMPLOYEE", predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"], async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  });
}
```

## remoteQuery

```TypeScript
remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array<string>): Promise<ResultSet>
```

根据指定条件查询远程设备数据库中的数据。使用Promise异步回调。

> **说明：**
> 
> 其中device通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> 方法得到。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 指定的远程设备ID，不能为空字符串。 |
| table | string | 是 | 指定的目标表名，不能为空字符串。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象，指定查询的条件。 |
| columns | Array &lt;string&gt; | 是 | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ResultSet&gt; | Promise对象。返回ResultSet对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.greaterThan("id", 0);
if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).remoteQuery(deviceId, "EMPLOYEE", predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet是一个数据集合的游标，默认指向第-1个记录，有效的数据从0开始。
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // 释放数据集的内存，若不释放可能会引起fd泄漏与内存泄漏。
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to remoteQuery, code is ${err.code},message is ${err.message}`);
  });
}
```

## restore

```TypeScript
restore(srcName: string, callback: AsyncCallback<void>): void
```

从指定的数据库备份文件恢复数据库，使用callback异步回调。该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcName | string | 是 | 指定数据库的备份文件名，不能为空字符串。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当恢复成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).restore("dbBackup.db", (err) => {
    if (err) {
      console.error(`Restore failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Restore success.');
  });
}
```

## restore

```TypeScript
restore(srcName: string): Promise<void>
```

从指定的数据库备份文件恢复数据库，使用Promise异步回调。该接口支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcName | string | 是 | 指定数据库的备份文件名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  let promiseRestore = (store as relationalStore.RdbStore).restore("dbBackup.db");
  promiseRestore.then(() => {
    console.info('Restore success.');
  }).catch((err: BusinessError) => {
    console.error(`Restore failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## rollBack

```TypeScript
rollBack(): void
```

回滚已经执行的SQL语句。此接口不允许嵌套事务，且不支持在多进程或多线程中使用。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error.<br>**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

if (store != undefined) {
  try {
    (store as relationalStore.RdbStore).beginTransaction();
    const valueBucket: relationalStore.ValuesBucket = {
      'NAME': value1,
      'AGE': value2,
      'SALARY': value3,
      'CODES': value4
    };
    (store as relationalStore.RdbStore).insert("test", valueBucket);
    (store as relationalStore.RdbStore).commit();
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Transaction failed, code is ${code},message is ${message}`);
    (store as relationalStore.RdbStore).rollBack();
  }
}
```

## rollback

```TypeScript
rollback(txId : number): Promise<void>
```

回滚已经执行的SQL语句，跟[beginTrans](#begintrans)配合使用，使用Promise异步回调。该接口仅支持向量数据库（在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置vector为true）使用。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| txId | number | 是 | 通过[beginTrans](#begintrans)获取的事务ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>, callback: AsyncCallback<void>): void
```

设置分布式数据库表，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tables | Array &lt;string&gt; | 是 | 要设置的分布式数据库的表名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置分布式列表成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], (err) => {
    if (err) {
      console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('SetDistributedTables successfully.');
  });
}
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>): Promise<void>
```

设置分布式数据库表，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tables | Array &lt;string&gt; | 是 | 要设置的分布式数据库的表名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"]).then(() => {
    console.info('SetDistributedTables successfully.');
  }).catch((err: BusinessError) => {
    console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>, type: DistributedType, callback: AsyncCallback<void>): void
```

设置分布式数据库表，支持指定表的分布式类型，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tables | Array &lt;string&gt; | 是 | 要设置的分布式数据库的表名。 |
| type | [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | 是 | 表的分布式类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置分布式列表成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800051](../errorcode-data-rdb.md#14800051-分布式表类型不匹配) | The type of the distributed table does not match. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], relationalStore.DistributedType.DISTRIBUTED_CLOUD, (err) => {
    if (err) {
      console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('SetDistributedTables successfully.');
  });
}
```

## setDistributedTables

```TypeScript
setDistributedTables(
      tables: Array<string>,
      type: DistributedType,
      config: DistributedConfig,
      callback: AsyncCallback<void>
    ): void
```

设置分布式数据库表，支持指定表的分布式类型和表的分布式配置信息，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tables | Array &lt;string&gt; | 是 | 要设置的分布式数据库的表名。 |
| type | [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | 是 | 表的分布式类型。 |
| config | [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md) | 是 | 表的分布式配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置分布式列表成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800051](../errorcode-data-rdb.md#14800051-分布式表类型不匹配) | The type of the distributed table does not match. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], relationalStore.DistributedType.DISTRIBUTED_CLOUD, {
    autoSync: true
  }, (err) => {
    if (err) {
      console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('SetDistributedTables successfully.');
  });
}
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>, type?: DistributedType, config?: DistributedConfig): Promise<void>
```

设置分布式数据库表，支持指定表的分布式类型和表的分布式配置信息，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tables | Array &lt;string&gt; | 是 | 要设置的分布式数据库的表名。 |
| type | [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | 否 | 表的分布式类型。默认值是relationalStore.DistributedType.DISTRIBUTED_DEVICE。 |
| config | [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md) | 否 | 表的分布式配置信息。不传入时默认autoSync为false，需要调用 [cloudSync](#cloudsync) 接口触发端云同步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800051](../errorcode-data-rdb.md#14800051-分布式表类型不匹配) | The type of the distributed table does not match. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], relationalStore.DistributedType.DISTRIBUTED_CLOUD, {
    autoSync: true
  }).then(() => {
    console.info('SetDistributedTables successfully.');
  }).catch((err: BusinessError) => {
    console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## setLocale

```TypeScript
setLocale(locale: string) : Promise<void>
```

设置自定义排序的语言。使用Promise异步回调。该值符合ISO 639标准，但是仅支持ICU中的部分语言，对于不支持的语言，设置自定义排序的语言时会报错14800001。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | 设置自定义排序的语言，不能为空字符串。该值符合ISO 639标准，如："zh"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
try {
  if (store != undefined) {
    await store.setLocale("zh");
    store.querySql("SELECT * FROM EMPLOYEE ORDER BY NAME COLLATE LOCALES", async (err, resultSet) => {
      if (err) {
        console.error(`Query failed, code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`ResultSet rowCount ${resultSet.rowCount}`);
    });
  }
} catch (err) {
  console.error(`SetLocale failed, code: ${err.code}, message: ${err.message}`);
}
```

## stopCloudSync

```TypeScript
stopCloudSync(): Promise<void>
```

停止与云端的数据同步，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the device does not support the cloud synchronization capability. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
if (store != undefined) {
  (store as relationalStore.RdbStore).stopCloudSync().then(() => {
    console.info('Succeeded in stopping cloud sync');
  }).catch((err: BusinessError) => {
    console.error(`Failed to stop cloud sync. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback<Array<[string, number]>>): void
```

在设备之间同步数据，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 指同步模式。该值可以是relationalStore.SyncMode.SYNC_MODE_PUSH、 relationalStore.SyncMode.SYNC_MODE_PULL。 |
| predicates | RdbPredicates | 是 | 约束同步数据和设备。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | 是 | 回调函数，用于向调用者发送同步结果。string：设备ID；number：每个设备同步状态，0表示成功，1表示 失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceIds: Array<string> = [];

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].networkId!;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.inDevices(deviceIds);
if (store != undefined) {
  (store as relationalStore.RdbStore).sync(relationalStore.SyncMode.SYNC_MODE_PUSH, predicates, (err, result) => {
    if (err) {
      console.error(`Sync failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Sync done.');
    for (let i = 0; i < result.length; i++) {
      console.info(`device= ${result[i][0]}, status= ${result[i][1]}`);
    }
  });
}
```

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates): Promise<Array<[string, number]>>
```

在设备之间同步数据，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 指同步模式。该值可以是relationalStore.SyncMode.SYNC_MODE_PUSH、 relationalStore.SyncMode.SYNC_MODE_PULL。 |
| predicates | RdbPredicates | 是 | 约束同步数据和设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;[string, number]&gt;&gt; | Promise对象。返回同步结果。string：设备ID；number：每个设备同步状态，0表示成功，1表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceIds: Array<string> = [];

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].networkId!;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.inDevices(deviceIds);
if (store != undefined) {
  (store as relationalStore.RdbStore).sync(relationalStore.SyncMode.SYNC_MODE_PUSH, predicates).then((result: Object[][]) => {
    console.info('Sync done.');
    for (let i = 0; i < result.length; i++) {
      console.info(`device= ${result[i][0]}, status= ${result[i][1]}`);
    }
  }).catch((err: BusinessError) => {
    console.error(`Sync failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## syncEx

```TypeScript
syncEx(mode: SyncMode, predicates: RdbPredicates): Promise<Array<SyncResult>>
```

在设备之间同步数据，使用Promise异步回调，可以返回具体的同步状态信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | SyncMode | 是 | 同步模式。该值可以是relationalStore.SyncMode.SYNC_MODE_PUSH、 relationalStore.SyncMode.SYNC_MODE_PULL。 |
| predicates | RdbPredicates | 是 | 约束同步数据和设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;SyncResult&gt;&gt; | Promise对象。返回SyncResult数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceIds: Array<string> = [];

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].networkId!;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.inDevices(deviceIds);
store.syncEx(relationalStore.SyncMode.SYNC_MODE_PUSH, predicates).then((result: relationalStore.SyncResult[]) => {
  for (let i = 0; i < result.length; i++) {
    let code = result[i].code;
    let message = result[i].message;
    if (code === 0) {
      console.info(`SyncEx success`);
    } else {
      console.error(`SyncEx failed, message: ${message} code : ${code}`);
    }
  }
}).catch((err: Error) => {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error("syncEx errCode:" + code + ",errMessage:" + message);
});
```

## unlockRow

```TypeScript
unlockRow(predicates: RdbPredicates): Promise<void>
```

根据RdbPredicates的指定实例对象从数据库中解锁数据，使用Promise异步回调。该接口只支持主键为基本类型的表、不支持共享表、无主键表和复合类型主键表。该接口不支持依赖关系表之间的锁传递，如果表存在依赖关系，需要根据依赖关系手动调用该接口。该接口不支持对已删除数据的操作。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的锁定条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800018](../errorcode-data-rdb.md#14800018-查询结果没有数据符合条件) | No data meets the condition. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).unlockRow(predicates).then(() => {
    console.info(`Unlock success`);
  }).catch((err: BusinessError) => {
    console.error(`Unlock failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

根据RdbPredicates的指定实例对象更新数据库中的数据，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当更新数据成功，err为undefined，data为受影响的行数；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates, (err, rows) => {
    if (err) {
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Updated row count: ${rows}`);
  });
}
```

## update

```TypeScript
update(
      values: ValuesBucket,
      predicates: RdbPredicates,
      conflict: ConflictResolution,
      callback: AsyncCallback<number>
    ): void
```

根据RdbPredicates的指定实例对象更新数据库中的数据，可以通过conflict参数指定冲突解决模式 [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，使用callback异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当更新数据成功，err为undefined，data为受影响的行数；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE, (err, rows) => {
    if (err) {
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Updated row count: ${rows}`);
  });
}
```

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates): Promise<number>
```

根据RdbPredicates的指定实例对象更新数据库中的数据，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates).then(async (rows: number) => {
    console.info(`Updated row count: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, conflict: ConflictResolution): Promise<number>
```

根据RdbPredicates的指定实例对象更新数据库中的数据，可以通过conflict参数指定冲突解决模式 [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，使用Promise异步回调。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| conflict | ConflictResolution | 是 | 指定冲突解决模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象。返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.<br>**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.<br>**适用版本：** 12+ |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond.<br>**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.<br>**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.<br>**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.<br>**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.<br>**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.<br>**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then(async (rows: number) => {
    console.info(`Updated row count: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## updateSync

```TypeScript
updateSync(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): number
```

根据RdbPredicates的指定实例对象更新数据库中的数据。由于共享内存的大小限制为2MB，因此单条数据的大小也必须严格小于2MB。如果单条数据超过此限制，在后续通过RdbStore的 [query](#query) 或 [querySql](#querysql) 接口获取ResultSet后，调用[getValue](arkts-arkdata-relationalstore-resultset-i.md#getvalue)、 [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)等get方法时将无法成功获取数据，并可能导致操作失败或抛出异常。如需读取超过2MB的数据，请使用 [queryByStep](#querybystep)接口。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认值是relationalStore.ConflictResolution.ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回受影响的行数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-数据库没有响应) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// 以下三种方式可用
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  try {
    let rows: number = (store as relationalStore.RdbStore).updateSync(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`Updated row count: ${rows}`);
  } catch (err) {
    console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
  }
}
```

```TypeScript
const valueBucketG: relationalStore.ValuesBucket = {
  NAME: 'Rose',
  AGE: 22,
  SALARY: 200.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
let predicates1 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates1.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rows = transaction.updateSync(valueBucketG, predicates1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      await transaction.commit();
      console.info(`Updated row count: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## updateWithReturning

```TypeScript
updateWithReturning(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig,
      conflict?: ConflictResolution): Promise<Result>
```

根据RdbPredicates的指定实例对象更新数据库中的数据，可以通过conflict参数指定当发生数据冲突时的解决模式 [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回[Result](arkts-arkdata-relationalstore-result-i.md)，使用Promise 异步回调。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Result&gt; | Promise对象。返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
async function updateWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = await rdbStore.updateWithReturning(valueBucket1, predicates, config);
    console.info(`updateWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`updateWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`updateWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
async function transUpdateWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = await trans.updateWithReturning(valueBucket1, predicates, config);
    console.info(`transUpdateWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transUpdateWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transUpdateWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## updateWithReturningSync

```TypeScript
updateWithReturningSync(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig,
      conflict?: ConflictResolution): Result
```

根据RdbPredicates的指定实例对象更新数据库中的数据，可以通过conflict参数指定当发生数据冲突时的解决模式 [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md)，返回[Result](arkts-arkdata-relationalstore-result-i.md)。conflict参数不建议使用ON_CONFLICT_FAIL策略，可能无法返回正确的结果。单条字符串类型字段最大支持写入8MB，超出部分将被截断，仅保留前8MB数据，若需存储超过8MB的内容，建议使用blob类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | ValuesBucket | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | RdbPredicates | 是 | RdbPredicates的实例对象指定的更新条件。 |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | 是 | 指定返回值的配置信息。 |
| conflict | ConflictResolution | 否 | 指定冲突解决模式。默认为ON_CONFLICT_NONE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Result | 返回受影响的数据集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit. |

**示例**

```TypeScript
function updateWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = rdbStore.updateWithReturningSync(valueBucket1, predicates, config);
    console.info(`updateWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`updateWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`updateWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

```TypeScript
function transUpdateWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = trans.updateWithReturningSync(valueBucket1, predicates, config);
    console.info(`transUpdateWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transUpdateWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transUpdateWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## rebuilt

```TypeScript
rebuilt: RebuildType
```

rebuilt: [RebuildType](arkts-arkdata-relationalstore-rebuildtype-e.md)用于获取数据库是否进行过重建或修复。

**类型：** [RebuildType](arkts-arkdata-relationalstore-rebuildtype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## version

```TypeScript
version: number
```

version: int设置和获取数据库版本，值为正整数。读取和设置version属性会占用数据库连接，避免对该属性进行频繁操作。使用临时变量保存读取到的version值，在数据库变更完成后将其赋值给RdbStore实例的version属性。数据库升 级时变更version属性的场景，请参考[开发步骤](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/database/data-persistence-by-rdb-store.md#开发步骤)。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
