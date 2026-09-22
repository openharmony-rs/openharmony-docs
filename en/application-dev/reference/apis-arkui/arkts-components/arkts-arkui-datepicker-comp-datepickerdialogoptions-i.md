# DatePickerDialogOptions

```TypeScript
declare interface DatePickerDialogOptions extends DatePickerOptions
```

Defines the configuration options of the date picker dialog box.

Inherited from [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md).

**Inheritance/Implementation:** DatePickerDialogOptions extends [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: (value: DatePickerResult) => void
```

Callback invoked when the OK button in the dialog box is clicked.

**NOTE:** 

This API is supported since API version 8 and deprecated since API version 10. You are advised to use **onDateAccept** instead.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** onDateAccept

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DatePickerResult](arkts-arkui-datepicker-comp-datepickerresult-i.md) | Yes |  |

## onCancel

```TypeScript
onCancel?: VoidCallback
```

Callback invoked when the Cancel button in the dialog box is clicked.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: DatePickerResult) => void
```

Callback invoked when the selected item in the picker changes.

**NOTE:** 

This API is supported since API version 8 and deprecated since API version 10. You are advised to use **onDateChange** instead.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** onDateChange

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DatePickerResult](arkts-arkui-datepicker-comp-datepickerresult-i.md) | Yes |  |

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

Event callback after the dialog box appears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onDateAccept/onCancel/onDateChange) &gt;
onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onDidAppear**.
The settings take effect next time the dialog box appears.
3. If the user closes the dialog box immediately after it appears, **onWillDisappear** is
invoked before **onDidAppear**.
4. If the dialog box is closed before its entrance animation is finished, this callback is not invoked.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

Event callback after the dialog box disappears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onDateAccept/onCancel/onDateChange) &gt;
onWillDisappear &gt; onDidDisappear.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

Event callback when the dialog box is about to appear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onDateAccept/onCancel/onDateChange) &gt;
onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onWillAppear**.
The settings take effect next time the dialog box appears.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

Event callback when the dialog box is about to disappear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onDateAccept/onCancel/onDateChange) &gt;
onWillDisappear &gt; onDidDisappear.
2. If the user closes the dialog box immediately after it appears, onWillDisappear is invoked before onDidAppear.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

Style of the accept button.

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**。
If both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp and remains fixed even in accessibility and large-font modes.
In addition, even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment mode of the dialog box in the vertical direction.

Default value: **DialogAlignment.Default**

**Type:** [DialogAlignment](../arkts-apis/arkts-arkui-dialogalignment-e.md)

**Default:** 
- API version 11+: DialogAlignment.Default

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the dialog box.

Default value: **BlurStyle.COMPONENT_ULTRA_THICK**

**NOTE:** 

Setting this parameter to **BlurStyle.NONE** disables the background blur. When **backgroundBlurStyle** is set to a value other than **NONE**, do not set **backgroundColor**. If you do, the color display may not produce the expected visual effect.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Options for customizing the background blur style.

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Backplane color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

When **backgroundColor** is set to a non-transparent color, **backgroundBlurStyle** must be set to **BlurStyle.NONE**; otherwise, the color display may not meet the expected effect.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Options for customizing the background effect.

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

Style of the cancel button.

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**.
If both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp and remains fixed even in accessibility and large-font modes.
In addition, even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop?: boolean
```

Whether to enable cyclic scrolling.

Default value: **true**

**NOTE:** 

**true**: Cyclic scrolling is enabled, where the year values increment or decrement with month cycling, and month values increment or decrement with day cycling.

**false**: Cyclic scrolling is disabled, preventing out-of-bounds scrolling in year, month, and day columns and cross-column value synchronization.

**Type:** boolean

**Default:** true

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dateTimeOptions

```TypeScript
dateTimeOptions?: DateTimeOptions
```

Whether to display a leading zero for the hours and minutes. Currently only the configuration of the **hour** and **minute** parameters is supported.

Default value:

**hour**: For the 24-hour format, the default value is **"2-digit"**, meaning the hour is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X". For the 12-hour format, the default value is **"numeric"**, meaning no leading zero.

**minute**: The default value is **"2-digit"**, meaning the minute is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X".

**Type:** [DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md)

**Default:** hour: In the 24-hour format, it defaults to 2-digit, which means a leading zero is used; <br>In the 12-hour format, it defaults to numeric, which means no leading zero is used. <br>minute: defaults to 2-digit, which means a leading zero is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: PickerTextStyle
```

Text color, font size, and font weight of edge items (the second item above or below the selected item).

