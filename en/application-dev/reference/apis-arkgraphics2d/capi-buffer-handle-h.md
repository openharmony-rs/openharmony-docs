# buffer_handle.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=c9742d4d4a757fbb6f0510281af0e732af135c64 translatedAt=2026-08-24T08:19:56.308Z pushedAt=2026-08-25T06:55:24.829Z -->

## Overview

This file declares the **BufferHandle** struct used by the **NativeWindow** module.

**File to include**: <native_window/buffer_handle.h>

**Library**: libnative_window.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Related module**: [NativeWindow](capi-nativewindow.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [BufferHandle](capi-nativewindow-bufferhandle.md) | BufferHandle | Describes the buffer handle, which is used to transfer and obtain buffer information. The handle contains the file descriptor, size, format, usage, virtual address, shared memory key, physical address, and custom data of the buffer.|