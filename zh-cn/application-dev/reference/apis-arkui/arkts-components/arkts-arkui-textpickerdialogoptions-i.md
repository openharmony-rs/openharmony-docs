# TextPickerDialogOptions

文本选择器弹窗的参数继承自[TextPickerOptions](arkts-arkui-textpickeroptions-i.md)。

**继承/实现关系：** TextPickerDialogOptions extends [TextPickerOptions](arkts-arkui-textpickeroptions-i.md)

**起始版本：** 8

<!--Device-unnamed-declare interface TextPickerDialogOptions extends TextPickerOptions--><!--Device-unnamed-declare interface TextPickerDialogOptions extends TextPickerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

设置确认按钮显示样式、样式和重要程度、角色、背景色、圆角、文本颜色、字号、字体粗细、字体样式、字体列表、按钮是否默认响应Enter键。

**说明：**

1.acceptButtonStyle与cancelButtonStyle中最多只能有一个primary字段配置为true，如果同时设置为true，则primary字段不生效，保持默认值false。

2.按钮高度默认40vp，在关怀模式-大字体场景下高度不变，即使按钮样式设置为圆角矩形[ROUNDED_RECTANGLE](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype枚举说明)，呈现效果依然是胶囊型按钮[Capsule](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype枚举说明)。

**类型：** PickerDialogButtonStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-TextPickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

弹窗在竖直方向上的对齐方式。

默认值：DialogAlignment.Default

**类型：** DialogAlignment

