# CommonArcButtonOptions

ArcButton的默认样式或自定义样式参数。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcButton, ArcButtonOptions, ArcButtonProgressConfig, ArcButtonPosition, ArcButtonStyleMode, ArcButtonStatus } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弧形按钮背景模糊能力。默认值：BlurStyle.NONE。

**类型：** BlurStyle

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

弧形按钮背景颜色。ArcButtonStyleMode需要设置为CUSTOM。默认值：Color.Black。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

弧形按钮文本颜色。ArcButtonStyleMode需要设置为CUSTOM。默认值：Color.White。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontFamily

```TypeScript
fontFamily?: string | Resource
```

弧形按钮字体名。

**类型：** string \| Resource

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontMargin

```TypeScript
fontMargin?: LocalizedMargin
```

弧形按钮文本边距，单位：vp。默认值：{start:24vp, top: 10vp,end: 24vp, bottom:16vp }。

**类型：** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

弧形按钮文本大小，单位：fp。默认值：19fp。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

弧形按钮文本样式。默认值：FontStyle.Normal。

**类型：** FontStyle

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## label

```TypeScript
label?: ResourceStr
```

弧形按钮显示文本。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

弧形按钮点击动作触发该回调。

**类型：** Callback&lt;[ClickEvent](../arkts-components/arkts-arkui-clickevent-i.md)&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

弧形按钮手指触摸动作触发该回调。

**类型：** Callback&lt;TouchEvent&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## position

```TypeScript
position?: ArcButtonPosition
```

上下弧形按钮类型属性。默认值：ArcButtonPosition.BOTTOM_EDGE。

**类型：** [ArcButtonPosition](arkts-arkui-arkui-advanced-arcbutton-arcbuttonposition-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## pressedFontColor

```TypeScript
pressedFontColor?: ColorMetrics
```

弧形按钮按下文本颜色。ArcButtonStyleMode需要设置为CUSTOM。默认值：Color.White。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## progressConfig

```TypeScript
progressConfig?: ArcButtonProgressConfig
```

ArcButton进度条参数。不设置该属性时ArcButton组件表现为按钮样式（ [示例1](arkts-arkui-arkui-advanced-arcbutton-arcbutton-s.md)），设置后表现为进度条样式（ [示例2](arkts-arkui-arkui-advanced-arcbutton-arcbutton-s.md)），进度条样式不受 [ArcButtonStyleMode](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)属性设置影响。默认值：[ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md) 的各项子属性均取其默认值。

**类型：** [ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowColor

```TypeScript
shadowColor?: ColorMetrics
```

弧形按钮阴影颜色。默认值：Color.Black。

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowEnabled

```TypeScript
shadowEnabled?: boolean
```

弧形按钮阴影开关。默认值：false值为true时，显示阴影。值为false时，不显示阴影。

**类型：** boolean

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## status

```TypeScript
status?: ArcButtonStatus
```

弧形按钮状态。默认值：ArcButtonStatus.NORMAL。

**类型：** [ArcButtonStatus](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstatus-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## styleMode

```TypeScript
styleMode?: ArcButtonStyleMode
```

弧形按钮样式模式。该样式不支持与[ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md)同时使用。默认值：ArcButtonStyleMode.EMPHASIZED_LIGHT。

**类型：** [ArcButtonStyleMode](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle
