# DatePickerDialogOptions

```TypeScript
declare interface DatePickerDialogOptions extends DatePickerOptions
```

Defines the configuration options of the date picker dialog box.

Inherited from [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md).

**Inheritance/Implementation:** DatePickerDialogOptions extends [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md)

**Since:** 8

<!--Device-unnamed-declare interface DatePickerDialogOptions extends DatePickerOptions--><!--Device-unnamed-declare interface DatePickerDialogOptions extends DatePickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: VoidCallback
```

Triggered when the "Cancel" button in the dialog box is tapped. Callback signature: () =&gt; void, with no parameters and no return value.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-onCancel?: VoidCallback--><!--Device-DatePickerDialogOptions-onCancel?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

Event callback after the dialog box is displayed.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;>
(**onDateAccept**\/**onCancel**\/**onDateChange**) &gt;  
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. Callback events that change the display effect of the dialog box set in **onDidAppear** take effect the next
time **showDatePickerDialog** is called.
3. When the dialog box is rapidly and consecutively triggered to pop up and close, **onWillDisappear** may take
effect before **onDidAppear**.
4. When the dialog box is closed before its entrance animation is complete, this callback is not triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-onDidAppear?: VoidCallback--><!--Device-DatePickerDialogOptions-onDidAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

Event callback after the dialog box disappears.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> (onDateAccept/onCancel/onDateChange)
> 
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. When the dialog box is rapidly and consecutively triggered to pop up and close, **onWillDisappear** may take
effect before **onDidAppear**.
3. When the dialog box is closed before its entrance animation is complete, this callback is not triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-onDidDisappear?: VoidCallback--><!--Device-DatePickerDialogOptions-onDidDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

Event callback before the dialog box display animation.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> (onDateAccept/onCancel/onDateChange)
> 
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. Callback events that change the display effect of the dialog box set in **onWillAppear** take effect the next
time **showDatePickerDialog** is called.
3. When the dialog box is rapidly and consecutively triggered to pop up and close, **onWillDisappear** may take
effect before **onDidAppear**.
4. When the dialog box is closed before its entrance animation is complete, **onDidAppear** and subsequent
callbacks are not triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-onWillAppear?: VoidCallback--><!--Device-DatePickerDialogOptions-onWillAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

Event callback before the dialog box exit animation.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> (onDateAccept/onCancel/onDateChange)
> 
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. When the dialog box is rapidly and consecutively triggered to pop up and close, **onWillDisappear** may take
effect before **onDidAppear**.
3. When the dialog box is closed before its entrance animation is complete, this callback is not triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-onWillDisappear?: VoidCallback--><!--Device-DatePickerDialogOptions-onWillDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: (value: DatePickerResult) => void
```

Triggered when the "OK" button in the dialog box is tapped. The callback parameter value is the currently selected date, including the year, month, and day.

**NOTE:** 

Supported since API version 8 and deprecated since API version 10. Use **onDateAccept** instead.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** onDateAccept

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DatePickerDialogOptions-onAccept?: (value: DatePickerResult) => void--><!--Device-DatePickerDialogOptions-onAccept?: (value: DatePickerResult) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DatePickerResult](arkts-arkui-datepicker-comp-datepickerresult-i.md) | Yes |  |

## onChange

```TypeScript
onChange?: (value: DatePickerResult) => void
```

Triggered when the current selected item changes as the sliding picker in the dialog box is swiped. The callback parameter value is the currently selected date, including the year, month, and day.

**NOTE:** 

Supported since API version 8 and deprecated since API version 10. Use onDateChange instead.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** onDateChange

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DatePickerDialogOptions-onChange?: (value: DatePickerResult) => void--><!--Device-DatePickerDialogOptions-onChange?: (value: DatePickerResult) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DatePickerResult](arkts-arkui-datepicker-comp-datepickerresult-i.md) | Yes |  |

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

Display style, importance, role, background color, corner radius, text color, font size, font weight, font style, font list, and whether the button responds to the Enter key by default for the confirm button. Pass this parameter when you need to customize the appearance or behavior of the confirm button. If not passed, the system default button style is used.

**NOTE:** 

1. At most one of **acceptButtonStyle** and **cancelButtonStyle** can have the **primary** field set to **true**.
If both are set to **true**, the **primary** field does not take effect and remains at the default value **false**.
2. The button height is 40 vp by default and does not change in the care mode - large font scenario. Even if the
button style is set to the rounded rectangle ROUNDED_RECTANGLE, the button is still displayed as a capsule button Capsule.

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-DatePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment of the dialog box in the vertical direction.

Default value: **DialogAlignment.Default**

**Type:** [DialogAlignment](../arkts-apis/arkts-arkui-dialogalignment-e.md)

**Default:** 
- API version 11+: DialogAlignment.Default

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-alignment?: DialogAlignment--><!--Device-DatePickerDialogOptions-alignment?: DialogAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur material of the dialog box.

Default value: **BlurStyle.COMPONENT_ULTRA_THICK**

**NOTE:** 

Set this parameter to **BlurStyle.NONE** to disable the background blur. When **backgroundBlurStyle** is set to a value other than NONE, do not set **backgroundColor**. Otherwise, the displayed color will not meet the expected effect.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-DatePickerDialogOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur effect parameters, used to customize the display style of the dialog box background blur. It supports configuring attributes such as the color mode, adaptive color, and scale ratio to achieve different background blur visual effects. For the default value, see the **BackgroundBlurStyleOptions** type description.

**NOTE:** 

When not set, the default effect of **backgroundBlurStyle (BlurStyle.COMPONENT_ULTRA_THICK)** is used.

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-DatePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-DatePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

When **backgroundColor** is set to a non-transparent color, **backgroundBlurStyle** must be set to **BlurStyle.NONE**. Otherwise, the displayed color will not meet the expected effect.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-backgroundColor?: ResourceColor--><!--Device-DatePickerDialogOptions-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Background effect parameters, used to customize the display effect of the dialog box background. It supports configuring attributes such as the blur radius, saturation, brightness, and color to achieve different background visual effects. For the default value, see the **BackgroundEffectOptions** type description.

**NOTE:** 

When not set, this parameter does not take effect, and the dialog box background blur effect is determined by **backgroundBlurStyle**. When set, it overrides the effect of **backgroundBlurStyle**. Since API version 26.0.0, after **systemMaterial** is set, neither **backgroundEffect** nor **backgroundBlurStyle** takes effect.

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-DatePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-DatePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

Display style, importance, role, background color, corner radius, text color, font size, font weight, font style, font list, and whether the button responds to the Enter key by default for the cancel button. Pass this parameter when you need to customize the appearance or behavior of the cancel button. If not passed, the system default button style is used.

**NOTE:** 

1. At most one of **acceptButtonStyle** and **cancelButtonStyle** can have the **primary** field set to **true**.
If both are set to **true**, the **primary** field does not take effect and remains at the default value **false**.
2. The button height is 40 vp by default and does not change in the care mode - large font scenario. Even if the
button style is set to the rounded rectangle ROUNDED_RECTANGLE, the button is still displayed as a capsule button Capsule.

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-DatePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop?: boolean
```

Whether cyclic scrolling is supported.

- **true**: cyclic scrolling is supported. The year is linked and incremented or decremented as the month scrolls  
cyclically, and the month is linked and incremented or decremented as the day scrolls cyclically.  
- **false**: cyclic scrolling is not supported. When the year, month, or day reaches the top or bottom of its  
column, it can no longer be scrolled, and the year, month, and day can no longer be linked and incremented or decremented.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DatePickerDialogOptions-canLoop?: boolean--><!--Device-DatePickerDialogOptions-canLoop?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dateTimeOptions

```TypeScript
dateTimeOptions?: DateTimeOptions
```

Whether the hour and minute are displayed with a leading zero. Currently, only the hour and minute parameters are supported, and this parameter takes effect only when **showTime** is **true**.

Default value:

**hour**: The default value is "2-digit" in the 24-hour format. Sets whether the hour is displayed as two digits. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". The default value is "numeric" in the 12-hour format, that is, no leading zero. The optional values are "numeric" or "2-digit". Ifanother value is passed, the default value is used.

**minute**: The default value is "2-digit". Sets whether the minute is displayed as two digits. If the actual value is less than 10, a leading zero is added and displayed, that is, "0X". The optional values are "numeric" or "2- digit". If another value is passed, the default value is used.

**Type:** [DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md)

**Default:** hour: In the 24-hour format, it defaults to 2-digit, which means a leading zero is used; <br>In the 12-hour format, it defaults to numeric, which means no leading zero is used. <br>minute: defaults to 2-digit, which means a leading zero is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-dateTimeOptions?: DateTimeOptions--><!--Device-DatePickerDialogOptions-dateTimeOptions?: DateTimeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: PickerTextStyle
```

