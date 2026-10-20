# TimePickerDialogOptions

```TypeScript
declare interface TimePickerDialogOptions extends TimePickerOptions
```

Defines the configuration options of the time picker dialog box.

Inherited from [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md).

**Inheritance/Implementation:** TimePickerDialogOptions extends [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md)

**Since:** 8

<!--Device-unnamed-declare interface TimePickerDialogOptions extends TimePickerOptions--><!--Device-unnamed-declare interface TimePickerDialogOptions extends TimePickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: (value: TimePickerResult) => void
```

Callback invoked when the OK button in the dialog box is clicked. The callback parameter is the selected time value, which is of the **TimePickerResult** type.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-onAccept?: (value: TimePickerResult) => void--><!--Device-TimePickerDialogOptions-onAccept?: (value: TimePickerResult) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TimePickerResult](arkts-arkui-timepicker-comp-timepickerresult-i.md) | Yes |  |

## onCancel

```TypeScript
onCancel?: () => void
```

Callback invoked when the cancel button in the dialog box is clicked. This callback has no parameter.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-onCancel?: () => void--><!--Device-TimePickerDialogOptions-onCancel?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: TimePickerResult) => void
```

Triggered when the text picker in the dialog box snaps to the selected item. The callback parameter is the selected time value, which is of the **TimePickerResult** type.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-onChange?: (value: TimePickerResult) => void--><!--Device-TimePickerDialogOptions-onChange?: (value: TimePickerResult) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TimePickerResult](arkts-arkui-timepicker-comp-timepickerresult-i.md) | Yes |  |

## onDidAppear

```TypeScript
onDidAppear?: () => void
```

Event callback after the dialog box appears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange)

> onWillDisappear
> onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onDidAppear**. The settings
take effect next time the dialog box appears.
3. If the user closes the dialog box immediately after it appears, **onWillDisappear** is invoked before  
**onDidAppear**.
4. If the dialog box is closed before its entrance animation is finished, this callback is not invoked.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-onDidAppear?: () => void--><!--Device-TimePickerDialogOptions-onDidAppear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: () => void
```

Event callback after the dialog box disappears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange)

> onWillDisappear
> onDidDisappear.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-onDidDisappear?: () => void--><!--Device-TimePickerDialogOptions-onDidDisappear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

Event callback when the dialog box is about to appear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange)

> onWillDisappear
> onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onWillAppear**. The settings
take effect next time the dialog box appears.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-onWillAppear?: () => void--><!--Device-TimePickerDialogOptions-onWillAppear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

Event callback when the dialog box is about to disappear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange)

> onWillDisappear
> onDidDisappear.
2. If the user closes the dialog box immediately after it appears, **onWillDisappear** is invoked before  
**onDidAppear**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-onWillDisappear?: () => void--><!--Device-TimePickerDialogOptions-onWillDisappear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

Style of the accept button.

Default value: See [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md).

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**.
If both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp, and the unit of **borderRadius** is vp. The default button height remains
fixed even in accessibility and large-font modes. In addition, even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-TimePickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment mode of the dialog box in the vertical direction.

Default value: **DialogAlignment.Default**

**Type:** [DialogAlignment](../arkts-apis/arkts-arkui-dialogalignment-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-alignment?: DialogAlignment--><!--Device-TimePickerDialogOptions-alignment?: DialogAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the dialog box.

Default value: **BlurStyle.COMPONENT_ULTRA_THICK**

**NOTE:** 

1. Setting this parameter to **BlurStyle.NONE** disables the background blur. When **backgroundBlurStyle** is
set to a value other than **NONE**, do not set **backgroundColor**. If you do, the color display may not produce the expected visual effect.
2. Since API version 26.0.0, **backgroundBlurStyle** does not take effect after **systemMaterial** is set.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-TimePickerDialogOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur effect parameter, which is used to customize the display style of the pop-up window background blur. You can configure attributes such as the color mode, adaptive color, and zoom ratio to achieve different background blur effects.

**NOTE:** 

If this parameter is not set, the default effect of [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle) (**BlurStyle.COMPONENT_ULTRA_THICK**) is used.

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-TimePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-TimePickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Backplane color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

1. When **backgroundColor** is set to a non-transparent color, **backgroundBlurStyle** must be set to  
**BlurStyle.NONE**; otherwise, the color display may not meet the expected effect.
2. In 26.0.0 and later versions, the **backgroundColor** parameter does not take effect after  
**systemMaterial** is set.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-backgroundColor?: ResourceColor--><!--Device-TimePickerDialogOptions-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Background effect parameter, which is used to customize the display effect of the pop-up window background. You can configure attributes such as the blur radius, saturation, brightness, and color to achieve different background effects.

**NOTE:** 

If this parameter is not set, the setting does not take effect. In this case, the background blur effect of the dialog box is determined by [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle). If this parameter is set, the **backgroundBlurStyle** effect will be overwritten. From API version 26.0.0, after **systemMaterial** is set, neither **backgroundEffect** nor **backgroundBlurStyle** takes effect.

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-TimePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-TimePickerDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

Style of the cancel button.

Default value: See [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md).

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**.
If both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp, and the unit of **borderRadius** is vp. The default button height remains
fixed even in accessibility and large-font modes. In addition, even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-TimePickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dateTimeOptions

```TypeScript
dateTimeOptions?: DateTimeOptions
```

Whether to display leading zeros for the time. Currently, only the **hour** and **minute** parameters can be set. Setting other parameters does not take effect.

Default value:

**hour**: For the 24-hour format, the default value is **"2-digit"**, meaning the hour is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X". For the 12-hour format, the default value is **"numeric"**, meaning no leading zero.

**minute**: The default value is **"2-digit"**, meaning the minute is displayed as a two-digit number. If the actual value is less than 10, a leading zero is added, displayed as "0X".

**Type:** [DateTimeOptions](arkts-arkui-timepicker-comp-datetimeoptions-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-dateTimeOptions?: DateTimeOptions--><!--Device-TimePickerDialogOptions-dateTimeOptions?: DateTimeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: PickerTextStyle
```

