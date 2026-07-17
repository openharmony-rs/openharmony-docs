# TimePickerDialogOptions

时间选择器弹窗选项。

继承自[TimePickerOptions](arkts-arkui-time-picker-timepickeroptions-i.md)。

**继承/实现关系：** TimePickerDialogOptions extends [TimePickerOptions](arkts-arkui-time-picker-timepickeroptions-i.md)

**起始版本：** 8

<!--Device-unnamed-declare interface TimePickerDialogOptions extends TimePickerOptions--><!--Device-unnamed-declare interface TimePickerDialogOptions extends TimePickerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

设置确认按钮显示样式、样式和重要程度、角色、背景色、圆角、文本颜色、字号、字体粗细、字体样式、字体列表、按钮是否默认响应Enter键。

**说明：**

1.acceptButtonStyle与cancelButtonStyle中最多只能有一个primary字段配置为true，如果同时设置为true，则primary字段不生效，保持默认值false。2.按钮高度默认40vp，在关怀模式-大字体场景下高度不变，即使按钮样式设置为圆角矩形[ROUNDED_RECTANGLE](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype)，呈现效果依然是胶囊型按钮[Capsule](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype)。

**类型：** PickerDialogButtonStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-TimePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

设置弹窗在垂直方向上的对齐方式。

默认值：DialogAlignment.Default

**类型：** DialogAlignment

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-alignment?: DialogAlignment--><!--Device-TimePickerDialogOptions-alignment?: DialogAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。

默认值：BlurStyle.COMPONENT_ULTRA_THICK

**说明：**

设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则显示的颜色将不符合预期效果。

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-TimePickerDialogOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-TimePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

弹窗背板颜色。

默认值：Color.Transparent

**说明：**

当设置了backgroundColor为非透明色时，backgroundBlurStyle需要设置为BlurStyle.NONE，否则显示的颜色将不符合预期效果。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-backgroundColor?: ResourceColor--><!--Device-TimePickerDialogOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数。

**类型：** BackgroundEffectOptions

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-TimePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

设置取消按钮显示样式、样式和重要程度、角色、背景色、圆角、文本颜色、字号、字体粗细、字体样式、字体列表、按钮是否默认响应Enter键。

**说明：**

1.acceptButtonStyle与cancelButtonStyle中最多只能有一个primary字段配置为true，如果同时设置为true，则primary字段不生效，保持默认值false。2.按钮高度默认40vp，在关怀模式-大字体场景下高度不变，即使按钮样式设置为圆角矩形[ROUNDED_RECTANGLE](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype)，呈现效果依然是胶囊型按钮[Capsule](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype)。

**类型：** PickerDialogButtonStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-TimePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dateTimeOptions

```TypeScript
dateTimeOptions?: DateTimeOptions
```

设置时分是否显示前导0，目前只支持设置hour和minute参数。

默认值：

hour: 24小时制默认为"2-digit"，设置hour是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"；12小时制默认为"numeric"，即没有前导0。

minute: 默认为"2-digit"，设置minute是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。

**类型：** DateTimeOptions

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-dateTimeOptions?: DateTimeOptions--><!--Device-TimePickerDialogOptions-dateTimeOptions?: DateTimeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: PickerTextStyle
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。

默认值：{ color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }

**类型：** PickerTextStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-disappearTextStyle?: PickerTextStyle--><!--Device-TimePickerDialogOptions-disappearTextStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableCascade

```TypeScript
enableCascade?: boolean
```

设置上午和下午的标识是否根据小时数自动切换，仅在useMilitaryTime设置为false时生效。

- true：自动切换。  
- false：不自动切换。

默认值：false

当enableCascade设置为true时，仅在loop参数同时为true时生效。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-enableCascade?: boolean--><!--Device-TimePickerDialogOptions-enableCascade?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

设置是否开启触控反馈。

- true：开启触控反馈。  
- false：不开启触控反馈。

默认值：true

**说明**：

1. 设置为true后，其生效情况取决于系统的硬件是否支持。2. 开启触控反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限。

**类型：** boolean

**默认值：** true

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-enableHapticFeedback?: boolean--><!--Device-TimePickerDialogOptions-enableHapticFeedback?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态。

- true：响应悬停态。  
- false：不响应悬停态。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-enableHoverMode?: boolean--><!--Device-TimePickerDialogOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

