# SheetOptions

```TypeScript
declare interface SheetOptions extends BindOptions
```

Optional attributes of the sheet. Inherits from [BindOptions](arkts-arkui-common-comp-bindoptions-i.md).

**Inheritance/Implementation:** SheetOptions extends [BindOptions](arkts-arkui-common-comp-bindoptions-i.md)

**Since:** 10

<!--Device-unnamed-declare interface SheetOptions extends BindOptions--><!--Device-unnamed-declare interface SheetOptions extends BindOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shouldDismiss

```TypeScript
shouldDismiss?: (sheetDismiss: SheetDismiss) => void
```

Callback function when the sheet interactive dismiss

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-shouldDismiss?: (sheetDismiss: SheetDismiss) => void--><!--Device-SheetOptions-shouldDismiss?: (sheetDismiss: SheetDismiss) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sheetDismiss | [SheetDismiss](arkts-arkui-common-comp-sheetdismiss-i.md) | Yes |  |

## blurStyle

```TypeScript
blurStyle?: BlurStyle
```

Defines sheet background blur Style

**Type:** [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)

**Default:** BlurStyle.NONE

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-blurStyle?: BlurStyle--><!--Device-SheetOptions-blurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors
```

Defines the sheet's border color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; EdgeColors &#124; [LocalizedEdgeColors](../arkts-apis/arkts-arkui-localizededgecolors-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors--><!--Device-SheetOptions-borderColor?: ResourceColor | EdgeColors | LocalizedEdgeColors-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderStyle

```TypeScript
borderStyle?: BorderStyle | EdgeStyles
```

Defines the sheet's border style.

**Type:** [BorderStyle](../arkts-apis/arkts-arkui-borderstyle-e.md) &#124; EdgeStyles

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-borderStyle?: BorderStyle | EdgeStyles--><!--Device-SheetOptions-borderStyle?: BorderStyle | EdgeStyles-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths
```

Defines the sheet's border width.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](../arkts-apis/arkts-arkui-localizededgewidths-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths--><!--Device-SheetOptions-borderWidth?: Dimension | EdgeWidths | LocalizedEdgeWidths-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## detents

```TypeScript
detents?: [(SheetSize | Length), (SheetSize | Length)?, (SheetSize | Length)?]
```

Defines sheet detents

