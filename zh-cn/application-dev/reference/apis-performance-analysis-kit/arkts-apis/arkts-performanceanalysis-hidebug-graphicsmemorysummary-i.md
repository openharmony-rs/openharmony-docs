# GraphicsMemorySummary

描述应用显存数据，包括gl和graph部分。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-interface GraphicsMemorySummary--><!--Device-hidebug-interface GraphicsMemorySummary-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## gl

```TypeScript
gl: int
```

gl显存大小，RenderService渲染进程加载所需资源占用的内存，例如图片、纹理等，以KB为单位。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GraphicsMemorySummary-gl: int--><!--Device-GraphicsMemorySummary-gl: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## graph

```TypeScript
graph: int
```

graph显存大小，进程统计的DMA内存占用，包括直接通过接口申请的DMA buffer和通过allocator_host申请的DMA buffer，以KB为单位。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GraphicsMemorySummary-graph: int--><!--Device-GraphicsMemorySummary-graph: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

