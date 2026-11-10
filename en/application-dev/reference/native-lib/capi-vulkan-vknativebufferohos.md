# VkNativeBufferOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=68d36fe6a470724ea3793d2df73c0f7910331ef9 translatedAt=2026-11-06T12:13:06.471Z pushedAt=2026-11-09T11:49:00.743Z nl=1 -->

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