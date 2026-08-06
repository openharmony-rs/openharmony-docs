# ArcButtonOptions

定义ArcButton的默认样式或自定义样式参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ArcButtonOptions--><!--Device-unnamed-export declare class ArcButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(options: CommonArcButtonOptions)
```

弧形按钮的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-constructor(options: CommonArcButtonOptions)--><!--Device-ArcButtonOptions-constructor(options: CommonArcButtonOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 定义ArcButton组件的文本、背景色、阴影等参数。 |

## backgroundBlurStyle

```TypeScript
public backgroundBlurStyle: BlurStyle
```

弧形按钮背景模糊能力。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：BlurStyle.NONE

**类型：** BlurStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public backgroundBlurStyle: BlurStyle--><!--Device-ArcButtonOptions-public backgroundBlurStyle: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## backgroundColor

```TypeScript
public backgroundColor: ColorMetrics
```

弧形按钮背景颜色。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ArcButtonStyleMode需要设置为CUSTOM。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：Color.Black

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public backgroundColor: ColorMetrics--><!--Device-ArcButtonOptions-public backgroundColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontColor

```TypeScript
public fontColor: ColorMetrics
```

弧形按钮文本颜色。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ArcButtonStyleMode需要设置为CUSTOM。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：Color.White

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public fontColor: ColorMetrics--><!--Device-ArcButtonOptions-public fontColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontFamily

```TypeScript
public fontFamily: string | Resource
```

弧形按钮字体名。

**类型：** string \| Resource

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public fontFamily: string | Resource--><!--Device-ArcButtonOptions-public fontFamily: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontMargin

```TypeScript
public fontMargin: LocalizedMargin
```

弧形按钮文本边距。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：{start:24vp, top: 10vp,end: 24vp, bottom:16vp }

**类型：** LocalizedMargin

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public fontMargin: LocalizedMargin--><!--Device-ArcButtonOptions-public fontMargin: LocalizedMargin-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontSize

```TypeScript
public fontSize: LengthMetrics
```

弧形按钮文本大小。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：19fp

**类型：** LengthMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public fontSize: LengthMetrics--><!--Device-ArcButtonOptions-public fontSize: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## fontStyle

```TypeScript
public fontStyle: FontStyle
```

弧形按钮文本样式。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：FontStyle.Normal

**类型：** FontStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public fontStyle: FontStyle--><!--Device-ArcButtonOptions-public fontStyle: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## label

```TypeScript
public label: ResourceStr
```

弧形按钮显示文本。

**类型：** ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public label: ResourceStr--><!--Device-ArcButtonOptions-public label: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onClick

```TypeScript
public onClick?: Callback<ClickEvent>
```

弧形按钮点击动作触发该回调。

**类型：** Callback&lt;ClickEvent&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public onClick?: Callback<ClickEvent>--><!--Device-ArcButtonOptions-public onClick?: Callback<ClickEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
public onTouch?: Callback<TouchEvent>
```

弧形按钮手指触摸动作触发该回调。

**类型：** Callback&lt;TouchEvent&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public onTouch?: Callback<TouchEvent>--><!--Device-ArcButtonOptions-public onTouch?: Callback<TouchEvent>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## position

```TypeScript
public position: ArcButtonPosition
```

上下弧形按钮类型属性。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：ArcButtonPosition.BOTTOM\_EDGE。

**类型：** ArcButtonPosition

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public position: ArcButtonPosition--><!--Device-ArcButtonOptions-public position: ArcButtonPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## pressedFontColor

```TypeScript
public pressedFontColor: ColorMetrics
```

弧形按钮按下文本颜色。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ArcButtonStyleMode需要设置为CUSTOM。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：Color.White

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public pressedFontColor: ColorMetrics--><!--Device-ArcButtonOptions-public pressedFontColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## progressConfig

```TypeScript
public progressConfig?: ArcButtonProgressConfig
```

ArcButton进度条参数。不设置该属性时ArcButton组件表现为按钮样式（ \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_），设置后表现为进度条样式（ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_），进度条样式不受 [ArcButtonStyleMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_属性设置影响。 默认值：[ArcButtonProgressConfig]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_ 的各项子属性均取其默认值。

**类型：** ArcButtonProgressConfig

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonOptions-public progressConfig?: ArcButtonProgressConfig--><!--Device-ArcButtonOptions-public progressConfig?: ArcButtonProgressConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowColor

```TypeScript
public shadowColor: ColorMetrics
```

弧形按钮阴影颜色。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：Color.Black

**类型：** ColorMetrics

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public shadowColor: ColorMetrics--><!--Device-ArcButtonOptions-public shadowColor: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## shadowEnabled

```TypeScript
public shadowEnabled: boolean
```

弧形按钮阴影开关。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：false\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_值为true时，显示阴影。值为false时，不显示阴影。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public shadowEnabled: boolean--><!--Device-ArcButtonOptions-public shadowEnabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## status

```TypeScript
public status: ArcButtonStatus
```

弧形按钮状态。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_默认值：ArcButtonStatus.NORMAL

**类型：** ArcButtonStatus

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public status: ArcButtonStatus--><!--Device-ArcButtonOptions-public status: ArcButtonStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## styleMode

```TypeScript
public styleMode: ArcButtonStyleMode
```

弧形按钮样式模式。该样式不支持与\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_样式同时使用。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值：ArcButtonStyleMode.EMPHASIZED\_LIGHT

**类型：** ArcButtonStyleMode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArcButtonOptions-public styleMode: ArcButtonStyleMode--><!--Device-ArcButtonOptions-public styleMode: ArcButtonStyleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

