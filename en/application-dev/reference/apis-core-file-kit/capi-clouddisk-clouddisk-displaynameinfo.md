# CloudDisk_DisplayNameInfo
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8f945fc466618eb449a6fc25874599465b1fce70 translatedAt=2026-11-03T03:40:52.275Z pushedAt=2026-11-04T03:11:33.420Z nl=1 -->

```c
typedef struct CloudDisk_DisplayNameInfo {...} CloudDisk_DisplayNameInfo
```

## Overview

Defines the display name information of a synchronization root path, which is used to configure the display name of the synchronization root path in the UI. Developers can set the display name through a static resource ID or a custom alias, making it easier for users to identify and manage the synchronization root path.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t displayNameResId | Static resource ID corresponding to the display name of the application's sync root path.|
| char *customAlias | Custom alias. It cannot contain the following characters: \\\/\*\?\<\>\|\:\", and cannot use ".", "..", or pure spaces as the complete name. |
| size_t customAliasLength | Length of the custom alias. Value range: [0, 255]. If the value is out of range, the API returns a parameter error. |


