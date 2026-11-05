# Swapfs (System Interface)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T04:00:39.915Z pushedAt=2026-11-04T03:11:33.493Z nl=1 -->

## Overview

The Swapfs module provides error code definitions related to the swap file system, which are used to manage and monitor the swap partition usage of applications.<br> This module supports operations such as creating, mounting, and unmounting swap partitions, and is suitable for scenarios that require optimizing memory management and improving application runtime performance.<br> This module helps developers effectively utilize system swap resources and improve the application experience when memory is insufficient.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

## Files

| Name | Description |
| -- | -- |
| [swapfs_errcode.h (System Interface)](capi-swapfs-errcode-h-sys.md) | Declares the error codes of the Swapfs module, including the definitions of various error states during file system operations. |
| [oh_swapfs.h (System Interface)](capi-oh-swapfs-h-sys.md) | Defines the native APIs of swapfs (swap file system), providing operation interfaces for creating, mounting, and unmounting file system swap space.<br> The Swapfs module is used to manage and monitor the swap partition usage of applications.<br> This module supports operations such as creating, mounting, and unmounting swap space, and is suitable for scenarios that require optimizing memory management and improving application runtime performance.<br> It supports swapping data out to disk and managing it, and swapping it back in when it needs to be retrieved later, thereby enabling flexible memory management and performance improvement.<br> This module helps developers effectively utilize system swap resources and improve the application experience when memory is insufficient. |