The text color, font size, and font weight of the edge items (the second item above or below the selected item).

Default value:

**{

color: '#ff182431',

font: {

size: '14fp',

weight: FontWeight.Regular

}

}**

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Default:** 
- API version 11+: { color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-disappearTextStyle?: PickerTextStyle--><!--Device-DatePickerDialogOptions-disappearTextStyle?: PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Whether to enable touch feedback.

- **true**: enable touch feedback (select this when you need to provide operation feedback to users).  
- **false**: disable touch feedback (select this when touch feedback is not needed or the device does not support  
it).

Default value: **true**

**NOTE:** 

1. After this parameter is set to **true**, whether it takes effect depends on whether the system hardware
supports it.
2. To enable touch feedback, configure the **requestPermissions** field in the "module" of the  
**src/main/module.json5** file of the project to enable the vibration permission. The configuration is as follows:

"requestPermissions": [{"name": "ohos.permission.VIBRATE"}]

**Type:** boolean

**Default:** true

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerDialogOptions-enableHapticFeedback?: boolean--><!--Device-DatePickerDialogOptions-enableHapticFeedback?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond to the hover state. The hover state refers to the interaction mode when devices such as foldable devices are in the hover folded state, rather than mouse hover.

- true: respond to the hover state.  
- **false**: do not respond to the hover state.

Default value: **false**

**Type:** boolean

**Default:** false - meaning not to enable the hover mode.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-DatePickerDialogOptions-enableHoverMode?: boolean--><!--Device-DatePickerDialogOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Default display area of the dialog box in the hover state. This parameter takes effect only when **enableHoverMode** is **true**.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-DatePickerDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-DatePickerDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lunar

```TypeScript
lunar?: boolean
```

Whether the date is displayed in the lunar calendar.

- **true**: displayed in the lunar calendar.  
- **false**: not displayed in the lunar calendar.

Default value: **false**

**NOTE:** 

This attribute takes effect only in the Simplified Chinese and Traditional Chinese language environments. In other language environments, setting this attribute has no effect.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-lunar?: boolean--><!--Device-DatePickerDialogOptions-lunar?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lunarSwitch

```TypeScript
lunarSwitch?: boolean
```

Whether to display the switch for switching to the lunar calendar.

- **true**: display the switch for switching to the lunar calendar.  
- **false**: do not display the switch for switching to the lunar calendar.

Default value: **false**

**NOTE:** 

After the switch is turned on, it takes effect only in the Simplified Chinese and Traditional Chinese environments. In other language environments, the lunar calendar does not take effect. Therefore, it is recommended that the switch not be displayed in other language environments.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-lunarSwitch?: boolean--><!--Device-DatePickerDialogOptions-lunarSwitch?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lunarSwitchStyle

```TypeScript
lunarSwitchStyle?: LunarSwitchStyle
```

Color style of the lunar calendar switch. This parameter takes effect only when **lunarSwitch** is **true**.

Default value: **{

selectedColor: `$r('sys.color.ohos_id_color_text_primary_actived')`,

unselectedColor: `$r('sys.color.ohos_id_color_switch_outline_off')`,

strokeColor: Color.White

}**

**Type:** [LunarSwitchStyle](arkts-arkui-datepicker-comp-lunarswitchstyle-i.md)

**Default:** { selectedColor: $r('sys.color.ohos_id_color_text_primary_actived'), unselectedColor: $r('sys.color.ohos_id_color_switch_outline_off'), strokeColor: Color.White }.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-DatePickerDialogOptions-lunarSwitchStyle?: LunarSwitchStyle--><!--Device-DatePickerDialogOptions-lunarSwitchStyle?: LunarSwitchStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events within the mask area are not passed through, while events outside the mask area are passed through.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**Type:** [Rectangle](arkts-arkui-common-comp-rectangle-i.md)

**Default:** 
- API version 11+: { x: 0, y: 0, width: '100%', height: '100%' }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-maskRect?: Rectangle--><!--Device-DatePickerDialogOptions-maskRect?: Rectangle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog box relative to the position specified by alignment. Set this parameter when you need to fine- tune the position of the dialog box (for example, to achieve precise position control together with alignment). If not set, the dialog box is displayed at the position aligned by alignment.

Default value: **{ dx: 0 , dy: 0 }**

**Type:** Offset

**Default:** 
- API version 11+: { dx: 0 , dy: 0 }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-offset?: Offset--><!--Device-DatePickerDialogOptions-offset?: Offset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDateAccept

```TypeScript
onDateAccept?: Callback<Date>
```

Triggered when the "OK" button in the dialog box is tapped. Callback signature: **(value: Date) =&gt; void**, where **value** is the date selected by the user, including the year, month, and day. When **showTime** is true, it also includes the hour and minute. Developers can save the date selected by the user or execute subsequent business logic in this callback.

**NOTE:** 

When **showTime** is set to **true**, the hour and minute in **value** are those selected by the picker. Otherwise, the hour and minute in **value** are those of the system time.

**Type:** Callback&lt;Date&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-onDateAccept?: Callback<Date>--><!--Device-DatePickerDialogOptions-onDateAccept?: Callback<Date>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDateChange

```TypeScript
onDateChange?: Callback<Date>
```

Triggered when the current selected item changes as the date in the dialog box is swiped. Callback signature: **(value: Date) =&gt; void**, where **value** is the currently selected date, including the year, month, and day. When **showTime** is **true**, it also includes the hour and minute. This callback is triggered in real time while the user swipes the picker, which differs from **onDateAccept**, which is triggered only after the OK button is tapped.

**NOTE:** 

When **showTime** is set to **true**, the hour and minute in value are those selected by the picker. Otherwise, the hour and minute in value are those of the system time.

**Type:** Callback&lt;Date&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-onDateChange?: Callback<Date>--><!--Device-DatePickerDialogOptions-onDateChange?: Callback<Date>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: PickerTextStyle
```

Text color, font size, and font weight of the selected item.

Default value:

**{

color: '#ff007dff',

font: {

size: '20fp',

weight: FontWeight.Medium

}

}**

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Default:** 
- API version 11+: { color: '#ff007dff', font: { size: '20vp', weight: FontWeight.Medium }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-selectedTextStyle?: PickerTextStyle--><!--Device-DatePickerDialogOptions-selectedTextStyle?: PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box background.

On 2-in-1 devices, in the default scenario, the focused shadow value is **ShadowStyle.OUTER_FLOATING_MD**, and the unfocused shadow value is **ShadowStyle.OUTER_FLOATING_SM**. Other devices have no shadow by default.

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DatePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-DatePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showTime

```TypeScript
showTime?: boolean
```

Whether to display the time picker in the dialog box.

- **true**: display the time picker.  
- **false**: do not display the time picker.

Default value: **false**

**NOTE:** 

1. When **showTime** is true, tapping the title date of the dialog box switches between the "date picker" and
"date picker + time picker" pages.
2. When **showTime** is **true**, the mode parameter does not take effect, and the date-only page always displays
the year, month, and day columns.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-showTime?: boolean--><!--Device-DatePickerDialogOptions-showTime?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

System material of the dialog box.

**NOTE:** 

- The default value is an **ImmersiveMaterial** object whose style of **ImmersiveOptions** is  
**ImmersiveStyle.ULTRA_THICK**. When set to **undefined**, it is consistent with the default value. Different materials have different effects. For details about **ImmersiveMaterial**, see the [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md) type definition.  
- This interface affects the background color [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), background blur [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle), background blur effect [backgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md), background effect [backgroundEffect](arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect), border color [borderColor](arkts-arkui-common-comp-commonmethod-c.md#bordercolor), border width [borderWidth](arkts-arkui-common-comp-commonmethod-c.md#borderwidth), and shadow [shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow). When the system material is set, the preceding interfaces do not take effect.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerDialogOptions-systemMaterial?: SystemUiMaterial--><!--Device-DatePickerDialogOptions-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: PickerTextStyle
```

Text color, font size, and font weight of the candidate items (the first item above or below the selected item).

Default value:

**{

color: '#ff182431',

font: {

size: '16fp',

weight: FontWeight.Regular

}

}**

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Default:** 
- API version 11+: { color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-textStyle?: PickerTextStyle--><!--Device-DatePickerDialogOptions-textStyle?: PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

Whether the time picker displayed in the dialog box uses the 24-hour format. This parameter takes effect only when **showTime** is **true**.

- true: display the 24-hour format.  
- false: display the 12-hour format.

Default value: **false**

**NOTE:** 

When the displayed time picker uses the 12-hour format, the AM and PM indicators do not switch automatically based on the hour.

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerDialogOptions-useMilitaryTime?: boolean--><!--Device-DatePickerDialogOptions-useMilitaryTime?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
