# OH_CloudDisk_FetchData
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=59e1d2830ff9882daf27e6188f02c78dfe2439b8 translatedAt=2026-11-23T02:47:23.221Z pushedAt=2026-11-24T12:07:41.275Z nl=1 -->

```c
typedef struct OH_CloudDisk_FetchData {...} OH_CloudDisk_FetchData
```

## Overview

Result of fetching cloud file data.

**Since:** 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint64_t offset | Starting offset of this data in the file, in bytes.<br>**Since:** 26.0.1 |
| uint64_t size | Length of the data downloaded this time, in bytes.<br>**Since:** 26.0.1 |
| uint64_t totalSize | Total size of the cloud file, in bytes. It is determined when [OH_CloudDisk_Execute()](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_execute) is first called to return the data, and must remain consistent in subsequent returns.<br>**Since:** 26.0.1 |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) data | File data buffer.<br>**Since:** 26.0.1 |
| bool isComplete | Whether this is the last block of data. true indicates that the current data block is the last block of file hydration; false indicates that more data remains to be transferred.<br>**Since:** 26.0.1 |
