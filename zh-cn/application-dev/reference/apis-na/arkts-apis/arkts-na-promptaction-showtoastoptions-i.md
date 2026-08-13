# ShowToastOptions

Toast的选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-promptAction-export interface ShowToastOptions--><!--Device-promptAction-export interface ShowToastOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: Alignment
```

对齐方式。 默认值：undefined，当未设置alignment且存在导航条或软键盘时，Toast会自动根据导航条或软键盘位置进行调整，可参考bottom的说明。 **说明：** 不同alignment下，Toast位置对齐效果，如下图所示。  Toast的文本显示默认自左向右，不支持其他对齐方式。

**类型：** Alignment

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-alignment?: Alignment--><!--Device-ShowToastOptions-alignment?: Alignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Toast的背板模糊材质。 默认值：BlurStyle.COMPONENT_ULTRA_THICK **说明：** 设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。

**类型：** BlurStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-backgroundBlurStyle?: BlurStyle--><!--Device-ShowToastOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Toast的背板颜色。 默认值：Color.Transparent **说明：** backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-backgroundColor?: ResourceColor--><!--Device-ShowToastOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom?: string | double
```

设置Toast底部边框距离导航条的高度，软键盘拉起时，如果bottom值过小，Toast要被软键盘遮挡时，会自动避让至距离软键盘80vp处。 默认值：80vp **说明：** 当底部没有导航条时，bottom为设置弹窗底部边框距离窗口底部的高度。 设置对齐方式alignment后，bottom不生效。

**类型：** string \| double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-bottom?: string | double--><!--Device-ShowToastOptions-bottom?: string | double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: int
```

设置Toast弹出的持续时间。 默认值：1500ms 取值范围：[1500, 10000] 若小于1500ms则取默认值，若大于10000ms则取上限值10000ms。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-duration?: int--><!--Device-ShowToastOptions-duration?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态，值为true时，响应悬停态。 默认值：false，默认不响应。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-enableHoverMode?: boolean--><!--Device-ShowToastOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

响应悬停态时，弹窗的显示区域。 默认值：HoverModeAreaType.BOTTOM_SCREEN，默认显示在下半屏。

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-hoverModeArea?: HoverModeAreaType--><!--Device-ShowToastOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string | Resource
```

显示的文本信息。 **说明：** 默认字体为'Harmony Sans'，不支持设置其他字体。

**类型：** string \| Resource

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-message: string | Resource--><!--Device-ShowToastOptions-message: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

在对齐方式上的偏移。 默认值：{ dx: 0, dy: 0 }，默认没有偏移。 **说明：** 仅支持设置px类型的数值。如需设置其他类型的数值，应将其他类型转换为px类型后传入。例如，若需设置vp，应将其转换为px后传入。

**类型：** Offset

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-offset?: Offset--><!--Device-ShowToastOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Toast的背板阴影。 默认值：ShadowStyle.OUTER_DEFAULT_MD

**类型：** ShadowOptions \| ShadowStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-ShowToastOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showMode

```TypeScript
showMode?: ToastShowMode
```

设置Toast层级。 默认值：ToastShowMode.DEFAULT，默认显示在应用内。

**类型：** [ToastShowMode](arkts-na-promptaction-toastshowmode-e.md)

**默认值：** ToastShowMode.DEFAULT

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-showMode?: ToastShowMode--><!--Device-ShowToastOptions-showMode?: ToastShowMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for toast. Different materials have different effects, which can influence backgroundColor, border, shadow, and other visual attributes of toast.

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-systemMaterial?: SystemUiMaterial--><!--Device-ShowToastOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textColor

```TypeScript
textColor?: ResourceColor
```

Toast的文本颜色。 默认值：Color.Black

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShowToastOptions-textColor?: ResourceColor--><!--Device-ShowToastOptions-textColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

