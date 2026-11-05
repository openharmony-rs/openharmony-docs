# NodeRenderType

```TypeScript
export declare enum NodeRenderType
```

Enumerates the node rendering types.

> **NOTE:** 
> 
> - Currently, the **RENDER_TYPE_TEXTURE** type takes effect only for the XComponentNode and the BuilderNode holding a component tree whose root node is a custom component.
> 
> - The following custom components currently support texture export as root nodes in BuilderNode scenarios: [Badge](../arkts-components/arkts-arkui-badge-comp.md),[Blank](../arkts-components/arkts-arkui-blank-comp-attribute.md#blankattribute), Button,[CanvasGradient](../arkts-components/arkts-arkui-canvas-comp-canvasgradient-c.md),[CanvasPattern](../arkts-components/arkts-arkui-canvas-comp-canvaspattern-i.md),[CanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md),[Canvas](../arkts-components/arkts-arkui-canvas-comp.md), [CheckboxGroup](../arkts-components/arkts-arkui-checkboxgroup-comp.md),Checkbox, Circle,[ColumnSplit](../arkts-components/arkts-arkui-columnsplit-comp.md), Column,[ContainerSpan](../arkts-components/arkts-arkui-containerspan-comp-attribute.md#containerspanattribute),[Counter](../arkts-components/arkts-arkui-counter-comp-attribute.md#counterattribute), [DataPanel](../arkts-components/arkts-arkui-datapanel-comp.md),[Divider](../arkts-components/arkts-arkui-divider-comp-attribute.md#dividerattribute), [Ellipse](../arkts-components/arkts-arkui-ellipse-comp.md),[Flex](../arkts-components/arkts-arkui-flex-comp.md), [Gauge](../arkts-components/arkts-arkui-gauge-comp.md),[Hyperlink](../arkts-components/arkts-arkui-hyperlink-comp-attribute.md#hyperlinkattribute), [ImageBitmap](../arkts-components/arkts-arkui-canvas-comp-imagebitmap-c.md),[ImageData](../arkts-components/arkts-arkui-canvas-comp-imagedata-c.md), Image,Line,[LoadingProgress](../arkts-components/arkts-arkui-loadingprogress-comp.md),[Marquee](../arkts-components/arkts-arkui-marquee-comp.md), [Matrix2D](arkts-arkui-matrix2d-c.md),[OffscreenCanvasRenderingContext2D](../arkts-components/arkts-arkui-canvas-comp-offscreencanvasrenderingcontext2d-c.md),[OffscreenCanvas](../arkts-components/arkts-arkui-canvas-comp-offscreencanvas-c.md), [Path2D](../arkts-components/arkts-arkui-canvas-comp-path2d-c.md),[Path](../arkts-components/arkts-arkui-path-comp.md), [PatternLock](../arkts-components/arkts-arkui-patternlock-comp.md),[Polygon](../arkts-components/arkts-arkui-polygon-comp.md), [Polyline](../arkts-components/arkts-arkui-polyline-comp.md),[Progress](../arkts-components/arkts-arkui-progress-comp.md), [QRCode](../arkts-components/arkts-arkui-qrcode-comp-attribute.md#qrcodeattribute),[Radio](../arkts-components/arkts-arkui-radio-comp.md), [Rating](../arkts-components/arkts-arkui-rating-comp.md),[Rect](../arkts-components/arkts-arkui-rect-comp.md),[RelativeContainer](../arkts-components/arkts-arkui-relativecontainer-comp.md),[RowSplit](../arkts-components/arkts-arkui-rowsplit-comp-attribute.md#rowsplitattribute), Row,[Shape](../arkts-components/arkts-arkui-shape-comp.md), [Slider](../arkts-components/arkts-arkui-slider-comp.md),[Span](../arkts-components/arkts-arkui-span-comp.md), Stack,[TextArea](../arkts-components/arkts-arkui-textarea-comp.md), [TextClock](../arkts-components/arkts-arkui-textclock-comp.md),[TextInput](../arkts-components/arkts-arkui-textinput-comp.md), [TextTimer](../arkts-components/arkts-arkui-texttimer-comp.md),[Text](../arkts-components/arkts-arkui-text-comp.md), [Toggle](../arkts-components/arkts-arkui-toggle-comp.md),[Video](../arkts-components/arkts-arkui-video-comp.md) (excluding full-screen playback),[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp.md), [XComponent](../arkts-components/arkts-arkui-xcomponent-comp.md).
> 
> - Since API version 12, the following components also support texture export:[DatePicker](../arkts-components/arkts-arkui-datepicker-comp.md), [ForEach](../arkts-components/arkts-arkui-foreach-comp-attribute.md#foreachattribute),[Grid](../arkts-components/arkts-arkui-grid-comp.md),[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md), [List](../arkts-components/arkts-arkui-list-comp.md),Scroll, [Swiper](../arkts-components/arkts-arkui-swiper-comp.md),[TimePicker](../arkts-components/arkts-arkui-timepicker-comp.md), custom components decorated with [@Component](../../../ui/state-management/arkts-create-custom-components.md#component),[NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute), and FrameNode and RenderNode mounted to [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute).
> 
> - For details, see [Rendering and Drawing Video and Button Components at the Same Layer](../../../web/web-same-layer.md).

**Since:** 11

<!--Device-unnamed-export declare enum NodeRenderType--><!--Device-unnamed-export declare enum NodeRenderType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_DISPLAY

```TypeScript
RENDER_TYPE_DISPLAY = 0
```

The node is displayed on the screen.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeRenderType-RENDER_TYPE_DISPLAY = 0--><!--Device-NodeRenderType-RENDER_TYPE_DISPLAY = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_TEXTURE

```TypeScript
RENDER_TYPE_TEXTURE = 1
```

The node is exported as a texture.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1--><!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
