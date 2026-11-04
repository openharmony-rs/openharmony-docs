# CloudDisk_ChangesResult
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8f945fc466618eb449a6fc25874599465b1fce70 translatedAt=2026-11-03T03:40:50.378Z pushedAt=2026-11-04T03:11:33.422Z nl=1 -->

```c
typedef struct CloudDisk_ChangesResult {...} CloudDisk_ChangesResult
```

## Overview

The result of querying file changes in the sync root path. This structure contains the change data of files in the sync root path, including the next queryable update sequence number, the end flag, and the array of change data items. It is applicable to scenarios where file change records in the sync root path are queried incrementally.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t nextUsn{0} | The next valid starting change sequence number that can be queried. Developers can use this value in the next incremental query to continue obtaining subsequent changes. |
| bool isEof{false} | Whether this change is the last batch of modification records recorded in the sync root path. true indicates that it is the last batch of modification records, and false indicates that it is not. |
| size_t bufferLength{0} | Number of elements in the historical change record array, corresponding to the number of elements in the changeDatas array. |
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) changeDatas[] | Historical change record array. The array length is specified by bufferLength. |


