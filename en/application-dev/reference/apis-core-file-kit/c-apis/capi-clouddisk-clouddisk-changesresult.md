# CloudDisk_ChangesResult

```c
typedef struct CloudDisk_ChangesResult {...} CloudDisk_ChangesResult
```

## Overview

A struct that encapsulates the file change result under the sync root path. It includes the next change sequence number, end flag, and an array of change data items.

<!--Device-struct CloudDisk_ChangesResult {...}--><!--Device-struct CloudDisk_ChangesResult {...}-End-->

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 21

**Related module**: [CloudDisk](capi-core-file-kit-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t nextUsn{0} | Valid start change sequence number that can be queried next time.<br>**Since**: 21<br><!--Device-uint64_t nextUsn{0}--><!--Device-uint64_t nextUsn{0}-End--> |
| bool isEof{false} | Whether the change is the last entry in the sync root path's change history. The value true means it is the last one; the value false means it is not.<br>**Since**: 21<br><!--Device-bool isEof{false}--><!--Device-bool isEof{false}-End--> |
| size_t bufferLength{0} | Number of elements in the change history array.<br>**Since**: 21<br><!--Device-size_t bufferLength{0}--><!--Device-size_t bufferLength{0}-End--> |
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) changeDatas[] | Change history array.<br>**Since**: 21<br><!--Device-CloudDisk_ChangeData changeDatas[]--><!--Device-CloudDisk_ChangeData changeDatas[]-End--> |


