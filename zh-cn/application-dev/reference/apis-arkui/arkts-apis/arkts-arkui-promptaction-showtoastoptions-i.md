# ShowToastOptions

Toast的选项。

**起始版本：** 9

<!--Device-promptAction-interface ShowToastOptions--><!--Device-promptAction-interface ShowToastOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## alignment

```TypeScript
alignment?: Alignment
```

对齐方式。<br/>默认值：undefined，当未设置alignment且存在导航条或软键盘时，Toast会自动根据导航条或软键盘位置进行调整，可参考bottom的说明。<br>**说明：**<br/>不同alignment下，Toast位置对齐效果，如下图所示。<br/>![zh-cn_image_0001](figures/toast_alignment.PNG)<br/>Toast的文本显示默认自左向右，不支持其他对齐方式。

**类型：** Alignment

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-alignment?: Alignment--><!--Device-ShowToastOptions-alignment?: Alignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Toast的背板模糊材质。<br/>默认值：从API版本26.0.0开始，为BlurStyle.NONE，API版本26.0.0之前，为BlurStyle.COMPONENT_ULTRA_THICK。<br/>**说明：**<br/>设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。

**类型：** BlurStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-backgroundBlurStyle?: BlurStyle--><!--Device-ShowToastOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Toast的背板颜色。<br/>默认值：Color.Transparent<br/>**说明：**<br/>backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-backgroundColor?: ResourceColor--><!--Device-ShowToastOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom?: string | number
```

设置Toast底部边框距离导航条的高度，软键盘拉起时，如果bottom值过小，Toast要被软键盘遮挡时，会自动避让至距离软键盘80vp处。<br/>默认值：80vp<br/>**说明：**<br/>当底部没有导航条时，bottom为设置弹窗底部边框距离窗口底部的高度。<br/>设置对齐方式alignment后，bottom不生效。

**类型：** string | number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-bottom?: string | number--><!--Device-ShowToastOptions-bottom?: string | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

设置Toast弹出的持续时间。<br/>默认值：1500ms<br/>取值范围：[1500, 10000]<br/>若小于1500ms则取默认值，若大于10000ms则取上限值10000ms。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-duration?: number--><!--Device-ShowToastOptions-duration?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态，值为true时，响应悬停态。<br/>默认值：false，默认不响应。

**类型：** boolean

**默认值：** false

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-enableHoverMode?: boolean--><!--Device-ShowToastOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

响应悬停态时，弹窗的显示区域。<br/>默认值：HoverModeAreaType.BOTTOM_SCREEN，默认显示在下半屏。

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-hoverModeArea?: HoverModeAreaType--><!--Device-ShowToastOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string | Resource
```

显示的文本信息。<br>**说明：**<br/>默认字体为'Harmony Sans'，不支持设置其他字体。

**类型：** string | Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-message: string | Resource--><!--Device-ShowToastOptions-message: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

在对齐方式上的偏移。<br/>默认值：{ dx: 0, dy: 0 }，默认没有偏移。<br/>**说明：**<br/>仅支持设置px类型的数值。如需设置其他类型的数值，应将其他类型转换为px类型后传入。例如，若需设置vp，应将其转换为px后传入。

**类型：** Offset

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-offset?: Offset--><!--Device-ShowToastOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Toast的背板阴影。<br/>默认值：ShadowStyle.OUTER_DEFAULT_MD

**类型：** ShadowOptions | ShadowStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-ShowToastOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showMode

```TypeScript
showMode?: ToastShowMode
```

设置Toast层级。<br>默认值：ToastShowMode.DEFAULT，默认显示在应用内。

**类型：** ToastShowMode

**默认值：** ToastShowMode.DEFAULT

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-showMode?: ToastShowMode--><!--Device-ShowToastOptions-showMode?: ToastShowMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置组件的系统材质。<br/>默认值：如果主动设置了backgroundBlurStyle或backgroundColor接口，默认值是无系统材质效果，否则默认值是style为ImmersiveStyle.ULTRA_THICK的[ImmersiveMaterial](arkts-apis-uimaterial.md#immersivematerial)对象。设置undefined时与默认值保持一致。<br/>**说明：**<br />不同系统材质对应不同的属性影响效果，该接口影响背景色[backgroundColor](arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](arkui-ts/ts-universal-attributes-border.md#bordercolor)、边框宽度[borderWidth](arkui-ts/ts-universal-attributes-border.md#borderwidth)、阴影[shadow](arkui-ts/ts-universal-attributes-image-effect.md#shadow)，不建议与上述接口一起使用。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-systemMaterial?: SystemUiMaterial--><!--Device-ShowToastOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textColor

```TypeScript
textColor?: ResourceColor
```

Toast的文本颜色。<br/>默认值：Color.Black

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShowToastOptions-textColor?: ResourceColor--><!--Device-ShowToastOptions-textColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

