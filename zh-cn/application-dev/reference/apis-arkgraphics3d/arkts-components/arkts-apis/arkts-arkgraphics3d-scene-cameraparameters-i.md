# CameraParameters

相机创建参数配置，用于定义相机创建的额外选项。

@interface CameraParameters

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

## msaa

```TypeScript
msaa?: boolean
```

相机是否使能MSAA，true表示使能MSAA，false表示不使能MSAA。默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 22

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderingPipeline

```TypeScript
renderingPipeline?: RenderingPipelineType
```

选择初始渲染管线类型，默认为轻量级前向渲染管线类型。

**类型：** [RenderingPipelineType](arkts-arkgraphics3d-scenetypes-renderingpipelinetype-e.md)

**默认值：** RenderingPipelineType.FORWARD_LIGHTWEIGHT

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D
