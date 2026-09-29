# NodeRenderType

```TypeScript
export declare enum NodeRenderType
```

节点渲染类型枚举。

> **说明：** 
> 
> - RENDER_TYPE_TEXTURE类型目前仅在[BuilderNode](arkts-arkui-buildernode-c.md)持有组件树的根节点为自定义组件时以及[XComponentNode](arkts-arkui-xcomponentnode-c.md)中设置生效。
> 
> - 在[BuilderNode](arkts-arkui-buildernode-c.md)的情况下，目前在作为根节点的自定义组件中支持纹理导出的有以下组件：[Badge](../arkts-components/arkts-arkui-badge-comp.md)、[Blank](../arkts-components/arkts-arkui-blank-comp-attribute.md)、[Button](../arkts-components/arkts-arkui-button-comp.md)、[CanvasGradient](../arkts-components/arkts-arkui-canvas-comp.md)、[CanvasPattern](../arkts-components/arkts-arkui-canvas-comp.md)、[CanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp.md)、[Canvas](../arkts-components/arkts-arkui-canvas-comp.md)、[CheckboxGroup](../arkts-components/arkts-arkui-checkboxgroup-comp.md)、[Checkbox](../arkts-components/arkts-arkui-checkbox-comp.md)、[Circle](../arkts-components/arkts-arkui-circle-comp.md)、[ColumnSplit](../arkts-components/arkts-arkui-columnsplit-comp.md)、[Column](../arkts-components/arkts-arkui-column-comp.md)、[ContainerSpan](../arkts-components/arkts-arkui-containerspan-comp-attribute.md)、[Counter](../arkts-components/arkts-arkui-counter-comp-attribute.md)、[DataPanel](../arkts-components/arkts-arkui-datapanel-comp.md)、[Divider](../arkts-components/arkts-arkui-divider-comp-attribute.md)、[Ellipse](../arkts-components/arkts-arkui-ellipse-comp.md)、[Flex](../arkts-components/arkts-arkui-flex-comp.md)、[Gauge](../arkts-components/arkts-arkui-gauge-comp.md)、[Hyperlink](../arkts-components/arkts-arkui-hyperlink-comp.md)、[ImageBitmap](../arkts-components/arkts-arkui-canvas-comp.md)、[ImageData](../arkts-components/arkts-arkui-canvas-comp.md)、[Image](../arkts-components/arkts-arkui-image-comp.md)、[Line](../arkts-components/arkts-arkui-line-comp.md)、[LoadingProgress](../arkts-components/arkts-arkui-loadingprogress-comp.md)、[Marquee](../arkts-components/arkts-arkui-marquee-comp.md)、[Matrix2D](../arkts-components/arkts-arkui-canvas-comp.md)、[OffscreenCanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp.md)、[OffscreenCanvas](../arkts-components/arkts-arkui-canvas-comp.md)、[Path2D](../arkts-components/arkts-arkui-canvas-comp.md)、[Path](../arkts-components/arkts-arkui-path-comp.md)、[PatternLock](../arkts-components/arkts-arkui-patternlock-comp.md)、[Polygon](../arkts-components/arkts-arkui-polygon-comp.md)、[Polyline](../arkts-components/arkts-arkui-polyline-comp.md)、[Progress](../arkts-components/arkts-arkui-progress-comp.md)、[QRCode](../arkts-components/arkts-arkui-qrcode-comp-attribute.md)、[Radio](../arkts-components/arkts-arkui-radio-comp.md)、[Rating](../arkts-components/arkts-arkui-rating-comp.md)、[Rect](../arkts-components/arkts-arkui-rect-comp.md)、[RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md)、[RowSplit](../arkts-components/arkts-arkui-rowsplit-comp-attribute.md)、[Row](../arkts-components/arkts-arkui-row-comp.md)、[Shape](../arkts-components/arkts-arkui-shape-comp.md)、[Slider](../arkts-components/arkts-arkui-slider-comp.md)、[Span](../arkts-components/arkts-arkui-span-comp.md)、[Stack](../arkts-components/arkts-arkui-stack-comp.md)、[TextArea](../arkts-components/arkts-arkui-textarea-comp.md)、[TextClock](../arkts-components/arkts-arkui-textclock-comp.md)、[TextInput](../arkts-components/arkts-arkui-textinput-comp.md)、[TextTimer](../arkts-components/arkts-arkui-texttimer-comp.md)、[Text](../arkts-components/arkts-arkui-text-comp.md)、[Toggle](../arkts-components/arkts-arkui-toggle-comp.md)、[Video](../arkts-components/arkts-arkui-video-comp.md)（不含全屏播放能力）、[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp.md)、[XComponent](../arkts-components/arkts-arkui-xcomponent-comp.md)。
> 
> - 从API version 12开始，新增以下组件支持纹理导出：[DatePicker](../arkts-components/arkts-arkui-datepicker-comp.md)、[ForEach](../arkts-components/arkts-arkui-foreach-comp-attribute.md)、[Grid](../arkts-components/arkts-arkui-grid-comp.md)、[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、[LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md)、[List](../arkts-components/arkts-arkui-list-comp.md)、[Scroll](../arkts-components/arkts-arkui-scroll-comp.md)、[Swiper](../arkts-components/arkts-arkui-swiper-comp.md)、[TimePicker](../arkts-components/arkts-arkui-timepicker-comp.md)、[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)修饰的自定义组件、[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md)以及[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md)下挂载的[FrameNode](arkts-arkui-typenode-n.md)和[RenderNode](arkts-arkui-rendernode-c.md)。
> 
> - 使用方式可参考[同层渲染绘制](../../../web/web-same-layer.md)。

**起始版本：** 11

<!--Device-unnamed-export declare enum NodeRenderType--><!--Device-unnamed-export declare enum NodeRenderType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_DISPLAY

```TypeScript
RENDER_TYPE_DISPLAY = 0
```

表示该节点将被显示到屏幕上。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-NodeRenderType-RENDER_TYPE_DISPLAY = 0--><!--Device-NodeRenderType-RENDER_TYPE_DISPLAY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_TEXTURE

```TypeScript
RENDER_TYPE_TEXTURE = 1
```

表示该节点将被导出为纹理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1--><!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
