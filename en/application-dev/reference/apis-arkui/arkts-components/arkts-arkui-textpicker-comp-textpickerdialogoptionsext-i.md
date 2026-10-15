# TextPickerDialogOptionsExt

```TypeScript
declare interface TextPickerDialogOptionsExt extends TextPickerOptions
```

Inherits from [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md).

**Inheritance/Implementation:** TextPickerDialogOptionsExt extends [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md)

**Since:** 20

<!--Device-unnamed-declare interface TextPickerDialogOptionsExt extends TextPickerOptions--><!--Device-unnamed-declare interface TextPickerDialogOptionsExt extends TextPickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: VoidCallback
```

Triggered when the Cancel button in the dialog box is clicked.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onCancel?: VoidCallback--><!--Device-TextPickerDialogOptionsExt-onCancel?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
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

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onDidAppear?: VoidCallback--><!--Device-TextPickerDialogOptionsExt-onDidAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

Event callback after the dialog box disappears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt;
(onAccept/onCancel/onChange/onScrollStop) &gt; onWillDisappear &gt; onDidDisappear.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onDidDisappear?: VoidCallback--><!--Device-TextPickerDialogOptionsExt-onDidDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

Event callback when the dialog box is about to appear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt;
(onAccept/onCancel/onChange/onScrollStop) &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onWillAppear**. The settings take
effect next time the dialog box appears.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onWillAppear?: VoidCallback--><!--Device-TextPickerDialogOptionsExt-onWillAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

Event callback when the dialog box is about to disappear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt;
(onAccept/onCancel/onChange/onScrollStop) &gt; onWillDisappear &gt; onDidDisappear.
2. If the user closes the dialog box immediately after it appears, **onWillDisappear** is invoked before  
**onDidAppear**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onWillDisappear?: VoidCallback--><!--Device-TextPickerDialogOptionsExt-onWillDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

Style of the accept button.

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**. If
both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp and remains fixed even in accessibility and large-font modes. In addition,
even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-acceptButtonStyle?: PickerDialogButtonStyle--><!--Device-TextPickerDialogOptionsExt-acceptButtonStyle?: PickerDialogButtonStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment mode of the dialog box in the vertical direction.

Default value: **DialogAlignment.Default**

**Type:** [DialogAlignment](../arkts-apis/arkts-arkui-dialogalignment-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-alignment?: DialogAlignment--><!--Device-TextPickerDialogOptionsExt-alignment?: DialogAlignment-End-->

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

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-backgroundBlurStyle?: BlurStyle--><!--Device-TextPickerDialogOptionsExt-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur effect parameters, which are used to customize the display style of the pop-up window background blur. You can configure attributes such as the color mode, adaptive color, and zoom ratio to achieve different background blur visual effects.

**NOTE:** 

If this parameter is not set, the default effect of **BlurStyle.COMPONENT_ULTRA_THICK** is used. If this parameter is set, the effect of **backgroundBlurStyle** is overwritten.

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-TextPickerDialogOptionsExt-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

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

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-backgroundColor?: ResourceColor--><!--Device-TextPickerDialogOptionsExt-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Background effect parameters, which are used to customize the display effect of the dialog box background. You can configure attributes such as the blur radius, saturation, brightness, and color to achieve different background visual effects.

**NOTE:** 

If this parameter is not set, the blur effect of the dialog box background is determined by the value of **backgroundBlurStyle**. If this parameter is set, the value of **backgroundBlurStyle** will be overridden. Since API version 26.0.0, **backgroundEffect** and **backgroundBlurStyle** do not take effect after **systemMaterial** is set.

**Type:** [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-backgroundEffect?: BackgroundEffectOptions--><!--Device-TextPickerDialogOptionsExt-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

Style of the cancel button.

**NOTE:** 

1. In **acceptButtonStyle** and **cancelButtonStyle**, at most one **primary** field can be set to **true**. If
both are set to **true**, the **primary** field will remain at the default value of **false**.
2. The default button height is 40 vp and remains fixed even in accessibility and large-font modes. In addition,
even if the button style is set to ROUNDED_RECTANGLE, the displayed effect is still a capsule button (Capsule).

**Type:** [PickerDialogButtonStyle](arkts-arkui-common-comp-pickerdialogbuttonstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-cancelButtonStyle?: PickerDialogButtonStyle--><!--Device-TextPickerDialogOptionsExt-cancelButtonStyle?: PickerDialogButtonStyle-End-->

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

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-canLoop?: boolean--><!--Device-TextPickerDialogOptionsExt-canLoop?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight?: number | string
```

