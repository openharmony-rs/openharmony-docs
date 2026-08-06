# DatePickerDialogOptions

日期选择器弹窗选项。 继承自[DatePickerOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** DatePickerDialogOptions extends [DatePickerOptions](../arkts-apis/arkts-arkui-component/datepicker-datepickeroptions-i.md)

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

<!--Device-unnamed-declare interface DatePickerDialogOptions extends DatePickerOptions--><!--Device-unnamed-declare interface DatePickerDialogOptions extends DatePickerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

设置确认按钮显示样式、重要程度、角色、背景色、圆角、文本颜色、字号、字体粗细、字体样式、字体列表、按钮是否默认响应Enter键。 当需要自定义确认按钮外观或行为时传入此参数。不传入时使用系统默认按钮样式。 > **说明：** > > 1. acceptButtonStyle与cancelButtonStyle中最多只能有一个primary字段配置为true，如果同时设置为true，则primary字段不生效， > 保持默认值false。 > > 2. 按钮高度默认40vp，在关怀模式-大字体场景下高度不变，即使按钮样式设置为圆角矩形 > [ROUNDED\_RECTANGLE]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，呈现效果依然是胶囊型按钮[Capsule]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**类型：** PickerDialogButtonStyle

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-DatePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

弹窗在竖直方向上的对齐方式。 > 默认值：DialogAlignment.Default

**类型：** DialogAlignment

**默认值：** DialogAlignment.Default [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-alignment?: DialogAlignment--><!--Device-DatePickerDialogOptions-alignment?: DialogAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

弹窗背板模糊材质。 > 默认值：BlurStyle.COMPONENT\_ULTRA\_THICK > **说明：** > > 设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor， > 否则显示的颜色将不符合预期效果。

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-DatePickerDialogOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

背景模糊效果参数，用于自定义弹窗背景模糊的显示样式，支持配置颜色模式、自适应颜色、缩放比例等属性，实现不同的背景模糊视觉效果。 默认值请参考BackgroundBlurStyleOptions类型说明。 > **说明：** > > 未设置时沿用backgroundBlurStyle的默认效果（BlurStyle.COMPONENT\_ULTRA\_THICK）。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-DatePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

弹窗背板颜色。 > 默认值：Color.Transparent > **说明：** > > 当设置了backgroundColor为非透明色时，backgroundBlurStyle需要设置为BlurStyle.NONE，否则显示的颜色将不符合预期效果。

**类型：** ResourceColor

**默认值：** Color.Transparent

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-backgroundColor?: ResourceColor--><!--Device-DatePickerDialogOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

背景效果参数，用于自定义弹窗背景的显示效果，支持配置模糊半径、饱和度、亮度、颜色等属性，实现不同的背景视觉效果。默认值请参考 BackgroundEffectOptions类型说明。 > **说明：** > > 未设置时不生效，此时弹窗背景模糊效果由backgroundBlurStyle决定；设置后将覆盖backgroundBlurStyle的效果。从API版本26.0.0开始， > 设置systemMaterial后backgroundEffect与backgroundBlurStyle均不生效。

**类型：** BackgroundEffectOptions

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-DatePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop?: boolean
```

设置是否可循环滚动。 - true：可循环，年份随着月份的循环滚动进行联动加减，月份随着日的循环滚动进行联动加减。 - false：不可循环，年、月、日到达本列的顶部或底部时，无法再进行滚动，年、月、日之间也无法再联动加减。 > 默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-canLoop?: boolean--><!--Device-DatePickerDialogOptions-canLoop?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

设置取消按钮显示样式、重要程度、角色、背景色、圆角、文本颜色、字号、字体粗细、字体样式、字体列表、按钮是否默认响应Enter键。 当需要自定义取消按钮外观或行为时传入此参数。不传入时使用系统默认按钮样式。 > **说明：** > > 1. acceptButtonStyle与cancelButtonStyle中最多只能有一个primary字段配置为true，如果同时设置为true，则primary字段不生效， > 保持默认值false。 > > 2. 按钮高度默认40vp，在关怀模式-大字体场景下高度不变，即使按钮样式设置为圆角矩形 > [ROUNDED\_RECTANGLE]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，呈现效果依然是胶囊型按钮[Capsule]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**类型：** PickerDialogButtonStyle

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-DatePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dateTimeOptions

```TypeScript
dateTimeOptions?: DateTimeOptions
```

设置时分是否显示前导0，目前只支持设置hour和minute参数，仅当showTime为true时生效。 > 默认值： > > - hour: 24小时制默认为"2-digit"，设置hour是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"； > 12小时制默认为"numeric"，即没有前导0。可选值为"numeric"或"2-digit"，传入其他值时按默认值处理。 > - minute: 默认为"2-digit"，设置minute是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。 > 可选值为"numeric"或"2-digit"，传入其他值时按默认值处理。

**类型：** DateTimeOptions

**默认值：** hour: In the 24-hour format, it defaults to 2-digit, which means a leading zero is used;
<br>In the 12-hour format, it defaults to numeric, which means no leading zero is used.
<br>minute: defaults to 2-digit, which means a leading zero is used.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-dateTimeOptions?: DateTimeOptions--><!--Device-DatePickerDialogOptions-dateTimeOptions?: DateTimeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: PickerTextStyle
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。 > 默认值： > > \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_{ > \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_color: '#ff182431', > \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_font: { > \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_size: '14fp', > \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_weight: FontWeight.Regular > \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_} > \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_}

**类型：** PickerTextStyle

**默认值：** { color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } } [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-disappearTextStyle?: PickerTextStyle--><!--Device-DatePickerDialogOptions-disappearTextStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

设置是否开启触控反馈。 - true：开启触控反馈（当需要为用户提供操作反馈时选择）。 - false：不开启触控反馈（当不需要触控反馈或设备不支持时选择）。 > 默认值：true > **说明：** > > 1. 设置为true后，其生效情况取决于系统的硬件是否支持。 > 2. 开启触控反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限，配置如下： > > "requestPermissions": [{"name": "ohos.permission.VIBRATE"}]

**类型：** boolean

**默认值：** true

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-enableHapticFeedback?: boolean--><!--Device-DatePickerDialogOptions-enableHapticFeedback?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

是否响应悬停态。悬停态指折叠屏等设备处于悬停折叠状态时的交互模式，而非鼠标悬停。 - true：响应悬停态。 - false：不响应悬停态。 默认值：false

**类型：** boolean

**默认值：** false - meaning not to enable the hover mode.

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-enableHoverMode?: boolean--><!--Device-DatePickerDialogOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

设置悬停态下弹窗默认展示区域，仅在enableHoverMode为true时生效。 默认值：HoverModeAreaType.BOTTOM\_SCREEN

**类型：** HoverModeAreaType

**默认值：** HoverModeAreaType.BOTTOM_SCREEN

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-DatePickerDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lunar

```TypeScript
lunar?: boolean
```

日期是否显示为农历。 - true：显示为农历。 - false：不显示为农历。 > 默认值：false > **说明：** > > 仅在简体中文和繁体中文语言环境下生效，其他语言环境下设置该属性无效果。

**类型：** boolean

**默认值：** false [since 11]

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-lunar?: boolean--><!--Device-DatePickerDialogOptions-lunar?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lunarSwitch

```TypeScript
lunarSwitch?: boolean
```

是否展示切换农历的开关。 - true：展示切换农历的开关。 - false：不展示切换农历的开关。 > 默认值：false > **说明：** > > 开关打开后，仅在简体中文和繁体中文环境下生效，在其他语言环境农历不生效，因此建议在其他语言环境设置为不展示开关。

**类型：** boolean

**默认值：** false [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-lunarSwitch?: boolean--><!--Device-DatePickerDialogOptions-lunarSwitch?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lunarSwitchStyle

```TypeScript
lunarSwitchStyle?: LunarSwitchStyle
```

设置农历开关的颜色样式。仅当lunarSwitch为true时生效。 > 默认值： > \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_{ > \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_selectedColor: \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_, > \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_unselectedColor: \_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_, > \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_strokeColor: Color.White > \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_}

**类型：** LunarSwitchStyle

**默认值：** { selectedColor: $r('sys.color.ohos_id_color_text_primary_actived'),
unselectedColor: $r('sys.color.ohos_id_color_switch_outline_off'),
strokeColor: Color.White }.

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-lunarSwitchStyle?: LunarSwitchStyle--><!--Device-DatePickerDialogOptions-lunarSwitchStyle?: LunarSwitchStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

弹窗遮蔽层区域，在遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。 > 默认值：{ x: 0, y: 0, width: '100%', height: '100%' }

**类型：** Rectangle

**默认值：** { x: 0, y: 0, width: '100%', height: '100%' } [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-maskRect?: Rectangle--><!--Device-DatePickerDialogOptions-maskRect?: Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

弹窗相对alignment所在位置的偏移量。当需要微调弹窗位置时设置此参数（如与alignment配合实现精确位置控制）， 不设置时弹窗按alignment对齐位置显示。 > 默认值：{ dx: 0 , dy: 0 }

**类型：** Offset

**默认值：** { dx: 0 , dy: 0 } [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-offset?: Offset--><!--Device-DatePickerDialogOptions-offset?: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: (value: DatePickerResult) => void
```

点击弹窗中的“确定”按钮时触发该回调。回调参数value为当前选中的日期，包含年、月、日信息。 > **说明：** > > 从API version 8开始支持，从API version 10开始废弃。建议使用onDateAccept。

**类型：** (value: DatePickerResult) =&gt; void

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 10

**替代接口：** datePicker/DatePickerDialogOptions#onDateAccept

<!--Device-DatePickerDialogOptions-onAccept?: (value: DatePickerResult) => void--><!--Device-DatePickerDialogOptions-onAccept?: (value: DatePickerResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: VoidCallback
```

点击弹窗中的“取消”按钮时触发该回调。回调签名：() => void，无参数和返回值。

**类型：** VoidCallback

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-onCancel?: VoidCallback--><!--Device-DatePickerDialogOptions-onCancel?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: DatePickerResult) => void
```

滑动弹窗中的滑动选择器使当前选中项改变时触发该回调。回调参数value为当前选中的日期，包含年、月、日信息。 > **说明：** > > 从API version 8开始支持，从API version 10开始废弃。建议使用onDateChange。

**类型：** (value: DatePickerResult) =&gt; void

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 10

**替代接口：** datePicker/DatePickerDialogOptions#onDateChange

<!--Device-DatePickerDialogOptions-onChange?: (value: DatePickerResult) => void--><!--Device-DatePickerDialogOptions-onChange?: (value: DatePickerResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDateAccept

```TypeScript
onDateAccept?: Callback<Date>
```

点击弹窗中的“确定”按钮时触发该回调。回调签名：(value: Date) => void，其中value为用户选择的日期，包含年月日信息；当showTime为true时， 还包含时和分信息。开发者可在此回调中保存用户选择的日期或执行后续业务逻辑。 > **说明：** > > 当showTime设置为true时，value中时和分为选择器选择的时和分。否则，value中时和分为系统时间的时和分。

**类型：** Callback&lt;Date&gt;

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-onDateAccept?: Callback<Date>--><!--Device-DatePickerDialogOptions-onDateAccept?: Callback<Date>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDateChange

```TypeScript
onDateChange?: Callback<Date>
```

滑动弹窗中的日期使当前选中项改变时触发该回调。回调签名：(value: Date) => void，其中value为当前选中的日期，包含年月日信息； 当showTime为true时，还包含时和分信息。此回调在用户滑动选择器过程中实时触发，与onDateAccept仅在点击确定后触发的时机不同。 > **说明：** > > 当showTime设置为true时，value中时和分为选择器选择的时和分。否则，value中时和分为系统时间的时和分。

**类型：** Callback&lt;Date&gt;

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-onDateChange?: Callback<Date>--><!--Device-DatePickerDialogOptions-onDateChange?: Callback<Date>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

弹窗弹出后的事件回调。 > **说明：** > > 1. 正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 > > 2. 在onDidAppear内设置改变弹窗显示效果的回调事件，再次调用showDatePickerDialog时生效。 > > 3. 快速连续触发弹出与关闭时，存在onWillDisappear在onDidAppear前生效。 > > 4. 当弹窗入场动效未完成时关闭弹窗，该回调不会触发。

**类型：** VoidCallback

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-onDidAppear?: VoidCallback--><!--Device-DatePickerDialogOptions-onDidAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

弹窗消失后的事件回调。 > **说明：** > > 1. 正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 > > 2. 快速连续触发弹出与关闭时，存在onWillDisappear在onDidAppear前生效。 > > 3. 当弹窗入场动效未完成时关闭弹窗，该回调不会触发。

**类型：** VoidCallback

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-onDidDisappear?: VoidCallback--><!--Device-DatePickerDialogOptions-onDidDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

弹窗显示动效前的事件回调。 > **说明：** > > 1. 正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 > > 2. 在onWillAppear内设置改变弹窗显示效果的回调事件，再次调用showDatePickerDialog时生效。 > > 3. 快速连续触发弹出与关闭时，存在onWillDisappear在onDidAppear前生效。 > > 4. 当弹窗入场动效未完成时关闭弹窗，onDidAppear和后续回调不会触发。

**类型：** VoidCallback

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-onWillAppear?: VoidCallback--><!--Device-DatePickerDialogOptions-onWillAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

弹窗退出动效前的事件回调。 > **说明：** > > 1. 正常时序依次为：onWillAppear>>onDidAppear>>(onDateAccept/onCancel/onDateChange)>>onWillDisappear>>onDidDisappear。 > > 2. 快速连续触发弹出与关闭时，存在onWillDisappear在onDidAppear前生效。 > > 3. 当弹窗入场动效未完成时关闭弹窗，该回调不会触发。

**类型：** VoidCallback

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-onWillDisappear?: VoidCallback--><!--Device-DatePickerDialogOptions-onWillDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: PickerTextStyle
```

设置选中项的文本颜色、字号、字体粗细。 > 默认值： > > \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_{ > \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_color: '#ff007dff', > \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_font: { > \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_size: '20fp', > \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_weight: FontWeight.Medium > \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_} > \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_}

**类型：** PickerTextStyle

**默认值：** { color: '#ff007dff', font: { size: '20vp', weight: FontWeight.Medium } [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-selectedTextStyle?: PickerTextStyle--><!--Device-DatePickerDialogOptions-selectedTextStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置弹窗背板的阴影。 当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER\_FLOATING\_MD，失焦为ShadowStyle.OUTER\_FLOATING\_SM。其他设备默认无阴影。

**类型：** ShadowOptions \| ShadowStyle

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-DatePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showTime

```TypeScript
showTime?: boolean
```

是否在弹窗内展示时间选择器。 - true：展示时间选择器。 - false：不展示时间选择器。 > 默认值：false > **说明：** > > 1. 当showTime为true时，点击弹窗的标题日期可以在"日期选择器"和"日期选择器+时间选择器"两个页面中切换。 > 2. 当showTime为true时，mode参数不生效，此时纯日期选择页面固定显示年、月、日三列。

**类型：** boolean

**默认值：** false [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-showTime?: boolean--><!--Device-DatePickerDialogOptions-showTime?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置弹窗的系统材质。 > **说明：** > > - 默认值为ImmersiveOptions的style为ImmersiveStyle.ULTRA\_THICK的ImmersiveMaterial对象，设置undefined时与默认值保持一致。 > 不同的材质具有不同的效果。关于ImmersiveMaterial的详细说明，请参考[SystemUiMaterial]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型定义。 > - 该接口影响背景色[backgroundColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、背景模糊 > [backgroundBlurStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ > 、背景模糊效果[backgroundBlurStyleOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、背景效果 > [backgroundEffect]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_、边框颜色 > [borderColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_、边框宽度[borderWidth]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_、阴影 > [shadow]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_，当设置系统材质时，上述接口不生效。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-systemMaterial?: SystemUiMaterial--><!--Device-DatePickerDialogOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: PickerTextStyle
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。 > 默认值： > > \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_{ > \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_color: '#ff182431', > \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_font: { > \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_size: '16fp', > \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_weight: FontWeight.Regular > \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_} > \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_}

**类型：** PickerTextStyle

**默认值：** { color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } } [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-textStyle?: PickerTextStyle--><!--Device-DatePickerDialogOptions-textStyle?: PickerTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

弹窗内展示的时间选择器是否为24小时制，仅当showTime为true时生效。 - true：显示24小时制。 - false：显示12小时制。 > 默认值：false > **说明：** > > 当展示的时间选择器为12小时制时，上午和下午的标识不会根据小时数自动切换。

**类型：** boolean

**默认值：** false [since 11]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialogOptions-useMilitaryTime?: boolean--><!--Device-DatePickerDialogOptions-useMilitaryTime?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

