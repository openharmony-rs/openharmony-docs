# @ohos.data.distributedData

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

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [distributedData](arkts-arkdata-distributeddata-n.md) | 分布式数据管理为应用程序提供不同设备间数据库的分布式协同能力。通过调用分布式数据各个接口，应用程序可将数据保存到分布式数据库中，并可对分布式数据库中的数据进行增加、删除、修改、查询、同步等操作。该模块提供以下分布式数据管理相关的常用功能：  - [KVManager](arkts-arkdata-distributeddata-kvmanagerconfig-i.md)：数据管理实例，用于获取KVStore的相关信息。  - [KvStoreResultSet<sup>8+</sup>](arkts-arkdata-distributeddata-kvstoreresultset-i.md)：提供获取KVStore数据库结果集的相关方法，包括查询和移动数据读取位置等。  - [Query<sup>8+</sup>](arkts-arkdata-distributeddata-query-c.md)：使用谓词表示数据库查询，提供创建Query实例、查询数据库中的数据和添加谓词的方法。  - [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)：KVStore数据库实例，提供增加数据、删除数据和订阅数据变更、订阅数据同步完成的方法。  - [SingleKVStore](arkts-arkdata-distributeddata-singlekvstore-i.md)：单版本分布式数据库，继承自[KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)，不对数据所属设备进行区分，提供查询数据和同步数据的方法。  - [DeviceKVStore<sup>8+</sup>](arkts-arkdata-distributeddata-devicekvstore-i.md)：设备协同数据库，继承自[KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)，以设备维度对数据进行区分，提供查询数据和同步数据的方法。 |

