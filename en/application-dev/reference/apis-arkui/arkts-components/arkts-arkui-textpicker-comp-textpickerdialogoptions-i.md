# TextPickerDialogOptions

```TypeScript
declare interface TextPickerDialogOptions extends TextPickerOptions
```

Inherits from [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md).

**Inheritance/Implementation:** TextPickerDialogOptions extends [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md)

**Since:** 8

<!--Device-unnamed-declare interface TextPickerDialogOptions extends TextPickerOptions--><!--Device-unnamed-declare interface TextPickerDialogOptions extends TextPickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: (value: TextPickerResult) => void
```

Triggered when the OK button in the dialog box is clicked.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-onAccept?: (value: TextPickerResult) => void--><!--Device-TextPickerDialogOptions-onAccept?: (value: TextPickerResult) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md) | Yes |  |

## onCancel

```TypeScript
onCancel?: () => void
```

Triggered when the Cancel button in the dialog box is clicked.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-onCancel?: () => void--><!--Device-TextPickerDialogOptions-onCancel?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: TextPickerResult) => void
```

Callback Triggered when the text picker in the dialog box snaps to the selected item. This callback is used to obtain the final selection result.

This callback is triggered only after the scroll animation completes. To obtain real-time index changes, use **onEnterSelectedArea** instead.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-onChange?: (value: TextPickerResult) => void--><!--Device-TextPickerDialogOptions-onChange?: (value: TextPickerResult) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md) | Yes |  |

## onDidAppear

```TypeScript
onDidAppear?: () => void
```

Event callback after the dialog box appears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt;
(onAccept/onCancel/onChange/onScrollStop) &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onDidAppear**. The settings take
effect next time the dialog box appears.
3. If you quickly tap to display and then close a dialog box, the **onWillDisappear** callback may take effect
before the **onDidAppear** callback. In this case, the parameter settings in **onDidAppear** may not take effect in the current dialog box.
4. If the dialog box is closed before its entrance animation is finished, this callback is not invoked.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-onDidAppear?: () => void--><!--Device-TextPickerDialogOptions-onDidAppear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: () => void
```

Event callback after the dialog box disappears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt;
(onAccept/onCancel/onChange/onScrollStop) &gt; onWillDisappear &gt; onDidDisappear.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-onDidDisappear?: () => void--><!--Device-TextPickerDialogOptions-onDidDisappear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: () => void
```

Event callback when the dialog box is about to appear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt;
(onAccept/onCancel/onChange/onScrollStop) &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onWillAppear**. The settings take
effect next time the dialog box appears.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-onWillAppear?: () => void--><!--Device-TextPickerDialogOptions-onWillAppear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: () => void
```

Event callback when the dialog box is about to disappear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt;
(onAccept/onCancel/onChange/onScrollStop) &gt; onWillDisappear &gt; onDidDisappear.
2. If the user closes the dialog box immediately after it appears, **onWillDisappear** is invoked before  
**onDidAppear**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-onWillDisappear?: () => void--><!--Device-TextPickerDialogOptions-onWillDisappear?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

Style of the accept button.

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**. If
both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp, and the unit of **borderRadius** is vp. The default button height remains
fixed even in accessibility and large-font modes. In addition, even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-TextPickerDialogOptions-acceptButtonStyle?: PickerDialogButtonStyle-End-->

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

<!--Device-TextPickerDialogOptions-alignment?: DialogAlignment--><!--Device-TextPickerDialogOptions-alignment?: DialogAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the dialog box.

Default value: **BlurStyle.COMPONENT_ULTRA_THICK**

**NOTE:** 

1. Setting this parameter to **BlurStyle.NONE** disables the background blur. When **backgroundBlurStyle** is set
to a value other than **NONE**, do not set **backgroundColor**. If you do, the color display may not produce the expected visual effect.
2. Since API version 26.0.0, this attribute does not take effect after **systemMaterial** is set.

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-backgroundBlurStyle?: BlurStyle--><!--Device-TextPickerDialogOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur effect parameters, which are used to customize the display style of the pop-up window background blur. You can configure attributes such as the color mode, adaptive color, and zoom ratio to achieve different background blur visual effects.

**NOTE:** 

If this attribute is not set, the default effect of **BlurStyle.COMPONENT_ULTRA_THICK** is used. If this attribute is set, the effect of **backgroundBlurStyle** will be overwritten.

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-TextPickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-TextPickerDialogOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Backplane color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

1. If you set **backgroundColor** to a non-transparent color, set **backgroundBlurStyle** to  
**BlurStyle.NONE.** Do not set **backgroundBlurStyle** to a value other than **NONE**. Otherwise, the displayed color will not meet the expected effect.
2. Since API version 26.0.0, this attribute does not take effect after **systemMaterial** is set.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-backgroundColor?: ResourceColor--><!--Device-TextPickerDialogOptions-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Background effect parameters, which are used to customize the display effect of the dialog box background. You can configure attributes such as the blur radius, saturation, brightness, and color to achieve different background visual effects.

**NOTE:** 

If this parameter is not set, the blur effect of the pop-up window background is determined by the value of **backgroundBlurStyle**. If this parameter is set, the value of **backgroundBlurStyle** will be overridden. Since API version 26.0.0, **backgroundEffect** and **backgroundBlurStyle** do not take effect after **systemMaterial** is set.

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-TextPickerDialogOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-TextPickerDialogOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

Style of the cancel button.

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**. If
both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp, and the unit of **borderRadius** is vp. The default button height remains
fixed even in accessibility and large-font modes. In addition, even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextPickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-TextPickerDialogOptions-cancelButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop?: boolean
```

