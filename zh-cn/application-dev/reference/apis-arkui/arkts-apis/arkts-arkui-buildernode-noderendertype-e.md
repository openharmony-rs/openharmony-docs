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
> > [Badge](../../apis-arkui/arkts-components/arkts-arkui-badge-i)、[Blank](../../apis-arkui/arkts-components/arkts-arkui-blank-i)、  
> > [Button](../../apis-arkui/arkts-components/arkts-arkui-button-i)、[CanvasGradient](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [CanvasPattern](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [CanvasRenderingContext2D](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [Canvas](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [CheckboxGroup](../../apis-arkui/arkts-components/arkts-arkui-checkboxgroup-i)、  
> > [Checkbox](../../apis-arkui/arkts-components/arkts-arkui-checkbox-i)、[Circle](../../apis-arkui/arkts-components/arkts-arkui-circle-i)、  
> > [ColumnSplit](../../apis-arkui/arkts-components/arkts-arkui-column_split-i)、[Column](../../apis-arkui/arkts-components/arkts-arkui-column-i)、  
> > [ContainerSpan](../../apis-arkui/arkts-components/arkts-arkui-container_span-i)、  
> > [Counter](../../apis-arkui/arkts-components/arkts-arkui-counter-i)、[DataPanel](../../apis-arkui/arkts-components/arkts-arkui-data_panel-i)、  
> > [Divider](../../apis-arkui/arkts-components/arkts-arkui-divider-i)、[Ellipse](../../apis-arkui/arkts-components/arkts-arkui-ellipse-i)、  
> > [Flex](../../apis-arkui/arkts-components/arkts-arkui-flex-i)、[Gauge](../../apis-arkui/arkts-components/arkts-arkui-gauge-i)、  
> > [Hyperlink](../../apis-arkui/arkts-components/arkts-arkui-hyperlink-i)、[ImageBitmap](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [ImageData](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、[Image](../../apis-arkui/arkts-components/arkts-arkui-image-i)、  
> > [Line](../../apis-arkui/arkts-components/arkts-arkui-line-i)、  
> > [LoadingProgress](../../apis-arkui/arkts-components/arkts-arkui-loading_progress-i)、  
> > [Marquee](../../apis-arkui/arkts-components/arkts-arkui-marquee-i)、[Matrix2D](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [OffscreenCanvasRenderingContext2D](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [OffscreenCanvas](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、[Path2D](../../apis-arkui/arkts-components/arkts-arkui-canvas-i)、  
> > [Path](../../apis-arkui/arkts-components/arkts-arkui-path-i)、[PatternLock](../../apis-arkui/arkts-components/arkts-arkui-pattern_lock-i)、  
> > [Polygon](../../apis-arkui/arkts-components/arkts-arkui-polygon-i)、[Polyline](../../apis-arkui/arkts-components/arkts-arkui-polyline-i)、  
> > [Progress](../../apis-arkui/arkts-components/arkts-arkui-progress-i)、[QRCode](../../apis-arkui/arkts-components/arkts-arkui-qrcode-i)、  
> > [Radio](../../apis-arkui/arkts-components/arkts-arkui-radio-i)、[Rating](../../apis-arkui/arkts-components/arkts-arkui-rating-i)、  
> > [Rect](../../apis-arkui/arkts-components/arkts-arkui-rect-i)、  
> > [RelativeContainer](../../apis-arkui/arkts-components/arkts-arkui-relative_container-i)、  
> > [RowSplit](../../apis-arkui/arkts-components/arkts-arkui-row_split-i)、[Row](../../apis-arkui/arkts-components/arkts-arkui-row-i)、  
> > [Shape](../../apis-arkui/arkts-components/arkts-arkui-shape-i)、[Slider](../../apis-arkui/arkts-components/arkts-arkui-slider-i)、  
> > [Span](../../apis-arkui/arkts-components/arkts-arkui-span-i)、[Stack](../../apis-arkui/arkts-components/arkts-arkui-stack-i)、  
> > [TextArea](../../apis-arkui/arkts-components/arkts-arkui-text_area-i)、[TextClock](../../apis-arkui/arkts-components/arkts-arkui-text_clock-i)  
> > 、[TextInput](../../apis-arkui/arkts-components/arkts-arkui-text_input-i)、  
> > [TextTimer](../../apis-arkui/arkts-components/arkts-arkui-text_timer-i)、[Text](../../apis-arkui/arkts-components/arkts-arkui-text-i)、  
> > [Toggle](../../apis-arkui/arkts-components/arkts-arkui-toggle-i)、[Video](../../apis-arkui/arkts-components/arkts-arkui-video-i)（不含全屏播放能力）、  
> > [Web](../../apis-arkui/arkts-components/arkts-arkui-web-i)、[XComponent](../../apis-arkui/arkts-components/arkts-arkui-xcomponent-i)。  
> >  
> > - 从API version 12开始，新增以下组件支持纹理导出：[DatePicker](../../apis-arkui/arkts-components/arkts-arkui-date_picker-i)、  
> > [ForEach](../../apis-arkui/arkts-components/arkts-arkui-for_each-i)、[Grid](../../apis-arkui/arkts-components/arkts-arkui-grid-i)、  
> > [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> > [LazyForEach](../../apis-arkui/arkts-components/arkts-arkui-lazy_for_each-i)、[List](../../apis-arkui/arkts-components/arkts-arkui-list-i)、  
> > [Scroll](../../apis-arkui/arkts-components/arkts-arkui-scroll-i)、[Swiper](../../apis-arkui/arkts-components/arkts-arkui-swiper-i)、  
> > [TimePicker](../../apis-arkui/arkts-components/arkts-arkui-time_picker-i)、  
> > [@Component](../../../ui/state-management/arkts-create-custom-components.md#component)修饰的自定义组件、  
> > [NodeContainer](../../apis-arkui/arkts-components/arkts-arkui-node_container-i)以及  
> > [NodeContainer](../../apis-arkui/arkts-components/arkts-arkui-node_container-i)下挂载的[FrameNode](arkts-arkui-framenode-c.md)和  
> > [RenderNode](arkts-arkui-rendernode-c.md)。  
> >  
> > - 使用方式可参考[同层渲染绘制](../../../web/web-same-layer.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1--><!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

