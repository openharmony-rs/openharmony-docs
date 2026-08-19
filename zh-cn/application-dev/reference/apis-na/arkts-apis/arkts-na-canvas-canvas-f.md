# Canvas

## Canvas

```TypeScript
@ComponentBuilder
export declare function Canvas(
  context?: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions?: ImageAIOptions
): CanvasAttribute
```

创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。 CanvasRenderingContext2D: 不支持多个Canvas共用一个CanvasRenderingContext2D对象。 DrawingRenderingContext: 不支持多个Canvas共用一个DrawingRenderingContext对象。 异常值null和undefined按未设置context处理。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Canvas(  context?: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions?: ImageAIOptions): CanvasAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Canvas(  context?: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions?: ImageAIOptions): CanvasAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-na-canvas-canvasrenderingcontext2d-c.md) \| [DrawingRenderingContext](arkts-na-canvas-drawingrenderingcontext-c.md) | 否 | Canvas组件的绘图上下文。 |
| imageAIOptions | [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md) | 否 | 给组件设置一个AI分析选项， 通过此项可配置分析类型或绑定一个分析控制器。 异常值null和undefined按ImageAIOptions的默认值处理， 默认取值为{ type: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT], aiController: new ImageAnalyzerController() }， 即开启主体识别和文字识别功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CanvasAttribute | The attribute of the Canvas. |


## Canvas

```TypeScript
@ComponentBuilder
export declare function Canvas(
  params: CanvasParams
): CanvasAttribute
```

使用CanvasParams创建不缓存指令的Canvas组件。 创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。 Canvas组件未设置固定尺寸时，默认扩展至其最大可用尺寸。 > **说明：** > > - 使用本接口创建的Canvas组件将在onReady回调的入参中返回一个 > DrawingRenderingContext对象，可用于在该Canvas组件上进行绘制。 > > - 使用这个接口创建的Canvas组件在组件不可见时将不响应绘制指令。 > > - 不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、 > 设置visibility属性为隐藏等，不包括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Canvas(  params: CanvasParams): CanvasAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Canvas(  params: CanvasParams): CanvasAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [CanvasParams](arkts-na-canvas-canvasparams-i.md) | 是 | Canvas组件的构造参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CanvasAttribute | The attribute of the Canvas. |


## Canvas

```TypeScript
@Builder
export declare function Canvas(
    style_: CustomBuilderT<CanvasAttribute>
): CanvasAttribute
```

Defines Canvas Component.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Canvas(    style_: CustomBuilderT<CanvasAttribute>): CanvasAttribute--><!--Device-unnamed-@Builderexport declare function Canvas(    style_: CustomBuilderT<CanvasAttribute>): CanvasAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;CanvasAttribute&gt; | 是 | Canvas attribute instance. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CanvasAttribute |  |