悬停态下弹窗默认展示区域。

默认值：HoverModeAreaType.BOTTOM_SCREEN

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-TimePickerDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域，在遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。

默认值：{ x: 0, y: 0, width: '100%', height: '100%' }

**类型：** Rectangle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-maskRect?: Rectangle--><!--Device-TimePickerDialogOptions-maskRect?: Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

设置弹窗相对alignment所在位置的偏移量。

默认值：{ dx: 0 , dy: 0 }

**类型：** Offset

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-offset?: Offset--><!--Device-TimePickerDialogOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: (value: TimePickerResult) => void
```

点击弹窗中的“确定”按钮时触发该回调。

**类型：** (value: TimePickerResult) => void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onAccept?: (value: TimePickerResult) => void--><!--Device-TimePickerDialogOptions-onAccept?: (value: TimePickerResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: () => void
```

点击弹窗中的“取消”按钮时触发该回调。

**类型：** () => void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onCancel?: () => void--><!--Device-TimePickerDialogOptions-onCancel?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: TimePickerResult) => void
```

滑动弹窗中的选择器后，选项归位至选中项位置时，触发该回调。

**类型：** (value: TimePickerResult) => void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onChange?: (value: TimePickerResult) => void--><!--Device-TimePickerDialogOptions-onChange?: (value: TimePickerResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: () => void
```

弹窗弹出后的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange)>>onWillDisappear>>onDidDisappear。

2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

3.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。

4.当弹窗入场动效未完成时关闭弹窗，该回调不会触发。

**类型：** () => void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onDidAppear?: () => void--><!--Device-TimePickerDialogOptions-onDidAppear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: () => void
```

弹窗消失后的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange)>>onWillDisappear>>onDidDisappear。

**类型：** () => void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onDidDisappear?: () => void--><!--Device-TimePickerDialogOptions-onDidDisappear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea?: Callback<TimePickerResult>
```

滑动过程中，选项进入分割线区域内，触发该回调。与onChange事件的差别在于，该事件的触发时机早于onChange事件，当当前滑动列滑动距离超过选中项高度的一半时，选项此时已经进入分割线区域内，会触发该事件。

**说明：**

当enableCascade设置为true时，由于上午/下午列与小时列存在联动关系，不建议使用该回调。该回调标识的是滑动过程中选项进入分割线区域内的节点，而联动变化的选项并不涉及滑动，因此，回调的返回值中，仅当前滑动列的值会正常变化，其余未滑动列的值保持不变。

**类型：** Callback<TimePickerResult>

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onEnterSelectedArea?: Callback<TimePickerResult>--><!--Device-TimePickerDialogOptions-onEnterSelectedArea?: Callback<TimePickerResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

弹窗显示动效前的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange)>>onWillDisappear>>onDidDisappear。

2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

**类型：** () => void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onWillAppear?: () => void--><!--Device-TimePickerDialogOptions-onWillAppear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

弹窗退出动效前的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange)>>onWillDisappear>>onDidDisappear。

2.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。

**类型：** () => void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-onWillDisappear?: () => void--><!--Device-TimePickerDialogOptions-onWillDisappear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: PickerTextStyle
```

设置选中项的文本颜色、字号、字体粗细。

默认值：{ color: '#ff007dff', font: { size: '20fp', weight: FontWeight.Medium } }

**类型：** PickerTextStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-selectedTextStyle?: PickerTextStyle--><!--Device-TimePickerDialogOptions-selectedTextStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置弹窗背板的阴影。

**说明：**

当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM。

**类型：** ShadowOptions | ShadowStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-TimePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

为对话框设置系统风格的材质。不同的材质具有不同的效果，可以影响对话框的背景颜色、边框、阴影等视觉属性。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-systemMaterial?: SystemUiMaterial--><!--Device-TimePickerDialogOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: PickerTextStyle
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。

默认值：{ color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }

**类型：** PickerTextStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-textStyle?: PickerTextStyle--><!--Device-TimePickerDialogOptions-textStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

时间是否以24小时制展示。

- true：时间以24小时制展示。  
- false：时间以12小时制展示。

默认值：false

**类型：** boolean

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialogOptions-useMilitaryTime?: boolean--><!--Device-TimePickerDialogOptions-useMilitaryTime?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

