# CloudDisk_DisplayNameInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct CloudDisk_DisplayNameInfo {...} CloudDisk_DisplayNameInfo
```

## Overview

A struct that encapsulates the display name of the sync root path.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t displayNameResId | Static resource ID corresponding to the display name of the application's sync root path.|
| char *customAlias | Pointer to the custom alias, which cannot contain the following characters: \\\/\*\?\<\>\|\:\". Additionally, the full name cannot be composed solely of spaces, a single dot (.), or two consecutive dots (..).| |
| size_t customAliasLength | Length of the custom alias. Value range: [0, 255].|