Text color, font size, and font weight of edge items (the second item above or below the selected item).

Default value:

{

color: '#ff182431',

font: {

size: '14fp',

weight: FontWeight.Regular

}

}

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-disappearTextStyle?: PickerTextStyle--><!--Device-TimePickerDialogOptions-disappearTextStyle?: PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableCascade

```TypeScript
enableCascade?: boolean
```

Whether the AM/PM indicator automatically switches based on the hour value. Only takes effect when **useMilitaryTime** is set to **false**.

- **true**: The AM/PM indicator automatically switches based on the hour value.  
- **false**: The AM/PM indicator remains static regardless of hour changes.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerDialogOptions-enableCascade?: boolean--><!--Device-TimePickerDialogOptions-enableCascade?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Whether to enable haptic feedback.

- **true**: Enable haptic feedback.  
- **false**: Disable haptic feedback.

Default value: **true**.

**NOTE:** 

1. Whether this parameter takes effect after being set to **true** depends on hardware support.
2. To enable haptic feedback, you must declare the following permission under **requestPermissions** in  
**module** in **src/main/module.json5** of the project.

"requestPermissions": [{"name": "ohos.permission.VIBRATE"}]

**Type:** boolean

**Default:** true

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerDialogOptions-enableHapticFeedback?: boolean--><!--Device-TimePickerDialogOptions-enableHapticFeedback?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to enable the hover mode. The hover state refers to the interaction mode when a device such as a foldable device is in the hover and folded state, not the mouse hover state.

- **true**: Respond when the device is in semi-folded mode.  
- **false**: Do not respond when the device is in semi-folded mode.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TimePickerDialogOptions-enableHoverMode?: boolean--><!--Device-TimePickerDialogOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Display area of the dialog box in hover mode. This parameter is valid only when **enableHoverMode** is set to **true**.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TimePickerDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-TimePickerDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events outside the mask area are transparently transmitted, and events within the mask area are not.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**Type:** [Rectangle](arkts-arkui-common-comp-rectangle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-maskRect?: Rectangle--><!--Device-TimePickerDialogOptions-maskRect?: Rectangle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog box relative to the alignment position.

Default value: **{ dx: 0 , dy: 0 }**

Unit: vp

**Type:** Offset

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-offset?: Offset--><!--Device-TimePickerDialogOptions-offset?: Offset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea?: Callback<TimePickerResult>
```

Callback invoked when the sliding distance of the current column exceeds half of the height of the selected item and the item enters the selection zone during scrolling. The difference between this event and the **onChange** event is that this event is triggered in real time during the sliding, which is applicable to scenarios where a real-time listener is required. The **onChange** event is triggered after the item is moved back to the selected position, which is applicable to scenarios where the final selected value needs to be confirmed.

**NOTE:** 

When **enableCascade** is set to **true**, using this callback is not recommended due to the interdependent relationship between the AM/PM and hour columns. This callback indicates the moment an option enters the divider area during scrolling, and only the value of the currently scrolled column will change. The values of other non- scrolled columns will remain unchanged.

**Type:** Callback&lt;[TimePickerResult](arkts-arkui-timepicker-comp-timepickerresult-i.md)&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TimePickerDialogOptions-onEnterSelectedArea?: Callback<TimePickerResult>--><!--Device-TimePickerDialogOptions-onEnterSelectedArea?: Callback<TimePickerResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: PickerTextStyle
```

Font color, font size, and font weight of the selected item.

Default value:

{

color: '#ff007dff',

font: {

size: '20fp',

weight: FontWeight.Medium

}

}

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-selectedTextStyle?: PickerTextStyle--><!--Device-TimePickerDialogOptions-selectedTextStyle?: PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box.

Default value on 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_MD** when the dialog box is focused and **ShadowStyle.OUTER_FLOATING_SM** otherwise. On other devices, the dialog box has no shadow by default.

**NOTE:** 

In API version 26.0.0 and later, the **shadow** effect does not take effect after **systemMaterial** is set.

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TimePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-TimePickerDialogOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

System material of the dialog box.

**NOTE:** 

- Default value: [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md)  
object whose **style** in [ImmersiveOptions](../arkts-apis/arkts-arkui-uimaterial-immersiveoptions-i.md) is **ImmersiveStyle.ULTRA_THICK** If this parameter is set to **undefined**, the default value is used.  
- Different materials produce distinct effects. This API impacts the following attributes:[backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle), [backgroundEffect](arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect), [borderColor](arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](arkts-arkui-common-comp-commonmethod-c.md#borderwidth), and [shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow). When the system material is set, the aforementioned attributes do not take effect.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TimePickerDialogOptions-systemMaterial?: SystemUiMaterial--><!--Device-TimePickerDialogOptions-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: PickerTextStyle
```

Text color, font size, and font weight of candidate items (the first item immediately above or below the selected item).

Default value:

{

color: '#ff182431',

font: {

size: '16fp',

weight: FontWeight.Regular

}

}

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-textStyle?: PickerTextStyle--><!--Device-TimePickerDialogOptions-textStyle?: PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

Whether to display the time in 24-hour format or 12-hour format.

- **true**: 24-hour format.  
- **false**: 12-hour format.

Default value: **false**.

**Note:**  The enableCascade parameter takes effect only when this parameter is set to false.

**Type:** boolean

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerDialogOptions-useMilitaryTime?: boolean--><!--Device-TimePickerDialogOptions-useMilitaryTime?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
