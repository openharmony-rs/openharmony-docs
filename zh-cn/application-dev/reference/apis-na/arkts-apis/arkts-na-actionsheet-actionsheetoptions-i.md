# ActionSheetOptions

列表选择弹窗的样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ActionSheetOptions--><!--Device-unnamed-export interface ActionSheetOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

弹窗在竖直方向上的对齐方式。 默认值：DialogAlignment.Bottom **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **说明：** 若在[UIExtension](../../apis-arkui/arkts-apis/arkts-arkui-uiextension.md#@ohos.arkui.uiExtension)中设置showInSubWindow为true，弹窗将基于UIExtension的宿主窗口对齐。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** [DialogAlignment](arkts-na-alertdialog-dialogalignment-e.md)

**默认值：** DialogAlignment.Bottom

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-alignment?: DialogAlignment--><!--Device-ActionSheetOptions-alignment?: DialogAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

点击遮障层时，是否关闭弹窗。 默认值：true 值为true时，点击遮障层关闭弹窗，值为false时，点击遮障层不关闭弹窗。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** boolean

**默认值：** true - The value true means to close the dialog box when the overlay is clicked, and false means the opposite.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-autoCancel?: boolean--><!--Device-ActionSheetOptions-autoCancel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。 默认值：从API版本26.0.0开始，为BlurStyle.NONE，API版本26.0.0之前，为BlurStyle.COMPONENT_ULTRA_THICK。 **说明：** 设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** [BlurStyle](../../apis-arkui/arkts-components/arkts-arkui-blurstyle-e.md)

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-backgroundBlurStyle?: BlurStyle--><!--Device-ActionSheetOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果。默认值请参考BackgroundBlurStyleOptions类型说明。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 19 **ArkTS-Sta起始版本：** 23

**类型：** [BackgroundBlurStyleOptions](../../apis-arkui/arkts-components/arkts-arkui-backgroundblurstyleoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-ActionSheetOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

弹窗背板颜色。 默认值：Color.Transparent **说明：** backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** Color.Transparent

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-backgroundColor?: ResourceColor--><!--Device-ActionSheetOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数。默认值请参考BackgroundEffectOptions类型说明。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 19 **ArkTS-Sta起始版本：** 23

**类型：** [BackgroundEffectOptions](../../apis-arkui/arkts-components/arkts-arkui-backgroundeffectoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-ActionSheetOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors
```

设置弹窗背板的边框颜色。 默认值：Color.Black 如果使用borderColor属性，需要和borderWidth属性一起使用。 **说明：** 当borderColor属性类型为LocalizedEdgeColors时，支持随语言习惯改变布局顺序。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| [EdgeColors](../../apis-arkui/arkts-apis/arkts-arkui-edgecolors-t.md) \| [LocalizedEdgeColors](../../apis-arkui/arkts-apis/arkts-arkui-localizededgecolors-i.md)

**默认值：** Color.Black - borderColor must be used with borderWidth in pairs.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors--><!--Device-ActionSheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

设置弹窗背板的边框样式。 默认值：BorderStyle.Solid。 如果使用borderStyle属性，需要和borderWidth属性一起使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [BorderStyle](../../apis-arkui/arkts-apis/arkts-arkui-borderstyle-e.md) \| [EdgeStyles](../../apis-arkui/arkts-apis/arkts-arkui-edgestyles-t.md)

**默认值：** BorderStyle.Solid - borderStyle must be used with borderWidth in pairs.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-ActionSheetOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths
```

设置弹窗背板的边框宽度。 可分别设置4个边框宽度。 默认值：0 百分比参数方式：以父元素弹窗宽的百分比来设置弹窗的边框宽度。 当弹窗左边框和右边框大于弹窗宽度，弹窗上边框和下边框大于弹窗高度，显示可能不符合预期。 **说明：** 当borderWidth属性类型为LocalizedEdgeWidths时，支持随语言习惯改变布局顺序。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| [EdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-edgewidths-t.md) \| [LocalizedEdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-localizededgewidths-i.md)

**默认值：** 0 - When set to a percentage, the value defines the border width as a percentage of the parent dialog box's width. If the left and right borders are greater than its width, or the top and bottom borders are greater than its height, the dialog box may not display as expected.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths--><!--Device-ActionSheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: VoidCallback
```

点击遮障层关闭dialog时的回调。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 18 **ArkTS-Sta起始版本：** 23

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-cancel?: VoidCallback--><!--Device-ActionSheetOptions-cancel?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## confirm

```TypeScript
confirm?: ActionSheetButtonOptions
```

确认Button的使能状态、默认焦点、按钮风格、文本内容和点击回调。在弹窗获焦且未进行tab键走焦时，该按钮默认响应Enter键。多重弹窗情况下，可自动获焦并连续响应。默认响应Enter键能力在defaultFocus为 true时不生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 18 **ArkTS-Sta起始版本：** 23

**类型：** [ActionSheetButtonOptions](arkts-na-actionsheet-actionsheetbuttonoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-confirm?: ActionSheetButtonOptions--><!--Device-ActionSheetOptions-confirm?: ActionSheetButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses
```

设置背板的圆角半径。 可分别设置4个圆角的半径。 默认值：{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' } 圆角大小受组件尺寸限制，最大值为组件宽或高的一半，若值为负，则按照默认值处理。 百分比参数方式：以父元素弹窗宽和高的百分比来设置弹窗的圆角。 **说明：** 当cornerRadius属性类型为LocalizedBorderRadiuses时，支持随语言习惯改变布局顺序。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| [BorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-borderradiuses-t.md) \| [LocalizedBorderRadiuses](../../apis-arkui/arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**默认值：** - {topLeft:'32vp', topRight:'32vp', bottomLeft:'32vp', bottomRight:'32vp'}, The corner radius is subject to the component size, with the maximum value being half of the component width or height. If the value is negative, the default value is used. When set to a percentage, the value defines the radius as a percentage of the parent component's width or height.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-cornerRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-ActionSheetOptions-cornerRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态，值为true表示响应悬停态。 默认值：false，默认不响应。 **说明：** PC/2in1设备弹窗默认显示在上半屏，在enableHoverMode设置为true时，可以通过设置hoverModeArea参数显示在下半屏。其他设备弹窗在enableHoverMode设置为true时默认显示在下半屏，可 以通过设置hoverModeArea参数显示在上半屏。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 14 **ArkTS-Sta起始版本：** 23

**类型：** boolean

**默认值：** false - meaning not to enable the hover mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-enableHoverMode?: boolean--><!--Device-ActionSheetOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

设置弹窗背板的高度。 **说明：** - 弹窗高度默认最大值：0.9 *（窗口高度 - 安全区域）。 - 百分比参数方式：弹窗参考高度为（窗口高度 - 安全区域），在此基础上调小或调大。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** - Default maximum height of the dialog box: 0.9 x (Window height – Safe area) <br>When this parameter is set to a percentage, the reference height of the dialog box is the height of the window where the dialog box is located minus the safe area. You can decrease or increase the height as needed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-height?: Dimension--><!--Device-ActionSheetOptions-height?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停态下弹窗默认展示区域。 默认值：HoverModeAreaType.BOTTOM_SCREEN。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 14开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 14 **ArkTS-Sta起始版本：** 23

**类型：** [HoverModeAreaType](../../apis-arkui/arkts-components/arkts-arkui-hovermodeareatype-e.md)

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-hoverModeArea?: HoverModeAreaType--><!--Device-ActionSheetOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

设置页面内弹窗蒙层效果。 **说明：** - 默认值：ImmersiveMode.DEFAULT - 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 15 **ArkTS-Sta起始版本：** 23

**类型：** [ImmersiveMode](arkts-na-promptaction-immersivemode-e.md)

**默认值：** ImmersiveMode.DEFAULT - This parameter takes effect only when levelMode is set to LevelMode.EMBEDDED.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-immersiveMode?: ImmersiveMode--><!--Device-ActionSheetOptions-immersiveMode?: ImmersiveMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

弹窗是否为模态窗口，模态窗口有蒙层，非模态窗口无蒙层。值为false时，弹窗为非模态窗口，无蒙层。 默认值：true，此时弹窗有蒙层。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-isModal?: boolean--><!--Device-ActionSheetOptions-isModal?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置弹窗显示层级。 **说明：** - 默认值：LevelMode.OVERLAY - 仅当showInSubWindow属性设置为false时生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 15 **ArkTS-Sta起始版本：** 23

**类型：** [LevelMode](arkts-na-promptaction-levelmode-e.md)

**默认值：** LevelMode.OVERLAY - This parameter takes effect only when showInSubWindow is set to false.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-levelMode?: LevelMode--><!--Device-ActionSheetOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

设置弹窗显示的顺序。 **说明：** - 默认值：LevelOrder.clamp(0) - 不支持动态刷新顺序。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 18开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 18 **ArkTS-Sta起始版本：** 23

**类型：** [LevelOrder](arkts-na-promptaction-levelorder-c.md)

**默认值：** The value returns by LevelOrder.clamp(0)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-levelOrder?: LevelOrder--><!--Device-ActionSheetOptions-levelOrder?: LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: int
```

设置页面级弹窗需要显示的层级下的[getUniqueId](arkts-na-framenode-c.md#getUniqueId)。 取值范围：大于等于0的数字。传入小于0的数字本项配置不生效。 **说明：** - 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 15 **ArkTS-Sta起始版本：** 23

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-levelUniqueId?: int--><!--Device-ActionSheetOptions-levelUniqueId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域，在遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。 默认值：{ x: 0, y: 0, width: '100%', height: '100%' } **说明：** showInSubWindow为true时，maskRect不生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 10 **ArkTS-Sta起始版本：** 23

**类型：** [Rectangle](../../apis-arkui/arkts-components/arkts-arkui-rectangle-i.md)

**默认值：** - {x:0,y:0, width:'100%', height:'100%'}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-maskRect?: Rectangle--><!--Device-ActionSheetOptions-maskRect?: Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string | Resource
```

弹窗内容。 文本超长时会触发滚动条。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-message: string | Resource--><!--Device-ActionSheetOptions-message: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: ActionSheetOffset
```

弹窗相对alignment所在位置的偏移量。 默认值： 1.alignment设置为Top、TopStart、TopEnd时默认值为{dx: 0,dy: "40vp"} 2.alignment设置为其他时默认值为{dx: 0,dy: "-40vp"} **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 18 **ArkTS-Sta起始版本：** 23

**类型：** [ActionSheetOffset](arkts-na-actionsheet-actionsheetoffset-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-offset?: ActionSheetOffset--><!--Device-ActionSheetOptions-offset?: ActionSheetOffset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

弹窗弹出后的事件回调。 **说明：** 1.正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。 2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。 3.快速点击弹出，关闭弹窗时，onWillDisappear在onDidAppear前生效。 4.弹窗入场动效未完成时彻底关闭弹窗，动效打断，onDidAppear不会触发。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 19 **ArkTS-Sta起始版本：** 23

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-onDidAppear?: VoidCallback--><!--Device-ActionSheetOptions-onDidAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

弹窗消失时的事件回调。 **说明：** 正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 19 **ArkTS-Sta起始版本：** 23

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-onDidDisappear?: VoidCallback--><!--Device-ActionSheetOptions-onDidDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

弹窗显示动效前的事件回调。 **说明：** 1.正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。 2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 19 **ArkTS-Sta起始版本：** 23

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-onWillAppear?: VoidCallback--><!--Device-ActionSheetOptions-onWillAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

弹窗退出动效前的事件回调。 **说明：** 正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 19开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 19 **ArkTS-Sta起始版本：** 23

**类型：** [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-onWillDisappear?: VoidCallback--><!--Device-ActionSheetOptions-onWillDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

交互式关闭回调函数。 **说明：** 1.当用户执行点击遮障层关闭、侧滑（左滑/右滑）、三键back、键盘ESC关闭交互操作时，如果注册该回调函数，则不会立刻关闭弹窗。在回调函数中可以通过reason得到阻拦关闭弹窗的操作类型，从而根据原因选择是否能关闭弹窗。当前 组件返回的reason中，暂不支持CLOSE_BUTTON的枚举值。 2.在onWillDismiss回调中，不能再做onWillDismiss拦截。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[DismissDialogAction](arkts-na-actionsheet-dismissdialogaction-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-onWillDismiss?: Callback<DismissDialogAction>--><!--Device-ActionSheetOptions-onWillDismiss?: Callback<DismissDialogAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置弹窗背板的阴影。 当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM。其他设备默认无阴影。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [ShadowOptions](../../apis-arkui/arkts-components/arkts-arkui-shadowoptions-i.md) \| [ShadowStyle](../../apis-arkui/arkts-components/arkts-arkui-shadowstyle-e.md)

**默认值：** - Default value on 2-in-1 devices: ShadowStyle.OUTER_FLOATING_MD when the dialog box is focused and ShadowStyle.OUTER_FLOATING_SM otherwise.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-ActionSheetOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sheets

```TypeScript
sheets: Array<SheetInfo>
```

设置选项内容，每个选择项支持设置图片、文本和选中的回调。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** Array&lt;[SheetInfo](arkts-na-actionsheet-sheetinfo-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-sheets: Array<SheetInfo>--><!--Device-ActionSheetOptions-sheets: Array<SheetInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

某弹窗需要显示在主窗口之外时，是否在子窗口显示此弹窗。值为true表示在子窗口显示弹窗。 默认值：false，弹窗显示在应用内，而非独立子窗口。 **说明：** showInSubWindow为true的弹窗无法触发显示另一个showInSubWindow为true的弹窗。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-showInSubWindow?: boolean--><!--Device-ActionSheetOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

弹窗副标题。 当文本内容过长无法显示时，用省略号代替未显示的部分。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 10 **ArkTS-Sta起始版本：** 23

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-subtitle?: ResourceStr--><!--Device-ActionSheetOptions-subtitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置弹窗的系统材质。 **说明：** - 默认值：ImmersiveOptions的style为ImmersiveStyle.ULTRA_THICK的ImmersiveMaterial对象。设置undefined时与默认值保持一致。 - 不同的材质具有不同的效果，该接口影响背景色backgroundColor、背景模糊 backgroundBlurStyle 、背景效果backgroundEffect、边框颜色 borderColor、边框宽度borderWidth、阴影 shadow，不建议与上述接口一起使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**类型：** [SystemUiMaterial](../../apis-arkui/arkts-components/arkts-arkui-systemuimaterial-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-systemMaterial?: SystemUiMaterial--><!--Device-ActionSheetOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: string | Resource
```

弹窗标题。 当文本内容过长无法显示时，用省略号代替未显示的部分。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 11 **ArkTS-Sta起始版本：** 23

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-title: string | Resource--><!--Device-ActionSheetOptions-title: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

设置弹窗显示和退出的过渡效果。 **说明：** 1.如果不设置，则使用默认的显示/退出动效。 2.显示动效中按back键，打断显示动效，执行退出动效，动画效果为显示动效与退出动效的曲线叠加后的效果。 3.退出动效中按back键，不会打断退出动效，退出动效继续执行，继续按back键退出应用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [TransitionEffect](../../apis-arkui/arkts-components/arkts-arkui-transitioneffect-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-transition?: TransitionEffect--><!--Device-ActionSheetOptions-transition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置弹窗背板的宽度。 **说明：** - 弹窗宽度默认最大值：400vp。 - 百分比参数方式：弹窗参考宽度为所在窗口的宽度，在此基础上调小或调大。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 **ArkTS-Dyn起始版本：** 12 **ArkTS-Sta起始版本：** 23

**类型：** [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** - Default maximum width of the dialog box: 400 vp, When this parameter is set to a percentage, the reference width of the dialog box is the width of the window where the dialog box is located. You can decrease or increase the width as needed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionSheetOptions-width?: Dimension--><!--Device-ActionSheetOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

