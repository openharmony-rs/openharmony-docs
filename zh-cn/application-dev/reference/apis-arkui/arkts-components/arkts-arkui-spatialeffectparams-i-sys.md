# SpatialEffectParams（系统接口）

空间效果选项。用于为组件设置空间效果参数。

> **说明：** 
> 
> - 空间效果仅作用于[DepthComponent](./ts-basic-components-depthcomponent-sys.md)的子组件，且仅当DepthComponent相关参数设置正确才能生效。
> 
> - 空间效果不支持[Web](../../../web/web-component-overview.md)、[XComponent](./ts-basic-components-xcomponent.md)、[RichEditor](./ts-basic-components-richeditor.md)、[RichText](./ts-basic-components-richtext.md)、[Video](./ts-media-components-video.md)、[Component3D](./ts-basic-components-component3d.md)、[EmbeddedComponent](./ts-container-embedded-component.md)组件。
> 
> - 本模块为系统接口。

@interface SpatialEffectParams

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## occlusionWeight

```TypeScript
occlusionWeight?: number
```

空间效果的遮挡权重。<br>取值范围:[0, 1]。默认值:0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: SpatialPosition | number
```

由角点或深度值定义的空间位置。

**类型：** [SpatialPosition](arkts-arkui-spatialposition-i-sys.md) &#124; number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
