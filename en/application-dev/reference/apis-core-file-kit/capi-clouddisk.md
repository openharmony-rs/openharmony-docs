# CloudDisk
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=4165f338bbfe7f5ad0b3bd882976a1f16b4d44a0 translatedAt=2026-11-04T03:43:53.224Z pushedAt=2026-11-04T10:12:33.423Z nl=1 -->

## Overview

This module provides APIs and error codes for cloud disk management. When an application registers a sync path as the root node, all subdirectories within this path are included in the sync scope, and this parent directory is referred to as the "sync root path".<br> Under this sync root path, you can listen for file changes, obtain the file change history, and set or query the file sync state.

**Since**: 21
## Files

| Name| Description|
| -- | -- |
| [cloud_disk_error_code.h](capi-cloud-disk-error-code-h.md) | Provides error code definitions for the cloud disk management module, used to identify exceptions during cloud disk management API calls and help developers locate and handle issues such as permission verification failure, invalid parameters, path conflicts, and IPC connection failure. |
| [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md) | Defines the interfaces of the cloud disk management module, providing capabilities for registering, activating, listening to, and querying cloud disk sync root paths. It supports listening for file changes, setting and querying file sync status, and provides capabilities for creating, hydrating, dehydrating placeholder files, and registering callbacks. It is suitable for scenarios where cloud disk file sync, change listening, and on-demand download need to be implemented within an application. |
