# ActionSheetOptions

Provides **ActionSheet** configuration options.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: VoidCallback
```

Callback invoked when the dialog box is closed after the overlay is clicked.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment mode of the dialog box in the vertical direction.

Default value: **DialogAlignment.Bottom**

**NOTE:** 

If **showInSubWindow** is set to **true** in **UIExtension**, the dialog box is aligned with the host window based on **UIExtension**.

**Type:** [DialogAlignment](arkts-arkui-dialogalignment-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

Whether to close the dialog box when the overlay is clicked.

Default value: **true**

The value **true** means to close the dialog box when the overlay is clicked, and **false** means the opposite.

**Type:** boolean

**Since:** 8

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

**Type:** [BlurStyle](../arkts-components/arkts-arkui-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Options for customizing the background blur style. For details about the default value, see **BackgroundBlurStyleOptions**.

**Type:** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

The background color will be visually combined with the blur effect when both properties are set. If the resulting effect does not match your design requirements, you can disable the blur effect entirely by explicitly setting the **backgroundBlurStyle** property to **BlurStyle.NONE**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Options for customizing the background effect. For details about the default value, see **BackgroundEffectOptions**.

**Type:** [BackgroundEffectOptions](../arkts-components/arkts-arkui-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors
```

Border color of the dialog box.

Default value: **Color.Black**

**borderColor** must be used with **borderWidth** in pairs.

**NOTE:** 

When **borderColor** is of type LocalizedEdgeColors, the layout order can be dynamically adjusted based on the user's language settings.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; EdgeColors &#124; [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md)

**Default:** Color.Black - borderColor must be used with borderWidth in pairs.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

Border style of the dialog box.

Default value: **BorderStyle.Solid**

**borderStyle** must be used with **borderWidth** in pairs.

**Type:** [BorderStyle](arkts-arkui-borderstyle-e.md) &#124; EdgeStyles

**Default:** BorderStyle.Solid - borderStyle must be used with borderWidth in pairs.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths
```

Border width of the dialog box.

You can set the width for all four sides or set separate widths for individual sides.

Default value: **0**

When set to a percentage, the value defines the border width as a percentage of the parent dialog box's width.

If the left and right borders are greater than its width, or the top and bottom borders are greater than its height, the dialog box may not display as expected.

**NOTE:** 

When **borderWidth** is of type LocalizedEdgeWidths, the layout order can be dynamically adjusted based on the user's language settings.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**Default:** 0 - When set to a percentage, the value defines the border width as a percentage of the parent dialog box's width. If the left and right borders are greater than its width, or the top and bottom borders are greater than its height, the dialog box may not display as expected.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## confirm

```TypeScript
confirm?: ActionSheetButtonOptions
```

Information about the confirm button. When the dialog box has focus and the **Tab** key is not pressed for sequential focus navigation, the button responds to the **Enter** key by default. Multiple dialog boxes can automatically gain focus and respond to user interactions in a sequential manner. The default response to the **Enter** key does not work when **defaultFocus** is set to **true**.

**Type:** [ActionSheetButtonOptions](arkts-arkui-actionsheetbuttonoptions-i.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses
```

Corner radius of the background.

You can set the radius for each of the four corners individually.

