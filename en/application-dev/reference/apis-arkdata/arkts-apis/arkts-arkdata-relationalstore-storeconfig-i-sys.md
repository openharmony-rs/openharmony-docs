# StoreConfig (System API)

```TypeScript
interface StoreConfig
```

Defines the RDB store configuration.

**Since:** 9

<!--Device-relationalStore-interface StoreConfig--><!--Device-relationalStore-interface StoreConfig-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## autoCleanDeviceDirtyData

```TypeScript
autoCleanDeviceDirtyData?: boolean
```

Specifies whether to clean up dirty data that is synchronized to the local but deleted on the remote device. <br>Default value:true.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-StoreConfig-autoCleanDeviceDirtyData?: boolean--><!--Device-StoreConfig-autoCleanDeviceDirtyData?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## dumpStackOnFileDel

```TypeScript
dumpStackOnFileDel?: boolean
```

Specifies whether to enable dump-stack on file deletion for the RDB store, which is used to locate issues where database files are unexpectedly deleted.

**true**: enable dump-stack on file deletion. After the RDB store is opened, the file system outputs the call stack of the deletion operation when the database files (**db**, **wal**, and **shm**) are directly deleted through file interfaces.

**false** (default): disable dump-stack on file deletion.

This parameter takes effect only for the **db**, **wal**, and **shm** files of both primary and replica databases. Database auxiliary files such as journal and binlog files are not included.

This parameter depends on the dump-stack capability of the device file system. If the file system does not support this capability, this parameter does not take effect and opening the RDB store is not affected.

This parameter is not persisted to the metadata database and needs to be configured each time the RDB store is opened. Normal operations such as deleting, restoring, and rebuilding the RDB store, as well as primary/replica switchover and attach/detach mode switching, do not trigger the call stack output.

Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-StoreConfig-dumpStackOnFileDel?: boolean--><!--Device-StoreConfig-dumpStackOnFileDel?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## haMode

```TypeScript
haMode?: HAMode
```

Enumerates the high availability modes of the RDB store.

**Type:** [HAMode](arkts-arkdata-relationalstore-hamode-e-sys.md)

**Since:** 12

<!--Device-StoreConfig-haMode?: HAMode--><!--Device-StoreConfig-haMode?: HAMode-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## isSearchable

```TypeScript
isSearchable?: boolean
```

Specifies whether data can be searched.

**Type:** boolean

**Since:** 11

<!--Device-StoreConfig-isSearchable?: boolean--><!--Device-StoreConfig-isSearchable?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.
