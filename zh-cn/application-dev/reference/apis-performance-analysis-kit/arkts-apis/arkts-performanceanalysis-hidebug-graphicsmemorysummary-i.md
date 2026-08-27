# GraphicsMemorySummary

描述应用显存数据，包括gl和graph部分。

**起始版本：** 21

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
```

## gl

```TypeScript
gl: number
```

gl显存大小，RenderService渲染进程加载所需资源占用的内存，例如图片、纹理等，以KB为单位。

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## graph

```TypeScript
graph: number
```

graph显存大小，进程统计的DMA内存占用，包括直接通过接口申请的DMA buffer和通过allocator_host申请的DMA buffer，以KB为单位。

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug
