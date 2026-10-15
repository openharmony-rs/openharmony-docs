# ActionSheetOptions

```TypeScript
interface ActionSheetOptions
```

Provides **ActionSheet** configuration options.

**Since:** 8

<!--Device-unnamed-interface ActionSheetOptions--><!--Device-unnamed-interface ActionSheetOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cancel

```TypeScript
cancel?: VoidCallback
```

Callback invoked when the dialog box is closed by tapping the mask.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-cancel?: VoidCallback--><!--Device-ActionSheetOptions-cancel?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogAlignment
```

Alignment mode of the dialog box in the vertical direction.

Default value: **DialogAlignment.Bottom**

**NOTE:** 

If **showInSubWindow** is set to true in **UIExtension**, the dialog box is aligned based on the host window of **UIExtension**.

**Type:** [DialogAlignment](arkts-arkui-dialogalignment-e.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-alignment?: DialogAlignment--><!--Device-ActionSheetOptions-alignment?: DialogAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

Whether to close the dialog box when the mask is tapped.

Default value: **true**

When the value is **true**, tapping the mask closes the dialog box; when the value is **false**, tapping the mask does not close the dialog box.

**Type:** boolean

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-autoCancel?: boolean--><!--Device-ActionSheetOptions-autoCancel?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Blur material of the dialog box background.

Default value: **BlurStyle.NONE** since API version 26.0.0, and **BlurStyle.COMPONENT_ULTRA_THICK** before API version 26.0.0.

**NOTE:** 

Set this attribute to **BlurStyle.NONE** to disable background blur. When **backgroundBlurStyle** is set to a value other than NONE, do not set **backgroundColor**; otherwise, the color display will not meet expectations.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-backgroundBlurStyle?: BlurStyle--><!--Device-ActionSheetOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur effect. For the default value, see the **BackgroundBlurStyleOptions** type description.

**Type:** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ActionSheetOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-ActionSheetOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the dialog box.

Default value: **Color.Transparent**

**NOTE:** 

**backgroundColor** is superimposed with the blur attribute **backgroundBlurStyle** to produce an effect. If the effect does not meet expectations, set **backgroundBlurStyle** to **BlurStyle.NONE** to cancel the blur. When **backgroundBlurStyle** is set to a value other than NONE, do not set **backgroundColor**; otherwise, the color display will not meet expectations.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-backgroundColor?: ResourceColor--><!--Device-ActionSheetOptions-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Background effect parameters. For the default value, see the **BackgroundEffectOptions** type description.

**Type:** [BackgroundEffectOptions](../arkts-components/arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ActionSheetOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-ActionSheetOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors
```

Border color of the dialog box background.

Default value: **Color.Black**

If the **borderColor** attribute is used, it must be used together with the **borderWidth** attribute.

**NOTE:** 

When the **borderColor** attribute type is **LocalizedEdgeColors**, the layout order can be changed based on the language habit.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; EdgeColors &#124; [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md)

**Default:** Color.Black - borderColor must be used with borderWidth in pairs.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors--><!--Device-ActionSheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

Border style of the dialog box background.

Default value: **BorderStyle.Solid**.

If the **borderStyle** attribute is used, it must be used together with the **borderWidth** attribute.

**Type:** [BorderStyle](arkts-arkui-borderstyle-e.md) &#124; EdgeStyles

