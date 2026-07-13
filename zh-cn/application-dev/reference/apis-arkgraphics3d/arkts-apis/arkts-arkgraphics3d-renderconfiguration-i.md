# RenderConfiguration

全局渲染配置控制

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowResolution

```TypeScript
shadowResolution?: Vec2
```

单个阴影贴图缓冲区的分辨率, undefined by default,
which means we use (1024, 1024) as the resolution of a single shadow map.
需要提供相同的x和y值以获得正确的阴影效果，单位为像素.

**类型：** Vec2

**默认值：** { 1024, 1024 }

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## softShadowConfig

```TypeScript
softShadowConfig?: SoftShadowConfig
```

软阴影配置参数，控制算法类型及其配置

**类型：** SoftShadowConfig

**默认值：** { undefined }, 表示使用默认硬阴影算法

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

