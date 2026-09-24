# NodeRenderType

```TypeScript
export declare enum NodeRenderType
```

节点渲染类型枚举。

> **说明：** 
> 
> - RENDER_TYPE_TEXTURE类型目前仅在[BuilderNode](arkts-arkui-buildernode-c.md)持有组件树的根节点为自定义组件时以及[XComponentNode](arkts-arkui-xcomponentnode-c.md)中设置生效。
> 
> - 在[BuilderNode](arkts-arkui-buildernode-c.md)的情况下，目前在作为根节点的自定义组件中支持纹理导出的有以下组件：Badge、[Blank](../arkts-components/arkts-arkui-blank-comp-attribute.md)、Button、CanvasGradient、CanvasPattern、CanvasRenderingContext2D、Canvas、CheckboxGroup、Checkbox、Circle、ColumnSplit、Column、[ContainerSpan](../arkts-components/arkts-arkui-containerspan-comp-attribute.md)、[Counter](../arkts-components/arkts-arkui-counter-comp-attribute.md)、DataPanel、[Divider](../arkts-components/arkts-arkui-divider-comp-attribute.md)、Ellipse、Flex、Gauge、Hyperlink、ImageBitmap、ImageData、Image、Line、LoadingProgress、Marquee、Matrix2D、OffscreenCanvasRenderingContext2D、OffscreenCanvas、Path2D、Path、PatternLock、Polygon、Polyline、Progress、[QRCode](../arkts-components/arkts-arkui-qrcode-comp-attribute.md)、Radio、Rating、Rect、RelativeContainer、[RowSplit](../arkts-components/arkts-arkui-rowsplit-comp-attribute.md)、Row、Shape、Slider、Span、Stack、TextArea、TextClock、TextInput、TextTimer、Text、Toggle、Video（不含全屏播放能力）、Web、XComponent。
> 
> - 从API version 12开始，新增以下组件支持纹理导出：DatePicker、[ForEach](../arkts-components/arkts-arkui-foreach-comp-attribute.md)、Grid、[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、LazyForEach、List、Scroll、Swiper、TimePicker、[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)修饰的自定义组件、[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md)以及[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md)下挂载的[FrameNode](arkts-arkui-typenode-n.md)和[RenderNode](arkts-arkui-rendernode-c.md)。
> 
> - 使用方式可参考[同层渲染绘制](../../../web/web-same-layer.md)。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_DISPLAY

```TypeScript
RENDER_TYPE_DISPLAY = 0
```

表示该节点将被显示到屏幕上。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_TEXTURE

```TypeScript
RENDER_TYPE_TEXTURE = 1
```

表示该节点将被导出为纹理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
