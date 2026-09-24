# Canvas属性/事件

```TypeScript
declare class CanvasAttribute extends CommonMethod<CanvasAttribute>
```

除支持[通用属性](arkts-arkui-common-comp-commonmethod-c.md)外，还支持以下属性：

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能，支持[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)动态设置属性方法。

需要搭配[CanvasRenderingContext2D](arkts-arkui-canvas-comp.md#canvas)中的[startImageAnalyzer](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md#startimageanalyzer)和[stopImageAnalyzer](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md#stopimageanalyzer)一起使用。

不能和[overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay)属性同时使用，两者同时设置时overlay中CustomBuilder属性将失效。该特性依赖设备能力，可通过[ImageAnalyzerController.getImageAnalyzerSupportTypes](../arkts-apis/arkts-arkui-imageanalyzercontroller-c.md#getimageanalyzersupporttypes)接口查询设备支持的分析类型。

除支持[通用事件](arkts-arkui-common-comp-commonmethod-c.md)外，还支持如下事件：

**继承/实现关系：** CanvasAttribute extends CommonMethod<CanvasAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能，支持[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)动态设置属性方法。

需要搭配[CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md)中的StartImageAnalyzer和StopImageAnalyzer一起使用。

不能和[overlay](arkts-arkui-common-comp-commonmethod-c.md#overlay)属性同时使用，两者同时设置时overlay中CustomBuilder属性将失效。该特性依赖设备能力。

> **说明：** 
> 
> 从API version 20开始，该接口支持在
> [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 组件支持AI分析，需要组件内容支持主体识别、文字识别或对象查找。<br>设置为true时，组件可进行AI分析，设置为false时，组件不可进行AI分析。<br>异常值null和undefined按默认值处理。<br>默认值：false |

## onReady

```TypeScript
onReady(event: VoidCallback)
```

Canvas组件初始化完成或者发生大小变化时的事件回调，支持[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)动态设置属性方法。

当该事件被触发时画布被清空，该事件之后Canvas组件宽高确定且可获取，可使用Canvas相关API进行绘制。当Canvas组件仅发生位置变化时，只触发[onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange)事件，不触发onReady事件。[onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange)事件在onReady事件后触发。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | Canvas组件初始化完成或者发生大小变化时的回调事件。 |

<a id="onready-1"></a>

## onReady

```TypeScript
onReady(event: Callback<DrawingRenderingContext | undefined> | undefined)
```

Canvas组件初始化完成或者发生大小变化时的事件回调，支持[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)动态设置属性方法。

当该事件被触发时画布被清空，该事件之后Canvas组件宽高确定且可获取，可使用Canvas相关API进行绘制。当Canvas组件仅发生位置变化时，只触发[onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange)事件，不触发onReady事件。[onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange)事件在onReady事件后触发。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;[DrawingRenderingContext](arkts-arkui-canvas-comp-drawingrenderingcontext-c.md) &#124; undefined&gt; &#124; undefined | 是 | Canvas组件初始化完成或者发生大小变化时的回调事件。<br>关于Callback&lt;DrawingRenderingContext &#124;undefined&gt;类型的入参：<br>1. 只有使用[CanvasParams](arkts-arkui-canvas-comp-canvasparams-i.md)创建的Canvas组件在该回调中返回DrawingRenderingContext对象，否则返回undefined。<br>2. 该回调返回的DrawingRenderingContext对象不允许作为参数创建Canvas组件，否则会导致应用崩溃。 |
