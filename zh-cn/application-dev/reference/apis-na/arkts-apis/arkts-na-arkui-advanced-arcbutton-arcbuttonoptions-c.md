# ArcButtonOptions

定义ArcButton的默认样式或自定义样式参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class ArcButtonOptions--><!--Device-unnamed-export declare class ArcButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(options: CommonArcButtonOptions)
```

弧形按钮的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-constructor(options: CommonArcButtonOptions)--><!--Device-ArcButtonOptions-constructor(options: CommonArcButtonOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CommonArcButtonOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-commonarcbuttonoptions-i.md) | 是 | 定义ArcButton组件的文本、背景色、阴影等参数。 |

## backgroundBlurStyle

```TypeScript
@Trace
  public backgroundBlurStyle: BlurStyle
```

弧形按钮背景模糊能力。&lt;br/&gt;默认值：BlurStyle.NONE

**类型：** BlurStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public backgroundBlurStyle: BlurStyle--><!--Device-ArcButtonOptions-@Trace  public backgroundBlurStyle: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## backgroundColor

```TypeScript
@Trace
  public backgroundColor: ColorMetrics
```

弧形按钮背景颜色。&lt;br/&gt;ArcButtonStyleMode需要设置为CUSTOM。&lt;br/&gt;默认值：Color.Black

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public backgroundColor: ColorMetrics--><!--Device-ArcButtonOptions-@Trace  public backgroundColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontColor

```TypeScript
@Trace
  public fontColor: ColorMetrics
```

弧形按钮文本颜色。&lt;br/&gt;ArcButtonStyleMode需要设置为CUSTOM。&lt;br/&gt;默认值：Color.White

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public fontColor: ColorMetrics--><!--Device-ArcButtonOptions-@Trace  public fontColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontFamily

```TypeScript
@Trace
  public fontFamily: string | Resource
```

弧形按钮字体名。

**类型：** string \| Resource

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public fontFamily: string | Resource--><!--Device-ArcButtonOptions-@Trace  public fontFamily: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontMargin

```TypeScript
@Trace
  public fontMargin: LocalizedMargin
```

弧形按钮文本边距。&lt;br/&gt;默认值：{start:24vp, top: 10vp,end: 24vp, bottom:16vp }

**类型：** LocalizedMargin

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public fontMargin: LocalizedMargin--><!--Device-ArcButtonOptions-@Trace  public fontMargin: LocalizedMargin-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontSize

```TypeScript
@Trace
  public fontSize: LengthMetrics
```

弧形按钮文本大小。&lt;br/&gt;默认值：19fp

**类型：** LengthMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public fontSize: LengthMetrics--><!--Device-ArcButtonOptions-@Trace  public fontSize: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontStyle

```TypeScript
@Trace
  public fontStyle: FontStyle
```

弧形按钮文本样式。&lt;br/&gt;默认值：FontStyle.Normal

**类型：** FontStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public fontStyle: FontStyle--><!--Device-ArcButtonOptions-@Trace  public fontStyle: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## label

```TypeScript
@Trace
  public label: ResourceStr
```

弧形按钮显示文本。

**类型：** ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public label: ResourceStr--><!--Device-ArcButtonOptions-@Trace  public label: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onClick

```TypeScript
@Trace
  public onClick?: Callback<ClickEvent>
```

弧形按钮点击动作触发该回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;ClickEvent&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public onClick?: Callback<ClickEvent>--><!--Device-ArcButtonOptions-@Trace  public onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
@Trace
  public onTouch?: Callback<TouchEvent>
```

弧形按钮手指触摸动作触发该回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;TouchEvent&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public onTouch?: Callback<TouchEvent>--><!--Device-ArcButtonOptions-@Trace  public onTouch?: Callback<TouchEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## position

```TypeScript
@Trace
  public position: ArcButtonPosition
```

上下弧形按钮类型属性。&lt;br/&gt;默认值：ArcButtonPosition.BOTTOM_EDGE。

**类型：** [ArcButtonPosition](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonposition-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public position: ArcButtonPosition--><!--Device-ArcButtonOptions-@Trace  public position: ArcButtonPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## pressedFontColor

```TypeScript
@Trace
  public pressedFontColor: ColorMetrics
```

弧形按钮按下文本颜色。&lt;br/&gt;ArcButtonStyleMode需要设置为CUSTOM。&lt;br/&gt;默认值：Color.White

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public pressedFontColor: ColorMetrics--><!--Device-ArcButtonOptions-@Trace  public pressedFontColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## progressConfig

```TypeScript
@Trace
  public progressConfig?: ArcButtonProgressConfig
```

ArcButton进度条参数。不设置该属性时ArcButton组件表现为按钮样式（ 示例1），设置后表现为进度条样式（ 示例2），进度条样式不受 [ArcButtonStyleMode](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md#ArcButtonStyleMode)属性设置影响。 默认值：[ArcButtonProgressConfig](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md#ArcButtonProgressConfig) 的各项子属性均取其默认值。

**类型：** [ArcButtonProgressConfig](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonOptions-@Trace  public progressConfig?: ArcButtonProgressConfig--><!--Device-ArcButtonOptions-@Trace  public progressConfig?: ArcButtonProgressConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowColor

```TypeScript
@Trace
  public shadowColor: ColorMetrics
```

弧形按钮阴影颜色。&lt;br/&gt;默认值：Color.Black

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public shadowColor: ColorMetrics--><!--Device-ArcButtonOptions-@Trace  public shadowColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowEnabled

```TypeScript
@Trace
  public shadowEnabled: boolean
```

弧形按钮阴影开关。&lt;br/&gt;默认值：false&lt;br/&gt;值为true时，显示阴影。值为false时，不显示阴影。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public shadowEnabled: boolean--><!--Device-ArcButtonOptions-@Trace  public shadowEnabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## status

```TypeScript
@Trace
  public status: ArcButtonStatus
```

弧形按钮状态。&lt;br/&gt;默认值：ArcButtonStatus.NORMAL

**类型：** [ArcButtonStatus](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonstatus-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public status: ArcButtonStatus--><!--Device-ArcButtonOptions-@Trace  public status: ArcButtonStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## styleMode

```TypeScript
@Trace
  public styleMode: ArcButtonStyleMode
```

弧形按钮样式模式。该样式不支持与[ArcButtonProgressConfig](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md#ArcButtonProgressConfig)样式同时使用。&lt;br&gt;默认值：ArcButtonStyleMode.EMPHASIZED_LIGHT

**类型：** [ArcButtonStyleMode](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ArcButtonOptions-@Trace  public styleMode: ArcButtonStyleMode--><!--Device-ArcButtonOptions-@Trace  public styleMode: ArcButtonStyleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

