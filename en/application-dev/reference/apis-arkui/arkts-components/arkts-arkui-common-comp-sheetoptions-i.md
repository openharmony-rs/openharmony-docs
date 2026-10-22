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

Interactive dismissal callback of the sheet.

**Note:** 

When the user performs pull-down dismissal, side-swipe dismissal, tapping the mask to dismiss, or tapping the close button, if the callback is registered, the modal window is not dismissed immediately. To dismiss the sheet, call the shouldDismiss.dismiss() method in the callback.

If this callback is not registered, when the user performs pull-down dismissal, side-swipe dismissal, tapping the mask to dismiss, or tapping the close button, the sheet is dismissed normally without any other behavior.

Side-swipe dismissal also includes side sliding (left/right swipe), the three-key Back button, and the keyboard ESC key.

When the onWillSpringBackWhenDismiss callback is also registered, the spring-back behavior of pull-down dismissal is controlled by onWillSpringBackWhenDismiss.

shouldDismiss and [onWillDismiss](arkts-arkui-common-comp-sheetoptions-i.md) are both interactive dismissal callbacks of the sheet. Registering both is not recommended. If you need to obtain the type of the dismissal operation and decide whether to dismiss, use [onWillDismiss](arkts-arkui-common-comp-sheetoptions-i.md) instead of shouldDismiss.

It is recommended to use this in the [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) scenario.

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

Blur background of the sheet panel. Different BlurStyle enum values correspond to blur effects of different intensities (for example, Thin for slight blur, Regular for normal blur, and Thick for heavy blur). By default, there is no blur background.

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

Sets the border color of the sheet.

Default value: Color.Black

If the borderColor attribute is used, it must be used together with the borderWidth attribute. If borderWidth is not set, the border color is invisible because the default value of borderWidth is 0.

**Note:** 

For a bottom sheet, the bottom border color does not take effect. When the systemMaterial attribute is set, the effect of this attribute may be overridden. Using it together with systemMaterial is not recommended.

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

Sets the border style of the sheet.

Default value: BorderStyle.Solid

If the borderStyle attribute is used, it must be used together with the borderWidth attribute. If borderWidth is not set, the border style is invisible because the default value of borderWidth is 0.

**Note:** 

For a bottom sheet, the bottom border style does not take effect.

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

Sets the border width of the sheet.

The border width can be set for the four borders separately.

Default value: 0vp

Percentage parameter: sets the border width of the sheet as a percentage of the sheet width.

When the left and right borders of the sheet are greater than the sheet width, and the top and bottom borders of the sheet are greater than the sheet height, the display may not meet expectations.

**Note:** 

For a bottom sheet, the bottom border width does not take effect. When the systemMaterial attribute is set, the effect of this attribute may be overridden. Using it together with systemMaterial is not recommended. The value range is non-negative numbers. Setting a negative value does not take effect.

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

Detents for switching the height of the sheet. If this attribute is not set, the height attribute is used by default to determine the sheet height.

**Note:** 

For a bottom sheet, the height attribute does not take effect when detents is set.

Since API version 12, this attribute takes effect for a bottom sheet in landscape orientation.

For a bottom sheet in portrait orientation, this attribute takes effect, and the first height in the tuple is the initial height.

The panel can be slid by hand to switch detents. After release, whether it slides to the target detent is determined by two conditions: velocity and distance. If the velocity exceeds the threshold, the sheet slides to the target detent in the direction consistent with the hand velocity. If the velocity is below the threshold, the distance condition is introduced: when the displacement distance is greater than 1/2 of the distance between the current position and the target position, the sheet slides to the target detent in the direction consistent with the hand velocity; when the displacement distance is less than 1/2 of the distance between the current position and the target position, the sheet returns to the current detent. Velocity threshold: 1000 px/s. Distance threshold: 50%.

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

Supports switching detents without gestures.

**Default value:** detents[0].

**Note:** 

1. The value range of this API is the range of the detents array. If the set value is outside the detents range, this API does not take effect.
2. When SheetSize.FIT_CONTENT is set, this API does not take effect.
3. It is not recommended to use gesture-based detent switching and this API-based detent switching at the same time. When both take effect, the detent switching behavior may be unpredictable.

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

Whether to display the drag bar.

Default value: true

true: displays the drag bar.

false: does not display the drag bar.

**Note:** 

When the detents attribute of the sheet panel is set to multiple different heights and takes effect, the drag bar is displayed by default. When detents is not set to multiple detents, the drag bar is not displayed by default.

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

Sets the edge spring-back effect of the content area of the sheet panel. Supports taking effect on a single edge.

**Default value**: By default, both edges take effect, that is, [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).START | [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).END (value 3).

**Note:** 