**默认值：** DialogAlignment.Default [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-alignment?: DialogAlignment--><!--Device-TextPickerDialogOptions-alignment?: DialogAlignment-End-->

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

<!--Device-TextPickerDialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-TextPickerDialogOptions-backgroundBlurStyle?: BlurStyle-End-->

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

<!--Device-TextPickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-TextPickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

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

<!--Device-TextPickerDialogOptions-backgroundColor?: ResourceColor--><!--Device-TextPickerDialogOptions-backgroundColor?: ResourceColor-End-->

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

<!--Device-TextPickerDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-TextPickerDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop?: boolean
```

设置是否可循环滚动。

- true：可循环。  
- false：不可循环。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-canLoop?: boolean--><!--Device-TextPickerDialogOptions-canLoop?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

设置取消按钮显示样式、样式和重要程度、角色、背景色、圆角、文本颜色、字号、字体粗细、字体样式、字体列表、按钮是否默认响应Enter键。

**说明：**

1.acceptButtonStyle与cancelButtonStyle中最多只能有一个primary字段配置为true，如果同时设置为true，则primary字段不生效，保持默认值false。

2.按钮高度默认40vp，在关怀模式-大字体场景下高度不变，即使按钮样式设置为圆角矩形[ROUNDED_RECTANGLE](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype枚举说明)，呈现效果依然是胶囊型按钮[Capsule](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-button.md#buttontype枚举说明)。

**类型：** PickerDialogButtonStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-TextPickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight?: number | string
```

设置选择器中选项的高度。number类型取值范围：[0, +∞)，string类型仅支持number类型取值的字符串形式，例如"56"。

默认值：选中项56vp，非选中项36vp。设置该参数后，选中项与非选中项的高度均为所设置的值。

**类型：** number \| string

**默认值：** 56 vp (selected) and 36 vp (unselected) [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-defaultPickerItemHeight?: number | string--><!--Device-TextPickerDialogOptions-defaultPickerItemHeight?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultTextStyle

```TypeScript
defaultTextStyle?: TextPickerTextStyle
```

设置关闭滑动过程中文本样式变化动效时的各个选项的文本样式，仅当disableTextStyleAnimation为true时生效。

默认值：与[Text](./text)组件默认值相同。

**类型：** TextPickerTextStyle

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-defaultTextStyle?: TextPickerTextStyle--><!--Device-TextPickerDialogOptions-defaultTextStyle?: TextPickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableTextStyleAnimation

```TypeScript
disableTextStyleAnimation?: boolean
```

设置是否关闭滑动过程中文本样式变化的动效。

- true：关闭文本样式变化动效。  
- false：不关闭文本样式变化动效。

默认值：false

**说明：**

设置为true时，滑动过程中无字号、字重、字体颜色等变化动效，且文本均显示为defaultTextStyle属性设置的样式。如未设置defaultTextStyle，则显示为[Text](./text)组件默认样式。

**类型：** boolean

**默认值：** false

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-disableTextStyleAnimation?: boolean--><!--Device-TextPickerDialogOptions-disableTextStyleAnimation?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: PickerTextStyle
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。

默认值：{ color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }

**类型：** PickerTextStyle

**默认值：** { color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-disappearTextStyle?: PickerTextStyle--><!--Device-TextPickerDialogOptions-disappearTextStyle?: PickerTextStyle-End-->

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

<!--Device-TextPickerDialogOptions-enableHapticFeedback?: boolean--><!--Device-TextPickerDialogOptions-enableHapticFeedback?: boolean-End-->

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

**默认值：** false - meaning not to enable the hover mode.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-enableHoverMode?: boolean--><!--Device-TextPickerDialogOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

设置悬停态下弹窗默认展示区域。

默认值：HoverModeAreaType.BOTTOM_SCREEN

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-TextPickerDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域，在遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。

默认值：{ x: 0, y: 0, width: '100%', height: '100%' }

**类型：** Rectangle

**默认值：** { x: 0, y: 0, width: '100%', height: '100%' } [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-maskRect?: Rectangle--><!--Device-TextPickerDialogOptions-maskRect?: Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

弹窗相对alignment所在位置的偏移量。

默认值：{ dx: 0 , dy: 0 }

**类型：** Offset

**默认值：** { dx: 0 , dy: 0 } [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-offset?: Offset--><!--Device-TextPickerDialogOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: (value: TextPickerResult) => void
```

点击弹窗中的“确定”按钮时触发该回调。

**类型：** (value: TextPickerResult) =&gt; void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onAccept?: (value: TextPickerResult) => void--><!--Device-TextPickerDialogOptions-onAccept?: (value: TextPickerResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: () => void
```

点击弹窗中的“取消”按钮时触发该回调。

**类型：** () =&gt; void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onCancel?: () => void--><!--Device-TextPickerDialogOptions-onCancel?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: TextPickerResult) => void
```

滑动弹窗中的选择器后，选项归位至选中项位置时，触发该回调。

回调会在滑动动画结束后触发，如果需要快速获取索引值变化，建议使用onEnterSelectedArea接口。

**类型：** (value: TextPickerResult) =&gt; void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onChange?: (value: TextPickerResult) => void--><!--Device-TextPickerDialogOptions-onChange?: (value: TextPickerResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: () => void
```

弹窗弹出后的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange/onScrollStop)>>onWillDisappear>>onDidDisappear。

2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

3.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。

4. 当弹窗入场动效未完成时关闭弹窗，该回调不会触发。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onDidAppear?: () => void--><!--Device-TextPickerDialogOptions-onDidAppear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: () => void
```

弹窗消失后的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange/onScrollStop)>>onWillDisappear>>onDidDisappear。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onDidDisappear?: () => void--><!--Device-TextPickerDialogOptions-onDidDisappear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea?: Callback<TextPickerResult>
```

滑动过程中，选项进入分割线区域内，触发该回调。与onChange事件的差别在于，该事件的触发时机早于onChange事件，当当前滑动列滑动距离超过选中项高度的一半时，选项此时已经进入分割线区域内，会触发该事件。

**说明：**

在多列联动场景中，不建议使用该回调，由于该回调标识的是滑动过程中选项进入分割线区域内的节点，而跟随变化的选项并不涉及滑动，因此，回调的返回值中，仅当前滑动列的值会正常变化，其余未滑动列的值保持不变。

**类型：** Callback&lt;TextPickerResult&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onEnterSelectedArea?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptions-onEnterSelectedArea?: Callback<TextPickerResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<TextPickerResult>
```

滑动弹窗中的选择器的选择列停止时，触发该回调。

**类型：** Callback&lt;TextPickerResult&gt;

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onScrollStop?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptions-onScrollStop?: Callback<TextPickerResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

弹窗显示动效前的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange/onScrollStop)>>onWillDisappear>>onDidDisappear。

2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onWillAppear?: () => void--><!--Device-TextPickerDialogOptions-onWillAppear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

弹窗退出动效前的事件回调。

**说明：**

1.正常时序依次为：onWillAppear>>onDidAppear>>(onAccept/onCancel/onChange/onScrollStop)>>onWillDisappear>>onDidDisappear。

2.快速点击弹出，消失弹窗时，存在onWillDisappear在onDidAppear前生效。

**类型：** () =&gt; void

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-onWillDisappear?: () => void--><!--Device-TextPickerDialogOptions-onWillDisappear?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundStyle

```TypeScript
selectedBackgroundStyle?: PickerBackgroundStyle
```

设置选中项背景样式。

默认值：{ color: $r('sys.color.comp_background_tertiary'), borderRadius: $r('sys.float.corner_radius_level12') }

**类型：** PickerBackgroundStyle

**默认值：** { color: $r('sys.color.comp_background_tertiary'), borderRadius: $r('sys.float.corner_radius_level12') }

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-selectedBackgroundStyle?: PickerBackgroundStyle--><!--Device-TextPickerDialogOptions-selectedBackgroundStyle?: PickerBackgroundStyle-End-->

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

<!--Device-TextPickerDialogOptions-selectedTextStyle?: PickerTextStyle--><!--Device-TextPickerDialogOptions-selectedTextStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置弹窗背板的阴影。

当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM

**类型：** ShadowOptions \| ShadowStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-TextPickerDialogOptions-shadow?: ShadowOptions | ShadowStyle-End-->

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

<!--Device-TextPickerDialogOptions-systemMaterial?: SystemUiMaterial--><!--Device-TextPickerDialogOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: PickerTextStyle
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。

默认值：{ color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }

**类型：** PickerTextStyle

**默认值：** { color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialogOptions-textStyle?: PickerTextStyle--><!--Device-TextPickerDialogOptions-textStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

