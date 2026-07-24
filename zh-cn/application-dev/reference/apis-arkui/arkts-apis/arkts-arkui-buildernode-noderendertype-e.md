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
> > Badge、Blank、  
> > Button、CanvasGradient、  
> > CanvasPattern、  
> > CanvasRenderingContext2D、  
> > Canvas、  
> > CheckboxGroup、  
> > Checkbox、Circle、  
> > ColumnSplit、Column、  
> > ContainerSpan、  
> > Counter、DataPanel、  
> > Divider、Ellipse、  
> > Flex、Gauge、  
> > Hyperlink、ImageBitmap、  
> > ImageData、Image、  
> > Line、  
> > LoadingProgress、  
> > Marquee、Matrix2D、  
> > OffscreenCanvasRenderingContext2D、  
> > OffscreenCanvas、Path2D、  
> > Path、PatternLock、  
> > Polygon、Polyline、  
> > Progress、QRCode、  
> > Radio、Rating、  
> > Rect、  
> > RelativeContainer、  
> > RowSplit、Row、  
> > Shape、Slider、  
> > Span、Stack、  
> > TextArea、TextClock  
> > 、TextInput、  
> > TextTimer、Text、  
> > Toggle、Video（不含全屏播放能力）、  
> > Web、XComponent。  
> >  
> > - 从API version 12开始，新增以下组件支持纹理导出：DatePicker、  
> > ForEach、Grid、  
> > [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> > LazyForEach、List、  
> > Scroll、Swiper、  
> > TimePicker、  
> > [@Component](../../../ui/state-management/arkts-create-custom-components.md#component)修饰的自定义组件、  
> > NodeContainer以及  
> > NodeContainer下挂载的[FrameNode](arkts-arkui-framenode-c.md)和  
> > [RenderNode](arkts-arkui-rendernode-c.md)。  
> >  
> > - 使用方式可参考[同层渲染绘制](../../../web/web-same-layer.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1--><!--Device-NodeRenderType-RENDER_TYPE_TEXTURE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

