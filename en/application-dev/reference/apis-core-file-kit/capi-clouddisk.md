# CloudDisk
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=129ae9ac672af572fa2f5d2a59eb096f01eee9a0 translatedAt=2026-11-03T03:46:00.557Z pushedAt=2026-11-04T03:11:33.455Z nl=1 -->

## Overview

This module provides the APIs and error codes for cloud disk management, enabling file synchronization management between applications and the cloud disk. An application registers a synchronization path as the root node, and all subdirectories under this path fall within the synchronization scope. This directory is referred to as the synchronization root path.<br>After successful registration, the application can listen for file changes under the synchronization root path, query the historical operation records of files, and set or query the synchronization status of files. It is applicable to scenarios where cloud disk synchronization needs to be integrated into an application, file synchronization status needs to be tracked, or cloud file changes need to be managed.

**Since**: 21
## Files

| Name| Description|
| -- | -- |
| [cloud_disk_error_code.h](capi-cloud-disk-error-code-h.md) | Provides error code definitions for the cloud disk management module, used to identify exceptions during cloud disk management API calls and help developers locate and handle issues such as permission verification failure, invalid parameters, path conflicts, and IPC connection failure. |
| [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md) | Defines the interfaces of the cloud disk management module, providing capabilities for registering, activating, listening to, and querying cloud disk sync root paths. It supports listening for file changes, setting and querying file sync status, and provides capabilities for creating, hydrating, dehydrating placeholder files, and registering callbacks. It is suitable for scenarios where cloud disk file sync, change listening, and on-demand download need to be implemented within an application. |
