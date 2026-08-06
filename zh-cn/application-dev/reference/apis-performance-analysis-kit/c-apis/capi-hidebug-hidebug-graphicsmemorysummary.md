# HiDebug_GraphicsMemorySummary

```c
typedef struct HiDebug_GraphicsMemorySummary {...} HiDebug_GraphicsMemorySummary
```

## 概述

Defines a struct for the application graphics memory usage details.

**起始版本：** 21

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t gl | GL memory size (memory occupied by RenderService for loading required resources, such as images and textures),in KB. |
| uint32_t graph | Graph memory size (DMA memory usage of the process), in KB, including the DMA buffers obtained directly throughthe API and those obtained through **allocator_host**. |