1. Only the top edge takes effect: [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).START.
2. Only the bottom edge takes effect: [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).END.
3. Both edges take effect: [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).START | [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).END (value 3).
4. Neither edge takes effect: [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).START & [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).END (value 0).

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

Whether the drag bar is displayed in a floating manner. true means floating display, and false means non-floating display.

Default value: false

**Note:** 

The floating effect takes effect only in the scenario where the drag bar is displayed, and the drag bar does not occupy space.

When title is set to [CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8), enableFloatingDragBar is always false.

The side sheet style does not support the floating drag bar.

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

Whether to respond to the hover state.

Default value: false, which means no response by default.

On 2-in-1 devices, the default value is true.

true: responds to the hover state.

false: does not respond to the hover state.

**Note:** 

The bottom sheet style, follow-hand sheet style, side sheet style, and full-screen modal style do not respond to the hover state. The subwindow mode does not support the hover state.

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

Whether the underlying page is allowed to be interactive when the sheet is displayed.

**Note:** 

When set to true, interaction is allowed and no mask is displayed. When set to false, interaction is not allowed and a mask is displayed. If this attribute is not set, the bottom sheet and center sheet do not allow interaction by default, and the follow-hand sheet allows interaction by default. When set to true, maskColor does not take effect.

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

Height of the sheet. The default value is LARGE.

**Note:** 

1. Since API version 14, when a bottom sheet is in landscape orientation, the maximum height is 8 vp from the top
of the screen if there is no status bar, and 8 vp from the status bar if there is a status bar.
2. For a bottom sheet, this attribute does not take effect when detents is set.
3. For a bottom sheet in portrait orientation, the maximum height is 8 vp from the status bar.
4. For center sheets and follow-hand sheets, setting the type to SheetSize.LARGE or SheetSize.MEDIUM does not
take effect, and the default height of 560 vp is displayed.
5. For center sheets and follow-hand sheets, the minimum height is 320 vp and the maximum height is 90% of the
short side of the window.
6. For center sheets and follow-hand sheets, when the height is set using Length, the maximum height is displayed
if the height is greater than the maximum height, and the minimum height is displayed if the height is less than the minimum height.
7. If the sheet uses the SheetSize.FIT_CONTENT adaptive mode and the type is set to center sheet or follow-hand
sheet, in API version 22 and earlier, the maximum height is displayed when the height is greater than the maximum height, and the minimum height is displayed when the height is less than the minimum height. Since API version 23, the maximum height is displayed when the height is greater than the maximum height, and the actual adaptive height takes effect when the height is less than the minimum height.
8. For the side sheet style, only the full-screen height is supported.
9. For the full-screen modal style, only the full-screen height is supported.

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

Default display area of the sheet in the hover state. This attribute takes effect only when [enableHoverMode](arkts-arkui-common-comp-sheetoptions-i.md) is set to true.

Default value: HoverModeAreaType.BOTTOM_SCREEN

On 2-in-1 devices, the default value is HoverModeAreaType.TOP_SCREEN.

**Note:** 

The side sheet style and full-screen sheet style do not support the hover state area setting.

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

Sets the avoidance mode for the soft keyboard when the sheet activates the input method.

**Default value:** TRANSLATE_AND_SCROLL

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

Color of the background mask of the sheet.

Default value: $r('sys.color.ohos_id_color_mask_thin').

**Note:** 

When enableOutsideInteractive is set to true, maskColor does not take effect.

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

System transition mode of the full-screen modal style of bindSheet. This attribute takes effect only when [preferType](arkts-arkui-common-comp-sheetoptions-i.md) is set to [SheetType.CONTENT_COVER](arkts-arkui-common-comp-sheettype-e.md) (full-screen sheet style). Setting this attribute for other sheet styles does not take effect.

Default value: ModalTransition.DEFAULT

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

Sets the display layer of the sheet.

Default value: SheetMode.OVERLAY

**Note:** 

1. During the display of the sheet, the mode attribute does not support dynamic switching. The display layers of the two modes are completely different, and the same sheet cannot be transformed from one layer to another during display. It is recommended to fix the mode value based on the requirement.

  2. When SheetMode.EMBEDDED is set, setting the UIContext attribute is not supported, because the display layer effects of the two conflict with each other.
3. When a sheet is started using [openBindSheet](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#openbindsheet), if no valid targetId is passed, setting SheetMode.EMBEDDED is not supported, and the default is SheetMode.OVERLAY.

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

Callback for the detent change of the sheet. If this attribute is not set, the callback is not triggered.

**Note:** 

This callback is triggered only in the bottom sheet scenario, and the final height is returned when the detent changes.

The return value is in px.

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

Callback for the height change of the sheet. If this attribute is not set, the callback is not triggered.

**Note:** 

For a bottom sheet, the height of each frame is returned only when the detent changes and when the sheet is dragged by hand. When the sheet is pulled up and when the soft keyboard is avoided, only the final height is returned. For other sheets, only the final height is returned when the sheet is pulled up.

The return value is in px.

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

Callback for the style change of the sheet.

**Note:** 

The final style is returned when the style changes.

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

Callback for the width change of the sheet. If this attribute is not set, the callback is not triggered.

**Note:** 

The final width is returned when the width changes.

The return value is in px.

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

Interactive dismissal callback of the sheet. Allows developers to register a callback to obtain the type of the dismissal operation and decide whether to dismiss the sheet.

**Note:** 

When the user performs pull-down dismissal, side-swipe dismissal, tapping the mask to dismiss, or tapping the close button, if the callback is registered, the page is not dismissed immediately. Instead, the developer determines the type of the dismissal operation through the reason parameter in the callback [DismissSheetAction](arkts-arkui-common-comp-dismisssheetaction-i.md), and then decides whether to dismiss the sheet based on the specific reason.

If this callback is not registered, when the user performs a dismissal operation, the sheet is dismissed normally without any other behavior.

Side-swipe dismissal also includes side sliding (left/right swipe), the three-key Back button, and the keyboard ESC key.

In the onWillDismiss callback, onWillDismiss interception cannot be performed again.

It is recommended to use this in the [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) scenario.

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

Callback for controlling the spring-back effect before the interactive dismissal of the sheet. Allows developers to register a callback to control the spring-back effect when the sheet is interactively dismissed. It is recommended to use this in the [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) scenario or in scenarios where custom dismissal interaction feedback is required.

**Note:** 

When the user triggers a pull-down dismissal operation and both this callback and shouldDismiss or onWillDismiss are registered, the developer controls whether the sheet springs back during pull-down dismissal. In the callback, the spring-back effect can be implemented by calling springBack. The spring-back effect can also be canceled by not calling springBack.

If this callback is not registered but shouldDismiss or onWillDismiss is registered, the spring-back effect is triggered by default during pull-down dismissal, and after the spring-back, whether the sheet is dismissed is determined by the callback behavior in shouldDismiss or onWillDismiss.

If this callback is not registered and neither shouldDismiss nor onWillDismiss is registered, the sheet is dismissed by default during pull-down dismissal.

For the side sheet style, springBack takes effect in the side-swipe dismissal scenario.

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

Sets the display position of the popup-style sheet relative to the target. For the side sheet style, this attribute supports only the bubble style.

Default value: Placement.Bottom

**Note:** 

1. On the premise that the specified position can accommodate the sheet size, the popup-style sheet is displayed preferentially based on the set placement. If this is not feasible, the display position is adjusted following the rule of vertical flipping first and then attempting a 90-degree horizontal rotation. Taking the preset direction of bottom as an example, the adjustment order is: bottom, top, right, left.
2. If the set alignment causes the component layout to exceed the window range, the component is shifted horizontally or vertically based on the alignment until it is fully displayed within the window.
3. If the current popup-style sheet cannot be accommodated in any of the four directions, the handling follows the placementOnTarget attribute set by the developer:

1) If the attribute value is true, the sheet is translated in the mirror direction of the set placement until it can be fully displayed. 2) If the attribute value is false, among the four directions, the direction that can fully display the sheet width and has the largest remaining height is selected, and the sheet height is adjusted to fit the current direction to ensure that the sheet can be placed, while keeping the alignment corresponding to the preset placement unchanged.

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

When the popup-style sheet cannot be accommodated in any of the four directions in the current window, sets whether to allow it to cover the target node. For the side sheet style, this attribute supports only the bubble style. This attribute must be used together with the [placement](arkts-arkui-common-comp-sheetoptions-i.md) attribute, and the handling of placementOnTarget is based on the display direction set by placement.

Default value: true

true: allows it to cover the target node.

false: does not allow it to cover the target node.

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

Style of the sheet.

**Note:** 

Display types supported by the sheet in different windows:

1. Width &lt; 600 vp: bottom and full-screen. The default style is bottom.
2. 600 vp &lt;= width &lt; 840 vp: bottom, center, follow-hand, side, and full-screen. The default style is center.
3. Width &gt;= 840 vp: bottom, center, follow-hand, side, and full-screen. The default style is follow-hand.
4. Since API version 20, when the window width is greater than 600 vp, preferType can be set to SheetType.SIDE.
5. Since API version 20, preferType can be set to SheetType.CONTENT_COVER, which supports the
full-screen modal style.

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

Sets the corner radius of the sheet.

It is not recommended to set four unequal corner radii. The visual experience is best when the corner radii are equal.

**Default value**: 32vp

**Note:** 

