# OH_NativeBuffer_Smpte2086
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1f370dd3425411b659f906071e53860b94f0e2f1 translatedAt=2026-11-04T10:34:43.196Z pushedAt=2026-11-04T10:36:03.380Z nl=1 -->

```c
typedef struct OH_NativeBuffer_Smpte2086 {...} OH_NativeBuffer_Smpte2086
```
## Overview

Represents the SMPTE 2086 static metadata.

**Since**: 12

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

**Header file**: [buffer_common.h](capi-buffer-common-h.md)

## Summary

### Member Variables

| Name                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) displayPrimaryRed | Red primary color.      |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) displayPrimaryGreen | Green primary color.      |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) displayPrimaryBlue | Blue primary color.      |
| [OH_NativeBuffer_ColorXY](capi-oh-nativebuffer-oh-nativebuffer-colorxy.md) whitePoint | White point.        |
| float maxLuminance                                           | Maximum luminance.|
| float minLuminance                                           | Minimum luminance.|

