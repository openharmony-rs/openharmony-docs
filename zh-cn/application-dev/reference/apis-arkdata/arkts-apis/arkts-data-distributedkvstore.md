# @ohos.data.distributedKVStore

分布式键值数据库为应用程序提供不同设备间数据库的分布式协同能力。通过调用分布式键值数据库各个接口，应用程序可将数据保存到分布式键值数据库中，并可对分布式键值数据库中的数据进行增加、删除、修改、查询、端端同步等操作。

该模块提供以下常用功能：

- [KVManager](arkts-arkdata-distributedkvstore-kvmanager-i.md)：分布式键值数据库管理实例，用于获取数据库的相关信息。  
- [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md)：提供获取数据库结果集的相关方法，包括查询和移动数据读取位置等。  
- [Query](arkts-arkdata-distributedkvstore-query-c.md)：使用谓词表示数据库查询，提供创建Query实例、查询数据库中的数据和添加谓词的方法。  
- [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md)：单版本分布式键值数据库，不对数据所属设备进行区分，提供查询数据和端端同步数据的方法。  
- [DeviceKVStore](arkts-arkdata-distributedkvstore-devicekvstore-i.md)：设备协同数据库，继承自[SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md)，以设备维度对数据进行区分，提供查询数据和端端同步数据的方法。

**起始版本：** 9

<!--Device-unnamed-declare namespace distributedKVStore--><!--Device-unnamed-declare namespace distributedKVStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createKVManager](arkts-arkdata-distributedkvstore-createkvmanager-f.md#createkvmanager) | 创建一个KVManager对象实例，用于管理数据库对象。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [FieldNode](arkts-arkdata-distributedkvstore-fieldnode-c.md) | 表示 Schema 实例的节点，提供定义存储在数据库中的值的方法。 |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | 使用谓词表示数据库查询，提供创建Query实例、查询数据库中的数据和添加谓词的方法。Query对象的谓词方法均返回自身，支持链式调用。一个Query对象中谓词数量上限为256个。 |
| [Schema](arkts-arkdata-distributedkvstore-schema-c.md) | 表示数据库模式，可以在创建或打开数据库时创建Schema对象并将它们放入[Options](arkts-arkdata-distributedkvstore-options-i.md)中。  STRICT：STRICT模式要求用户插入的值必须与Schema定义严格匹配，字段数量和格式都不能有差异。如果不匹配，数据库将在插入数据时返回错误。  COMPATIBLE：选择为COMPATIBLE模式时，数据库在检查Value格式时较为宽松，只要Value具有Schema描述的特征即可，允许存在额外字段。例如，定义了id、name字段时，可以插入id、name、age等多个字段。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackupConfig](arkts-arkdata-distributedkvstore-backupconfig-i.md) | 用于备份数据库的配置信息。 |
| [ChangeNotification](arkts-arkdata-distributedkvstore-changenotification-i.md) | 数据变更时通知的对象，包括插入的数据、更新的数据、删除的数据和设备ID。 |
| [Constants](arkts-arkdata-distributedkvstore-constants-i.md) | 分布式键值数据库常量。 |
| [DeviceKVStore](arkts-arkdata-distributedkvstore-devicekvstore-i.md) | 设备协同数据库，继承自SingleKVStore，提供查询数据和端端同步数据的方法，可以使用SingleKVStore的方法例如：put、putBatch等。  设备协同数据库，以设备维度对数据进行区分，每台设备仅能写入和修改本设备的数据，其它设备的数据对其是只读的，无法修改其它设备的数据。  比如，可以使用设备协同数据库实现设备间的图片分享，可以查看其他设备的图片，但无法修改和删除其他设备的图片。  在调用DeviceKVStore的方法前，需要先通过[getKVStore](distributedKVStore.KVManager.getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个DeviceKVStore实例。 |
| [Entry](arkts-arkdata-distributedkvstore-entry-i.md) | 存储在数据库中的键值对。 |
| [KVManager](arkts-arkdata-distributedkvstore-kvmanager-i.md) | 分布式键值数据库管理实例，用于获取分布式键值数据库的相关信息。在调用KVManager的方法前，需要先通过[createKVManager](arkts-arkdata-distributedkvstore-createkvmanager-f.md#createkvmanager-1)构建一个KVManager实例。 |
| [KVManagerConfig](arkts-arkdata-distributedkvstore-kvmanagerconfig-i.md) | 提供KVManager实例的配置信息，包括调用方的包名和应用的上下文。 |
| [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md) | 提供获取数据库结果集的相关方法，包括查询和移动数据读取位置等。同时允许打开的结果集的最大数量为8个。  KVStoreResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。  在调用KVStoreResultSet的方法前，需要先通过[getKVStore](distributedKVStore.KVManager.getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个SingleKVStore或者DeviceKVStore实例。 |
| [Options](arkts-arkdata-distributedkvstore-options-i.md) | 用于提供创建数据库的配置信息。 |
| [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md) | SingleKVStore数据库实例，提供增加数据、删除数据和订阅数据变更、订阅数据端端同步完成的方法。  在调用SingleKVStore的方法前，需要先通过[getKVStore](distributedKVStore.KVManager.getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个SingleKVStore实例。 |
| [Value](arkts-arkdata-distributedkvstore-value-i.md) | 存储在数据库中的值对象。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceKVStore](arkts-arkdata-distributedkvstore-devicekvstore-i-sys.md) | 设备协同数据库，继承自SingleKVStore，提供查询数据和端端同步数据的方法，可以使用SingleKVStore的方法例如：put、putBatch等。  设备协同数据库，以设备维度对数据进行区分，每台设备仅能写入和修改本设备的数据，其它设备的数据对其是只读的，无法修改其它设备的数据。  比如，可以使用设备协同数据库实现设备间的图片分享，可以查看其他设备的图片，但无法修改和删除其他设备的图片。  在调用DeviceKVStore的方法前，需要先通过[getKVStore](distributedKVStore.KVManager.getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个DeviceKVStore实例。 |
| [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i-sys.md) | SingleKVStore数据库实例，提供增加数据、删除数据和订阅数据变更、订阅数据端端同步完成的方法。  在调用SingleKVStore的方法前，需要先通过[getKVStore](distributedKVStore.KVManager.getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个SingleKVStore实例。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [KVStoreType](arkts-arkdata-distributedkvstore-kvstoretype-e.md) | 分布式键值数据库类型枚举。 |
| [SecurityLevel](arkts-arkdata-distributedkvstore-securitylevel-e.md) | 数据库的安全级别枚举。 |
| [SubscribeType](arkts-arkdata-distributedkvstore-subscribetype-e.md) | 订阅类型枚举。 |
| [SyncMode](arkts-arkdata-distributedkvstore-syncmode-e.md) | 同步模式枚举。 |
| [ValueType](arkts-arkdata-distributedkvstore-valuetype-e.md) | 数据类型枚举。 |