Whether to enable loop scrolling.

- **true**: Enable loop scrolling.  
- **false**: Disable loop scrolling.

Default value: **true**.

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-canLoop?: boolean--><!--Device-TextPickerDialogOptions-canLoop?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight?: number | string
```

Height of the picker item. The value is of the number type, ranging from [0, +∞). The default unit is vp. The default value is 56 vp for the selected item and 36 vp for the unselected item. The set value applies to both selected and unselected items. String type: numeric string only, for example, **"56"**.

**NOTE:** 

If the value of **defaultPickerItemHeight** is a negative number, the default value is used.

**Type:** number &#124; string

**Default:** 
- API version 11+: 56 vp (selected) and 36 vp (unselected)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-defaultPickerItemHeight?: number | string--><!--Device-TextPickerDialogOptions-defaultPickerItemHeight?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultTextStyle

```TypeScript
defaultTextStyle?: TextPickerTextStyle
```

Style of the text items when the text style change animation during the scrolling process is disabled. It is effective only when **disableTextStyleAnimation** is **true**.

Default value: same as the default value of the [Text](arkts-arkui-text-comp.md) component

**Type:** [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextPickerDialogOptions-defaultTextStyle?: TextPickerTextStyle--><!--Device-TextPickerDialogOptions-defaultTextStyle?: TextPickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableTextStyleAnimation

```TypeScript
disableTextStyleAnimation?: boolean
```

Whether to disable the animation effect of text style changes during scrolling.

- **true**: Disable the animation effect of text style changes.  
- **false**: Do not disable the animation effect of text style changes.

Default value: **false**.

**NOTE:** 

When this API is used with **true**, there are no text style changes, including the font size, weight, and color, during scrolling, and all text is displayed in the style set by **defaultTextStyle**. If **defaultTextStyle** is not set, the default style of the [Text](arkts-arkui-text-comp.md) component is used.

**Type:** boolean

**Default:** false

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextPickerDialogOptions-disableTextStyleAnimation?: boolean--><!--Device-TextPickerDialogOptions-disableTextStyleAnimation?: boolean-End-->

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

**Default:** { color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-disappearTextStyle?: PickerTextStyle--><!--Device-TextPickerDialogOptions-disappearTextStyle?: PickerTextStyle-End-->

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

<!--Device-TextPickerDialogOptions-enableHapticFeedback?: boolean--><!--Device-TextPickerDialogOptions-enableHapticFeedback?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond when the device is in semi-folded mode.

- **true**: Respond when the device is in semi-folded mode (applicable to interaction scenarios such as the hover  
mode on foldable devices).  
- **false**: Do not respond when the device is in semi-folded mode.

Default value: **false**.

**Type:** boolean

**Default:** false - meaning not to enable the hover mode.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TextPickerDialogOptions-enableHoverMode?: boolean--><!--Device-TextPickerDialogOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Default display area of a dialog box in hover mode. This method takes effect only when **enableHoverMode** is set to **true**.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TextPickerDialogOptions-hoverModeArea?: HoverModeAreaType--><!--Device-TextPickerDialogOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events outside the mask area are transparently transmitted, and events within the mask area are not. Set this parameter when you need to restrict the interaction area of the dialog box or implement special interaction effects.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**Type:** [Rectangle](arkts-arkui-common-comp-rectangle-i.md)

**Default:** 
- API version 11+: { x: 0, y: 0, width: '100%', height: '100%' }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-maskRect?: Rectangle--><!--Device-TextPickerDialogOptions-maskRect?: Rectangle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog box based on the **alignment** settings. Set this parameter when you need to fine-tune the position of the dialog box. If this parameter is not set, the dialog box is displayed based on the **alignment** settings.

Default value: **{ dx: 0 , dy: 0 }**

**Type:** Offset

**Default:** 
- API version 11+: { dx: 0 , dy: 0 }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-offset?: Offset--><!--Device-TextPickerDialogOptions-offset?: Offset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea?: Callback<TextPickerResult>
```