1. The sheet is displayed based on the set corner radius value. If it is not set, the default value is used. The bottom style does not display the two bottom corners of the sheet, and even if the two bottom corners are set, they do not take effect.
2. After setting the corner radii for the four directions separately, if the radius value of a direction is invalid (for example, a negative value), the radius of the abnormal direction is reset to the default value, and the radius of the non-abnormal directions remains the set value. If the uniformly set radius value is invalid (for example, a negative value), the radii of all four directions are reset to the default value.
3. When the radius is set as a percentage, the width of the sheet is used as the reference.
4. When the corner radius is greater than half of the sheet width, the corner radius takes the value of half of the sheet width.
5. When the sheet height is too small and the corner radius is set too large, the display may be abnormal.

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

Sets the mode for rendering the component corners.

Default value: RenderStrategy.FAST

**Note:** When the sheet has blur set, setting OFFSCREEN (off-screen mode) can resolve the abnormal display effect in the top or top corner area of the sheet. The popup style does not support setting the component corner rendering mode.

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

Sets the refresh timing of the content area when the sheet panel is slid.

Default value: ScrollSizeMode.FOLLOW_DETENT

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

Sets the shadow of the sheet. You can customize the shadow parameters through ShadowOptions, or use a preset shadow style through ShadowStyle (for example, OUTER_FLOATING_SM for a small outer floating shadow and OUTER_FLOATING_MD for a medium outer floating shadow).

**Default value**: On non-2-in-1 devices, there is no shadow by default. On 2-in-1 devices, the default value is ShadowStyle.OUTER_FLOATING_SM.

**Note:** 

When the systemMaterial attribute is set, the effect of this attribute may be overridden. Using it together with systemMaterial is not recommended. The full-screen modal style (CONTENT_COVER) does not support shadows, and this attribute does not take effect.

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

Whether to display the close icon.

On 2-in-1 devices, there is no button panel by default.

Default value: true.

true: displays the close icon.

false: does not display the close icon.

**Note:** 

1. Resource must be of the boolean type.
2. The full-screen modal style (CONTENT_COVER) does not support displaying the close button, and this
attribute does not take effect.

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

Whether the sheet is displayed in an independent subwindow.

Default value: false

**Note:** 

1. If the attribute value is true, the sheet can be displayed in an independent subwindow and can exceed the application window range.
2. If the attribute value is false, the sheet can be displayed only within the application window range.
3. It is not recommended to nest another sheet with showInSubWindow set to true inside a sheet with showInSubWindow set to true, because the sheet may affect the behavior of other components.
4. It is not recommended to use picker components such as CalendarPicker, CalendarPickerDialog, DatePickerDialog, TextPickerDialog, and TimePickerDialog in a sheet with showInSubWindow set to true, because the sheet affects the behavior of these components.
5. During the display of the sheet, this attribute does not support dynamic switching.

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

Sets the system material of the component.

Default value: undefined, which clears the material effect set by this API.

**Note:** Different system materials correspond to different attribute effects. This API affects the background color [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor-1), border color [borderColor](arkts-arkui-common-comp-commonmethod-c.md#bordercolor), border width [borderWidth](arkts-arkui-common-comp-commonmethod-c.md#borderwidth), and shadow [shadow](arkts-arkui-common-comp-commonmethod-c.md#shadow-1). Using it together with the preceding APIs is not recommended. For a usage example, see [Example 10 (Setting the System Material for a Half-Modal)](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#example-10-setting-the-system-material-for-a-half-modal).

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

Title of the sheet panel.

**Note:** 

When title is set to CustomBuilder, enableFloatingDragBar is always false, and the floating drag bar is not supported.

The full-screen modal style (CONTENT_COVER) does not support displaying the title bar, and this attribute does not take effect. By default, there is no title.

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
- SAFE_AREA_PADDING: The title bar is placed in the safe area padding region. The content expands  
into the safe area, and the scroll content is clipped to the safe area. The default value is **SheetTitleBarHoverMode.STANDARD**. After [BIND_SHEET_EXPAND_SAFE_AREA](../arkts-apis/arkts-arkui-immersivestrategy-e.md#bind_sheet_expand_safe_area) is successfully set via [applyDefaultImmersiveStrategy](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#applydefaultimmersivestrategy), the default value is **SheetTitleBarHoverMode.SAFE_AREA_PADDING**.

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

Displays the sheet in the window corresponding to the UIContext instance. If this parameter is not passed, the sheet is displayed in the window corresponding to the current UIContext by default. Pass this parameter when the sheet needs to be displayed in a specified window.

**Note:** 

For a sheet started using [openBindSheet](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#openbindsheet), setting and updating this attribute is not supported. Setting this attribute is also not supported when SheetMode.EMBEDDED is set, because the display layer effects of the two conflict with each other.

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

Sets the width of the sheet. If this attribute is not set, the default width specification corresponding to each sheet style is used.

Percentage parameter: sets the width of the sheet as a percentage of the parent element width.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SheetOptions-width?: Dimension--><!--Device-SheetOptions-width?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
