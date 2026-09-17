# CloudDisk_DisplayNameInfo

```c
typedef struct CloudDisk_DisplayNameInfo {...} CloudDisk_DisplayNameInfo
```

## Overview

A struct that encapsulates the display name of the sync root path.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t displayNameResId | Static resource ID corresponding to the display name of the application's sync root path.<br>**Since**: 21 |
| char *customAlias |  |
| size_t customAliasLength | Length of the custom alias. Value range: [0, 255].<br>**Since**: 21 |


