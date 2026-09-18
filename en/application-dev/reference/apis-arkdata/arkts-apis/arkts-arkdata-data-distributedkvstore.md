# @ohos.data.distributedKVStore(Distributed KV Store)

The **distributedKVStore** module implements collaboration between databases for different devices that form a Super Device. You can use the APIs provided by this module to save application data to a distributed key-value (KV) store and perform operations, such as adding, deleting, modifying, and querying data, and synchronizing data across devices. The **distributedKVStore** module provides the following functionalities:

- [KVManager](arkts-arkdata-distributedkvstore-kvmanagerconfig-i.md): provides a **KVManager** instance to obtain KV store  
information.  
- [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md): provides APIs for accessing the results obtained  
from a KV store.  
- [Query](arkts-arkdata-distributedkvstore-query-c.md): provides APIs for setting predicates for data query.  
- [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md): provides APIs for querying data in single KV stores and  
synchronizing data across devices. The single KV stores manage data without distinguishing devices.  
- [DeviceKVStore](arkts-arkdata-distributedkvstore-devicekvstore-i.md): provides APIs for querying data in device KV stores and  
synchronizing data across devices. This class inherits from [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md). The device KV stores manage data by device.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createKVManager](arkts-arkdata-distributedkvstore-createkvmanager-f.md) | Creates a **KVManager** instance for KV store management. |

### Classes

| Name | Description |
| --- | --- |
| [FieldNode](arkts-arkdata-distributedkvstore-fieldnode-c.md) | Represents a **Schema** instance, which provides the methods for defining the values stored in a KV store. |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | Provides methods to create a **Query** object, which defines different data query criteria. A **Query** object supports a maximum of 256 predicates. |
| [Schema](arkts-arkdata-distributedkvstore-schema-c.md) | Defines the schema of a KV store. You can create a **Schema** object and pass it in [Options](arkts-arkdata-distributedkvstore-options-i.md) when creating or opening a KV store. |

### Interfaces

| Name | Description |
| --- | --- |
| [BackupConfig](arkts-arkdata-distributedkvstore-backupconfig-i.md) | Provides backup config to backup or restore KVStore. |
| [ChangeNotification](arkts-arkdata-distributedkvstore-changenotification-i.md) | Defines the content of a data change notification, including inserted data, updated data, deleted data, and device ID. |
| [Constants](arkts-arkdata-distributedkvstore-constants-i.md) | Provides constants of the distributed KV store. |
| [DeviceKVStore](arkts-arkdata-distributedkvstore-devicekvstore-i.md) | Provides APIs for querying data in a device KV store and performing cross-device data sync. This class inherits from **SingleKVStore**. The **SingleKVStore** APIs such as **put** and **putBatch** can be used. Data is distinguished by device in a device KV store. Each device can only write and modify its own data. Data of other devices is read-only and cannot be modified. For example, a device KV store can be used to implement image sharing between devices. The images of other devices can be viewed, but not be modified or deleted. Before calling any method in **DeviceKVStore**, you must use getKVStore to obtain a **DeviceKVStore** object. |
| [Entry](arkts-arkdata-distributedkvstore-entry-i.md) | Provides key-value pairs stored in the distributedKVStore. |
| [KVManager](arkts-arkdata-distributedkvstore-kvmanager-i.md) | Provides an instance to obtain information about a distributed KV store. Before calling any API in **KVManager**, you must use [createKVManager](arkts-arkdata-distributedkvstore-createkvmanager-f.md) to create a **KVManager** instance. |
| [KVManagerConfig](arkts-arkdata-distributedkvstore-kvmanagerconfig-i.md) | Provides the **KVManager** instance configuration, including the bundle name of the invoker and the application context. |
| [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md) | Provides APIs for obtaining the distributed KV store result sets. A maximum of eight result sets can be opened at a time. The **KVStoreResultSet** instance is not refreshed in real time. After using the result set, if the data in the database is changed (by being added, deleted, or modified), you need to query the result set again to obtain the latest data. Before calling any API in **KVStoreResultSet**, you must use ** getKVStore ** to construct a **SingleKVStore** or **DeviceKVStore** instance. |
| [Options](arkts-arkdata-distributedkvstore-options-i.md) | Provides KV store configuration. |
| [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i.md) | Provides APIs for data management in a single KV store, such as adding data, deleting data, and subscribing to data changes or across-device data sync completion events. Before calling any method in **SingleKVStore**, you must use getKVStore to obtain a **SingleKVStore** instance. |
| [Value](arkts-arkdata-distributedkvstore-value-i.md) | Defines the **value** object in a KV store. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DeviceKVStore](arkts-arkdata-distributedkvstore-devicekvstore-i-sys.md) | Provides APIs for querying data in a device KV store and performing cross-device data sync. This class inherits from **SingleKVStore**. The **SingleKVStore** APIs such as **put** and **putBatch** can be used. Data is distinguished by device in a device KV store. Each device can only write and modify its own data. Data of other devices is read-only and cannot be modified. For example, a device KV store can be used to implement image sharing between devices. The images of other devices can be viewed, but not be modified or deleted. Before calling any method in **DeviceKVStore**, you must use getKVStore to obtain a **DeviceKVStore** object. |
| [SingleKVStore](arkts-arkdata-distributedkvstore-singlekvstore-i-sys.md) | Provides APIs for data management in a single KV store, such as adding data, deleting data, and subscribing to data changes or across-device data sync completion events. Before calling any method in **SingleKVStore**, you must use getKVStore to obtain a **SingleKVStore** instance. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [KVStoreType](arkts-arkdata-distributedkvstore-kvstoretype-e.md) | Enumerates the distributed KV store types. |
| [SecurityLevel](arkts-arkdata-distributedkvstore-securitylevel-e.md) | Enumerates the KV store security levels. |
| [SubscribeType](arkts-arkdata-distributedkvstore-subscribetype-e.md) | Enumerates the subscription types. |
| [SyncMode](arkts-arkdata-distributedkvstore-syncmode-e.md) | Enumerates the sync modes. |
| [ValueType](arkts-arkdata-distributedkvstore-valuetype-e.md) | Indicates the `ValueType`. |
