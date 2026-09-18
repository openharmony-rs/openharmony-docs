# GraphicsMemorySummary

Describes the GPU memory data of an application, including the GL and Graph parts.

**Since:** 21

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## gl

```TypeScript
gl: number
```

GL memory size (memory occupied by RenderService for loading required resources, such as images and textures), in KB.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## graph

```TypeScript
graph: number
```

Graph memory size (DMA memory usage of the process), in KB, including the DMA buffers obtained directly through the API and those obtained through **allocator_host**.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