Height of the picker item. For the number type, the value range is [0, +∞). For the string type, only numeric string values, for example, **"56"**, are supported.

Default value: 56 vp (selected) and 36 vp (unselected). The set value applies to both selected and unselected items.

**NOTE:** 

If the value of **defaultPickerItemHeight** is negative, the default value is used.

**Type:** number &#124; string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-defaultPickerItemHeight?: number | string--><!--Device-TextPickerDialogOptionsExt-defaultPickerItemHeight?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultTextStyle

```TypeScript
defaultTextStyle?: TextPickerTextStyle
```

Style of the text items when the text style change animation during the scrolling process is disabled. It is effective only when **disableTextStyleAnimation** is **true**.

Default value: same as the default value of the [Text](arkts-arkui-text-comp.md) component

**Type:** [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-defaultTextStyle?: TextPickerTextStyle--><!--Device-TextPickerDialogOptionsExt-defaultTextStyle?: TextPickerTextStyle-End-->

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

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-disableTextStyleAnimation?: boolean--><!--Device-TextPickerDialogOptionsExt-disableTextStyleAnimation?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: TextPickerTextStyle
```

Style of edge items (the second item above or below the selected item), covering the following: text color, font size, font weight, maximum font size, minimum font size, text overflow mode.

Default value:

{

color: '#ff182431',

font: {

size: '14fp',

weight: FontWeight.Regular

},

minFontSize: 0,

maxFontSize: 0,

overflow: TextOverflow.CLIP

}

**Type:** [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-disappearTextStyle?: TextPickerTextStyle--><!--Device-TextPickerDialogOptionsExt-disappearTextStyle?: TextPickerTextStyle-End-->

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

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-enableHapticFeedback?: boolean--><!--Device-TextPickerDialogOptionsExt-enableHapticFeedback?: boolean-End-->

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

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-enableHoverMode?: boolean--><!--Device-TextPickerDialogOptionsExt-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Default display area of a dialog box in hover mode. This parameter is valid only when **enableHoverMode** is set to **true**.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-hoverModeArea?: HoverModeAreaType--><!--Device-TextPickerDialogOptionsExt-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events outside the mask area are transparently transmitted, and events within the mask area are not.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**Type:** [Rectangle](arkts-arkui-common-comp-rectangle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-maskRect?: Rectangle--><!--Device-TextPickerDialogOptionsExt-maskRect?: Rectangle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog box based on the **alignment** settings. Set this parameter when you need to fine-tune the position of the dialog box. If this parameter is not set, the dialog box is displayed based on the **alignment** settings.

Default value: **{ dx: 0 , dy: 0 }**

**Type:** Offset

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-offset?: Offset--><!--Device-TextPickerDialogOptionsExt-offset?: Offset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: Callback<TextPickerResult>
```

Triggered when the OK button in the dialog box is clicked.

**Type:** Callback&lt;[TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onAccept?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptionsExt-onAccept?: Callback<TextPickerResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<TextPickerResult>
```

Callback triggered when the text picker in the dialog box snaps to the selected item. This callback is used to obtain the final selection result.

This callback is triggered only after the scroll animation completes. To obtain real-time index changes, use **onEnterSelectedArea** instead.

**Type:** Callback&lt;[TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onChange?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptionsExt-onChange?: Callback<TextPickerResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea?: Callback<TextPickerResult>
```

Represents the callback triggered during the scrolling of the text picker when an item enters the divider area. Compared to the **onChange** event, this event is triggered earlier, specifically when the scroll distance of the current column exceeds half the height of the selected item, which indicates that the item has entered the divider area.

**NOTE:** 

In scenarios where the picker contains linked columns, the use of this callback is not recommended. The reason is that it identifies nodes where items enter the divider area during scrolling. However, items that change in response to the scrolling do not themselves scroll. As a result, the callback's return values will only reflect changes for the currently scrolling column, while other non-scrolling columns will remain unchanged.

**Type:** Callback&lt;[TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onEnterSelectedArea?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptionsExt-onEnterSelectedArea?: Callback<TextPickerResult>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<TextPickerResult>
```

Callback triggered when the picker scrolling stops. This callback is used to listen for the physical scrolling stop event. The difference between the **onChange** and **onScrollStop** events is that the **onChange** event focuses on the selected option, while the **onScrollStop** event focuses on the end of the scrolling action.

**Type:** Callback&lt;[TextPickerResult](arkts-arkui-textpicker-comp-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-onScrollStop?: Callback<TextPickerResult>--><!--Device-TextPickerDialogOptionsExt-onScrollStop?: Callback<TextPickerResult>-End-->

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

<!--Device-TextPickerDialogOptionsExt-selectedBackgroundStyle?: PickerBackgroundStyle--><!--Device-TextPickerDialogOptionsExt-selectedBackgroundStyle?: PickerBackgroundStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: TextPickerTextStyle
```

Style of the selected item, covering the following: text color, font size, font weight, maximum font size, minimum font size, text overflow mode.

Default value:

{

color: '#ff007dff',

font: {

size: '20fp',

weight: FontWeight.Medium

},

minFontSize: 0,

maxFontSize: 0,

overflow: TextOverflow.CLIP

}

**Type:** [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-selectedTextStyle?: TextPickerTextStyle--><!--Device-TextPickerDialogOptionsExt-selectedTextStyle?: TextPickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box.

Default value on 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_MD** when the dialog box is focused and **ShadowStyle.OUTER_FLOATING_SM** otherwise

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-shadow?: ShadowOptions | ShadowStyle--><!--Device-TextPickerDialogOptionsExt-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

System material of the dialog box. Set this parameter when you need to use the predefined material effect to quickly achieve a unified visual effect.

**NOTE:** 

- The default value is the **ImmersiveMaterial** object whose style is **ImmersiveStyle.ULTRA_THICK** in  
**ImmersiveOptions**. If this parameter is set to **undefined**, the default value is used. Different materials have different effects.  
- This API affects the background color ([backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1)), background blur ([backgroundBlurStyle](arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle1)), background effect ([backgroundEffect](arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect1)), border color ([borderColor](arkts-arkui-common-comp-commonmethod-c.md#bordercolor)), border width ([borderWidth](arkts-arkui-common-comp-commonmethod-c.md#borderwidth)), and shadow ([shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow1)). When the system material is set, the preceding APIs do not take effect.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextPickerDialogOptionsExt-systemMaterial?: SystemUiMaterial--><!--Device-TextPickerDialogOptionsExt-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: TextPickerTextStyle
```

Style of candidate items (the first item immediately above or below the selected item), covering the following: text color, font size, font weight, maximum font size, minimum font size, text overflow mode.

Default value:

{

color: '#ff182431',

font: {

size: '16fp',

weight: FontWeight.Regular

},

minFontSize: 0,

maxFontSize: 0,

overflow: TextOverflow.CLIP

}

**Type:** [TextPickerTextStyle](arkts-arkui-textpicker-comp-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextPickerDialogOptionsExt-textStyle?: TextPickerTextStyle--><!--Device-TextPickerDialogOptionsExt-textStyle?: TextPickerTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