Default value: **{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' }**

The corner radius is subject to the component size, with the maximum value being half of the component width or height. If the value is negative, the default value is used.

When set to a percentage, the value defines the radius as a percentage of the parent dialog box's width or height.

**NOTE:** 

When **cornerRadius** is of type LocalizedBorderRadiuses, the layout order can be dynamically adjusted based on the user's language settings.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](arkts-arkui-localizedborderradiuses-i.md)

**Default:** - {topLeft:'32vp', topRight:'32vp', bottomLeft:'32vp', bottomRight:'32vp'}, The corner radius is subject to the component size, with the maximum value being half of the component width or height. If the value is negative, the default value is used. When set to a percentage, the value defines the radius as a percentage of the parent component's width or height.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond when the device is in semi-folded mode. The value **true** means to respond when the device is in semi-folded mode.

Default value: **false**, meaning not to enable the hover mode.

**NOTE:** 

For a PC or 2-in-1 device, the dialog box is displayed on the upper half of the screen by default when **enableHoverMode** is set to **true**. You can set **hoverModeArea** to display the dialog box on the lower half of the screen. For other devices, the dialog box is displayed on the lower half of the screen by default when **enableHoverMode** is set to **true**. You can set **hoverModeArea** to display the dialog box on the upper half of the screen.

**Type:** boolean

**Default:** false - meaning not to enable the hover mode.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

Height of the dialog box.

**NOTE:** 

- Default maximum height of the dialog box: 0.9 x (Window height – Safe area)  
- When this parameter is set to a percentage, the reference height of the dialog box is the height of the window  
where the dialog box is located minus the safe area. You can decrease or increase the height as needed.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Default:** - Default maximum height of the dialog box: 0.9 x (Window height – Safe area) <br>When this parameter is set to a percentage, the reference height of the dialog box is the height of the window where the dialog box is located minus the safe area. You can decrease or increase the height as needed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Display area of the dialog box in hover mode.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**

**Type:** [HoverModeAreaType](../arkts-components/arkts-arkui-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

Overlay effect for the page-level dialog box.

**NOTE:** 

- Default value: **ImmersiveMode.DEFAULT**  
- This parameter takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** [ImmersiveMode](arkts-arkui-immersivemode-t.md)

**Default:** ImmersiveMode.DEFAULT - This parameter takes effect only when levelMode is set to LevelMode.EMBEDDED.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

Whether the dialog box is a modal. A modal dialog box has a mask applied, while a non-modal dialog box does not. **false**: The dialog box is not a modal.

Default value: **true**

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Display level of the dialog box.

**NOTE:** 

- Default value: **LevelMode.OVERLAY**  
- This parameter takes effect only when **showInSubWindow** is set to **false**.

**Type:** [LevelMode](arkts-arkui-levelmode-t.md)

**Default:** LevelMode.OVERLAY - This parameter takes effect only when showInSubWindow is set to false.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

Display order of the dialog box.

**NOTE:** 

- Default value: **LevelOrder.clamp(0)**  
- Dynamic updating is not supported.

**Type:** [LevelOrder](arkts-arkui-levelorder-t.md)

**Default:** The value returns by LevelOrder.clamp(0)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

[Unique ID](arkts-arkui-framenode-c.md#getuniqueid) of the node under the display level for the page-level dialog box.

Value range: a number no less than 0

**NOTE:** 

- This parameter takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events outside the mask area are transparently transmitted, and events within the mask area are not.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**NOTE:** 

**maskRect** does not take effect when **showInSubWindow** is set to **true**.

**Type:** [Rectangle](../arkts-components/arkts-arkui-rectangle-i.md)

**Default:** 
- API version 11+: - {x:0,y:0, width:'100%', height:'100%'}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string | Resource
```

Content of the dialog box.

If the text is too long to display, a scrollbar is displayed.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: ActionSheetOffset
```

Offset of the dialog box relative to the alignment position.

Default value:

1. If **alignment** is set to **Top**, **TopStart**, or **TopEnd**, the default offset value is **{dx: 0,dy: "40vp"}**.
2. If **alignment** is set to other values, the default offset value is **{dx: 0,dy: "-40vp"}**.

**Type:** [ActionSheetOffset](arkts-arkui-actionsheetoffset-i.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: Callback<void>
```

Event callback after the dialog box appears.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onDidAppear**. The settings take effect next time the dialog box appears.
3. When a dialog box is dismissed immediately after being shown, **onWillDisappear** may be triggered before **onDidAppear**.
4. If the dialog box is dismissed before its entrance animation is finished, the animation will be interrupted, and **onDidAppear** will not be triggered.

**Type:** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: Callback<void>
```

Event callback after the dialog box disappears.

**NOTE:** 

The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.

**Type:** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: Callback<void>
```

Event callback when the dialog box is about to appear.

**NOTE:** 

1. The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.
2. You can set the callback event for changing the dialog box display effect in **onWillAppear**. The settings take effect next time the dialog box appears.

**Type:** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: Callback<void>
```

Event callback when the dialog box is about to disappear.

**NOTE:** 

The normal timing sequence is as follows: onWillAppear &gt; onDidAppear &gt; onWillDisappear &gt; onDidDisappear.

**Type:** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

Callback for interactive closure of the dialog box.

**NOTE:** 

1. If this callback is registered, the dialog box will not be dismissed immediately after the user touches the mask or the Back button, presses the Esc key, or swipes left or right on the screen. The **reason** parameter in the callback is used to determine whether the dialog box can be closed. The reason returned by the component does not support the value **CLOSE_BUTTON**.
2. In the **onWillDismiss** callback, another **onWillDismiss** callback is not allowed.

**Type:** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[DismissDialogAction](arkts-arkui-dismissdialogaction-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box.

Default value on 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_MD** when the dialog box is focused and **ShadowStyle.OUTER_FLOATING_SM** otherwise On other devices, the dialog box has no shadow by default.

**Type:** [ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-shadowstyle-e.md)

**Default:** - Default value on 2-in-1 devices: ShadowStyle.OUTER_FLOATING_MD when the dialog box is focused and ShadowStyle.OUTER_FLOATING_SM otherwise.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sheets

```TypeScript
sheets: Array<SheetInfo>
```

Options in the dialog box. Each option supports the image, text, and callback.

**Type:** Array&lt;[SheetInfo](arkts-arkui-sheetinfo-i.md)&gt;

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to show the dialog box in a subwindow when the dialog box needs to be displayed outside the main window. **true**: The dialog box is shown in a subwindow.

Default value: **false**, meaning the dialog box is displayed within the application, not in a separate subwindow.

**NOTE:** 

A dialog box whose **showInSubWindow** attribute is **true** cannot trigger the display of another dialog box whose **showInSubWindow** attribute is also **true**.

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

Subtitle of the dialog box.

If the text is too long to display, it is truncated with an ellipsis (...).

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for dialog. Different materials have different effects, which can influence backgroundColor, border, shadow, and other visual attributes of dialog.

Device Behavior Differences:The effect of same material may vary across different devices depending on their computing power.

**Type:** [SystemUiMaterial](../arkts-components/arkts-arkui-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: string | Resource
```

Title of the dialog box.

If the text is too long to display, it is truncated with an ellipsis (...).

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

Transition effect for the entrance and exit of the dialog box.

**NOTE:** 

1. If this parameter is not set, the default effect is used.
2. Touching the Back button during the entrance animation pauses the entrance animation and starts the exit animation. The final effect is one obtained after the curves of the entrance and exit animations are combined.
3. Touching the Back button during the exit animation does not affect the animation playback. Touching the Back button again closes the application.

**Type:** [TransitionEffect](../arkts-components/arkts-arkui-transitioneffect-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Width of the dialog box.

**NOTE:** 

- Default maximum width of the dialog box: 400 vp  
- When this parameter is set to a percentage, the reference width of the dialog box is the width of the window  
where the dialog box is located. You can decrease or increase the width as needed.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Default:** - Default maximum width of the dialog box: 400 vp, When this parameter is set to a percentage, the reference width of the dialog box is the width of the window where the dialog box is located. You can decrease or increase the width as needed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
