# distributedData(Distributed Data Management)

The distributed data management module implements collaboration between databases of different devices for applications. The APIs provided by distributed data management can be used to save data to distributed databases and perform operations such as adding, deleting, modifying, querying, and synchronizing data in distributed databases. This module provides the following functions:

- [KVManager](arkts-arkdata-distributeddata-kvmanagerconfig-i.md): provides a **KVManager** instance to manage key-value (KV)  
stores.  
- [KvStoreResultSet&lt;sup&gt;8+&lt;/sup&gt;](arkts-arkdata-distributeddata-kvstoreresultset-i.md): provides APIs to obtain the KV store  
result set and query or move the data read position.  
- [Query&lt;sup&gt;8+&lt;/sup&gt;](arkts-arkdata-distributeddata-query-c.md): provides APIs to query data from the database through a  
**Query** instance by using predicates.  
- [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md): provides APIs to add data, delete data, and observe data changes and  
data sync through a **KVStore** instance.  
- [SingleKVStore](arkts-arkdata-distributeddata-singlekvstore-i.md): provides APIs to query and synchronize data in a single KV  
store. This class inherits from [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md), and data is not distinguished by device.  
- [DeviceKVStore&lt;sup&gt;8+&lt;/sup&gt;](arkts-arkdata-distributeddata-devicekvstore-i.md): provides APIs to query and synchronize data in a  
device KV store. This class inherits from [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md), and data is distinguished by device.

[@ohos.data.distributedKVStore](arkts-arkdata-data-distributedkvstore.md).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [distributedKVStore](arkts-arkdata-data-distributedkvstore.md)

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## Modules to Import

```TypeScript
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [Constants](arkts-arkdata-distributeddata-constants-n.md) | Defines the KV store constants. |

### Functions

| Name | Description |
| --- | --- |
| [createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md) | Creates a **KVManager** instance to manage KV stores. This API uses an asynchronous callback to return the result. |
| [createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md) | Creates a **KVManager** instance to manage KV stores. This API uses a promise to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [Schema](arkts-arkdata-distributeddata-schema-c.md) | Defines the schema of a KV store. You can create a **Schema** object and place it in [Options](arkts-arkdata-distributeddata-options-i.md) when creating or opening a KV store. |
| [FieldNode](arkts-arkdata-distributeddata-fieldnode-c.md) | Represents a **Schema** instance, which provides the APIs for defining the values stored in a KV store. |
| [Query](arkts-arkdata-distributeddata-query-c.md) | Provides APIs to create a **Query** object, which defines different data query criteria. |

### Interfaces

| Name | Description |
| --- | --- |
| [KVManagerConfig](arkts-arkdata-distributeddata-kvmanagerconfig-i.md) | Represents the configuration of a **KVManager** instance, including the bundle name and user information of the caller. |
| [UserInfo](arkts-arkdata-distributeddata-userinfo-i.md) | Defines user information. |
| [Value](arkts-arkdata-distributeddata-value-i.md) | Defines the **value** object in a KV store. |
| [Entry](arkts-arkdata-distributeddata-entry-i.md) | Defines the KV pairs stored in the KV store. |
| [ChangeNotification](arkts-arkdata-distributeddata-changenotification-i.md) | Defines the content of data change notifications, including inserted data, updated data, deleted data, and device ID. |
| [Options](arkts-arkdata-distributeddata-options-i.md) | Provides KV store configuration. |
| [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | Provides APIs to obtain the KV store result sets, and query and move the data read position. Before calling any method in **KvStoreResultSet**, you must use getKVStore to obtain a **KVStore** object. |
| [KVStore](arkts-arkdata-distributeddata-kvstore-i.md) | Provides APIs to manage data in a KV store, for example, adding or deleting data and subscribing to data changes or completion of data sync. Before calling any method in **KVStore**, you must use getKVStore to obtain a **KVStore** object. |
| [SingleKVStore](arkts-arkdata-distributeddata-singlekvstore-i.md) | Provides APIs to query and synchronize data in a single KV store. This class inherits from [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md). |
| [DeviceKVStore](arkts-arkdata-distributeddata-devicekvstore-i.md) | Provides APIs to query and synchronize data in a device KV store. This class inherits from [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md). Data is distinguished by device in a device KV store. Each device can only write and modify its own data. Data of other devices is read-only and cannot be modified. For example, a device KV store can be used to implement image sharing between devices. The images of other devices can be viewed, but not be modified or deleted. Before calling any method in **DeviceKVStore**, you must use getKVStore to obtain a **DeviceKVStore** object. |
| [KVManager](arkts-arkdata-distributeddata-kvmanager-i.md) | Creates a **KVManager** object to obtain KV store information. Before calling any method in **KVManager**, you must use [createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md) to create a **KVManager** object. |

### Enums

| Name | Description |
| --- | --- |
| [UserType](arkts-arkdata-distributeddata-usertype-e.md) | Enumerates the user types. |
| [ValueType](arkts-arkdata-distributeddata-valuetype-e.md) | Enumerates the data types. |
| [SyncMode](arkts-arkdata-distributeddata-syncmode-e.md) | Enumerates the sync modes. |
| [SubscribeType](arkts-arkdata-distributeddata-subscribetype-e.md) | Enumerates the subscription types. |
| [KVStoreType](arkts-arkdata-distributeddata-kvstoretype-e.md) | Enumerates the KV store types. |
| [SecurityLevel](arkts-arkdata-distributeddata-securitylevel-e.md) | Enumerates the KV store security levels. |
