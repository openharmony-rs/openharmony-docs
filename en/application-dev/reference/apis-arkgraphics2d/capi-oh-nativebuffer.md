# OH_NativeBuffer

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=c9742d4d4a757fbb6f0510281af0e732af135c64 translatedAt=2026-08-24T09:19:03.887Z pushedAt=2026-08-25T07:22:14.846Z -->

## Overview

This module provides the capabilities of **NativeBuffer**. Using the functions provided by this module, you can apply for, use, and release the shared memory, and query its properties.

**Since**: 9

## Files

| Name                                      | Description                                                        |
| ------------------------------------------ | ------------------------------------------------------------ |
| [buffer_common.h](capi-buffer-common-h.md) | Declares the common types used in the NativeBuffer module.<br>Since API version 12, certain type definitions have been relocated from **native_buffer.h** to this header file for a more cohesive presentation. These types were available prior to API version 12 and can be used seamlessly across all versions.<br>File to include: <native_buffer/buffer_common.h>|
| [native_buffer.h](capi-native-buffer-h.md) | This file declares the functions for obtaining and using **NativeBuffer**.<br>File to include: <native_buffer/native_buffer.h>|