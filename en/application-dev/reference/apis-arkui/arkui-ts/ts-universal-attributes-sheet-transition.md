# Sheet Transition
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=21fb9e079b1023fcdd94644c9006a9dfa64d9f96 translatedAt=2026-09-02T12:12:43.451Z -->

You can bind a sheet to a component through the **bindSheet** attribute. The sheet supports multiple styles, including bottom, center, follow-hand, side, and full-screen. When the component is inserted, you can set a custom or preset height to determine the sheet size. (Side sheets and full-screen sheets do not support custom heights.)

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - Route hopping is not supported.

## bindSheet

bindSheet(isShow: boolean, builder: CustomBuilder, options?: SheetOptions): T

Binds a sheet to a component. The **isShow** parameter controls whether the sheet is displayed, the **builder** parameter configures the content of the sheet, and the **options** parameter configures the optional attributes of the sheet.

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                       | Mandatory| Description                                                        |
| ------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| isShow  | boolean                          | Yes  | Whether to show the semi-modal page.<br>true: The semi-modal page is shown.<br>false: The semi-modal page is hidden.<br>Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).<br>Since API version 18, this parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).|
| builder | [CustomBuilder](ts-types.md#custombuilder8) | Yes  | Content of the sheet.                                        |
| options | [SheetOptions](#sheetoptions)               | No  | Optional attributes of the semi-modal page. If this parameter is not passed, no additional attributes are configured for the semi-modal page, and each attribute uses its default value.                                   |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

> **NOTE**
>
> 1. In non-two-way binding scenarios, dismissing the sheet by dragging does not change the value of the **isShow** parameter.
>
> 2. To keep the value of the **isShow** parameter synchronized with the sheet state, you are advised to use [$$](../../../ui/state-management/arkts-two-way-sync.md) for two-way binding of the **isShow** parameter. Since API version 18, this parameter supports [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters) for two-way binding of variables.
>
> 3. When the sheet is dragged upward in single-detent mode or switched to a higher detent in multi-detent mode, the content updates its display area after the drag or detent switch ends.
>
> 4. A sheet is a popup strictly bound to its host node. To achieve an effect similar to "displaying the sheet the moment the page is shown", ensure that the host node has been mounted to the component tree. If **isShow** is set to **true** before the host node is mounted, the sheet does not take effect. You are advised to use the [onAppear](ts-universal-events-show-hide.md#onappear) function to ensure that the sheet is displayed only after the host node is mounted.
> In particular, when [SheetMode](#sheetmode12) is set to EMBEDDED, in addition to the host node, ensure that the corresponding page node is successfully mounted.
>
> 5. The exit animation of a sheet does not support interruption, and no other gestures can be responded to while the animation is running. Currently, the exit animation uses a [spring curve](../../../ui/arkts-spring-curve.md), which has a visually subtle trailing animation. Therefore, when the sheet exits, the sheet page visually disappears, but the animation may not have finished yet. If you tap again to pull up the sheet at this time, it does not respond. You need to wait until the animation is completely finished before pulling up the sheet again.
>
## SheetOptions

Inherits from [BindOptions](#bindoptions).

Provides content configuration options of the sheet.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| Name             | Type                                      | Read-Only| Optional  | Description             |
| --------------- | --------------------------- | ------------- | ---- | --------------- |
| height          | [SheetSize](#sheetsize )&nbsp;\|&nbsp;[Length](ts-types.md#length) | No | Yes   | Height of the sheet. The default value is LARGE.<br>**Note:**<br>1. Since API version 14, when a bottom sheet is in landscape orientation, the maximum height is 8 vp from the top of the screen if there is no status bar, and 8 vp from the status bar if there is a status bar.<br>2. For a bottom sheet, this attribute does not take effect when detents is set.<br>3. For a bottom sheet in portrait orientation, the maximum height is 8 vp from the status bar.<br>4. For center sheets and follow-hand sheets, setting the type to SheetSize.LARGE or SheetSize.MEDIUM does not take effect, and the default height of 560 vp is displayed.<br>5. For center sheets and follow-hand sheets, the minimum height is 320 vp and the maximum height is 90% of the short side of the window.<br>6. For center sheets and follow-hand sheets, when the height is set using Length, the maximum height is displayed if the height is greater than the maximum height, and the minimum height is displayed if the height is less than the minimum height.<br>7. If the sheet uses the SheetSize.FIT_CONTENT adaptive mode and the type is set to center sheet or follow-hand sheet, in API version 22 and earlier, the maximum height is displayed when the height is greater than the maximum height, and the minimum height is displayed when the height is less than the minimum height. Since API version 23, the maximum height is displayed when the height is greater than the maximum height, and the actual adaptive height takes effect when the height is less than the minimum height.<br>8. For the side sheet style, only the full-screen height is supported.<br>9. For the full-screen modal style, only the full-screen height is supported.<br>**Atomic service API:** This API is supported in atomic services since API version 11. |
| detents<sup>11+</sup> | [([SheetSize](#sheetsize) \| [Length](ts-types.md#length)), ( [SheetSize](#sheetsize) \| [Length](ts-types.md#length))?, ([SheetSize](#sheetsize) \| [Length](ts-types.md#length))?] | No | Yes | Detents for switching the height of the sheet. If this attribute is not set, the height attribute is used by default to determine the sheet height.<br>**Note:**<br>For a bottom sheet, the height attribute does not take effect when detents is set.<br>Since API version 12, this attribute takes effect for a bottom sheet in landscape orientation.<br>For a bottom sheet in portrait orientation, this attribute takes effect, and the first height in the tuple is the initial height.<br>The panel can be slid by hand to switch detents. After release, whether it slides to the target detent is determined by two conditions: velocity and distance. If the velocity exceeds the threshold, the sheet slides to the target detent in the direction consistent with the hand velocity. If the velocity is below the threshold, the distance condition is introduced: when the displacement distance is greater than 1/2 of the distance between the current position and the target position, the sheet slides to the target detent in the direction consistent with the hand velocity; when the displacement distance is less than 1/2 of the distance between the current position and the target position, the sheet returns to the current detent. Velocity threshold: 1000 px/s. Distance threshold: 50%.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| preferType<sup>11+</sup> | [SheetType](#sheettype11) | No | Yes | Style of the sheet.<br>**Note:**<br>Display types supported by the sheet in different windows:<br>1. Width &lt; 600 vp: bottom and full-screen. The default style is bottom.<br>2. 600 vp &lt;= width &lt; 840 vp: bottom, center, follow-hand, side, and full-screen. The default style is center.<br>3. Width >= 840 vp: bottom, center, follow-hand, side, and full-screen. The default style is follow-hand.<br>4. Since API version 20, when the window width is greater than 600 vp, preferType can be set to SheetType.SIDE.<br>5. Since API version 20, preferType can be set to SheetType.CONTENT_COVER, which supports the full-screen modal style.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| showClose<sup>11+</sup> | boolean \| [Resource](ts-types.md#resource) | No | Yes | Whether to display the close icon.<br> On 2-in-1 devices, there is no button panel by default.<br> Default value: true.<br> true: displays the close icon.<br> false: does not display the close icon.<br>**Note:**<br>1. Resource must be of the boolean type.<br>2. The full-screen modal style (CONTENT_COVER) does not support displaying the close button, and this attribute does not take effect.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| dragBar         | boolean                                  | No | Yes    | Whether to display the drag bar.<br> Default value: true <br>true: displays the drag bar.<br>false: does not display the drag bar.<br>**Note:**<br>When the detents attribute of the sheet panel is set to multiple different heights and takes effect, the drag bar is displayed by default. When detents is not set to multiple detents, the drag bar is not displayed by default.<br>**Atomic service API:** This API is supported in atomic services since API version 11. |
| blurStyle<sup>11+</sup> | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | No | Yes | Blur background of the sheet panel. Different BlurStyle enum values correspond to blur effects of different intensities (for example, Thin for slight blur, Regular for normal blur, and Thick for heavy blur). By default, there is no blur background.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| maskColor | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Color of the background mask of the sheet.<br> Default value: $r('sys.color.ohos_id_color_mask_thin').<br>**Note:**<br>When enableOutsideInteractive is set to true, maskColor does not take effect.<br>**Atomic service API:** This API is supported in atomic services since API version 11. |
| title<sup>11+</sup> | [SheetTitleOptions](#sheettitleoptions11) \| [CustomBuilder](ts-types.md#custombuilder8) | No | Yes | Title of the sheet panel.<br>**Note:**<br>When title is set to CustomBuilder, enableFloatingDragBar is always false, and the floating drag bar is not supported.<br>The full-screen modal style (CONTENT_COVER) does not support displaying the title bar, and this attribute does not take effect. By default, there is no title.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| enableOutsideInteractive<sup>11+</sup> | boolean | No | Yes | Whether the underlying page is allowed to be interactive when the sheet is displayed.<br>**Note:**<br>When set to true, interaction is allowed and no mask is displayed. When set to false, interaction is not allowed and a mask is displayed. If this attribute is not set, the bottom sheet and center sheet do not allow interaction by default, and the follow-hand sheet allows interaction by default. When set to true, maskColor does not take effect.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| shouldDismiss<sup>11+</sup> | (sheetDismiss: [SheetDismiss](#sheetdismiss11)) => void | No | Yes | Interactive dismissal callback of the sheet.<br>**Note:**<br>When the user performs pull-down dismissal, side-swipe dismissal, tapping the mask to dismiss, or tapping the close button, if the callback is registered, the modal window is not dismissed immediately. To dismiss the sheet, call the shouldDismiss.dismiss() method in the callback.<br>If this callback is not registered, when the user performs pull-down dismissal, side-swipe dismissal, tapping the mask to dismiss, or tapping the close button, the sheet is dismissed normally without any other behavior.<br>Side-swipe dismissal also includes side sliding (left/right swipe), the three-key Back button, and the keyboard ESC key.<br>When the onWillSpringBackWhenDismiss callback is also registered, the spring-back behavior of pull-down dismissal is controlled by onWillSpringBackWhenDismiss.<br>shouldDismiss and [onWillDismiss](#sheetoptions) are both interactive dismissal callbacks of the sheet. Registering both is not recommended. If you need to obtain the type of the dismissal operation and decide whether to dismiss, use [onWillDismiss](#sheetoptions) instead of shouldDismiss.<br>It is recommended to use this in the [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) scenario.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| onWillDismiss<sup>12+</sup> | [Callback](./ts-types.md#callback12)<[DismissSheetAction](#dismisssheetaction12)> | No | Yes    | Interactive dismissal callback of the sheet. Allows developers to register a callback to obtain the type of the dismissal operation and decide whether to dismiss the sheet.<br>**Note:**<br>When the user performs pull-down dismissal, side-swipe dismissal, tapping the mask to dismiss, or tapping the close button, if the callback is registered, the page is not dismissed immediately. Instead, the developer determines the type of the dismissal operation through the reason parameter in the callback [DismissSheetAction](#dismisssheetaction12), and then decides whether to dismiss the sheet based on the specific reason.<br>If this callback is not registered, when the user performs a dismissal operation, the sheet is dismissed normally without any other behavior.<br>Side-swipe dismissal also includes side sliding (left/right swipe), the three-key Back button, and the keyboard ESC key.<br>In the onWillDismiss callback, onWillDismiss interception cannot be performed again.<br>It is recommended to use this in the [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) scenario.<br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| onWillSpringBackWhenDismiss<sup>12+</sup> | [Callback](./ts-types.md#callback12)<[SpringBackAction](#springbackaction12)> | No | Yes    | Callback for controlling the spring-back effect before the interactive dismissal of the sheet. Allows developers to register a callback to control the spring-back effect when the sheet is interactively dismissed. It is recommended to use this in the [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) scenario or in scenarios where custom dismissal interaction feedback is required.<br>**Note:**<br>When the user triggers a pull-down dismissal operation and both this callback and shouldDismiss or onWillDismiss are registered, the developer controls whether the sheet springs back during pull-down dismissal. In the callback, the spring-back effect can be implemented by calling springBack. The spring-back effect can also be canceled by not calling springBack.<br>If this callback is not registered but shouldDismiss or onWillDismiss is registered, the spring-back effect is triggered by default during pull-down dismissal, and after the spring-back, whether the sheet is dismissed is determined by the callback behavior in shouldDismiss or onWillDismiss.<br>If this callback is not registered and neither shouldDismiss nor onWillDismiss is registered, the sheet is dismissed by default during pull-down dismissal.<br>For the side sheet style, springBack takes effect in the side-swipe dismissal scenario.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| onHeightDidChange<sup>12+</sup> | [Callback](./ts-types.md#callback12)&lt;number&gt; | No | Yes | Callback for the height change of the sheet. If this attribute is not set, the callback is not triggered.<br>**Note:**<br>For a bottom sheet, the height of each frame is returned only when the detent changes and when the sheet is dragged by hand. When the sheet is pulled up and when the soft keyboard is avoided, only the final height is returned. For other sheets, only the final height is returned when the sheet is pulled up.<br>The return value is in px. <br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| onDetentsDidChange<sup>12+</sup> | [Callback](./ts-types.md#callback12)&lt;number&gt; | No | Yes | Callback for the detent change of the sheet. If this attribute is not set, the callback is not triggered.<br>**Note:**<br>This callback is triggered only in the bottom sheet scenario, and the final height is returned when the detent changes.<br>The return value is in px. <br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| onWidthDidChange<sup>12+</sup> | [Callback](./ts-types.md#callback12)&lt;number&gt; | No | Yes | Callback for the width change of the sheet. If this attribute is not set, the callback is not triggered.<br>**Note:**<br>The final width is returned when the width changes.<br>The return value is in px. <br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| onTypeDidChange<sup>12+</sup> | [Callback](./ts-types.md#callback12)&lt;[SheetType](#sheettype11)&gt; | No | Yes | Callback for the style change of the sheet.<br>**Note:**<br>The final style is returned when the style changes.<br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| borderWidth<sup>12+</sup> | [Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[EdgeWidths](ts-types.md#edgewidths9)&nbsp;\|&nbsp;[LocalizedEdgeWidths](ts-types.md#localizededgewidths12)<sup>12+</sup>  | No | Yes | Sets the border width of the sheet.<br>The border width can be set for the four borders separately.<br>Default value: 0vp<br> Percentage parameter: sets the border width of the sheet as a percentage of the sheet width.<br>When the left and right borders of the sheet are greater than the sheet width, and the top and bottom borders of the sheet are greater than the sheet height, the display may not meet expectations.<br>**Note:**<br>For a bottom sheet, the bottom border width does not take effect. When the systemMaterial attribute is set, the effect of this attribute may be overridden. Using it together with systemMaterial is not recommended. The value range is non-negative numbers. Setting a negative value does not take effect. <br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| borderColor<sup>12+</sup> | [ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[EdgeColors](ts-types.md#edgecolors9)&nbsp;\|&nbsp;[LocalizedEdgeColors](ts-types.md#localizededgecolors12)<sup>12+</sup>  | No | Yes | Sets the border color of the sheet.<br>Default value: Color.Black<br> If the borderColor attribute is used, it must be used together with the borderWidth attribute. If borderWidth is not set, the border color is invisible because the default value of borderWidth is 0. <br>**Note:**<br>For a bottom sheet, the bottom border color does not take effect. When the systemMaterial attribute is set, the effect of this attribute may be overridden. Using it together with systemMaterial is not recommended. <br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| borderStyle<sup>12+</sup> | [BorderStyle](ts-appendix-enums.md#borderstyle)&nbsp;\|&nbsp;[EdgeStyles](ts-types.md#edgestyles9)  | No | Yes | Sets the border style of the sheet.<br>Default value: BorderStyle.Solid<br>If the borderStyle attribute is used, it must be used together with the borderWidth attribute. If borderWidth is not set, the border style is invisible because the default value of borderWidth is 0. <br>**Note:**<br>For a bottom sheet, the bottom border style does not take effect. <br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| width<sup>12+</sup> | [Dimension](ts-types.md#dimension10)   | No | Yes | Sets the width of the sheet. If this attribute is not set, the default width specification corresponding to each sheet style is used.<br> Percentage parameter: sets the width of the sheet as a percentage of the parent element width.<br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| shadow<sup>12+</sup> | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions )&nbsp;\|&nbsp;[ShadowStyle](ts-universal-attributes-image-effect.md#shadowstyle10)   | No | Yes | Sets the shadow of the sheet. You can customize the shadow parameters through ShadowOptions, or use a preset shadow style through ShadowStyle (for example, OUTER_FLOATING_SM for a small outer floating shadow and OUTER_FLOATING_MD for a medium outer floating shadow).<br>**Default value**: On non-2-in-1 devices, there is no shadow by default. On 2-in-1 devices, the default value is ShadowStyle.OUTER_FLOATING_SM.<br>**Note:**<br>When the systemMaterial attribute is set, the effect of this attribute may be overridden. Using it together with systemMaterial is not recommended. The full-screen modal style (CONTENT_COVER) does not support shadows, and this attribute does not take effect.<br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| uiContext<sup>12+</sup> | [UIContext](../arkts-apis-uicontext-uicontext.md)   | No | Yes | Displays the sheet in the window corresponding to the UIContext instance. If this parameter is not passed, the sheet is displayed in the window corresponding to the current UIContext by default. Pass this parameter when the sheet needs to be displayed in a specified window.<br>**Note:**<br>For a sheet started using [openBindSheet](../arkts-apis-uicontext-uicontext.md#openbindsheet12), setting and updating this attribute is not supported. Setting this attribute is also not supported when SheetMode.EMBEDDED is set, because the display layer effects of the two conflict with each other.<br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| mode<sup>12+</sup> | [SheetMode](#sheetmode12)   | No | Yes | Sets the display layer of the sheet.<br>Default value: SheetMode.OVERLAY<br>**Note:**<br> 1. During the display of the sheet, the mode attribute does not support dynamic switching. The display layers of the two modes are completely different, and the same sheet cannot be transformed from one layer to another during display. It is recommended to fix the mode value based on the requirement. <br> 2. When SheetMode.EMBEDDED is set, setting the UIContext attribute is not supported, because the display layer effects of the two conflict with each other.<br>3. When a sheet is started using [openBindSheet](../arkts-apis-uicontext-uicontext.md#openbindsheet12), if no valid targetId is passed, setting SheetMode.EMBEDDED is not supported, and the default is SheetMode.OVERLAY.<br>**Atomic service API:** This API is supported in atomic services since API version 12. |
| scrollSizeMode<sup>12+</sup> | [ScrollSizeMode](#scrollsizemode12)   | No | Yes | Sets the refresh timing of the content area when the sheet panel is slid.<br>Default value: ScrollSizeMode.FOLLOW_DETENT <br>**Atomic service API:** This API is supported in atomic services since API version 12.|
| keyboardAvoidMode<sup>13+</sup> | [SheetKeyboardAvoidMode](#sheetkeyboardavoidmode13) | No | Yes | Sets the avoidance mode for the soft keyboard when the sheet activates the input method.<br> **Default value:** TRANSLATE_AND_SCROLL<br>**Atomic service API:** This API is supported in atomic services since API version 13. |
| enableHoverMode<sup>14+</sup>              | boolean | No | Yes   | Whether to respond to the hover state.<br>Default value: false, which means no response by default.<br> On 2-in-1 devices, the default value is true. <br>true: responds to the hover state.<br>false: does not respond to the hover state.<br>**Note:**<br>The bottom sheet style, follow-hand sheet style, side sheet style, and full-screen modal style do not respond to the hover state. The subwindow mode does not support the hover state.<br>**Atomic service API:** This API is supported in atomic services since API version 14.|
| hoverModeArea<sup>14+</sup>              | [HoverModeAreaType](#hovermodeareatype14) | No | Yes   | Default display area of the sheet in the hover state. This attribute takes effect only when [enableHoverMode](#sheetoptions) is set to true.<br>Default value: HoverModeAreaType.BOTTOM_SCREEN <br> On 2-in-1 devices, the default value is HoverModeAreaType.TOP_SCREEN. <br>**Note:**<br>The side sheet style and full-screen sheet style do not support the hover state area setting.<br>**Atomic service API:** This API is supported in atomic services since API version 14.|
| radius<sup>15+</sup> | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)&nbsp;\|&nbsp;[BorderRadiuses](ts-types.md#borderradiuses9)&nbsp;\|&nbsp;[LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12) | No | Yes | Sets the corner radius of the sheet.<br>It is not recommended to set four unequal corner radii. The visual experience is best when the corner radii are equal.<br>**Default value**: 32vp<br>**Note:**<br>1. The sheet is displayed based on the set corner radius value. If it is not set, the default value is used. The bottom style does not display the two bottom corners of the sheet, and even if the two bottom corners are set, they do not take effect.<br>2. After setting the corner radii for the four directions separately, if the radius value of a direction is invalid (for example, a negative value), the radius of the abnormal direction is reset to the default value, and the radius of the non-abnormal directions remains the set value. If the uniformly set radius value is invalid (for example, a negative value), the radii of all four directions are reset to the default value.<br>3. When the radius is set as a percentage, the width of the sheet is used as the reference.<br>4. When the corner radius is greater than half of the sheet width, the corner radius takes the value of half of the sheet width.<br>5. When the sheet height is too small and the corner radius is set too large, the display may be abnormal.<br>**Atomic service API:** This API is supported in atomic services since API version 15. |
| detentSelection<sup>15+</sup>         <br> | [SheetSize](#sheetsize )&nbsp;\|&nbsp;[Length](ts-types.md#length) | No | Yes    | Supports switching detents without gestures.<br>**Default value:** detents[0].<br>**Note:**<br>1. The value range of this API is the range of the detents array. If the set value is outside the detents range, this API does not take effect.<br>2. When SheetSize.FIT_CONTENT is set, this API does not take effect.<br>3. It is not recommended to use gesture-based detent switching and this API-based detent switching at the same time. When both take effect, the detent switching behavior may be unpredictable.<br>**Atomic service API:** This API is supported in atomic services since API version 15. |
| placement<sup>18+</sup> | [Placement](ts-appendix-enums.md#placement8) | No | Yes | Sets the display position of the popup-style sheet relative to the target. For the side sheet style, this attribute supports only the bubble style.<br>Default value: Placement.Bottom<br>**Note:** <br> 1. On the premise that the specified position can accommodate the sheet size, the popup-style sheet is displayed preferentially based on the set placement. If this is not feasible, the display position is adjusted following the rule of vertical flipping first and then attempting a 90-degree horizontal rotation. Taking the preset direction of bottom as an example, the adjustment order is: bottom, top, right, left.<br>2. If the set alignment causes the component layout to exceed the window range, the component is shifted horizontally or vertically based on the alignment until it is fully displayed within the window.<br>3. If the current popup-style sheet cannot be accommodated in any of the four directions, the handling follows the placementOnTarget attribute set by the developer:<br>1) If the attribute value is true, the sheet is translated in the mirror direction of the set placement until it can be fully displayed.<br>2) If the attribute value is false, among the four directions, the direction that can fully display the sheet width and has the largest remaining height is selected, and the sheet height is adjusted to fit the current direction to ensure that the sheet can be placed, while keeping the alignment corresponding to the preset placement unchanged. <br>**Atomic service API:** This API is supported in atomic services since API version 18. |
| placementOnTarget<sup>18+</sup> | boolean | No | Yes | When the popup-style sheet cannot be accommodated in any of the four directions in the current window, sets whether to allow it to cover the target node. For the side sheet style, this attribute supports only the bubble style. This attribute must be used together with the [placement](#sheetoptions) attribute, and the handling of placementOnTarget is based on the display direction set by placement.<br> Default value: true <br>true: allows it to cover the target node.<br>false: does not allow it to cover the target node.<br>**Atomic service API:** This API is supported in atomic services since API version 18.|
| effectEdge<sup>18+</sup> | number | No | Yes | Sets the edge spring-back effect of the content area of the sheet panel. Supports taking effect on a single edge.<br>**Default value**: By default, both edges take effect, that is, [EffectEdge](ts-container-scrollable-common.md#effectedge18).START \| [EffectEdge](ts-container-scrollable-common.md#effectedge18).END (value 3).<br>**Note:**<br>1. Only the top edge takes effect: [EffectEdge](ts-container-scrollable-common.md#effectedge18).START.<br>2. Only the bottom edge takes effect: [EffectEdge](ts-container-scrollable-common.md#effectedge18).END.<br>3. Both edges take effect: [EffectEdge](ts-container-scrollable-common.md#effectedge18).START \| [EffectEdge](ts-container-scrollable-common.md#effectedge18).END (value 3).<br>4. Neither edge takes effect: [EffectEdge](ts-container-scrollable-common.md#effectedge18).START & [EffectEdge](ts-container-scrollable-common.md#effectedge18).END (value 0).<br>**Atomic service API:** This API is supported in atomic services since API version 18. |
| showInSubWindow<sup>19+</sup> | boolean                                  | No | Yes    | Whether the sheet is displayed in an independent subwindow.<br>Default value: false<br>**Note:** <br>1. If the attribute value is true, the sheet can be displayed in an independent subwindow and can exceed the application window range.<br>2. If the attribute value is false, the sheet can be displayed only within the application window range.<br>3. It is not recommended to nest another sheet with showInSubWindow set to true inside a sheet with showInSubWindow set to true, because the sheet may affect the behavior of other components.<br>4. It is not recommended to use picker components such as CalendarPicker, CalendarPickerDialog, DatePickerDialog, TextPickerDialog, and TimePickerDialog in a sheet with showInSubWindow set to true, because the sheet affects the behavior of these components.<br>5. During the display of the sheet, this attribute does not support dynamic switching.<br>**Atomic service API:** This API is supported in atomic services since API version 19. |
| enableFloatingDragBar<sup>20+</sup>              | boolean | No | Yes   | Whether the drag bar is displayed in a floating manner. true means floating display, and false means non-floating display.<br>Default value: false <br> **Note:** <br>The floating effect takes effect only in the scenario where the drag bar is displayed, and the drag bar does not occupy space.<br> When title is set to [CustomBuilder](ts-types.md#custombuilder8), enableFloatingDragBar is always false.<br>The side sheet style does not support the floating drag bar.<br>**Atomic service API:** This API is supported in atomic services since API version 20. |
| modalTransition<sup>20+</sup> | [ModalTransition](#modaltransition) | No | Yes | System transition mode of the full-screen modal style of bindSheet. This attribute takes effect only when [preferType](#sheetoptions) is set to [SheetType.CONTENT_COVER](#sheettype11) (full-screen sheet style). Setting this attribute for other sheet styles does not take effect.<br>Default value: ModalTransition.DEFAULT<br>**Atomic service API:** This API is supported in atomic services since API version 20. |
| radiusRenderStrategy<sup>23+</sup> |  [RenderStrategy](ts-appendix-enums.md#renderstrategy22) | No | Yes  |Sets the mode for rendering the component corners.<br>Default value: RenderStrategy.FAST <br>**Note:** When the sheet has blur set, setting OFFSCREEN (off-screen mode) can resolve the abnormal display effect in the top or top corner area of the sheet. The popup style does not support setting the component corner rendering mode.<br>**Atomic service API:** This API is supported in atomic services since API version 23.<br>**Model restriction:** This API can be used only in the stage model. |
| systemMaterial |  [SystemUiMaterial](ts-universal-attributes-image-effect.md#systemuimaterial) | No | Yes  |Sets the system material of the component.<br>Default value: undefined, which clears the material effect set by this API. <br>**Note:** Different system materials correspond to different attribute effects. This API affects the background color [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), border color [borderColor](ts-universal-attributes-border.md#bordercolor), border width [borderWidth](ts-universal-attributes-border.md#borderwidth), and shadow [shadow](ts-universal-attributes-image-effect.md#shadow). Using it together with the preceding APIs is not recommended. For a usage example, see [Example 10 (Setting the System Material for a Half-Modal)](#example-10-setting-the-system-material-for-a-half-modal).<br>**Since:** 26.0.0<br>**Atomic service API:** This API is supported in atomic services since API version 26.0.0.<br>**Model restriction:** This API can be used only in the stage model. |

## SheetSize

Enumerates the sheet height modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     | Value   | Description                        |
| ------------------------- | ---- | -------------------------------- |
| MEDIUM                    | 0    | Specifies the half-modal height as 60% of the window where the half-modal is located.<br>On TV devices, the half-modal height is 50% of the window where the half-modal is located.<br>**Note:**<br>This value is invalid for a centered dialog box or a follow-hand dialog box, in which case the default height 560 vp is used.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services.   |
| LARGE                     | 1    | Specifies the half-modal height as almost the height of the window where the half-modal is located.<br>On TV devices, the half-modal height is the height of the window where the half-modal is located.<br>**Note:**<br>This value is invalid for a centered dialog box or a follow-hand dialog box, in which case the default height 560 vp is used.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services.   |
| FIT_CONTENT<sup>11+</sup> | 2    | Specifies the half-modal height as the height that fits the content.<br>**Atomic service API:** Since API version 12, this API is supported in atomic services.<br>**Note:**<br>1. FIT_CONTENT means that the half-modal container height adapts to the layout of the root node of the child builder. In this scenario, the height of the root node of the builder cannot use a percentage, because the two cannot depend on each other's layout.<br>2. If the half-modal uses the SheetSize.FIT_CONTENT adaptive mode and its type is set to a centered dialog box or a follow-hand dialog box, in API version 22 and earlier, the maximum height is displayed when the height is greater than the maximum height, and the minimum height is displayed when the height is less than the minimum height.<br>Starting from API version 23, the maximum height is displayed when the height is greater than the maximum height, and the actual adaptive height takes effect when the height is less than the minimum height.<br>For a centered dialog box and a follow-hand dialog box, the minimum height is 320 vp and the maximum height is 90% of the short side of the window. |

## HoverModeAreaType<sup>14+</sup>

Enumerates the display area types when the device is in semi-folded mode.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value   | Description                           |
| ------ | ----------------------------- | ----------------------------- |
| TOP_SCREEN | 0 | Upper half screen.|
| BOTTOM_SCREEN | 1 | Lower half screen.|

## BindOptions

Defines the common configuration for sheets and modals.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                                      | Read-Only| Optional| Description                    |
| --------------- | --------------------------------- | --------- | ---- | ------------------------ |
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No | Yes | Background color of the semi-modal page.<br>Default value: Color.White.<br>**NOTE**<br>When the systemMaterial attribute is set, the effect of this attribute may be overwritten. It is not recommended to use this attribute together with systemMaterial.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| onWillAppear<sup>12+</sup>        | () => void                                 | No | Yes | Callback invoked when the semi-modal page is about to be displayed (before the animation starts). Timing relationship with onAppear: onWillAppear is triggered before the display animation starts, and onAppear is triggered after the display animation ends. Both can be used at the same time. To do preparation work before the animation starts, use onWillAppear. To update the UI after the animation ends, use onAppear. If not set, the callback is not triggered.<br>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| onAppear        | () => void                                 | No | Yes | Callback invoked when the semi-modal page is displayed (after the animation ends). If not set, the callback is not triggered.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| onWillDisappear<sup>12+</sup>     | () => void                                 | No | Yes | Callback invoked when the semi-modal page is about to be dismissed (before the animation starts). Timing relationship with onDisappear: onWillDisappear is triggered before the dismiss animation starts, and onDisappear is triggered after the dismiss animation ends. Both can be used at the same time. To save the state before the animation starts, use onWillDisappear. To release resources after the animation ends, use onDisappear. If not set, the callback is not triggered.<br>**NOTE**<br>Do not modify state variables in the onWillDisappear function, as this may cause unstable component behavior. **Atomic service API:** Since API version 12, this API is supported in atomic services. |
| onDisappear     | () => void                                 | No | Yes | Callback invoked when the semi-modal page is dismissed (after the animation ends). If not set, the callback is not triggered.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |

## ModalTransition

Enumerates the modal transition types.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value| Description          |
| ------- | ---- | -------- |
| DEFAULT | 0 | Slide-up and slide-down animation for the modal. |
| NONE    | 1 | No transition animation for the modal.  |
| ALPHA   | 2 | Opacity gradient animation for the modal.|

## SheetType<sup>11+</sup>

Enumerates the sheet styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description                                              |
| ------ | ---- | ------------------------------------------------------ |
| BOTTOM | 0    | Bottom dialog box. <br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| CENTER | 1    | Center dialog box. <br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| POPUP  | 2    | Follow-hand dialog box. The follow-hand dialog box panel does not support follow-hand sliding, and swiping down does not close the panel.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| SIDE<sup>20+</sup>   | 3    | Side dialog box.<br>**Atomic service API:** This API can be used in atomic services since API version 20.|
| CONTENT_COVER<sup>20+</sup>   | 4    | Full-screen dialog box.<br>**Atomic service API:** This API can be used in atomic services since API version 20.|

**Side sheet styles**

1. Transition animation: By default, the sheet enters from the right and exits to the right. In right-to-left (RTL) locales, it enters from the left and exits to the left. Custom transitions are not supported.

2. The multi-level detent is unavailable, and the **detents** and **detentSelection** APIs are not supported. The control bar-related APIs, such as **dragBar**, are not supported.

3. The bottom dialog box style can be swiped up after the transition ends. However, the side dialog box style can only be swiped right to close. The capabilities in the mirroring scenario are opposite.

4. The height cannot be customized and it is full screen by default.

5. Other display level APIs, such as **showInSubWindow = true** and **mode = SheetMode.EMBEDDED**, cannot be specified. The level of the side dialog box is the same as that of **SheetMode.OVERLAY**. Such dialog box can be displayed only at the top of the current **UIContext**. It is displayed at the same level as dialog boxes.

6. Hover state avoidance is not supported.

7. Default width of the side sheets:
   - md [breakpoint](../../../../application-dev/ui/arkts-layout-development-grid-layout.md#breakpoints): 1/2 window width
   - [Breakpoints](../../../../application-dev/ui/arkts-layout-development-grid-layout.md#breakpoints) larger than md: 400 vp fixed width


**APIs not supported by side sheets**
| Name            | Description             |
| --------------- |  --------------- |
| height          | Only full screen height is supported.|
| detents | No detent.|
| dragBar         | Does not support the drag bar.  |
| onDetentsDidChange | No detent.|
| uiContext | The display level cannot be specified.|
| mode | The display level cannot be specified.|
| scrollSizeMode | No detent. |
| enableHoverMode  | Hover state avoidance is not supported.|
| hoverModeArea    | Hover state avoidance is not supported.|
| detentSelection | No detent.|
| placement | Only the popup style is supported.|
| placementOnTarget | Only the popup style is supported.|
| showInSubWindow | The display level cannot be specified.|

**Full-screen bindSheet styles**

1. In full-screen mode, the border, shadow, title bar, close button, and rounded corner are not supported.

2. By default, the builder content is laid out in the safe area.

3. The full-screen style supports the system transition mode [ModalTransition](#modaltransition), whose default value is **ModalTransition.DEFAULT**. Customized transition is not supported.

4. The **detents** and **detentSelection** APIs are not supported.

5. The sheet can be closed only by side swiping.

6. The width and height cannot be customized, and they are set to full screen by default.

7. Other display level APIs, such as **showInSubWindow = true** and **mode = SheetMode.EMBEDDED**, cannot be specified. The display level of the full-screen popup is the same as that of **SheetMode.OVERLAY**. Such popup can be displayed only at the top of the current **UIContext**, and is displayed at the same level as the popup component.

8. The soft keyboard is not avoided by default. You need to customize the settings.

9. The mask is not supported.


**APIs not supported by the full-screen bindSheet style**
| Name            | Description             |
| --------------- |  --------------- |
| height          | Only full screen height is supported.|
| width           | Only full screen width is supported.|
| detents | No detent.|
| dragBar         | Does not support the drag bar.  |
| onDetentsDidChange | No detent.|
| showClose          | Does not support displaying the close icon. |
| title          | The title bar cannot be displayed.|
| uiContext | The display level cannot be specified.|
| mode | The display level cannot be specified.|
| scrollSizeMode | No detent. |
| keyboardAvoidMode | The soft keyboard is not avoided by default. You need to customize the settings.|
| enableHoverMode  | Hover state avoidance is not supported.|
| hoverModeArea    | Hover state avoidance is not supported.|
| detentSelection | No detent.|
| showInSubWindow | The display level cannot be specified.|
| radius         | The rounded corner is not supported. |
| borderWidth         | The border width is not supported. |
| borderColor         | The border color is not supported. |
| borderStyle         | The border style is not supported. |
| shadow         | The shadow is not supported. |
| maskColor      | The mask color is not supported. |
| enableOutsideInteractive | Whether interaction is allowed cannot be set. |
| effectEdge     | The edge rebound effect is not supported. |
| enableFloatingDragBar | Does not support the floating drag bar.  |
| onWillSpringBackWhenDismiss | The spring effect is not supported. |

## SheetDismiss<sup>11+</sup>

Controls the dismissal of a sheet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type      | Read-Only| Optional| Description                                                        |
| ------- | ---------- | ---- | ---- | ------------------------------------------------------------ |
| dismiss | () => void | No  | No  | Callback for dismissing the sheet. Call this API only when you need the sheet to exit.|

## SheetTitleOptions<sup>11+</sup>

Provides the options for configuring the title of a sheet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                                  | Read-Only| Optional| Description                |
| -------- | -------------------------------------- | ---- | ---- | -------------------- |
| title    | [ResourceStr](ts-types.md#resourcestr) | No  | No  | Main title of the sheet.|
| subtitle | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Subtitle of the half-modal panel. By default, no subtitle is displayed when this parameter is not passed. Pass this parameter when supplementary text needs to be displayed below the title. |

## SheetMode<sup>12+</sup>

Enumerates the display layer modes of a sheet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     | Value  | Description                        |
| ------------------------- | ---- | -------------------------------- |
| OVERLAY                   | 0    | The sheet is displayed at the top of the window corresponding to the current **UIContext** instance, above all pages. It is displayed at the same level as dialog boxes.  |
| EMBEDDED                  | 1    | Sets the semi-modal panel to be displayed at the top level of the current page. <br>**Note:**<br>Currently, the panel can be mounted only on a Page or NavDestination node. If a NavDestination exists, it is mounted on the NavDestination first. Top-level display is supported only in these two types of pages.<br> In this mode, a newly opened page can cover the semi-modal dialog box. After returning from the page, the semi-modal dialog box still exists and its content is not lost. <br> In this mode, ensure that the target page node (for example, the Page node) is mounted to the tree before the semi-modal dialog box is displayed. Otherwise, the semi-modal dialog box cannot be mounted to the corresponding page node.|

## ScrollSizeMode<sup>12+</sup>

Enumerates the content update modes of a sheet when it is scrolled vertically.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Value  | Description                        |
| ------------------------- | ---- | -------------------------------- |
| FOLLOW_DETENT | 0    | The sheet updates the content display area after a swipe ends.  |
| CONTINUOUS    | 1    | The sheet continuously updates the content display area during the scroll process.|

## DismissSheetAction<sup>12+</sup>

Defines the callback triggered when a sheet is about to be dismissed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type                                      | Read-Only  | Optional  | Description           |
| --------------- | ---------------------------------------- | ---- | ---- | ------------- |
| dismiss | [Callback](./ts-types.md#callback12)\<void> | No   | No   | Callback for dismissing the sheet. Call this API when you need to exit the page.|
| reason | [DismissReason](ts-universal-attributes-popup.md#dismissreason12) | No    | No    | Returns the operation type for exiting the current semi-modal page.<br>**Note:**<br> DismissReason.SLIDE takes effect only for the side popup style of the semi-modal page, indicating exit by swiping right. In a mirrored scenario, it indicates exit by swiping left.<br> DismissReason.SLIDE_DOWN takes effect for the bottom popup style and center popup style of the semi-modal page, indicating exit by swiping down.<br> The bubble popup style of the semi-modal page does not support swipe-to-exit.|

## SpringBackAction<sup>12+</sup>

Controls the interactive spring back of a sheet before it is dismissed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type                                      | Read-Only  | Optional  | Description           |
| --------------- | ---------------------------------------- | ---- | ---- | ------------- |
| springBack | [Callback](./ts-types.md#callback12)\<void> | No   | No   | Callback to control the interactive spring back before the sheet is dismissed. |

## SheetKeyboardAvoidMode<sup>13+</sup>

Defines how the sheet avoids the soft keyboard when it is brought up.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Value  | Description                        |
| ------------------------- | ---- | -------------------------------- |
| NONE | 0    | Sets the semi-modal to not avoid the soft keyboard.<br>**Atomic service API:** Since API version 13, this API is supported in atomic services. |
| TRANSLATE_AND_RESIZE    | 1    | Sets the semi-modal to first lift the panel to avoid the soft keyboard;<br>when the panel is lifted to the maximum height but still cannot avoid the soft keyboard, the overall content is compressed to complete the avoidance.<br>**Atomic service API:** Since API version 13, this API is supported in atomic services.|
| RESIZE_ONLY    | 2    | Sets the semi-modal to avoid the soft keyboard by compressing the overall content.<br>**Atomic service API:** Since API version 13, this API is supported in atomic services.|
| TRANSLATE_AND_SCROLL    | 3    | Sets the semi-modal to first lift the panel to avoid the soft keyboard;<br>when the panel is lifted to the maximum height but still cannot avoid the soft keyboard, the content is scrolled to complete the avoidance.<br>**Atomic service API:** Since API version 13, this API is supported in atomic services.|
| POPUP_SHEET<sup>20+</sup>    | 4    | Sets the semi-modal popup-style dialog box to avoid the soft keyboard. This avoidance mode takes effect only when [preferType](#sheetoptions) is set to [SheetType.POPUP](#sheettype11) (follow-hand popup style); other popup styles do not support this avoidance mode.<br> 1. When avoiding the soft keyboard, if the current display position of the popup-style dialog box cannot accommodate the dialog box size, the display position is adjusted following the rule of first vertical flip avoidance and then 90° horizontal rotation avoidance. Taking the preset direction as downward as an example, the avoidance order is: down, up, right, left.<br>2. If the set alignment causes the component layout to exceed the window range, the component is shifted horizontally or vertically according to the alignment until it is fully displayed within the window.<br>3. When avoiding the soft keyboard, if the current popup-style dialog box cannot be accommodated in any of the four directions, the handling follows the placementOnTarget attribute set by the developer:<br>(1) If the attribute value is true, the dialog box is translated toward the mirror direction of the set placement until it can be fully displayed.<br>(2) If the attribute value is false, among the four directions, the direction that can fully display the dialog box width and has the largest remaining height is selected, and the semi-modal height is adjusted to fit the current direction, ensuring that the dialog box can be placed while keeping the alignment corresponding to the preset placement unchanged.<br>4. If the semi-modal is not in the follow-hand style at this time, it does not have the ability to avoid the soft keyboard.<br>**Atomic service API:** Since API version 20, this API is supported in atomic services.|

> **NOTE**
>
> When the **POPUP_SHEET** avoidance mode is set, the sheet avoids only the soft keyboard started by the text box in the panel.
>

## Example
### Example 1: Setting Sheets with Different Heights

This example demonstrates how to set different heights for sheets using the **height** attribute.

```ts
// xxx.ets
@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;
  @State sheetHeight: number = 300;

  @Builder
  myBuilder() {
    Column() {
      Button("change height")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.sheetHeight = 500;
        })

      Button("Set Illegal height")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.sheetHeight = -1;
        })

      Button("close modal 1")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          height: this.sheetHeight,
          backgroundColor: Color.Green,
          onWillAppear: () => {
            console.info("BindSheet onWillAppear.");
          },
          onAppear: () => {
            console.info("BindSheet onAppear.");
          },
          onWillDisappear: () => {
            console.info("BindSheet onWillDisappear.");
          },
          onDisappear: () => {
            console.info("BindSheet onDisappear.");
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

![en-us_sheet](figures/sheet1.gif)

### Example 2: Setting Three Different Height Detents

This example demonstrates how to use the **detents** attribute of **bindSheet** to set three different height detents for a sheet.

1. The drag bar is effective only when there are multiple height detents.
2. Unlike the **height** attribute, which can set different heights at different times, the **detents** attribute provides a gesture to switch between detent heights and is more suitable for fixed height intervals.
3. If the height range is uncertain or there may be more than three different heights, avoid using the **detents** attribute.

```ts
// xxx.ets
@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("content1")
        .margin(10)
        .fontSize(20)

      Button("content2")
        .margin(10)
        .fontSize(20)
    }
    .width('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [SheetSize.MEDIUM, SheetSize.LARGE, 200],
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```

![en-us_sheet](figures/sheet2.gif)

### Example 3: Setting the Border Width and Color

This example demonstrates how to use the **borderWidth** and **borderColor** attributes with **LocalizedEdgeWidths** and **LocalizedEdgeColors** types in **bindSheet**.

```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("content1")
        .margin(10)
        .fontSize(20)

      Button("content2")
        .margin(10)
        .fontSize(20)
    }
    .width('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [SheetSize.MEDIUM, SheetSize.LARGE, 200],
          backgroundColor: Color.Gray,
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
          borderWidth: { top: LengthMetrics.vp(10), start: LengthMetrics.vp(10), end: LengthMetrics.vp(20) },
          borderColor: { top: Color.Pink, start: Color.Blue, end: Color.Yellow },
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```

The following shows how the example is represented with left-to-right scripts.

![en-us_sheet](figures/sheet3-ltr.png)

The following shows how the example is represented with right-to-left scripts.

![en-us_sheet](figures/sheet3-rtl.png)

### Example 4: Using Dismiss Callbacks

This example shows how to register **onWillDismiss** and **onWillSpringBackWhenDismiss** with **bindSheet**.

```ts
// xxx.ets
@Entry
@Component
struct BindSheetExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("CONTEXT")
        .margin(10)
        .fontSize(20)
    }
  }

  build() {
    Column() {
      Button("NoRegisterSpringback")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          height: SheetSize.MEDIUM,
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
          preferType: SheetType.CENTER,

          onWillDismiss: ((dismissSheetAction: DismissSheetAction) => {
            // Call dismiss to close the half-modal page only when the user swipes down.
            if (dismissSheetAction.reason == DismissReason.SLIDE_DOWN) {
                dismissSheetAction.dismiss(); // Close the half-modal page.
            }
          }),

          onWillSpringBackWhenDismiss: ((springBackAction: SpringBackAction) => {
          // No springBack is registered, so the modal sheet will not bounce back when swiped down.
          // SpringBackAction.springBack();
          }),
        })
    }
  }
}
```
![en-us_sheet](figures/sheet4.gif)

### Example 5: Setting the Content Update Mode

ScrollSizeMode.CONTINUOUS continuously updates the content and is suitable for scenarios where detents switch between multiple heights.

Whenever possible, minimize UI loading time within the builder, as real-time content refreshing during scrolling has higher performance requirements.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Column()
        .backgroundColor(Color.Blue)
        .height(200)
        .width('100%')
      Column()
        .backgroundColor(Color.Green)
        .height(200)
        .width('100%')
    }
  }

  build() {
    Column() {
      Button("BindSheet")
        .onClick(() => {
          this.isShow = true;
        })
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [300, 600, 900],
          uiContext: this.getUIContext(),
          mode: SheetMode.OVERLAY,
          scrollSizeMode: ScrollSizeMode.CONTINUOUS,
          backgroundColor: Color.Orange,
          title: { title: 'Title', subtitle: 'Subtitle' }
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```
When the sheet is dragged to switch between detents, the content height is refreshed only after the sheet is released.

![en-us_sheet](figures/sheet5-ltr.gif)

When the sheet is dragged to switch between detents, the content height is refreshed in real time during the drag.

![en-us_sheet](figures/sheet5-rtl.gif)

### Example 6: Configuring the Sheet to Resize to Avoid the Keyboard

This example demonstrates how to adjust the scrollable content within a sheet when the keyboard height changes by setting **SheetKeyboardAvoidMode** to **RESIZE_ONLY**.

```ts
// xxx.ets
import window from '@ohos.window';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct ListenKeyboardHeightChange {
  @State isShow: boolean = false;
  @State avoidMode: SheetKeyboardAvoidMode = SheetKeyboardAvoidMode.RESIZE_ONLY;
  scroller = new Scroller();
  private numberList: number[] = [0, 1, 2, 3, 4, 5, 6];
  windowClass: window.Window | undefined = undefined;

  aboutToAppear(): void {
    try {
      window.getLastWindow(this.getUIContext().getHostContext(), (err: BusinessError, data) => {
        if (err && err.code) {
          console.error(`Failed to obtain the top window, Code: ${err.code}, message: ${err.message}`);
          return;
        }
        this.windowClass = data;
        try {
          if (this.windowClass !== undefined) {
            console.info('success in listen height change');
            this.windowClass.on('keyboardHeightChange', this.callback);
          }
        } catch (exception) {
          console.error(`Failed to enable the listener for keyboard height changes, Cause code: ${exception.code}, message: ${exception.message}`);
        }
        console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
      });
    } catch (exception) {
      console.error(`Failed to obtain the top window, Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }

  callback = (height: number) => {
    console.info('height change: ' + height);
    if (height !== 0) {
      this.scroller.scrollTo({
        xOffset: 0, yOffset: height + this.scroller.currentOffset().yOffset,
        animation: { duration: 1000, curve: Curve.Ease, canOverScroll: false }
      });
    }
  }

  @Builder
  myBuilder() {
    Scroll(this.scroller) {
      Column() {
        ForEach(this.numberList, (item: number) => {
          Row() {
            Text(item.toString())
              .width('80%')
              .height(60)
              .backgroundColor('#3366CC')
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 5 })
          }
        }, (item: number) => item.toString())

        TextInput().height('100')

        Flex({ alignItems: ItemAlign.End }) {
          Row() {
            Button("click")
              .margin(10)
              .fontSize(20)
              .width('45%')

            Button("cancel")
              .margin(10)
              .fontSize(20)
              .width('45%')
          }.width('100%')
        }.height(100)
      }.margin({ right: 15, bottom: 50 })
    }
    .height('100%')
    .scrollBar(BarState.On)
    .scrollable(ScrollDirection.Vertical)
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          height: 750,
          backgroundColor: Color.Gray,
          blurStyle: BlurStyle.Thick,
          showClose: true,
          title: { title: "title", subtitle: "subtitle" },
          keyboardAvoidMode: SheetKeyboardAvoidMode.RESIZE_ONLY,
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```
![en-us_sheet](figures/sheet6.gif)

### Example 7: Setting the Corner Radius in a Mirrored Layout

This example demonstrates how to set different corner radii for a sheet in a mirrored layout. Typically, to avoid a poor visual experience, do not set different values.

Since API version 15, the **radius** attribute supports the LocalizedBorderRadiuses type.

```ts
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetTransitionExample {
  @State isShow: boolean = false;

  @Builder
  myBuilder() {
    Column() {
      Button("content1")
        .margin(10)
        .fontSize(20)

      Button("content2")
        .margin(10)
        .fontSize(20)
    }
    .width('100%')
  }

  build() {
    Column() {
      Button("transition modal 1")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShow, this.myBuilder(), {
          detents: [SheetSize.MEDIUM, SheetSize.LARGE, 200],
          title: { title: "title", subtitle: "subtitle" },
          radius: { topStart: LengthMetrics.vp(50), topEnd: LengthMetrics.vp(10) },
        })
    }
    .justifyContent(FlexAlign.Start)
    .width('100%')
    .height('100%')
  }
}
```

The following shows how the example is represented with left-to-right scripts.

![en-us_sheet](figures/sheet7-ltr.png)

The following shows how the example is represented with right-to-left scripts.

![en-us_sheet](figures/sheet7-rtl.png)

### Example 8: Implementing a Side Sheet

This example demonstrates how to implement a side sheet. This feature is supported since API version 20.

```ts
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetSideExample {
  @State isShowSide: boolean = false;
  @State enableOutsideInteractive: boolean = false;
  @State borderWidths: LocalizedEdgeWidths | undefined = undefined;
  @State borderColors: Resource | undefined = undefined;
  private numberList: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16];

  @Builder
  sideBuilder() {
    Column() {
      ForEach(this.numberList, (item: number) => {
        Row() {
          Text(item.toString())
            .width('90%')
            .height(60)
            .backgroundColor('#3366CC')
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .margin({ top: 5 })
        }
      }, (item: number) => item.toString())
      TextInput()
        .margin({ top: 5 })
      Text('Change Sheet Interaction Mode')
        .fontSize(22).fontColor(Color.White).fontWeight(FontWeight.Bold).textAlign(TextAlign.Center)
        .width('100%').height(50).backgroundColor('#2ebd82')
      Button("change enableOutsideInteractive = " + this.enableOutsideInteractive)
        .margin({ top: 5 })
        .onClick(() => {
          this.enableOutsideInteractive = !this.enableOutsideInteractive;
          if (this.enableOutsideInteractive) {
            this.borderWidths = {start : LengthMetrics.vp(1)};
            this.borderColors = $r('sys.color.comp_divider');
          } else {
            this.borderWidths = undefined;
            this.borderColors = undefined;
          }
        })
    }
    .width('100%')
    .height('auto')
  }


  build() {
    Column({space:3}) {
      Button("Side sheet")
        .onClick(() => {
          this.isShowSide = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShowSide, this.sideBuilder(), {
          title: { title: "SideSheet", subtitle: "Default width" },
          backgroundColor: Color.Grey,
          onWillAppear: () => {
            console.info("SideSheet onWillAppear.");
          },
          onAppear: () => {
            console.info("SideSheet onAppear.");
          },
          onWillDisappear: () => {
            console.info("SideSheet onWillDisappear.");
          },
          onDisappear: () => {
            console.info("SideSheet onDisappear.");
          },

          preferType: SheetType.SIDE,
          blurStyle: BlurStyle.Regular,
          maskColor: "#4bffc62d",  // Customize the mask color.
          enableOutsideInteractive: this.enableOutsideInteractive,

          borderWidth: this.borderWidths,
          borderColor: this.borderColors,

          onHeightDidChange: (height: number) => {
            console.info("SideSheet height change:" + height);
          },
          onTypeDidChange: (type: SheetType) => {
            console.info("SideSheet type change:" + type);
          },
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 9: Implementing a Full-Screen Content Cover Sheet

This example demonstrates how to implement a full-screen sheet. This feature is supported since API version 20.

```ts
// xxx.ets
@Entry
@Component
struct ContentCoverExample {
  @State isShow: boolean = false

  @Builder
  myBuilder() {
    Column() {
      Button("Close Content Cover Sheet")
        .margin(10)
        .fontSize(20)
        .onClick(() => {
          this.isShow = false;
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      Button("Show Content Cover Sheet")
        .onClick(() => {
          this.isShow = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.DEFAULT,
          preferType: SheetType.CONTENT_COVER,
          backgroundColor: '#ffd5d5d5',
          onWillAppear: () => {
            console.info("ContentCover onWillAppear.");
          },
          onAppear: () => {
            console.info("ContentCover onAppear.");
          },
          onWillDisappear: () => {
            console.info("ContentCover onWillDisappear.");
          },
          onDisappear: () => {
            console.info("ContentCover onDisappear.");
          },
        })
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.White)
    .width('100%')
    .height('100%')
  }
}
```
![en-us_sheet](figures/sheet9_content_cover.gif)

### Example 10: Setting the System Material for a Half-Modal

This example sets the system material through the systemMaterial attribute of the half-modal.

Since API version 26.0.0, the [SheetOptions](#sheetoptions) adds the systemMaterial attribute.

```ts
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SheetMaterialExample {
  @State isShow: boolean = false;
  @State sheetHeight: number = 300;
  @State myMaterial: SystemUiMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THICK,
  });

  @Builder
  myBuilder() {
    Column({ space: 10 }) {
      Text("Text")
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
  }

  build() {
    Stack() {
      // Replace this with the actual resource file.
      Image($r('app.media.startIcon'))
      Column() {
        Button("open Sheet")
          .onClick(() => {
            this.isShow = true;
          })
          .fontSize(20)
          .margin(10)
          .bindSheet($$this.isShow, this.myBuilder(), {
            height: this.sheetHeight,
            // The following APIs are not recommended for use together with systemMaterial.
            // borderWidth: 20,
            // borderColor: Color.Red,
            // backgroundColor: Color.Green,
            // shadow: { radius: 30, type: ShadowType.COLOR, color: Color.Yellow },
            // Some material effects do not have a background of their own and will be overridden by the color set through backgroundColor. To present such material effects, set the background color to transparent.
            backgroundColor: Color.Transparent,
            systemMaterial: this.myMaterial // The systemMaterial attribute is added since API version 26.0.0.
          })
      }
      .justifyContent(FlexAlign.Center)
      .width('100%')
      .height('100%')
    }
  }
}
```

![en-us_sheet](figures/sheetMaterial-new-s.jpg)