**Default:** BorderStyle.Solid - borderStyle must be used with borderWidth in pairs.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-ActionSheetOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths
```

Border width of the dialog box background.

The width of the four borders can be set separately.

Default value: **0**

Percentage parameter: the border width of the dialog box is set as a percentage of the width of the parent dialog box.

When the left and right borders of the dialog box are greater than the dialog box width, or the top and bottom borders are greater than the dialog box height, the display may not meet expectations.

**NOTE:** 

When the **borderWidth** attribute type is **LocalizedEdgeWidths**, the layout order can be changed based on the language habit.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**Default:** 0 - When set to a percentage, the value defines the border width as a percentage of the parent dialog box's width. If the left and right borders are greater than its width, or the top and bottom borders are greater than its height, the dialog box may not display as expected.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths--><!--Device-ActionSheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## confirm

```TypeScript
confirm?: ActionSheetButtonOptions
```

Enabling status, default focus, button style, text content, and click callback of the confirm button.

**Type:** [ActionSheetButtonOptions](arkts-arkui-actionsheetbuttonoptions-i.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-confirm?: ActionSheetButtonOptions--><!--Device-ActionSheetOptions-confirm?: ActionSheetButtonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cornerRadius

```TypeScript
cornerRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses
```

Corner radius of the dialog box background.

The radius of the four corners can be set separately.

Default value: **{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' }**

The corner radius is limited by the component size, and the maximum value is half of the component width or height. If the value is negative, the default value is used.

Percentage parameter: the corner radius of the dialog box is set as a percentage of the width and height of the parent dialog box.

**NOTE:** 

When the **cornerRadius** attribute type is **LocalizedBorderRadiuses**, the layout order can be changed based on the language habit.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](arkts-arkui-localizedborderradiuses-i.md)

**Default:** - {topLeft:'32vp', topRight:'32vp', bottomLeft:'32vp', bottomRight:'32vp'}, The corner radius is subject to the component size, with the maximum value being half of the component width or height. If the value is negative, the default value is used. When set to a percentage, the value defines the radius as a percentage of the parent component's width or height.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-cornerRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-ActionSheetOptions-cornerRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to respond to the hover state. The value **true** indicates that the hover state is responded to.

Default value: **false**, which means no response by default.

**NOTE:** 

On PCs/2-in-1 devices, the dialog box is displayed in the upper half of the screen by default. When **enableHoverMode** is set to **true**, it can be displayed in the lower half of the screen by setting the **hoverModeArea** parameter. On other devices, when **enableHoverMode** is set to **true**, the dialog box is displayed in the lower half of the screen by default, and can be displayed in the upper half of the screen by setting the **hoverModeArea** parameter.

**Type:** boolean

**Default:** false - meaning not to enable the hover mode.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ActionSheetOptions-enableHoverMode?: boolean--><!--Device-ActionSheetOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

Height of the dialog box background.

**NOTE:** 

- Default maximum height of the dialog box: 0.9 × (window height - safe area).  
- Percentage parameter: the reference height of the dialog box is (window height - safe area), and the height can  
be adjusted smaller or larger based on this.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Default:** - Default maximum height of the dialog box: 0.9 x (Window height – Safe area) <br>When this parameter is set to a percentage, the reference height of the dialog box is the height of the window where the dialog box is located minus the safe area. You can decrease or increase the height as needed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-height?: Dimension--><!--Device-ActionSheetOptions-height?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Default display area of the dialog box in the hover state.

**NOTE:** 

This attribute must be used together with the **enableHoverMode** attribute.

Default value: **HoverModeAreaType.BOTTOM_SCREEN**.

**Type:** [HoverModeAreaType](../arkts-components/arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ActionSheetOptions-hoverModeArea?: HoverModeAreaType--><!--Device-ActionSheetOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

Mask effect of the dialog box within the page.

**NOTE:** 

- Default value: **ImmersiveMode.DEFAULT**  
- This attribute takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** [ImmersiveMode](arkts-arkui-immersivemode-t.md)

**Default:** ImmersiveMode.DEFAULT - This parameter takes effect only when levelMode is set to LevelMode.EMBEDDED.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ActionSheetOptions-immersiveMode?: ImmersiveMode--><!--Device-ActionSheetOptions-immersiveMode?: ImmersiveMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

Whether the dialog box is a modal window. A modal window has a mask, while a non-modal window does not. When the value is **false**, the dialog box is a non-modal window without a mask.

Default value: **true**, which means the dialog box has a mask.

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-isModal?: boolean--><!--Device-ActionSheetOptions-isModal?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Display level of the dialog box.

**NOTE:** 

- Default value: **LevelMode.OVERLAY**  
- This attribute takes effect only when **showInSubWindow** is set to false.  
- When set to **LevelMode.EMBEDDED**, the level of the page-level dialog box can be set through **levelUniqueId**,  
and the mask effect of the dialog box within the page can be set through **immersiveMode**.

**Type:** [LevelMode](arkts-arkui-levelmode-t.md)

**Default:** LevelMode.OVERLAY - This parameter takes effect only when showInSubWindow is set to false.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ActionSheetOptions-levelMode?: LevelMode--><!--Device-ActionSheetOptions-levelMode?: LevelMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

Display order of the dialog box.

**NOTE:** 

- Default value: **LevelOrder.clamp(0)**  
- Dynamic refresh of the order is not supported.

**Type:** [LevelOrder](arkts-arkui-levelorder-t.md)

**Default:** The value returns by LevelOrder.clamp(0)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ActionSheetOptions-levelOrder?: LevelOrder--><!--Device-ActionSheetOptions-levelOrder?: LevelOrder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid) of the level where the page-level dialog box needs to be displayed.

Value range: a number greater than or equal to 0.

**NOTE:** 

- This attribute takes effect only when **levelMode** is set to **LevelMode.EMBEDDED**.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ActionSheetOptions-levelUniqueId?: number--><!--Device-ActionSheetOptions-levelUniqueId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events within the mask area are not passed through, while events outside the mask area are passed through.

Default value: **{ x: 0, y: 0, width: '100%', height: '100%' }**

**NOTE:** 

When **showInSubWindow** is **true**, **maskRect** does not take effect.

**Type:** [Rectangle](../arkts-components/arkts-arkui-common-comp-rectangle-i.md)

**Default:** 
- API version 11+: - {x:0,y:0, width:'100%', height:'100%'}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-maskRect?: Rectangle--><!--Device-ActionSheetOptions-maskRect?: Rectangle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string | Resource
```

