# @ohos.data.storage(Lightweight Data Storage)

Lightweight storage provides applications with data processing capability and allows applications to perform lightweight data storage and query. Data is stored in key-value (KV) pairs. Keys are of the string type, and values can be of the number, string, or Boolean type.

> **NOTE:** 

> - The APIs of this module are no longer maintained since API version 9. You are advised to use [@ohos.data.preferences](arkts-arkdata-data-preferences.md).

**Since:** 6

**Deprecated since:** 9

**Substitutes:** preferences

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## Modules to Import

```TypeScript
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [deleteStorage](arkts-arkdata-storage-deletestorage-f.md#deletestorage) | Deletes the singleton **Storage** instance of a file from the memory, and deletes the specified file, its backup file, and damaged files. After the specified files are deleted, the **Storage** instance cannot be used for data operations. Otherwise, data inconsistency will occur. This API uses an asynchronous callback to return the result. |
| [deleteStorage](arkts-arkdata-storage-deletestorage-f.md#deletestorage-1) | Deletes the singleton **Storage** instance of a file from the memory, and deletes the specified file, its backup file, and damaged files. After the specified files are deleted, the **Storage** instance cannot be used for data operations. Otherwise, data inconsistency will occur. This API uses a promise to return the result. |
| [deleteStorageSync](arkts-arkdata-storage-deletestoragesync-f.md) | Deletes the singleton **Storage** instance of a file from the memory, and deletes the specified file, its backup file, and damaged files. After the specified files are deleted, the **Storage** instance cannot be used for data operations. Otherwise, data inconsistency will occur. |
| [getStorage](arkts-arkdata-storage-getstorage-f.md#getstorage) | Reads the specified file and loads its data to the **Storage** instance for data operations. This API uses an asynchronous callback to return the result. |
| [getStorage](arkts-arkdata-storage-getstorage-f.md#getstorage-1) | Reads the specified file and loads its data to the **Storage** instance for data operations. This API uses a promise to return the result. |
| [getStorageSync](arkts-arkdata-storage-getstoragesync-f.md) | Reads the specified file and loads its data to the **Storage** instance for data operations. |
| [removeStorageFromCache](arkts-arkdata-storage-removestoragefromcache-f.md#removestoragefromcache) | Removes the singleton **Storage** instance of a file from the cache. The removed instance cannot be used for data operations. Otherwise, data inconsistency will occur. This API uses an asynchronous callback to return the result. |
| [removeStorageFromCache](arkts-arkdata-storage-removestoragefromcache-f.md#removestoragefromcache-1) | Removes the singleton **Storage** instance of a file from the cache. The removed instance cannot be used for data operations. Otherwise, data inconsistency will occur. This API uses a promise to return the result. |
| [removeStorageFromCacheSync](arkts-arkdata-storage-removestoragefromcachesync-f.md) | Removes the singleton **Storage** instance of a file from the cache. The removed instance cannot be used for data operations. Otherwise, data inconsistency will occur. |

### Interfaces

| Name | Description |
| --- | --- |
| [Storage](arkts-arkdata-storage-storage-i.md) | Provides APIs for obtaining and modifying storage data. |
| [StorageObserver](arkts-arkdata-storage-storageobserver-i.md) | Define the change data information object. |

### Types

| Name | Description |
| --- | --- |
| [ValueType](arkts-arkdata-storage-valuetype-t.md) | Enumerates the value types. |

### Constants

| Name | Description |
| --- | --- |
| [MAX_KEY_LENGTH](arkts-arkdata-storage-con.md#max_key_length) | Indicates the maximum length of a key (80 characters). |
| [MAX_VALUE_LENGTH](arkts-arkdata-storage-con.md#max_value_length) | Indicates the maximum length of a string (8192 characters). |
