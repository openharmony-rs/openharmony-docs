# NodeRenderType

节点渲染类型枚举。

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeRenderType-RENDER_TYPE_DISPLAY = 0--><!--Device-NodeRenderType-RENDER_TYPE_DISPLAY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RENDER_TYPE_TEXTURE

```TypeScript
RENDER_TYPE_TEXTURE = 1
```

表示该节点将被导出为纹理。

> **说明**  
> > **说明：**  
> >  
> > - RENDER_TYPE_TEXTURE类型目前仅在[BuilderNode](arkts-arkui-buildernode-c.md)持有组件树的根节点为自定义组件时以及  
> > [XComponentNode](arkts-arkui-xcomponentnode-c.md)中设置生效。  
> >  
> > - 在[BuilderNode](arkts-arkui-buildernode-c.md)的情况下，目前在作为根节点的自定义组件中支持纹理导出的有以下组件：  
> > [Badge](./../@internal/component/ets/badge)、[Blank](./../@internal/component/ets/blank)、  
> > [Button](./../@internal/component/ets/button)、[CanvasGradient](./../@internal/component/ets/canvas)、  
> > [CanvasPattern](./../@internal/component/ets/canvas)、  
> > [CanvasRenderingContext2D](./../@internal/component/ets/canvas)、  
> > [Canvas](./../@internal/component/ets/canvas)、  
> > [CheckboxGroup](./../@internal/component/ets/checkboxgroup)、  
> > [Checkbox](./../@internal/component/ets/checkbox)、[Circle](./../@internal/component/ets/circle)、  
> > [ColumnSplit](./../@internal/component/ets/column_split)、[Column](./../@internal/component/ets/column)、  
> > [ContainerSpan](./../@internal/component/ets/container_span)、  
> > [Counter](./../@internal/component/ets/counter)、[DataPanel](./../@internal/component/ets/data_panel)、  
> > [Divider](./../@internal/component/ets/divider)、[Ellipse](./../@internal/component/ets/ellipse)、  
> > [Flex](./../@internal/component/ets/flex)、[Gauge](./../@internal/component/ets/gauge)、  
> > [Hyperlink](./../@internal/component/ets/hyperlink)、[ImageBitmap](./../@internal/component/ets/canvas)、  
> > [ImageData](./../@internal/component/ets/canvas)、[Image](./../@internal/component/ets/image)、  
> > [Line](./../@internal/component/ets/line)、  
> > [LoadingProgress](./../@internal/component/ets/loading_progress)、  
> > [Marquee](./../@internal/component/ets/marquee)、[Matrix2D](./../@internal/component/ets/canvas)、  
> > [OffscreenCanvasRenderingContext2D](./../@internal/component/ets/canvas)、  
> > [OffscreenCanvas](./../@internal/component/ets/canvas)、[Path2D](./../@internal/component/ets/canvas)、  
> > [Path](./../@internal/component/ets/path)、[PatternLock](./../@internal/component/ets/pattern_lock)、  
> > [Polygon](./../@internal/component/ets/polygon)、[Polyline](./../@internal/component/ets/polyline)、  
> > [Progress](./../@internal/component/ets/progress)、[QRCode](./../@internal/component/ets/qrcode)、  
> > [Radio](./../@internal/component/ets/radio)、[Rating](./../@internal/component/ets/rating)、  
> > [Rect](./../@internal/component/ets/rect)、  
> > [RelativeContainer](./../@internal/component/ets/relative_container)、  
> > [RowSplit](./../@internal/component/ets/row_split)、[Row](./../@internal/component/ets/row)、  
> > [Shape](./../@internal/component/ets/shape)、[Slider](./../@internal/component/ets/slider)、  
> > [Span](./../@internal/component/ets/span)、[Stack](./../@internal/component/ets/stack)、  
> > [TextArea](./../@internal/component/ets/text_area)、[TextClock](./../@internal/component/ets/text_clock)  
> > 、[TextInput](./../@internal/component/ets/text_input)、  
> > [TextTimer](./../@internal/component/ets/text_timer)、[Text](./../@internal/component/ets/text)、  
> > [Toggle](./../@internal/component/ets/toggle)、[Video](./../@internal/component/ets/video)（不含全屏播放能力）、  
> > [Web](./../@internal/component/ets/web)、[XComponent](./../@internal/component/ets/xcomponent)。  
> >  
> > - 从API version 12开始，新增以下组件支持纹理导出：[DatePicker](./../@internal/component/ets/date_picker)、  
> > [ForEach](./../@internal/component/ets/for_each)、[Grid](./../@internal/component/ets/grid)、  
> > [if/else](../../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> > [LazyForEach](./../@internal/component/ets/lazy_for_each)、[List](./../@internal/component/ets/list)、  
> > [Scroll](./../@internal/component/ets/scroll)、[Swiper](./../@internal/component/ets/swiper)、  
> > [TimePicker](./../@internal/component/ets/time_picker)、  
> > [@Component](../../../../ui/state-management/arkts-create-custom-components.md#component)修饰的自定义组件、  
> > [NodeContainer](./../@internal/component/ets/node_container)以及  
> > [NodeContainer](./../@internal/component/ets/node_container)下挂载的[FrameNode](arkts-arkui-framenode-c.md)和  
> > [RenderNode](arkts-arkui-rendernode-c.md)。  
> >  
> > - 使用方式可参考[同层渲染绘制](../../../../web/web-same-layer.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1--><!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

