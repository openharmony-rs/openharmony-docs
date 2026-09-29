# DialogBaseOptions

```TypeScript
declare interface DialogBaseOptions
```

Base options shared by all dialog types.

**Since:** 26.0.1

<!--Device-dialog-declare interface DialogBaseOptions--><!--Device-dialog-declare interface DialogBaseOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

Callback function when the dialog appears.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-onDidAppear?: VoidCallback--><!--Device-DialogBaseOptions-onDidAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

Callback function when the dialog disappears.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-onDidDisappear?: VoidCallback--><!--Device-DialogBaseOptions-onDidDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

Callback function before the dialog open animation starts.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-onWillAppear?: VoidCallback--><!--Device-DialogBaseOptions-onWillAppear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

Callback function before the dialog close animation starts.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-onWillDisappear?: VoidCallback--><!--Device-DialogBaseOptions-onWillDisappear?: VoidCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignment

```TypeScript
alignment?: DialogBaseAlignment
```

Alignment of the dialog.

**Type:** [DialogBaseAlignment](arkts-arkui-arkui-dialog-dialogbasealignment-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-alignment?: DialogBaseAlignment--><!--Device-DialogBaseOptions-alignment?: DialogBaseAlignment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

Whether to allow dismissal by touching the mask or pressing the Back button.

**Type:** boolean

**Default:** true

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-autoCancel?: boolean--><!--Device-DialogBaseOptions-autoCancel?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the dialog box. <br>Setting this parameter to BlurStyle.NONE disables the background blur.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.COMPONENT_ULTRA_THICK

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-backgroundBlurStyle?: BlurStyle--><!--Device-DialogBaseOptions-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

Background blur style with options.

**Type:** [BackgroundBlurStyleOptions](../arkts-components/arkts-arkui-common-comp-backgroundblurstyleoptions-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-DialogBaseOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the dialog box. <br>When backgroundColor is set to a non-transparent color, backgroundBlurStyle must be set to BlurStyle.NONE.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-backgroundColor?: ResourceColor--><!--Device-DialogBaseOptions-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

Background effect with options.

**Type:** [BackgroundEffectOptions](../arkts-components/arkts-arkui-common-comp-backgroundeffectoptions-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-DialogBaseOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors
```

Border color of the dialog box.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; EdgeColors &#124; [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md)

**Default:** Color.Black

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors--><!--Device-DialogBaseOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses
```

Border radius of the background.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](arkts-arkui-localizedborderradiuses-i.md)

**Default:** { topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' }

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-borderRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-DialogBaseOptions-borderRadius?: Dimension | BorderRadiuses | LocalizedBorderRadiuses-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

Border style of the dialog box.

**Type:** [BorderStyle](arkts-arkui-borderstyle-e.md) &#124; EdgeStyles

**Default:** BorderStyle.Solid

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-DialogBaseOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths
```

Border width of the dialog box.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**Default:** 0

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths--><!--Device-DialogBaseOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: DialogBaseController
```

Dialog controller.

**Type:** [DialogBaseController](arkts-arkui-arkui-dialog-dialogbasecontroller-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-controller?: DialogBaseController--><!--Device-DialogBaseOptions-controller?: DialogBaseController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dialogTransition

```TypeScript
dialogTransition?: TransitionEffect
```

Dialog transition parameters for opening/closing the dialog content area.

**Type:** [TransitionEffect](../arkts-components/arkts-arkui-common-comp-transitioneffect-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-dialogTransition?: TransitionEffect--><!--Device-DialogBaseOptions-dialogTransition?: TransitionEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayModeInSubWindow

```TypeScript
displayModeInSubWindow?: DialogDisplayMode
```

Defines the dialog display mode when show in subwindow.

**Type:** [DialogDisplayMode](arkts-arkui-dialogdisplaymode-e.md)

**Default:** DialogDisplayMode.SCREEN_BASED

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-displayModeInSubWindow?: DialogDisplayMode--><!--Device-DialogBaseOptions-displayModeInSubWindow?: DialogDisplayMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Whether to enable the hover mode.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-enableHoverMode?: boolean--><!--Device-DialogBaseOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

Whether the dialog box can get focus.

**Type:** boolean

**Default:** true

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-focusable?: boolean--><!--Device-DialogBaseOptions-focusable?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

Height of the dialog box.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-height?: Dimension--><!--Device-DialogBaseOptions-height?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Display area of the dialog box in hover mode.

**Type:** [HoverModeAreaType](../arkts-components/arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-hoverModeArea?: HoverModeAreaType--><!--Device-DialogBaseOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

Overlay effect for the page-level dialog box.

**Type:** ImmersiveMode

**Default:** ImmersiveMode.DEFAULT

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-immersiveMode?: ImmersiveMode--><!--Device-DialogBaseOptions-immersiveMode?: ImmersiveMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

Whether the dialog box is a modal.

**Type:** boolean

**Default:** true

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-isModal?: boolean--><!--Device-DialogBaseOptions-isModal?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidDistance

```TypeScript
keyboardAvoidDistance?: LengthMetrics
```

Distance between the dialog and system keyboard.

**Type:** LengthMetrics

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-keyboardAvoidDistance?: LengthMetrics--><!--Device-DialogBaseOptions-keyboardAvoidDistance?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

Keyboard avoid mode.

**Type:** KeyboardAvoidMode

**Default:** KeyboardAvoidMode.DEFAULT

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-DialogBaseOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

Display level of the dialog box.

**Type:** LevelMode

**Default:** LevelMode.OVERLAY

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-levelMode?: LevelMode--><!--Device-DialogBaseOptions-levelMode?: LevelMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelOrder

```TypeScript
levelOrder?: LevelOrder
```

Display order of the dialog.

**Type:** LevelOrder

**Default:** The value returned by LevelOrder.clamp(0)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-levelOrder?: LevelOrder--><!--Device-DialogBaseOptions-levelOrder?: LevelOrder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: number
```

Unique ID of the node under the display level for the page-level dialog box. The value should be an integer. <br>This parameter takes effect only when levelMode is set to LevelMode.EMBEDDED.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-levelUniqueId?: int--><!--Device-DialogBaseOptions-levelUniqueId?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

Mask color of the dialog.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-maskColor?: ResourceColor--><!--Device-DialogBaseOptions-maskColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskRect

```TypeScript
maskRect?: Rectangle
```

Mask area of the dialog box. Events outside the mask area are transparently transmitted.

**Type:** [Rectangle](../arkts-components/arkts-arkui-common-comp-rectangle-i.md)

**Default:** { x: 0, y: 0, width: '100%', height: '100%' }

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-maskRect?: Rectangle--><!--Device-DialogBaseOptions-maskRect?: Rectangle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskTransition

```TypeScript
maskTransition?: TransitionEffect
```

Mask transition parameters for opening/closing the mask.

**Type:** [TransitionEffect](../arkts-components/arkts-arkui-common-comp-transitioneffect-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-maskTransition?: TransitionEffect--><!--Device-DialogBaseOptions-maskTransition?: TransitionEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the dialog relative to the alignment position.

**Type:** Offset

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-offset?: Offset--><!--Device-DialogBaseOptions-offset?: Offset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DialogDismissal>
```

Callback for interactive closure of the dialog box. <br>If this callback is registered, the dialog box will not be closed immediately after the user touches the mask or the Back button. The reason parameter in the callback is used to determine whether the dialog can be closed.

**Type:** Callback&lt;[DialogDismissal](arkts-arkui-arkui-dialog-dialogdismissal-i.md)&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-onWillDismiss?: Callback<DialogDismissal>--><!--Device-DialogBaseOptions-onWillDismiss?: Callback<DialogDismissal>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Shadow of the dialog box.

**Type:** [ShadowOptions](../arkts-components/arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](../arkts-components/arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-DialogBaseOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to display in a subwindow. <br>isModal = true and showInSubWindow = true cannot be used at the same time.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-showInSubWindow?: boolean--><!--Device-DialogBaseOptions-showInSubWindow?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for dialog. Different materials have different effects, which can influence backgroundColor, border, shadow, and other visual attributes of dialog.

**Type:** [SystemUiMaterial](../arkts-components/arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-systemMaterial?: SystemUiMaterial--><!--Device-DialogBaseOptions-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Width of the dialog box.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-DialogBaseOptions-width?: Dimension--><!--Device-DialogBaseOptions-width?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
