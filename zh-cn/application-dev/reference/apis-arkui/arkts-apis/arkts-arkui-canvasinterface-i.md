# CanvasInterface

提供画布组件，用于自定义绘制图形。

> **说明：**
> 
> 该组件从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## [[Call]]

```TypeScript
(context?: CanvasRenderingContext2D | DrawingRenderingContext): CanvasAttribute
```

创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。使用本接口创建的Canvas组件在组件不可见时将不响应绘制指令。不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、设置visibility属性为隐藏等，不包 括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) \| [DrawingRenderingContext](arkts-arkui-drawingrenderingcontext-c.md) | 否 | CanvasRenderingContext2D: 不支持多个Canvas共用一个 CanvasRenderingContext2D对象，具体描述见[CanvasRenderingContext2D](arkts-arkui-canvas-con.md)对象。DrawingRenderingContext: 不支持多个 Canvas共用一个DrawingRenderingContext对象，具体描述见[DrawingRenderingContext](arkts-arkui-canvas-con.md)对象。 异常值null和undefined按未设置context处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasAttribute](arkts-arkui-canvasattribute-c.md) |  |

## [[Call]]

```TypeScript
(context: CanvasRenderingContext2D | DrawingRenderingContext, imageAIOptions: ImageAIOptions): CanvasAttribute
```

创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。支持设置CanvasRenderingContext2D对象或DrawingRenderingContext对象，支持设置AI分析选 项。使用本接口创建的Canvas组件在组件不可见时将不响应绘制指令。不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、设置visibility属性为隐藏等，不包 括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) \| [DrawingRenderingContext](arkts-arkui-drawingrenderingcontext-c.md) | 是 | CanvasRenderingContext2D: 不支持多个Canvas共用一个 CanvasRenderingContext2D对象，具体描述见[CanvasRenderingContext2D](arkts-arkui-canvas-con.md)对象。DrawingRenderingContext: 不支持多个 Canvas共用一个DrawingRenderingContext对象，具体描述见[DrawingRenderingContext](arkts-arkui-canvas-con.md)对象。 异常值null和undefined按未设置context处理。 |
| imageAIOptions | [ImageAIOptions](arkts-arkui-imageaioptions-i.md) | 是 | 给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。 异常值null和undefined按[ImageAIOptions](arkts-arkui-imageaioptions-i.md)的默认值处理，默认取值为{ type: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT], aiController: new ImageAnalyzerController() }，即开启主体识别和文字识别 功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasAttribute](arkts-arkui-canvasattribute-c.md) |  |

## [[Call]]

```TypeScript
(params: CanvasParams): CanvasAttribute
```

使用CanvasParams创建不缓存指令的Canvas组件。创建Canvas组件时，最大面积不超过10000px*10000px，超过最大面积则无法正常创建。Canvas组件未设置固定尺寸时，默认扩展至其最大可用尺寸。

> **说明：**
> 
> - 使用本接口创建的Canvas组件将在
> [onReady&lt;sup&gt;23+&lt;/sup&gt;](arkts-arkui-canvasattribute-c.md#onready)
> 回调的入参中返回一个[DrawingRenderingContext&lt;sup&gt;12+&lt;/sup&gt;](arkts-arkui-canvas-con.md)对象，可用于在该Canvas组件上进行绘制。
> 
> - 使用本接口创建的Canvas组件在组件不可见时将不响应绘制指令。
> 
> - 不可见场景主要包括组件所在的页面进入后台、组件滑到窗口外、设置visibility属性为隐藏等，不包括组件被其他组件或是其他窗口遮挡导致不可见的场景。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [CanvasParams](arkts-arkui-canvasparams-i.md) | 是 | Canvas组件的构造参数，用于创建不缓存指令的Canvas组件。配置参数详见[CanvasParams](arkts-arkui-canvasparams-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasAttribute](arkts-arkui-canvasattribute-c.md) |  |
