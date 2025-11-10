# CloudDisk
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

## Overview

This module provides APIs and error codes for cloud disk management. When an application registers a sync path as the root node, all subdirectories within this path are included in the sync scope, and this parent directory is referred to as the "sync root path".<br> Under this sync root path, you can listen for file changes, obtain the file change history, and set or query the file sync state.

**Since**: 21
## Files

| Name| Description|
| -- | -- |
| [cloud_disk_error_code.h](capi-cloud-disk-error-code-h.md) | Defines the error codes for the cloud disk management module.|
| [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md) | Defines the APIs for the cloud disk management module.|
