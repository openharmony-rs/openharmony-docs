# NodeRenderType

```TypeScript
export declare enum NodeRenderType
```

节点渲染类型枚举。

> **说明：** 
> 
> - RENDER_TYPE_TEXTURE类型目前仅在[BuilderNode](arkts-arkui-buildernode-c.md)持有组件树的根节点为自定义组件时以及[XComponentNode](arkts-arkui-xcomponentnode-c.md)中设置生效。
> 
> - 在[BuilderNode](arkts-arkui-buildernode-c.md)的情况下，目前在作为根节点的自定义组件中支持纹理导出的有以下组件：[Badge](../arkts-components/arkts-arkui-badge-comp.md#badge)、[Blank](../arkts-components/arkts-arkui-blank-comp-attribute.md)、[Button](../arkts-components/arkts-arkui-button-comp.md#button)、[CanvasGradient](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[CanvasPattern](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[CanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[Canvas](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[CheckboxGroup](../arkts-components/arkts-arkui-checkboxgroup-comp.md#checkboxgroup)、[Checkbox](../arkts-components/arkts-arkui-checkbox-comp.md#checkbox)、[Circle](../arkts-components/arkts-arkui-circle-comp.md#circle)、[ColumnSplit](../arkts-components/arkts-arkui-columnsplit-comp.md#column_split)、[Column](../arkts-components/arkts-arkui-column-comp.md#column)、[ContainerSpan](../arkts-components/arkts-arkui-containerspan-comp-attribute.md)、[Counter](../arkts-components/arkts-arkui-counter-comp-attribute.md)、[DataPanel](../arkts-components/arkts-arkui-datapanel-comp.md#data_panel)、[Divider](../arkts-components/arkts-arkui-divider-comp-attribute.md)、[Ellipse](../arkts-components/arkts-arkui-ellipse-comp.md#ellipse)、[Flex](../arkts-components/arkts-arkui-flex-comp.md#flex)、[Gauge](../arkts-components/arkts-arkui-gauge-comp.md#gauge)、[Hyperlink](../arkts-components/arkts-arkui-hyperlink-comp.md#hyperlink)、[ImageBitmap](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[ImageData](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[Image](../arkts-components/arkts-arkui-image-comp.md#image)、[Line](../arkts-components/arkts-arkui-line-comp.md#line)、[LoadingProgress](../arkts-components/arkts-arkui-loadingprogress-comp.md#loading_progress)、[Marquee](../arkts-components/arkts-arkui-marquee-comp.md#marquee)、[Matrix2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[OffscreenCanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[OffscreenCanvas](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[Path2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas)、[Path](../arkts-components/arkts-arkui-path-comp.md#path)、[PatternLock](../arkts-components/arkts-arkui-patternlock-comp.md#pattern_lock)、[Polygon](../arkts-components/arkts-arkui-polygon-comp.md#polygon)、[Polyline](../arkts-components/arkts-arkui-polyline-comp.md#polyline)、[Progress](../arkts-components/arkts-arkui-progress-comp.md#progress)、[QRCode](../arkts-components/arkts-arkui-qrcode-comp-attribute.md)、[Radio](../arkts-components/arkts-arkui-radio-comp.md#radio)、[Rating](../arkts-components/arkts-arkui-rating-comp.md#rating)、[Rect](../arkts-components/arkts-arkui-rect-comp.md#rect)、[RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container)、[RowSplit](../arkts-components/arkts-arkui-rowsplit-comp-attribute.md)、[Row](../arkts-components/arkts-arkui-row-comp.md#row)、[Shape](../arkts-components/arkts-arkui-shape-comp.md#shape)、[Slider](../arkts-components/arkts-arkui-slider-comp.md#slider)、[Span](../arkts-components/arkts-arkui-span-comp.md#span)、[Stack](../arkts-components/arkts-arkui-stack-comp.md#stack)、[TextArea](../arkts-components/arkts-arkui-textarea-comp.md#text_area)、[TextClock](../arkts-components/arkts-arkui-textclock-comp.md#text_clock)、[TextInput](../arkts-components/arkts-arkui-textinput-comp.md#text_input)、[TextTimer](../arkts-components/arkts-arkui-texttimer-comp.md#text_timer)、[Text](../arkts-components/arkts-arkui-text-comp.md#text)、[Toggle](../arkts-components/arkts-arkui-toggle-comp.md#toggle)、[Video](../arkts-components/arkts-arkui-video-comp.md#video)（不含全屏播放能力）、[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp.md#webweb控制器)、[XComponent](../arkts-components/arkts-arkui-xcomponent-comp.md#xcomponent)。
> 
> - 从API version 12开始，新增以下组件支持纹理导出：[DatePicker](../arkts-components/arkts-arkui-datepicker-comp.md#date_picker)、[ForEach](../arkts-components/arkts-arkui-foreach-comp-attribute.md)、[Grid](../arkts-components/arkts-arkui-grid-comp.md#grid)、[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、[LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md#lazy_for_each)、[List](../arkts-components/arkts-arkui-list-comp.md#list)、[Scroll](../arkts-components/arkts-arkui-scroll-comp.md#scroll)、[Swiper](../arkts-components/arkts-arkui-swiper-comp.md#swiper)、[TimePicker](../arkts-components/arkts-arkui-timepicker-comp.md#time_picker)、[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)修饰的自定义组件、[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md)以及[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md)下挂载的[FrameNode](arkts-arkui-typenode-n.md)和[RenderNode](arkts-arkui-rendernode-c.md)。
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
