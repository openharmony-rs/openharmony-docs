# distributedData

分布式数据管理为应用程序提供不同设备间数据库的分布式协同能力。通过调用分布式数据各个接口，应用程序可将数据保存到分布式数据库中，并可对分布式数据库中的数据进行增加、删除、修改、查询、同步等操作。该模块提供以下分布式数据管理相关的常用功能：

- [KVManager](arkts-arkdata-distributeddata-kvmanagerconfig-i.md)：数据管理实例，用于获取KVStore的相关信息。  
- [KvStoreResultSet<sup>8+</sup>](arkts-arkdata-distributeddata-kvstoreresultset-i.md)：提供获取KVStore数据库结果集的相关方法，包括查询和移动数据读取位置等。  
- [Query<sup>8+</sup>](arkts-arkdata-distributeddata-query-c.md)：使用谓词表示数据库查询，提供创建Query实例、查询数据库中的数据和添加谓词的方法。  
- [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)：KVStore数据库实例，提供增加数据、删除数据和订阅数据变更、订阅数据同步完成的方法。  
- [SingleKVStore](arkts-arkdata-distributeddata-singlekvstore-i.md)：单版本分布式数据库，继承自[KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)，不对数据所属设备进行区分，提供查询数据和同步数据的方法。  
- [DeviceKVStore<sup>8+</sup>](arkts-arkdata-distributeddata-devicekvstore-i.md)：设备协同数据库，继承自[KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)，以设备维度对数据进行区分，提供查询数据和同步数据的方法。
> **说明：**
> - 从API Version 9开始，该接口不再维护，推荐使用新接口  
> [`@ohos.data.distributedKVStore`](arkts-data-distributedkvstore.md)。
> - 本模块中所有需要获取deviceId的接口，都仅系统应用可用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** distributedKVStore

<!--Device-unnamed-declare namespace distributedData--><!--Device-unnamed-declare namespace distributedData-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [Constants](arkts-arkdata-distributeddata-constants-n.md) | KVStore常量。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md#createkvmanager) | 创建一个KVManager对象实例，用于管理数据库对象，使用callback异步回调。 |
| [createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md#createkvmanager-1) | 创建一个KVManager对象实例，用于管理数据库对象，使用Promise异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Schema](arkts-arkdata-distributeddata-schema-c.md) | 表示数据库模式，可以在创建或打开数据库时创建Schema对象并将它们放入[Options](arkts-arkdata-distributeddata-options-i.md)中。 |
| [FieldNode](arkts-arkdata-distributeddata-fieldnode-c.md) | 表示 Schema 实例的节点，提供定义存储在数据库中的值的方法。 |
| [Query](arkts-arkdata-distributeddata-query-c.md) | 使用谓词表示数据库查询，提供创建Query实例、查询数据库中的数据和添加谓词的方法。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [KVManagerConfig](arkts-arkdata-distributeddata-kvmanagerconfig-i.md) | 提供KVManager实例的配置信息，包括调用方的Bundle名称和用户信息。 |
| [UserInfo](arkts-arkdata-distributeddata-userinfo-i.md) | 用户信息。 |
| [Value](arkts-arkdata-distributeddata-value-i.md) | 存储在数据库中的值对象。 |
| [Entry](arkts-arkdata-distributeddata-entry-i.md) | 存储在数据库中的键值对。 |
| [ChangeNotification](arkts-arkdata-distributeddata-changenotification-i.md) | 数据变更时通知的对象，包括数据插入的数据、更新的数据、删除的数据和设备ID。 |
| [Options](arkts-arkdata-distributeddata-options-i.md) | 用于提供创建数据库的配置信息。 |
| [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | 提供获取KVStore数据库结果集的相关方法，包括查询和移动数据读取位置等。在调用KvStoreResultSet的方法前，需要先通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)构建一个KVStore实例。 |
| [KVStore](arkts-arkdata-distributeddata-kvstore-i.md) | KVStore数据库实例，提供增加数据、删除数据和订阅数据变更、订阅数据同步完成的方法。在调用KVStore的方法前，需要先通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)构建一个KVStore实例。 |
| [SingleKVStore](arkts-arkdata-distributeddata-singlekvstore-i.md) | 单版本数据库，继承自[KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)数据库，提供查询数据和同步数据的方法。单版本数据库，不对数据所属设备进行区分，不同设备使用相同键写入数据会互相覆盖。比如，可以使用单版本数据库实现个人日历、联系人数据在不同设备间的数据同步。在调用SingleKVStore的方法前，需要先通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)构建一个SingleKVStore实例。 |
| [DeviceKVStore](arkts-arkdata-distributeddata-devicekvstore-i.md) | 设备协同数据库，继承自KVStore，提供查询数据和同步数据的方法。设备协同数据库，以设备维度对数据进行区分，每台设备仅能写入和修改本设备的数据，其它设备的数据对其是只读的，无法修改其它设备的数据。比如，可以使用设备协同数据库实现设备间的图片分享，可以查看其他设备的图片，但无法修改和删除其他设备的图片。在调用DeviceKVStore的方法前，需要先通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)构建一个DeviceKVStore实例。 |
| [KVManager](arkts-arkdata-distributeddata-kvmanager-i.md) | 数据管理实例，用于获取KVStore的相关信息。在调用KVManager的方法前，需要先通过[createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md#createkvmanager)构建一个KVManager实例。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [UserType](arkts-arkdata-distributeddata-usertype-e.md) | 用户类型枚举。 |
| [ValueType](arkts-arkdata-distributeddata-valuetype-e.md) | 数据类型枚举。 |
| [SyncMode](arkts-arkdata-distributeddata-syncmode-e.md) | 同步模式枚举。 |
| [SubscribeType](arkts-arkdata-distributeddata-subscribetype-e.md) | 订阅类型枚举。 |
| [KVStoreType](arkts-arkdata-distributeddata-kvstoretype-e.md) | KVStore数据库类型枚举。 |
| [SecurityLevel](arkts-arkdata-distributeddata-securitylevel-e.md) | 数据库的安全级别枚举。 |

