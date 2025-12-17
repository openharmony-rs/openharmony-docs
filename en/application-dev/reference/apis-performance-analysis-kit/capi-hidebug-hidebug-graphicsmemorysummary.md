# HiDebug_GraphicsMemorySummary

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

```c
typedef struct HiDebug_GraphicsMemorySummary {...} HiDebug_GraphicsMemorySummary
```

## Overview

Defines a struct for the application graphics memory usage details.

**Since**: 21

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t gl | GL memory size (memory occupied by RenderService for loading required resources, such as images and textures), in KB.|
| uint32_t graph | Graph memory size (DMA memory usage of the process), in KB, including the DMA buffers obtained directly through the API and those obtained through **allocator_host**.|
