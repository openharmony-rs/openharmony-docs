# NodeRenderType

```TypeScript
export declare enum NodeRenderType
```

Enumerates the node rendering types.

> **NOTE:** 
> 
> - Currently, the **RENDER_TYPE_TEXTURE** type takes effect only for the [XComponentNode](arkts-arkui-xcomponentnode-c.md) and the [BuilderNode](arkts-arkui-buildernode-c.md) holding a component tree whose root node is a custom component.
> 
> - The following custom components currently support texture export as root nodes in [BuilderNode](arkts-arkui-buildernode-c.md) scenarios: [Badge](../arkts-components/arkts-arkui-badge-comp.md#badge),[Blank](../arkts-components/arkts-arkui-blank-comp-attribute.md#blankattribute), [Button](../arkts-components/arkts-arkui-button-comp.md#button),[CanvasGradient](../arkts-components/arkts-arkui-canvas-comp.md#canvas),[CanvasPattern](../arkts-components/arkts-arkui-canvas-comp.md#canvas),[CanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas),[Canvas](../arkts-components/arkts-arkui-canvas-comp.md#canvas), [CheckboxGroup](../arkts-components/arkts-arkui-checkboxgroup-comp.md#checkboxgroup),[Checkbox](../arkts-components/arkts-arkui-checkbox-comp.md#checkbox), [Circle](../arkts-components/arkts-arkui-circle-comp.md#circle),[ColumnSplit](../arkts-components/arkts-arkui-columnsplit-comp.md#column_split), [Column](../arkts-components/arkts-arkui-column-comp.md#column),[ContainerSpan](../arkts-components/arkts-arkui-containerspan-comp-attribute.md#containerspanattribute),[Counter](../arkts-components/arkts-arkui-counter-comp-attribute.md#counterattribute), [DataPanel](../arkts-components/arkts-arkui-datapanel-comp.md#data_panel),[Divider](../arkts-components/arkts-arkui-divider-comp-attribute.md#dividerattribute), [Ellipse](../arkts-components/arkts-arkui-ellipse-comp.md#ellipse),[Flex](../arkts-components/arkts-arkui-flex-comp.md#flex), [Gauge](../arkts-components/arkts-arkui-gauge-comp.md#gauge),[Hyperlink](../arkts-components/arkts-arkui-hyperlink-comp.md#hyperlink), [ImageBitmap](../arkts-components/arkts-arkui-canvas-comp.md#canvas),[ImageData](../arkts-components/arkts-arkui-canvas-comp.md#canvas), [Image](../arkts-components/arkts-arkui-image-comp.md#image),[Line](../arkts-components/arkts-arkui-line-comp.md#line),[LoadingProgress](../arkts-components/arkts-arkui-loadingprogress-comp.md#loading_progress),[Marquee](../arkts-components/arkts-arkui-marquee-comp.md#marquee), [Matrix2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas),[OffscreenCanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas),[OffscreenCanvas](../arkts-components/arkts-arkui-canvas-comp.md#canvas), [Path2D](../arkts-components/arkts-arkui-canvas-comp.md#canvas),[Path](../arkts-components/arkts-arkui-path-comp.md#path), [PatternLock](../arkts-components/arkts-arkui-patternlock-comp.md#pattern_lock),[Polygon](../arkts-components/arkts-arkui-polygon-comp.md#polygon), [Polyline](../arkts-components/arkts-arkui-polyline-comp.md#polyline),[Progress](../arkts-components/arkts-arkui-progress-comp.md#progress), [QRCode](../arkts-components/arkts-arkui-qrcode-comp-attribute.md#qrcodeattribute),[Radio](../arkts-components/arkts-arkui-radio-comp.md#radio), [Rating](../arkts-components/arkts-arkui-rating-comp.md#rating),[Rect](../arkts-components/arkts-arkui-rect-comp.md#rect),[RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md#relative_container),[RowSplit](../arkts-components/arkts-arkui-rowsplit-comp-attribute.md#rowsplitattribute), [Row](../arkts-components/arkts-arkui-row-comp.md#row),[Shape](../arkts-components/arkts-arkui-shape-comp.md#shape), [Slider](../arkts-components/arkts-arkui-slider-comp.md#slider),[Span](../arkts-components/arkts-arkui-span-comp.md#span), [Stack](../arkts-components/arkts-arkui-stack-comp.md#stack),[TextArea](../arkts-components/arkts-arkui-textarea-comp.md#text_area), [TextClock](../arkts-components/arkts-arkui-textclock-comp.md#text_clock),[TextInput](../arkts-components/arkts-arkui-textinput-comp.md#text_input), [TextTimer](../arkts-components/arkts-arkui-texttimer-comp.md#text_timer),[Text](../arkts-components/arkts-arkui-text-comp.md#text), [Toggle](../arkts-components/arkts-arkui-toggle-comp.md#toggle),[Video](../arkts-components/arkts-arkui-video-comp.md#video) (excluding full-screen playback),[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp.md#web), [XComponent](../arkts-components/arkts-arkui-xcomponent-comp.md#xcomponent).
> 
> - Since API version 12, the following components also support texture export:[DatePicker](../arkts-components/arkts-arkui-datepicker-comp.md#date_picker), [ForEach](../arkts-components/arkts-arkui-foreach-comp-attribute.md#foreachattribute),[Grid](../arkts-components/arkts-arkui-grid-comp.md#grid),[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md#lazy_for_each), [List](../arkts-components/arkts-arkui-list-comp.md#list),[Scroll](../arkts-components/arkts-arkui-scroll-comp.md#scroll), [Swiper](../arkts-components/arkts-arkui-swiper-comp.md#swiper),[TimePicker](../arkts-components/arkts-arkui-timepicker-comp.md#time_picker), custom components decorated with [@Component](../../../ui/state-management/arkts-create-custom-components.md#component),[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute), and [FrameNode](arkts-arkui-typenode-n.md) and [RenderNode](arkts-arkui-rendernode-c.md) mounted to [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute).
> 
> - For details, see [Rendering and Drawing Video and Button Components at the Same Layer](../../../web/web-same-layer.md).

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_DISPLAY

```TypeScript
RENDER_TYPE_DISPLAY = 0
```

The node is displayed on the screen.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_TEXTURE

```TypeScript
RENDER_TYPE_TEXTURE = 1
```

The node is exported as a texture.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
