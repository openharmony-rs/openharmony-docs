# CanvasAttribute

除支持通用属性外，还支持以下属性：设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能，支持attributeModifier动态设置属性方法。需要搭配[CanvasRenderingContext2D](arkts-arkui-canvas-con.md)中的 [startImageAnalyzer](arkts-arkui-canvasrenderingcontext2d-c.md#startimageanalyzer)和 [stopImageAnalyzer](arkts-arkui-canvasrenderingcontext2d-c.md#stopimageanalyzer)一起使用。不能和overlay属性同时使用，两者同时设置时overlay中CustomBuilder属性将失效。该特性依赖设备能力，可通过 [ImageAnalyzerController.getImageAnalyzerSupportTypes](arkts-arkui-imageanalyzercontroller-c.md#getimageanalyzersupporttypes)接口查 询设备支持的分析类型。除支持通用事件外，还支持如下事件：

**继承/实现关系：** CanvasAttribute extends CommonMethod<CanvasAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean): CanvasAttribute
```

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能，支持attributeModifier 动态设置属性方法。需要搭配[CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)中的 StartImageAnalyzer和 StopImageAnalyzer 一起使用。不能和overlay属性同时使用， 两者同时设置时overlay中CustomBuilder属性将失效。该特性依赖设备能力。

> **说明：**
> 
> 从API version 20开始，该接口支持在
> attributeModifier
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 组件支持AI分析，需要组件内容支持主体识别、文字识别或对象查找。 设置为true时，组件可进行AI分析，设置为false时，组件不可进行AI分析。 异常值null和undefined按默认值处理。 默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasAttribute](arkts-arkui-canvasattribute-c.md) |  |

## onReady

```TypeScript
onReady(event: VoidCallback): CanvasAttribute
```

Canvas组件初始化完成或者发生大小变化时的事件回调，支持attributeModifier动态设置属性方法。当该事件被触发时画布被清空，该事件之后Canvas组件宽高确定且可获取，可使用Canvas相关API进行绘制。当Canvas组件仅发生位置变化时，只触发 onAreaChange事件，不触发onReady事件。 onAreaChange事件在onReady事件后触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](arkts-arkui-voidcallback-t.md) | 是 | Canvas组件初始化完成或者发生大小变化时的回调事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasAttribute](arkts-arkui-canvasattribute-c.md) |  |

## onReady

```TypeScript
onReady(event: Callback<DrawingRenderingContext | undefined> | undefined): CanvasAttribute
```

Canvas组件初始化完成或者发生大小变化时的事件回调，支持attributeModifier动态设置属性方法。当该事件被触发时画布被清空，该事件之后Canvas组件宽高确定且可获取，可使用Canvas相关API进行绘制。当Canvas组件仅发生位置变化时，只触发 onAreaChange事件，不触发onReady事件。 onAreaChange事件在onReady事件后触发。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;[DrawingRenderingContext](arkts-arkui-drawingrenderingcontext-c.md) \| undefined & gt; \ | undefined | 是 | Canvas组件初始化完成或者发生大小变化时的回调事件。 关于Callback & lt;DrawingRenderingContext \ |undefined&gt;类型的入参：  1. 只有使用[CanvasParams](arkts-arkui-canvasparams-i.md)创建的Canvas组件在该回调中返回DrawingRenderingContext对象，否则返回undefined。  2. 该回调返回的DrawingRenderingContext对象不允许作为参数创建Canvas组件，否则会导致应用崩溃。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasAttribute](arkts-arkui-canvasattribute-c.md) |  |