Represents the callback triggered during the scrolling of the text picker when an item enters the divider area. Compared to the **onChange** event, this event is triggered earlier, specifically when the scroll distance of the current column exceeds half the height of the selected item, which indicates that the item has entered the divider area.

**NOTE:** 

In scenarios where the picker contains linked columns, the use of this callback is not recommended. The reason is that it identifies nodes where items enter the divider area during scrolling. However, items that change in response to the scrolling do not themselves scroll. As a result, the callback's return values will only reflect changes for the currently scrolling column, while other non-scrolling columns will remain unchanged.

**Type:** Callback&lt;[TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md)&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerDialogOptions-onEnterSelectedArea?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptions-onEnterSelectedArea?: Callback<TextPickerResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<TextPickerResult>
```

Callback triggered when the picker scrolling stops. It is used to listen for the physical scrolling stop event. The difference between the **onChange** and **onScrollStop** events is that **onChange** focuses on the selected option, while **onScrollStop** focuses on the end of the scrolling action.

**Type:** Callback&lt;[TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md)&gt;

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-TextPickerDialogOptions-onScrollStop?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptions-onScrollStop?: Callback<TextPickerResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundStyle

```TypeScript
selectedBackgroundStyle?: PickerBackgroundStyle
```

Background color of the selected item.

Default value:

{

color: $r('sys.color.comp_background_tertiary'),

borderRadius: $r('sys.float.corner_radius_level12')

}

**Type:** [PickerBackgroundStyle](arkts-arkui-textpicker-comp-pickerbackgroundstyle-i.md)

**Default:** { color: $r('sys.color.comp_background_tertiary'), borderRadius: $r('sys.float.corner_radius_level12') }

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptions-selectedBackgroundStyle?: PickerBackgroundStyle--><!--Device-TextPickerDialogOptions-selectedBackgroundStyle?: PickerBackgroundStyle-End-->

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

<!--Device-TextPickerDialogOptions-selectedTextStyle?: PickerTextStyle--><!--Device-TextPickerDialogOptions-selectedTextStyle?: PickerTextStyle-End-->

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

<!--Device-TextPickerDialogOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-TextPickerDialogOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: PickerTextStyle
```

Text color, font size, and font weight of candidate items (the item immediately adjacent to the selected item, above or below).

Default value:

{

color: '#ff182431',

font: {

size: '16fp',

weight: FontWeight.Regular

}

}

**Type:** [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)

**Default:** { color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerDialogOptions-textStyle?: PickerTextStyle--><!--Device-TextPickerDialogOptions-textStyle?: PickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