**Type:** [(SheetSize &#124; Length), (SheetSize &#124; Length)?, (SheetSize &#124; Length)?]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-detents?: [(SheetSize | Length), (SheetSize | Length)?, (SheetSize | Length)?]--><!--Device-SheetOptions-detents?: [(SheetSize | Length), (SheetSize | Length)?, (SheetSize | Length)?]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## detentSelection

```TypeScript
detentSelection?: SheetSize | Length
```

Select a detent from detents property

**Type:** [SheetSize](arkts-arkui-common-comp-sheetsize-e.md) &#124; [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** detents[0]

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SheetOptions-detentSelection?: SheetSize | Length--><!--Device-SheetOptions-detentSelection?: SheetSize | Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dragBar

```TypeScript
dragBar?: boolean
```

Defines whether the control bar is displayed.

**Type:** boolean

**Default:** true

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SheetOptions-dragBar?: boolean--><!--Device-SheetOptions-dragBar?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## effectEdge

```TypeScript
effectEdge?: number
```

Sets whether the sheet edge has spring effect.

**Type:** number

**Default:** 3

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SheetOptions-effectEdge?: number--><!--Device-SheetOptions-effectEdge?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableFloatingDragBar

```TypeScript
enableFloatingDragBar?: boolean
```

Defines whether the sheet dragbar is floating, when it's displayed.

**Type:** boolean

**Default:** false

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SheetOptions-enableFloatingDragBar?: boolean--><!--Device-SheetOptions-enableFloatingDragBar?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Defines whether to respond to the hover mode.

**Type:** boolean

**Default:** false

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-SheetOptions-enableHoverMode?: boolean--><!--Device-SheetOptions-enableHoverMode?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableOutsideInteractive

```TypeScript
enableOutsideInteractive?: boolean
```

Set whether interaction is allowed outside the sheet

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-enableOutsideInteractive?: boolean--><!--Device-SheetOptions-enableOutsideInteractive?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: SheetSize | Length
```

Defines sheet height

**Type:** [SheetSize](arkts-arkui-common-comp-sheetsize-e.md) &#124; [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** SheetSize.LARGE

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SheetOptions-height?: SheetSize | Length--><!--Device-SheetOptions-height?: SheetSize | Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hoverModeArea

```TypeScript
hoverModeArea?: HoverModeAreaType
```

Defines the sheet's display area in hover mode.

**Type:** [HoverModeAreaType](arkts-arkui-common-comp-hovermodeareatype-e.md)

**Default:** HoverModeAreaType.BOTTOM_SCREEN

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-SheetOptions-hoverModeArea?: HoverModeAreaType--><!--Device-SheetOptions-hoverModeArea?: HoverModeAreaType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: SheetKeyboardAvoidMode
```

Determine the mode of sheet how to avoid keyboard.

**Type:** [SheetKeyboardAvoidMode](arkts-arkui-common-comp-sheetkeyboardavoidmode-e.md)

**Default:** SheetKeyboardAvoidMode.TRANSLATE_AND_SCROLL

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-SheetOptions-keyboardAvoidMode?: SheetKeyboardAvoidMode--><!--Device-SheetOptions-keyboardAvoidMode?: SheetKeyboardAvoidMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: ResourceColor
```

Defines sheet maskColor

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SheetOptions-maskColor?: ResourceColor--><!--Device-SheetOptions-maskColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modalTransition

```TypeScript
modalTransition?: ModalTransition
```

Defines transition type when preferType is SheetType.CONTENT_COVER

**Type:** [ModalTransition](arkts-arkui-common-comp-modaltransition-e.md)

**Default:** ModalTransition.DEFAULT

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SheetOptions-modalTransition?: ModalTransition--><!--Device-SheetOptions-modalTransition?: ModalTransition-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: SheetMode
```

Determine the level sheet shows, whether sheet should be displayed within the page

**Type:** [SheetMode](arkts-arkui-common-comp-sheetmode-e.md)

**Default:** SheetMode.OVERLAY

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-mode?: SheetMode--><!--Device-SheetOptions-mode?: SheetMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDetentsDidChange

```TypeScript
onDetentsDidChange?: Callback<number>
```

Called when detents of the sheet changed

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-onDetentsDidChange?: Callback<number>--><!--Device-SheetOptions-onDetentsDidChange?: Callback<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onHeightDidChange

```TypeScript
onHeightDidChange?: Callback<number>
```

Called when height of the sheet is changed

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-onHeightDidChange?: Callback<number>--><!--Device-SheetOptions-onHeightDidChange?: Callback<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTypeDidChange

```TypeScript
onTypeDidChange?: Callback<SheetType>
```

Called when the sheet type changed

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[SheetType](arkts-arkui-common-comp-sheettype-e.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-onTypeDidChange?: Callback<SheetType>--><!--Device-SheetOptions-onTypeDidChange?: Callback<SheetType>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWidthDidChange

```TypeScript
onWidthDidChange?: Callback<number>
```

Called when width of the sheet changed

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-onWidthDidChange?: Callback<number>--><!--Device-SheetOptions-onWidthDidChange?: Callback<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: Callback<DismissSheetAction>
```

Callback function when the sheet will dismiss

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[DismissSheetAction](arkts-arkui-common-comp-dismisssheetaction-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-onWillDismiss?: Callback<DismissSheetAction>--><!--Device-SheetOptions-onWillDismiss?: Callback<DismissSheetAction>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillSpringBackWhenDismiss

```TypeScript
onWillSpringBackWhenDismiss?: Callback<SpringBackAction>
```

Sheet springs back callback when dismiss

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[SpringBackAction](arkts-arkui-common-comp-springbackaction-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-onWillSpringBackWhenDismiss?: Callback<SpringBackAction>--><!--Device-SheetOptions-onWillSpringBackWhenDismiss?: Callback<SpringBackAction>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

The placement of popup sheet type. Supports all positions defined in Placement.

**Type:** [Placement](../arkts-apis/arkts-arkui-placement-e.md)

**Default:** Placement.Bottom

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SheetOptions-placement?: Placement--><!--Device-SheetOptions-placement?: Placement-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placementOnTarget

```TypeScript
placementOnTarget?: boolean
```

placement On target node

**Type:** boolean

**Default:** true

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SheetOptions-placementOnTarget?: boolean--><!--Device-SheetOptions-placementOnTarget?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## preferType

```TypeScript
preferType?: SheetType
```

Defines the sheet prefer type

**Type:** [SheetType](arkts-arkui-common-comp-sheettype-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-preferType?: SheetType--><!--Device-SheetOptions-preferType?: SheetType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses
```

Defines sheet radius

**Type:** LengthMetrics &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SheetOptions-radius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses--><!--Device-SheetOptions-radius?: LengthMetrics | BorderRadiuses | LocalizedBorderRadiuses-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radiusRenderStrategy

```TypeScript
radiusRenderStrategy?: RenderStrategy
```

Define strategy for drawing rounded corners. NOTE

1. **RenderStrategy.FAST**: The current component and its child components will be drawn directly
onto the canvas with rounded corners applied.
2. **RenderStrategy.OFFSCREEN**: The current component and its child components will first be rendered onto
an off-screen canvas, then undergo a rounded corner clipping, and finally be drawn onto the main canvas.

**Type:** [RenderStrategy](../arkts-apis/arkts-arkui-renderstrategy-e.md)

**Default:** RenderStrategy.FAST

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-SheetOptions-radiusRenderStrategy?: RenderStrategy--><!--Device-SheetOptions-radiusRenderStrategy?: RenderStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollBarState

```TypeScript
scrollBarState?: BarState
```

Scroll bar display state of the built-in Scroll component in bindSheet. Default value: **BarState.Off**.

**Type:** [BarState](../arkts-apis/arkts-arkui-barstate-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-SheetOptions-scrollBarState?: BarState--><!--Device-SheetOptions-scrollBarState?: BarState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollSizeMode

```TypeScript
scrollSizeMode?: ScrollSizeMode
```

Determine sheet scroll size mode.

**Type:** [ScrollSizeMode](arkts-arkui-common-comp-scrollsizemode-e.md)

**Default:** ScrollSizeMode.FELLOW_DETEND

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-scrollSizeMode?: ScrollSizeMode--><!--Device-SheetOptions-scrollSizeMode?: ScrollSizeMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

Defines the sheet's shadow.

**Type:** [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-SheetOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showClose

```TypeScript
showClose?: boolean | Resource
```

Defines whether the close icon is displayed

**Type:** boolean &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-showClose?: boolean | Resource--><!--Device-SheetOptions-showClose?: boolean | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

Whether to display in the sub window.

**Type:** boolean

**Default:** false

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-SheetOptions-showInSubWindow?: boolean--><!--Device-SheetOptions-showInSubWindow?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for sheet. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of sheet.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SheetOptions-systemMaterial?: SystemUiMaterial--><!--Device-SheetOptions-systemMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: SheetTitleOptions | CustomBuilder
```

Defines the sheet title

**Type:** [SheetTitleOptions](arkts-arkui-common-comp-sheettitleoptions-i.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-title?: SheetTitleOptions | CustomBuilder--><!--Device-SheetOptions-title?: SheetTitleOptions | CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## titleBarHoverMode

```TypeScript
titleBarHoverMode?: SheetTitleBarHoverMode
```

Title bar hover mode.  
- STANDARD: The title bar and content are arranged vertically without overlapping.  
- STACK: The title bar overlays on top of the content. Developers need to add padding to avoid occlusion.  
Default value: **SheetTitleBarHoverMode.STANDARD**.

**Type:** [SheetTitleBarHoverMode](arkts-arkui-common-comp-sheettitlebarhovermode-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-SheetOptions-titleBarHoverMode?: SheetTitleBarHoverMode--><!--Device-SheetOptions-titleBarHoverMode?: SheetTitleBarHoverMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## uiContext

```TypeScript
uiContext?: UIContext
```

The UIContext that the sheet belongs to

**Type:** [UIContext](arkts-arkui-common-comp-uicontext-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-uiContext?: UIContext--><!--Device-SheetOptions-uiContext?: UIContext-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

Defines the sheet's width.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-width?: Dimension--><!--Device-SheetOptions-width?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
