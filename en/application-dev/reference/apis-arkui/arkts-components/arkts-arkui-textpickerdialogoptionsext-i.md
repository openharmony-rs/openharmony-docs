# TextPickerDialogOptionsExt

Defines the TextPickerDialogOptionsExt for Text Picker Dialog.

**Inheritance/Implementation:** TextPickerDialogOptionsExt extends [TextPickerOptions](arkts-arkui-textpickeroptions-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel?: VoidCallback
```

Called when the Cancel button in the dialog is clicked.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

Callback function when the dialog appears.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

Callback function when the dialog disappears.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

Callback function before the dialog openAnimation starts.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

Callback function before the dialog closeAnimation starts.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## acceptButtonStyle

```TypeScript
acceptButtonStyle?: PickerDialogButtonStyle
```

Style of accept button.

**Type:** [PickerDialogButtonStyle](arkts-arkui-pickerdialogbuttonstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Defines the dialog alignment of the screen.

**Type:** [DialogAlignment](../arkts-apis/arkts-arkui-dialogalignment-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Defines the textPickerDialog's background blur Style

**Type:** [BlurStyle](arkts-arkui-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Defines the textPickerDialog's background blur style with options

**Type:** [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Defines the textPickerDialog's background color

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Defines the textPickerDialog's background effect with options

**Type:** [BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancelButtonStyle

```TypeScript
cancelButtonStyle?: PickerDialogButtonStyle
```

Style of cancel button.

**Type:** [PickerDialogButtonStyle](arkts-arkui-pickerdialogbuttonstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop?: boolean
```

Can scroll loop if true is set, on the contrary it can not.

Default Value: true

**Type:** boolean

**Default:** true

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultPickerItemHeight

```TypeScript
defaultPickerItemHeight?: number | string
```

Called when the default height of the selected element is set.

**Type:** number &#124; string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultTextStyle

```TypeScript
defaultTextStyle?: TextPickerTextStyle
```

Defines to set the default text style for options.

**Type:** [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableTextStyleAnimation

```TypeScript
disableTextStyleAnimation?: boolean
```

Defines whether to disable the text style animation.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disappearTextStyle

```TypeScript
disappearTextStyle?: TextPickerTextStyle
```

Text style of disappearing items.

**Type:** [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Enable or disable haptic feedback.

**Type:** boolean

**Default:** true

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Defines whether to respond to the hover mode.

**Type:** boolean

**Default:** false

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Defines the dialog's display area in hover mode.

**Type:** [HoverModeAreaType](arkts-arkui-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask Region of dialog. The size cannot exceed the main window.

**Type:** [Rectangle](arkts-arkui-rectangle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Defines the dialog offset.

**Type:** [Offset](../arkts-apis/arkts-arkui-offset-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAccept

```TypeScript
onAccept?: Callback<TextPickerResult>
```

Called when the OK button in the dialog is clicked.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[TextPickerResult](arkts-arkui-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<TextPickerResult>
```

This event is triggered when a TextPicker text is selected in dialog.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[TextPickerResult](arkts-arkui-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea?: Callback<TextPickerResult>
```

This event is triggered when an item enters the selected area in dialog.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[TextPickerResult](arkts-arkui-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<TextPickerResult>
```

This event is triggered when a TextPicker text is selected and scrolling has stopped in dialog.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[TextPickerResult](arkts-arkui-textpickerresult-i.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundStyle

```TypeScript
selectedBackgroundStyle?: PickerBackgroundStyle
```

Background style of selected items.

**Type:** [PickerBackgroundStyle](arkts-arkui-pickerbackgroundstyle-i.md)

**Default:** { color: $r('sys.color.comp_background_tertiary'), borderRadius: $r('sys.float.corner_radius_level12') }

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: TextPickerTextStyle
```

Text style of selected items

**Type:** [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Defines the dialog's shadow.

**Type:** [ShadowOptions](arkts-arkui-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-shadowstyle-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for dialog. Different materials have different effects, which can influence backgroundColor, border, shadow, and other visual attributes of dialog.

**Type:** [SystemUiMaterial](arkts-arkui-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle?: TextPickerTextStyle
```

Text style of normal items

**Type:** [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
