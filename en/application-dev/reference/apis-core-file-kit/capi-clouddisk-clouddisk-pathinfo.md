# CloudDisk_PathInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

```c
typedef struct CloudDisk_PathInfo {...} CloudDisk_PathInfo
```

## Overview

A struct that encapsulates the file path information.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *value | Pointer to the file path, which ends with '\0'.|
| size_t length | Length of the file path, excluding the '\0' character at the end.|