Dialog box content.

When the text is too long, a scroll bar is triggered.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-message: string | Resource--><!--Device-ActionSheetOptions-message: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: ActionSheetOffset
```

Offset of the dialog box relative to the position of **alignment**.

Default value:

1. When **alignment** is set to **Top**, **TopStart**, or **TopEnd**, the default value is **{dx: 0,dy: "40vp"}**.
2. When **alignment** is set to **Center**, **CenterStart**, **CenterEnd**, **Bottom**, **BottomStart**, **BottomEnd**, or **Default**, the default value is **{dx: 0,dy: "-40vp"}**.

**Type:** [ActionSheetOffset](arkts-arkui-actionsheetoffset-i.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-offset?: ActionSheetOffset--><!--Device-ActionSheetOptions-offset?: ActionSheetOffset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: Callback<void>
```

Event callback after the dialog box is displayed.

**NOTE:** 

1. The normal sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. Callback events that change the dialog box display effect set in **onDidAppear** take effect the second time the dialog box is displayed.
3. When the dialog box is quickly displayed and closed, **onWillDisappear** takes effect before **onDidAppear**.
4. If the dialog box is completely closed before the entrance animation is completed, the animation is interrupted and **onDidAppear** is not triggered.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ActionSheetOptions-onDidAppear?: Callback<void>--><!--Device-ActionSheetOptions-onDidAppear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: Callback<void>
```

Event callback after the dialog box disappears.

**NOTE:** 

The normal sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> **onWillDisappear** &gt;
> **onDidDisappear**.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ActionSheetOptions-onDidDisappear?: Callback<void>--><!--Device-ActionSheetOptions-onDidDisappear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: Callback<void>
```

Event callback before the dialog box display animation.

**NOTE:** 

1. The normal sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. Callback events that change the dialog box display effect set in **onWillAppear** take effect the second time the dialog box is displayed.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ActionSheetOptions-onWillAppear?: Callback<void>--><!--Device-ActionSheetOptions-onWillAppear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: Callback<void>
```

Event callback before the dialog box exit animation.

**NOTE:** 

1. The normal sequence is: **onWillAppear** &gt;  
> **onDidAppear** &gt;
> **onWillDisappear** &gt;
> **onDidDisappear**.
2. When the dialog box is quickly displayed and closed, **onWillDisappear** may take effect before **onDidAppear**.

**Type:** Callback&lt;void&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ActionSheetOptions-onWillDisappear?: Callback<void>--><!--Device-ActionSheetOptions-onWillDisappear?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissDialogAction>
```

Interactive dismiss callback.

**NOTE:** 

