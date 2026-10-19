# OH_Drawing_GpuContextOptions

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3b75f30d038321e59d140485862ef0f48205e17e translatedAt=2026-08-24T08:38:21.590Z pushedAt=2026-08-25T07:01:05.815Z -->

```c
typedef struct {...} OH_Drawing_GpuContextOptions
```

## Overview

This struct describes the options about the GPU context.

**Since**: 12

**Deprecated from**: 18

**Related module**: [Drawing](capi-drawing.md)

**Header file**: [drawing_gpu_context.h](capi-drawing-gpu-context-h.md)

## Summary

### Member Variables

| Name                     | Description                                                        |
| ------------------------- | ------------------------------------------------------------ |
| bool allowPathMaskCaching | Whether to allow path mask textures to be cached. The value **true** means to allow the path mask textures to be cached, and **false** means the opposite.|