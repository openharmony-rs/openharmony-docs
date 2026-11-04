# VkNativeBufferOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8daf9ee30888df1ab65f2de2ee84e32c5a71eb27 translatedAt=2026-11-04T02:54:56.325Z pushedAt=2026-11-04T03:24:28.631Z nl=1 -->

```c
typedef struct VkNativeBufferOHOS {...} VkNativeBufferOHOS
```

## Overview

Describes the parameters of the native display buffer.

**Since**: 10

**Deprecated since:** 23

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| VkStructureType sType | Struct type.|
| const void*        pNext | Pointer to the next-level struct; **pNext** is either null or a pointer to the next-level struct.|
| struct [OHBufferHandle*](capi-vulkan-ohbufferhandle.md)      handle | Device memory handle.|