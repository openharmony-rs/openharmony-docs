# Canvas属性/事件

除支持[通用属性](../../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)外，还支持以下属性：

除支持[通用事件](../../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md)外，还支持如下事件：

**继承/实现关系：** CanvasAttribute extends [CommonMethod<CanvasAttribute>](CommonMethod<CanvasAttribute>)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)
动态设置属性方法。

需要搭配[CanvasRenderingContext2D](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)中的
[StartImageAnalyzer](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md#startimageanalyzer12)和
[StopImageAnalyzer](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md#stopimageanalyzer12)
一起使用。

不能和[overlay](arkts-arkui-commonmethod-c.md#overlay-1)属性同时使用，
两者同时设置时overlay中CustomBuilder属性将失效。该特性依赖设备能力。

> **说明：**
>
> 从API version 20开始，该接口支持在
> [attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)
> 中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 组件支持AI分析，需要组件内容支持主体识别、文字识别或对象查找。<br>设置为true时，组件可进行AI分析，设置为false时，组件不可进行AI分析。<br>异常值null和undefined按默认值处理。<br/>默认值：false |

## onReady

```TypeScript
onReady(event: VoidCallback)
```

Canvas组件初始化完成或者发生大小变化时的事件回调，支持
[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)
动态设置属性方法。

当该事件被触发时画布被清空，该事件之后Canvas组件宽高确定且可获取，可使用Canvas相关API进行绘制。
当Canvas组件仅发生位置变化时，只触发
[onAreaChange](../../../../reference/apis-arkui/arkui-ts/ts-universal-component-area-change-event.md#onareachange)
事件，不触发onReady事件。
[onAreaChange](../../../../reference/apis-arkui/arkui-ts/ts-universal-component-area-change-event.md#onareachange)
事件在onReady事件后触发。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | VoidCallback | 是 | Canvas组件初始化完成或者发生大小变化时的事件回调事件。 |

## onReady

```TypeScript
onReady(event: Callback<DrawingRenderingContext | undefined> | undefined)
```

Canvas组件初始化完成或者发生大小变化时的事件回调，支持
[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)
动态设置属性方法。

当该事件被触发时画布被清空，该事件之后Canvas组件宽高确定且可获取，可使用Canvas相关API进行绘制。
当Canvas组件仅发生位置变化时，只触发
[onAreaChange](arkts-arkui-commonmethod-c.md#onareachange-1)事件，不触发onReady事件。
[onAreaChange](arkts-arkui-commonmethod-c.md#onareachange-1)事件在onReady事件后触发。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;DrawingRenderingContext \| undefined&gt; \| undefined | 是 | Canvas组件初始化完成或者发生大小变化时的回调事件。<br/>关于Callback&lt;DrawingRenderingContext \| undefined&gt;类型的入参：<br/>1. 只有使用[CanvasParams](arkts-arkui-canvasparams-i.md)创建的Canvas组件在该回调中返回DrawingRenderingContext对象，否则返回undefined。<br/>2. 该回调返回的DrawingRenderingContext对象不允许作为参数创建Canvas组件，否则会导致应用崩溃。 |

