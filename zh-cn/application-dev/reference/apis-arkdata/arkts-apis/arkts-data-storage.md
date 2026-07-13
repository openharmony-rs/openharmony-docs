# @ohos.data.storage

轻量级存储为应用提供key-value键值型的文件数据处理能力，支持应用对数据进行轻量级存储及查询。
数据存储形式为键值对，键的类型为字符串型，值的存储数据类型包括数字型、字符串型、布尔型。

> **说明**

> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 从API version 9开始，该接口不再维护，推荐使用新接口[@ohos.data.preferences](arkts-data-preferences.md).

**起始版本：** 6

**废弃版本：** 9

**替代接口：** preferences

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [deleteStorage](arkts-arkdata-deletestorage-f.md#deletestorage-1) | 从内存中移除指定文件对应的Storage单实例，并删除指定文件及其备份文件、损坏文件。删除指定文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题，使用callback方式返回结果，此方法为异步方法。 |
| [deleteStorage](arkts-arkdata-deletestorage-f.md#deletestorage-2) | 从内存中移除指定文件对应的Storage单实例，并删除指定文件及其备份文件、损坏文件。删除指定文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题，使用Promise方式返回结果，此方法为异步方法。 |
| [deleteStorageSync](arkts-arkdata-deletestoragesync-f.md#deletestoragesync-1) | 从内存中移除指定文件对应的Storage单实例，并删除指定文件及其备份文件、损坏文件。删除指定文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。 |
| [getStorage](arkts-arkdata-getstorage-f.md#getstorage-1) | 读取指定文件，将数据加载到Storage实例，用于数据操作，使用callback方式返回结果，此方法为异步方法。 |
| [getStorage](arkts-arkdata-getstorage-f.md#getstorage-2) | 读取指定文件，将数据加载到Storage实例，用于数据操作，使用Promise方式返回结果，此方法为异步方法。 |
| [getStorageSync](arkts-arkdata-getstoragesync-f.md#getstoragesync-1) | 读取指定文件，将数据加载到Storage实例，用于数据操作。 |
| [removeStorageFromCache](arkts-arkdata-removestoragefromcache-f.md#removestoragefromcache-1) | 从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。使用callback方式返回结果，此方法为异步方法。 |
| [removeStorageFromCache](arkts-arkdata-removestoragefromcache-f.md#removestoragefromcache-2) | 从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。使用Promise方式返回结果，此方法为异步方法。 |
| [removeStorageFromCacheSync](arkts-arkdata-removestoragefromcachesync-f.md#removestoragefromcachesync-1) | 从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Storage](arkts-arkdata-storage-i.md) | 提供获取和修改存储数据的接口。下列接口都需先使用[data_storage.getStorage](arkts-arkdata-getstorage-f.md#getstorage-1)或[data_storage.getStorageSync](arkts-arkdata-getstoragesync-f.md#getstoragesync-1)获取到Storage实例，再通过此实例调用对应接口。 |
| [StorageObserver](arkts-arkdata-storageobserver-i.md) |  |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ValueType](arkts-arkdata-valuetype-t.md) | 用于表示允许的数据字段类型。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [MAX_KEY_LENGTH](arkts-arkdata-storage-con.md#max_key_length) | key的最大长度限制为80字节。 |
| [MAX_VALUE_LENGTH](arkts-arkdata-storage-con.md#max_value_length) | value的最大长度限制为16MB。 |