1. When the user performs interactive operations such as tapping the mask to close, swiping (left/right), pressing the three-key back button, or pressing ESC on the keyboard, if this callback is registered, the dialog box will not be closed immediately. In the callback, you can obtain the operation type that blocks the dialog box closure through reason, and determine whether the dialog box can be closed based on the reason. To close the dialog box, call the **dismiss** method of [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) in the callback. The reason returned by the current component does not support the **CLOSE_BUTTON** enum value.
2. In the **onWillDismiss** callback, **onWillDismiss** interception cannot be performed again.

**Type:** Callback&lt;[DismissDialogAction](arkts-arkui-dismissdialogaction-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-onWillDismiss?: Callback<DismissDialogAction>--><!--Device-ActionSheetOptions-onWillDismiss?: Callback<DismissDialogAction>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box background.

On 2-in-1 devices, in the default scenario, the shadow value when the dialog box is focused is **ShadowStyle.OUTER_FLOATING_MD**, and when it loses focus, it is **ShadowStyle.OUTER_FLOATING_SM**. Other devices have no shadow by default.

**Type:** [ShadowOptions](../arkts-components/arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-common-comp-shadowstyle-e.md)

**Default:** - Default value on 2-in-1 devices: ShadowStyle.OUTER_FLOATING_MD when the dialog box is focused and ShadowStyle.OUTER_FLOATING_SM otherwise.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-ActionSheetOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sheets

```TypeScript
sheets: Array<SheetInfo>
```

Option content. Each option supports setting an image, text, and a callback for selection.

**Type:** Array&lt;[SheetInfo](arkts-arkui-sheetinfo-i.md)&gt;

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-sheets: Array<SheetInfo>--><!--Device-ActionSheetOptions-sheets: Array<SheetInfo>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to display the dialog box in a subwindow when it needs to be displayed outside the main window. The value **true** indicates that the dialog box is displayed in a subwindow.

Default value: **false**, which means the dialog box is displayed within the app instead of in an independent subwindow.

**NOTE:** 

A dialog box with **showInSubWindow** set to **true** cannot trigger the display of another dialog box with **showInSubWindow** set to **true**.

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-showInSubWindow?: boolean--><!--Device-ActionSheetOptions-showInSubWindow?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

Dialog box subtitle.

When the text is too long to be displayed, an ellipsis is used to replace the part that is not displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-subtitle?: ResourceStr--><!--Device-ActionSheetOptions-subtitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

System material of the dialog box.

**NOTE:** 

- Default value: an ImmersiveMaterial object whose style in [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md)  
is **ImmersiveStyle.ULTRA_THICK**. When set to **undefined**, the default value is used.  
- Different materials have different effects. This API affects the background color [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1), background blur [backgroundBlurStyle](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundblurstyle1), background effect [backgroundEffect](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundeffect1), border color [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), border width [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), and shadow [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow1). When the system material is set, the preceding APIs do not take effect.

**Type:** [SystemUiMaterial](../arkts-components/arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ActionSheetOptions-systemMaterial?: SystemUiMaterial--><!--Device-ActionSheetOptions-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: string | Resource
```

Dialog box title.

When the text is too long to be displayed, an ellipsis is used to replace the part that is not displayed.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ActionSheetOptions-title: string | Resource--><!--Device-ActionSheetOptions-title: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

Transition effect for the display and exit of the dialog box.

**NOTE:** 

1. If this attribute is not set, the default display/exit animation is used.
2. If the back key is pressed during the display animation, the display animation is interrupted and the exit animation is executed. The animation effect is the result of superimposing the curves of the display animation and the exit animation.
3. If the back key is pressed during the exit animation, the exit animation is not interrupted and continues to execute. Pressing the back key again exits the app.

**Type:** [TransitionEffect](../arkts-components/arkts-arkui-common-comp-transitioneffect-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-transition?: TransitionEffect--><!--Device-ActionSheetOptions-transition?: TransitionEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Width of the dialog box background.

**NOTE:** 

- Default maximum width of the dialog box: **400vp**.  
- Percentage parameter: the reference width of the dialog box is the width of the window where it is located, and  
the width can be adjusted smaller or larger based on this.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Default:** - Default maximum width of the dialog box: 400 vp, When this parameter is set to a percentage, the reference width of the dialog box is the width of the window where the dialog box is located. You can decrease or increase the width as needed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ActionSheetOptions-width?: Dimension--><!--Device-ActionSheetOptions-width?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
