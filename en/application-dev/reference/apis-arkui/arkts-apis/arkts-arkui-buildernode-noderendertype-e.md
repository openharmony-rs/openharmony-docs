# NodeRenderType

Enumerates the node rendering types.

> **NOTE:** 
> 
> - Currently, the **RENDER_TYPE_TEXTURE** type takes effect only for the [XComponentNode](arkts-arkui-xcomponentnode-c.md) and the [BuilderNode](arkts-arkui-buildernode-c.md) holding a component tree whose root node is a custom component.
> 
> - The following custom components currently support texture export as root nodes in [BuilderNode](arkts-arkui-buildernode-c.md) scenarios: Badge,Blank, Button,CanvasGradient,CanvasPattern,CanvasRenderingContext2D,Canvas, CheckboxGroup,Checkbox, Circle,ColumnSplit, Column,ContainerSpan,Counter, DataPanel,Divider, Ellipse,Flex, Gauge,Hyperlink, ImageBitmap,ImageData, Image,Line,LoadingProgress,Marquee, Matrix2D,OffscreenCanvasRenderingContext2D,OffscreenCanvas, Path2D,Path, PatternLock,Polygon, Polyline,Progress, QRCode,Radio, Rating,Rect,RelativeContainer,RowSplit, Row,Shape, Slider,Span, Stack,TextArea, TextClock,TextInput, TextTimer,Text, Toggle,Video (excluding full-screen playback),Web, XComponent.
> 
> - Since API version 12, the following components also support texture export:DatePicker, ForEach,Grid,[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),LazyForEach, List,Scroll, Swiper,TimePicker, custom components decorated with [@Component](../../../ui/state-management/arkts-create-custom-components.md#component),NodeContainer, and FrameNode and [RenderNode](arkts-arkui-rendernode-c.md) mounted to NodeContainer.
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
