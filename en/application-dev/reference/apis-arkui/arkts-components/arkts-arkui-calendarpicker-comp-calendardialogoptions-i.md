# CalendarDialogOptions

```TypeScript
declare interface CalendarDialogOptions extends CalendarOptions
```

Defines the configuration options of the calendar picker dialog box.

Inherits from [CalendarOptions](arkts-arkui-calendarpicker-comp-calendaroptions-i.md).

> **NOTE:** 
> 
> When the application window is resized, the width of the dialog box is continuously compressed. If the window width
> is reduced below a certain threshold, the content of the dialog box may not be fully visible. To ensure that the
> content of the **CalendarPickerDialog** component is fully displayed, the minimum window width required is 386 vp.

**Inheritance/Implementation:** CalendarDialogOptions extends [CalendarOptions](arkts-arkui-calendarpicker-comp-calendaroptions-i.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: VoidCallback
```

Triggered when the Cancel button in the dialog box is clicked.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

Event callback after the dialog box appears.

**NOTE:** 

1. The normal timing sequence is as follows:
onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange) &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onDidAppear**.
The settings take effect next time the dialog box appears.
3. If the user dismisses the dialog box immediately after it appears,  
**onWillDisappear** is invoked before **onDidAppear**.
4. If the dialog box is dismissed before its entrance animation is finished, this callback is not invoked.

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

1. The normal timing sequence is as follows:
onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange) &gt; onWillDisappear &gt; onDidDisappear.

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

1. The normal timing sequence is as follows:
onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange) &gt; onWillDisappear &gt; onDidDisappear.
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

1. The normal timing sequence is as follows:
onWillAppear &gt; onDidAppear &gt; (onAccept/onCancel/onChange) &gt; onWillDisappear &gt; onDidDisappear.
2. If the user closes the dialog box immediately after it appears,  
**onWillDisappear** is invoked before **onDidAppear**.

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

In the **acceptButtonStyle** and **cancelButtonStyle** configurations, only one **primary** field can be set to **true** at most. If both the **primary** fields are set to **true**, neither will take effect.

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

In the **acceptButtonStyle** and **cancelButtonStyle** configurations, only one **primary** field can be set to **true** at most. If both the **primary** fields are set to **true**, neither will take effect.

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond when the device is in semi-folded mode.

- **true**: Respond when the device is in semi-folded mode.  
- **false**: Do not respond when the device is in semi-folded mode.

Default value: **false**.

**Type:** boolean

**Default:** false

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

## markToday

```TypeScript
markToday?: boolean
```

Whether to highlight the current system date.

- **true**: Highlight the current system date.  
- **false**: Do not highlight the current system date.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: Callback<Date>
```

Triggered when the OK button in the dialog box is clicked.

The callback parameter represents the selected date value.

**Type:** Callback&lt;Date&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Date>
```

Triggered when the selection in the picker changes the selected date.

The callback parameter represents the selected date value.

**Type:** Callback&lt;Date&gt;

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
