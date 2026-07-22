# ArcButtonOptions

定义ArcButton的默认样式或自定义样式参数。

**起始版本：** 18

<!--Device-unnamed-export declare class ArcButtonOptions--><!--Device-unnamed-export declare class ArcButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcButtonPosition, ArcButton, ArcButtonStatus, ArcButtonStyleMode, ArcButtonOptions, ArcButtonProgressConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: CommonArcButtonOptions)
```

弧形按钮的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-constructor(options: CommonArcButtonOptions)--><!--Device-ArcButtonOptions-constructor(options: CommonArcButtonOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CommonArcButtonOptions](arkts-arkui-arkui-advanced-arcbutton-commonarcbuttonoptions-i.md) | 是 | 定义ArcButton组件的文本、背景色、阴影等参数。 |

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle: BlurStyle
```

弧形按钮背景模糊能力。

默认值：BlurStyle.NONE。

**类型：** BlurStyle

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-backgroundBlurStyle: BlurStyle--><!--Device-ArcButtonOptions-backgroundBlurStyle: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## backgroundColor

```TypeScript
backgroundColor: ColorMetrics
```

弧形按钮背景颜色。

ArcButtonStyleMode需要设置为CUSTOM。

默认值：Color.Black。

**类型：** ColorMetrics

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-backgroundColor: ColorMetrics--><!--Device-ArcButtonOptions-backgroundColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontColor

```TypeScript
fontColor: ColorMetrics
```

弧形按钮文本颜色。

ArcButtonStyleMode需要设置为CUSTOM。

默认值：Color.White。

**类型：** ColorMetrics

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-fontColor: ColorMetrics--><!--Device-ArcButtonOptions-fontColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontFamily

```TypeScript
fontFamily: string | Resource
```

弧形按钮字体名。

**类型：** string \| Resource

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-fontFamily: string | Resource--><!--Device-ArcButtonOptions-fontFamily: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontMargin

```TypeScript
fontMargin: LocalizedMargin
```

弧形按钮文本边距。

默认值：{start:24vp, top: 10vp,end: 24vp, bottom:16vp }。

**类型：** LocalizedMargin

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-fontMargin: LocalizedMargin--><!--Device-ArcButtonOptions-fontMargin: LocalizedMargin-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontSize

```TypeScript
fontSize: LengthMetrics
```

弧形按钮文本大小。

默认值：19fp。

**类型：** LengthMetrics

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-fontSize: LengthMetrics--><!--Device-ArcButtonOptions-fontSize: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontStyle

```TypeScript
fontStyle: FontStyle
```

弧形按钮文本样式。

默认值：FontStyle.Normal。

**类型：** FontStyle

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-fontStyle: FontStyle--><!--Device-ArcButtonOptions-fontStyle: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## label

```TypeScript
label: ResourceStr
```

弧形按钮显示文本。

**类型：** ResourceStr

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-label: ResourceStr--><!--Device-ArcButtonOptions-label: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

弧形按钮点击动作触发该回调。

**类型：** Callback&lt;ClickEvent&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-onClick?: Callback<ClickEvent>--><!--Device-ArcButtonOptions-onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

弧形按钮手指触摸动作触发该回调。

**类型：** Callback&lt;TouchEvent&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-onTouch?: Callback<TouchEvent>--><!--Device-ArcButtonOptions-onTouch?: Callback<TouchEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## position

```TypeScript
position: ArcButtonPosition
```

上下弧形按钮类型属性。

默认值：ArcButtonPosition.BOTTOM_EDGE。

**类型：** ArcButtonPosition

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-position: ArcButtonPosition--><!--Device-ArcButtonOptions-position: ArcButtonPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## pressedFontColor

```TypeScript
pressedFontColor: ColorMetrics
```

弧形按钮按下文本颜色。

ArcButtonStyleMode需要设置为CUSTOM。

默认值：Color.White。

**类型：** ColorMetrics

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-pressedFontColor: ColorMetrics--><!--Device-ArcButtonOptions-pressedFontColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## progressConfig

```TypeScript
progressConfig?: ArcButtonProgressConfig
```

ArcButton进度条参数。不设置该属性时ArcButton组件表现为按钮样式（[示例1](../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ArcButton.md#示例1-设置弧形按钮)），设置后表现为进度条样式（[示例2](../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ArcButton.md#示例2-设置设备进度条按钮)），进度条样式不受[ArcButtonStyleMode](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)属性设置影响。

默认值：[ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md) 的各项子属性均取其默认值。

**类型：** ArcButtonProgressConfig

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-progressConfig?: ArcButtonProgressConfig--><!--Device-ArcButtonOptions-progressConfig?: ArcButtonProgressConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowColor

```TypeScript
shadowColor: ColorMetrics
```

弧形按钮阴影颜色。

默认值：Color.Black。

**类型：** ColorMetrics

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-shadowColor: ColorMetrics--><!--Device-ArcButtonOptions-shadowColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowEnabled

```TypeScript
shadowEnabled: boolean
```

弧形按钮阴影开关。

默认值：false

值为true时，显示阴影。值为false时，不显示阴影。

**类型：** boolean

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-shadowEnabled: boolean--><!--Device-ArcButtonOptions-shadowEnabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## status

```TypeScript
status: ArcButtonStatus
```

弧形按钮状态。

默认值：ArcButtonStatus.NORMAL。

**类型：** ArcButtonStatus

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-status: ArcButtonStatus--><!--Device-ArcButtonOptions-status: ArcButtonStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## styleMode

```TypeScript
styleMode: ArcButtonStyleMode
```

弧形按钮样式模式。该样式不支持与[ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md)样式同时使用。

默认值：ArcButtonStyleMode.EMPHASIZED_LIGHT。

**类型：** ArcButtonStyleMode

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButtonOptions-styleMode: ArcButtonStyleMode--><!--Device-ArcButtonOptions-styleMode: ArcButtonStyleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

