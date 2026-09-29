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

<!--Device-unnamed-declare interface CalendarDialogOptions extends CalendarOptions--><!--Device-unnamed-declare interface CalendarDialogOptions extends CalendarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: VoidCallback
```

Callback invoked when the **Cancel** button in the dialog box is tapped.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CalendarDialogOptions-onCancel?: VoidCallback--><!--Device-CalendarDialogOptions-onCancel?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

Event callback after the dialog box is shown.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> (onAccept/onCancel/onChange) &gt;>
**onWillDisappear** &gt;  
> **onDidDisappear**.
2. Callback events that change the display effect set in **onDidAppear** take effect when **show** is called
again.
3. When the dialog box is rapidly and consecutively triggered to pop up and close, **onWillDisappear** may
take effect before **onDidAppear**.
4. When the dialog box is closed before its entrance animation is complete, this callback is not triggered.

**Selection guidance:**

- **onWillAppear**: suitable for preparing data and resetting the state before the dialog box is displayed.  
- **onDidAppear**: suitable for performing animations, initiating network requests, and setting focus after the  
dialog box is fully displayed, that is, operations that require the dialog box to be visible.  
- **onWillDisappear**: suitable for saving data, cleaning up resources, and canceling network requests before the  
dialog box disappears.  
- **onDidDisappear**: suitable for performing cleanup, resetting the state, and restoring other UI after the dialog  
box fully disappears.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-onDidAppear?: VoidCallback--><!--Device-CalendarDialogOptions-onDidAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

Event callback after the dialog box disappears.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> (onAccept/onCancel/onChange) &gt;>
**onWillDisappear** &gt;  
> **onDidDisappear**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-onDidDisappear?: VoidCallback--><!--Device-CalendarDialogOptions-onDidDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

Event callback before the dialog box display animation.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> (onAccept/onCancel/onChange) &gt;>
**onWillDisappear** &gt;  
> **onDidDisappear**.
2. Callback events that change the dialog box display effect set in **onWillAppear** take effect when the
dialog box is shown again.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-onWillAppear?: VoidCallback--><!--Device-CalendarDialogOptions-onWillAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

Event callback before the dialog box exit animation.

**NOTE:** 

1. The normal timing sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;>
(**onAccept**\/**onCancel**\/**onChange**) &gt;  
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. When the dialog box is rapidly and consecutively triggered to pop up and close, **onWillDisappear** may
take effect before **onDidAppear**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-onWillDisappear?: VoidCallback--><!--Device-CalendarDialogOptions-onWillDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

Display style, importance, role, background color, corner radius, text color, font size, font weight, font style, font list, and whether the button responds to the Enter key by default for the confirm button.

**NOTE:** 

1. At most one of **acceptButtonStyle** and **cancelButtonStyle** can have the **primary** field set to **true**.
If both are set to **true**, neither takes effect.
2. The button height is 40 vp by default and does not change in the care mode - large font scenario. Even if
the button style is set to the rounded rectangle ROUNDED_RECTANGLE, in the care mode - large font scenario the button is still displayed as a capsule button Capsule.

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-CalendarDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur material of the dialog box.

Default value: **BlurStyle.COMPONENT_ULTRA_THICK**

**NOTE:** 

Set this parameter to **BlurStyle.NONE** to disable the background blur. When **backgroundBlurStyle** is set to a value other than NONE, do not set **backgroundColor**. Otherwise, the displayed background color will not meet the expected effect. When **backgroundEffect** is set, it overrides the effect of this attribute.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-CalendarDialogOptions-backgroundBlurStyle?: BlurStyle-End-->

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

<!--Device-CalendarDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-CalendarDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

When **backgroundColor** is set to a non-transparent color, **backgroundBlurStyle** must be set to **BlurStyle.NONE**. Otherwise, the displayed background color will not meet the expected effect.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-backgroundColor?: ResourceColor--><!--Device-CalendarDialogOptions-backgroundColor?: ResourceColor-End-->

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

<!--Device-CalendarDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-CalendarDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

Display style, importance, role, background color, corner radius, text color, font size, font weight, font style, font list, and whether the button responds to the Enter key by default for the cancel button.

**NOTE:** 

1. At most one of **acceptButtonStyle** and **cancelButtonStyle** can have the **primary** field set to **true**.
If both are set to **true**, neither takes effect.
2. The button height is 40 vp by default and does not change in the care mode - large font scenario. Even if
the button style is set to the rounded rectangle ROUNDED_RECTANGLE, in the care mode - large font scenario the button is still displayed as a capsule button Capsule.

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-CalendarDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether the dialog box responds to the hover mode. This parameter applies to devices that support the hover mode, such as foldable devices.

- **true**: The dialog box responds to the hover mode. In the hover mode of foldable devices, the layout area is  
adaptively adjusted to provide a better multitasking experience.  
- **false**: The dialog box does not respond to the hover mode, and the default layout is retained in the hover  
mode.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-CalendarDialogOptions-enableHoverMode?: boolean--><!--Device-CalendarDialogOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Default display area of the dialog box in the hover mode. This parameter takes effect only when **enableHoverMode** is **true**. Different area values correspond to different layout positions of the dialog box in the hover mode of foldable devices (for example, **BOTTOM_SCREEN** indicates that the dialog box is displayed in the lower half of the screen, and **TOP_SCREEN** indicates that the dialog box is displayed in the upper half of the screen).

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-CalendarDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-CalendarDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## markToday

```TypeScript
markToday?: boolean
```

Whether the current system date remains highlighted in the calendar picker dialog box.

- **true**: The current system date remains highlighted in the calendar picker dialog box.  
- **false**: The current system date is not highlighted in the calendar picker dialog box.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CalendarDialogOptions-markToday?: boolean--><!--Device-CalendarDialogOptions-markToday?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: Callback<Date>
```

Callback invoked when the **OK** button in the dialog box is tapped.

The parameter of the callback indicates the selected date.

**Type:** Callback&lt;Date&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CalendarDialogOptions-onAccept?: Callback<Date>--><!--Device-CalendarDialogOptions-onAccept?: Callback<Date>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<Date>
```

Callback invoked when the selected date in the dialog box changes.

The parameter of the callback indicates the selected date.

**Type:** Callback&lt;Date&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CalendarDialogOptions-onChange?: Callback<Date>--><!--Device-CalendarDialogOptions-onChange?: Callback<Date>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box background.

On 2-in-1 devices, in the default scenario, the focused shadow value is **ShadowStyle.OUTER_FLOATING_MD**, and the unfocused shadow value is **ShadowStyle.OUTER_FLOATING_SM**.

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CalendarDialogOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-CalendarDialogOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

System material of the dialog box.

**NOTE:** 

- Default value: the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md)  
object whose [ImmersiveOptions](../arkts-apis/arkts-arkui-uimaterial-immersiveoptions-i.md) style is **ImmersiveStyle.ULTRA_THICK**. When set to **undefined**, it is consistent with the default value.  
- Different materials have different visual effects, including differences in background transparency, blur degree,  
and shadow style. This API affects the background color [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), background blur [backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle), background effect [backgroundEffect](arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect), border color [borderColor](arkts-arkui-common-comp-commonmethod-c.md#bordercolor), border width [borderWidth](arkts-arkui-common-comp-commonmethod-c.md#borderwidth), and shadow [shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow). When the system material is set, the preceding APIs do not take effect.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CalendarDialogOptions-systemMaterial?: SystemUiMaterial--><!--Device-CalendarDialogOptions-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
