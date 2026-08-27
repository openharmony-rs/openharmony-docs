# RenderConfiguration

渲染配置接口。@interface RenderConfiguration

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowResolution

```TypeScript
shadowResolution?: Vec2
```

表示全局阴影贴图分辨率，单位为像素（px）。默认值为undefined，表示阴影贴图分辨率设置为1024 * 1024。 输入的值需要大于0才能正确生效。如果输入值为浮点数则自动截取整数部分；如果输入值小于或等于0则无视该输入，维持原有配置。

**类型：** [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md)

**默认值：** undefined

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## softShadowConfig

```TypeScript
softShadowConfig?: SoftShadowConfig
```

软阴影配置参数，用于控制阴影渲染的算法类型及其具体配置。 当值为undefined或不设置该参数时，使用默认的硬阴影算法（无阴影柔化效果）。 当设置为有效的SoftShadowConfig对象（如PCFConfig）时，启用对应的软阴影算法。

**类型：** [SoftShadowConfig](arkts-arkgraphics3d-scene-softshadowconfig-c.md)

**默认值：** undefined

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D