Default value: { color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Default:** 
- API version 11+: { color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Whether to enable haptic feedback.

- **true**: Enable haptic feedback.  
- **false**: Disable haptic feedback.

Default value: **true**

**NOTE:** 

1. Whether this parameter takes effect after being set to **true** depends on hardware support.
2. To enable haptic feedback, you must declare the following permission under **requestPermissions** in **module**
in **src/main/module.json5** of the project:

"requestPermissions": [{"name": "ohos.permission.VIBRATE"}]

**Type:** boolean

**Default:** true

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond when the device is in semi-folded mode.

- **true**: Respond when the device is in semi-folded mode.  
- **false**: Do not respond when the device is in semi-folded mode.

Default value: **false**

**Type:** boolean

**Default:** false - meaning not to enable the hover mode.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Display area of the dialog box when the device is in semi-folded mode.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lunar

```TypeScript
lunar?: boolean
```

Whether to display dates in lunar calendar format.

- **true**: Display dates in lunar calendar format.  
- **false**: Do not display dates in lunar calendar format.

Default value: **false**

**NOTE:** 

This attribute takes effect only in Simplified Chinese and Traditional Chinese locales; it has no effect in other locales.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lunarSwitch

```TypeScript
lunarSwitch?: boolean
```

Whether to display the lunar calendar switch.

- **true**: Display the lunar calendar switch.  
- **false**: Do not display the lunar calendar switch.

Default value: **false**

**NOTE:** 

After being enabled, this attribute takes effect only in Simplified Chinese and Traditional Chinese; it has no effect in other locales. Therefore, you are advised to set this attribute to **false** in other locales.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lunarSwitchStyle

```TypeScript
lunarSwitchStyle?: LunarSwitchStyle
```

Style of the lunar calendar switch.

Default value: {

selectedColor: `$r('sys.color.ohos_id_color_text_primary_actived')`,

unselectedColor: `$r('sys.color.ohos_id_color_switch_outline_off')`,

strokeColor: Color.White

}

**Type:** [LunarSwitchStyle](arkts-arkui-datepicker-comp-lunarswitchstyle-i.md)

**Default:** { selectedColor: $r('sys.color.ohos_id_color_text_primary_actived'), unselectedColor: $r('sys.color.ohos_id_color_switch_outline_off'), strokeColor: Color.White }.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events outside the mask area are transparently transmitted, and events within the mask area are not.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**Type:** [Rectangle](arkts-arkui-common-comp-rectangle-i.md)

**Default:** 
- API version 11+: { x: 0, y: 0, width: '100%', height: '100%' }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog box based on the **alignment** settings.

Default value: **{ dx: 0 , dy: 0 }**

**Type:** Offset

**Default:** 
- API version 11+: { dx: 0 , dy: 0 }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDateAccept

```TypeScript
onDateAccept?: Callback<Date>
```

Callback invoked when the OK button in the dialog box is clicked.

**NOTE:** 

When **showTime** is set to **true**, the hour and minute in the value returned by the callback are the hour and minute selected in the picker. Otherwise, the hour and minute are the hour and minute of the system time.

**Type:** Callback&lt;Date&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDateChange

```TypeScript
onDateChange?: Callback<Date>
```

Callback triggered when date selection changes through scrolling in the dialog box.

**NOTE:** 

When **showTime** is set to **true**, the hour and minute in the value returned by the callback are the hour and minute selected in the picker. Otherwise, the hour and minute are the hour and minute of the system time.

**Type:** Callback&lt;Date&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: PickerTextStyle
```

Text color, font size, and font weight of the selected item.

Default value: { color: '#ff007dff', font: { size: '20vp', weight: FontWeight.Medium }

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Default:** 
- API version 11+: { color: '#ff007dff', font: { size: '20vp', weight: FontWeight.Medium }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box.

Default value on 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_MD** when the dialog box is focused and **ShadowStyle.OUTER_FLOATING_SM** otherwise

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showTime

```TypeScript
showTime?: boolean
```

Whether to display the time picker in the dialog box.

- **true**: Display the time picker.  
- **false**: Do not display the time picker.

Default value: **false**

**NOTE:** 

1. When showTime is true, clicking the date in the dialog box header toggles between date-only and date+time views.
2. When showTime is true, the mode parameter is ignored, meaning the date picker always shows year, month,
and day columns.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for dialog. Different materials have different effects, which can influence backgroundColor, border, shadow, and other visual attributes of dialog.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: PickerTextStyle
```

Text color, font size, and font weight of candidate items (the first item immediately above or below the selected item).

Default value: { color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Default:** 
- API version 11+: { color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

Whether the time picker in the dialog box is in 24-hour format. This parameter has effect only when **showTime** is **true**.

- **true**: 24-hour format.  
- **false**: 12-hour format.

Default value: **false**

**NOTE:** 

When 12-hour format is used in the time picker, the AM/PM indicator does not automatically update when the hour value changes.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
