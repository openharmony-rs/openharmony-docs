# Sheet Transition
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @yangfan229-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->

You can bind a sheet to a component through the **bindSheet** attribute. You can also set the sheet to the preset or custom height for when the component is inserted.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
>  Route hopping is not supported.

## bindSheet

bindSheet(isShow: boolean, builder: CustomBuilder, options?: SheetOptions): T

Binds a sheet to the component, which is displayed when the component is touched.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                       | Mandatory| Description                                                        |
| ------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| isShow  | boolean                          | Yes  | Whether to display the sheet.<br>**true**: Display the sheet.<br>**false**: Hide the sheet.<br>Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).<br>Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).|
| builder | [CustomBuilder](ts-types.md#custombuilder8) | Yes  | Content of the sheet.                                        |
| options | [SheetOptions](#sheetoptions)               | No  | Optional attributes of the sheet.                                  |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

> **NOTE**
>
> 1. When no two-way binding is set up for the **isShow** parameter, closing the sheet by dragging does not change the parameter value.
>
> 2. To synchronize the value of the **isShow** parameter with the sheet UI state, set up a two-way binding for **isShow** through [$$](../../../ui/state-management/arkts-two-way-sync.md). Since API version 18, this parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).
>
> 3. In scenarios where a sheet with a single detent is dragged upwards or a sheet with multiple detents is shifted to another detent by swiping up, the display area is updated after the drag ends or the shift is completed.
>
> 4. A sheet is a popup that is strictly bound to its host node. To achieve an effect where the sheet appears the moment the page is displayed, ensure that the host node is mounted in the view hierarchy. If the host node is not yet mounted when **isShow** is set to **true**, the sheet will not be displayed. You are advised to use the [onAppear](ts-universal-events-show-hide.md#onappear) to ensure that the sheet is shown after the host node is mounted.
> When [SheetMode](#sheetmode12) is set to **EMBEDDED**, in addition to the host node, also ensure that the corresponding page node is successfully mounted.
>
> 5. The exit animation of the sheet does not support interruption, and the sheet cannot respond to other gestures during the execution. The current exit animation uses a [spring curve](../../../ui/arkts-spring-curve.md), which has a subtle trailing effect that is not visually prominent. Therefore, when the sheet exits, although it may appear to have disappeared, the animation might not have fully finished, and attempting to initiate the sheet again by a touch will not work. You must wait for the animation to fully complete before you can initiate the sheet again.
>
## SheetOptions

Inherits from [BindOptions](#bindoptions).

Provides content configuration options of the sheet.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type                                      | Read-Only| Optional  | Description             |
| --------------- | --------------------------- | ------------- | ---- | --------------- |
| height          | [SheetSize](#sheetsize) \| [Length](ts-types.md#length) | No| Yes  | Height of the sheet. Default value: **LARGE**.<br>**NOTE**<br>Since API version 14, for a bottom sheet in landscape mode, the maximum height is 8 vp from the top of the screen if there is no status bar, and 8 vp from the status bar if there is one.<br>When a bottom sheet has **detents** set, this attribute is ineffective.<br>For a bottom sheet in portrait mode, the maximum height is 8 vp from the status bar.<br>For center and popup sheets set to **SheetSize.LARGE** or **SheetSize.MEDIUM**, this attribute is ineffective, with the default height being 560 vp. For center and popup sheets, the minimum height is 320 vp, and the maximum height is 90% of the shorter edge of the window. If the height specified by **Length** and the height adaptively set with **SheetSize.FIT_CONTENT** exceed the maximum height, the maximum height is used instead. If they are less than the minimum height, the minimum height is used instead.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| detents<sup>11+</sup> | [([SheetSize](#sheetsize) \| [Length](ts-types.md#length)), ( [SheetSize](#sheetsize) \| [Length](ts-types.md#length))?, ([SheetSize](#sheetsize) \| [Length](ts-types.md#length))?] | No| Yes| Array of heights where the sheet can rest.<br>**NOTE**<br>Since API version 12, this attribute takes effect for a bottom sheet in landscape mode.<br>In earlier versions, this attribute takes effect only for the bottom sheet in portrait mode. The first height in the tuple is the initial height.<br>The sheet can switch between heights by dragging. After the sheet is dragged and released, it switches to the target height or remains at the current height, depending on the velocity and distance.<br> If the velocity exceeds the threshold, the sheet switches to the target height in the same direction as the velocity. If the velocity is less than the threshold, the displacement distance is used for judgement. If the displacement distance is greater than 1/2 of the distance between the current and target positions, the sheet switches to the target height in the same direction as the velocity; otherwise, the sheet remains at the current height.<br> Velocity threshold: 1000; Distance threshold: 50%.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| preferType<sup>11+</sup> | [SheetType](#sheettype11)| No| Yes| Type of the sheet.<br>**NOTE**<br>The types supported by the sheet vary by window.<br>1. Width < 600 vp: bottom, full-screen.<br>2. 600 vp <= Width < 840 vp: bottom, center, popup, side-aligned, full-screen. (default)<br>3. Width >= 840 vp: bottom, center, popup, side-aligned, full-screen. (default)<br>4. Since API version 20, when the window width is greater than 600 vp, **preferType** can be set to **SheetType.SIDE**.<br>5. Since API version 20, **preferType** can be set to **SheetType.CONTENT_COVER**, enabling full-screen sheet style.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| showClose<sup>11+</sup> | boolean \| [Resource](ts-types.md#resource) | No| Yes| Whether to display the close icon.<br> On 2-in-1 devices, the icon does not have a background by default.<br> Default value: **true**.<br> **true**: Display the close icon.<br> **false**: Do not display the close icon.<br>**NOTE**<br>The value of **Resource** must be of the Boolean type.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| dragBar         | boolean                                  | No| Yes   | Whether to display the drag bar.<br>**NOTE**<br>By default, the drag bar is displayed only when the sheet's **detents** attribute is set to multiple heights and the settings take effect.  <br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| blurStyle<sup>11+</sup> | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | No| Yes| Background blur of the sheet. By default, there is no background blur.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| maskColor | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Mask color of the sheet.<br> Default value: **$r('sys.color.ohos_id_color_mask_thin')**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| title<sup>11+</sup> | [SheetTitleOptions](#sheettitleoptions11) \| [CustomBuilder](ts-types.md#custombuilder8) | No| Yes| Title of the sheet.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| enableOutsideInteractive<sup>11+</sup> | boolean | No| Yes| Whether to allow users to interact with the underlying page when the sheet is displayed.<br>**NOTE**<br>The value **true** means that interactions are allowed, in which case no mask is not displayed. The value **false** means that interactions are not allowed, in which case a mask is displayed. If this parameter is not set, interactions are allowed for the popup sheet, but not for bottom and center sheets. If this parameter is set to **true**, the setting of **maskColor** does not take effect.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| shouldDismiss<sup>11+</sup> | (sheetDismiss: [SheetDismiss](#sheetdismiss11)) => void | No| Yes| Callback invoked when the user performs an interactive dismiss operation: pulling down, side swiping, or clicking the mask or the close icon.<br>**NOTE**<br>If this callback is registered, the sheet is not dismissed immediately when the user performs the above operations. To dismiss the sheet, you must call **shouldDismiss.dismiss()** in the callback.<br>If this callback is not registered, the sheet is dismissed immediately when the user performs the above operations, without any additional behavior.<br>Side swiping for dismissal refers to any of the following operations: swiping left or right, touching the Back button, and pressing the Esc key.<br>It is recommended that this API be used in scenarios where a [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) is required<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onWillDismiss<sup>12+</sup> | [Callback](./ts-types.md#callback12)<[DismissSheetAction](#dismisssheetaction12)> | No| Yes   | Callback invoked when the user performs an interactive dismiss operation: pulling down, side swiping, or clicking the mask or the close icon. Allows developers to register the closure operation type and determine whether to close the semi-modal state.<br>**NOTE**<br>If this callback is registered, the sheet is not dismissed immediately when the user performs the above operations. Instead, you can use the **reason** parameter in the [DismissSheetAction](#dismisssheetaction12) callback to determine the type of dismiss operation and decide whether to dismiss the sheet.<br>If this callback is not registered, the sheet is dismissed immediately when the user performs the above operations, without any additional behavior.<br>Side swiping for dismissal refers to any of the following operations: swiping left or right, touching the Back button, and pressing the Esc key.<br>No further interception with **onWillDismiss** is allowed in an **onWillDismiss** callback.<br>It is recommended that this API be used in scenarios where a [secondary confirmation](../../../ui/arkts-sheet-page.md#secondary-confirmation-capability) is required<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onWillSpringBackWhenDismiss<sup>12+</sup> | [Callback](./ts-types.md#callback12)<[SpringBackAction](#springbackaction12)> | No| Yes   | Callback to control the interactive spring back before the sheet is dismissed. Allows developers to register this callback to control the rebound effect when the sheet page is closed interactively.<br>**NOTE**<br>If this callback is registered along with **shouldDismiss** or **onWillDismiss**, you can control whether the sheet bounces back during the pull-down-to-dismiss operation by calling **springBack** in the callback.<br>If this callback is not registered but **shouldDismiss** or **onWillDismiss** is registered, the sheet will bounce back before remaining open or being dismissed based on the callback behavior.<br>If neither this callback nor **shouldDismiss** or **onWillDismiss** is registered, the sheet is dismissed by default during the pull-down-to-dismiss operation.<br>For side-aligned sheets, **springBack** works only side swiping is performed for dismissal.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onHeightDidChange<sup>12+</sup> | Callback&lt;number&gt; | No| Yes| Callback for changes in the height of the sheet.<br>**NOTE**<br>For a bottom sheet, the height of each frame is only returned when there are changes in detents or during drag actions. When the sheet is pulled up or making space for the soft keyboard, only the final height is returned. For other types of sheets, the final height is only returned when the sheet is pulled up.<br>The return value is in px.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onDetentsDidChange<sup>12+</sup> | Callback&lt;number&gt; | No| Yes| Callback for changes in the detents of the sheet.<br>**NOTE**<br>For a bottom sheet, the final height is returned when there are changes in detents.<br>The return value is in px.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onWidthDidChange<sup>12+</sup> | Callback&lt;number&gt; | No| Yes| Callback for changes in the width of the sheet.<br>**NOTE**<br>The final height is returned when there are changes in the width.<br>The return value is in px.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| onTypeDidChange<sup>12+</sup> | Callback&lt;[SheetType](#sheettype11)&gt;| No| Yes| Callback for changes in the type of the sheet.<br>**NOTE**<br>The final type is returned when there are changes in the type.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| borderWidth<sup>12+</sup> | [Dimension](ts-types.md#dimension10) \| [EdgeWidths](ts-types.md#edgewidths9) \| [LocalizedEdgeWidths](ts-types.md#localizededgewidths12)<sup>12+</sup>  | No| Yes| Border width of the sheet.<br>You can set the width for all four sides or set separate widths for individual sides.<br>Default value: **0**<br> Percentage parameter method: Set the border width of the sheet as a percentage of the width of the parent element.<br>If the left and right border widths of the sheet are greater than the width of the sheet, and the top and bottom border widths are greater than the height of the sheet, the display may not appear as expected.<br>**NOTE**<br>For bottom sheets, the bottom border width setting is ineffective.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| borderColor<sup>12+</sup> | [ResourceColor](ts-types.md#resourcecolor) \| [EdgeColors](ts-types.md#edgecolors9) \| [LocalizedEdgeColors](ts-types.md#localizededgecolors12)<sup>12+</sup>  | No| Yes| Border color of the sheet.<br>Default value: **Color.Black**<br> **borderColor** must be used with **borderWidth** in pairs.<br>**NOTE**<br>For bottom sheets, the bottom border color setting is ineffective.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| borderStyle<sup>12+</sup> | [BorderStyle](ts-appendix-enums.md#borderstyle) \| [EdgeStyles](ts-types.md#edgestyles9)  | No| Yes| Border style of the sheet.<br>Default value: **BorderStyle.Solid**<br>**borderStyle** must be used with **borderWidth** in pairs.<br>**NOTE**<br>For bottom sheets, the bottom border style setting is ineffective.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| width<sup>12+</sup> | [Dimension](ts-types.md#dimension10)   | No| Yes| Width of the sheet.<br> Percentage parameter method: Set the width of the sheet as a percentage of the width of the parent element. <br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| shadow<sup>12+</sup> | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions) \| [ShadowStyle](ts-universal-attributes-image-effect.md#shadowstyle10)   | No| Yes| Shadow of the sheet.<br>Default value for 2-in-1 devices: **ShadowStyle.OUTER_FLOATING_SM**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| uiContext<sup>12+</sup> | [UIContext](../arkts-apis-uicontext-uicontext.md)   | No| Yes| **UIContext** instance corresponding to the window where the sheet is displayed.<br>**NOTE**<br>The sheet launched with [openBindSheet](../arkts-apis-uicontext-uicontext.md#openbindsheet12) does not support setting or updating this attribute.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| mode<sup>12+</sup> | [SheetMode](#sheetmode12)   | No| Yes| Display mode of the sheet.<br>Default value: **SheetMode.OVERLAY**<br>**NOTE**<br> 1. During the display of the sheet, the **mode** attribute does not support dynamic changes. The display hierarchy of the two modes is entirely different, making it impossible to switch a sheet from one mode to another while it is being displayed. You are advised to clearly define and fix the **mode** value to ensure consistency in the display hierarchy.<br> 2. The **UIContext** attribute cannot be set when **SheetMode.EMBEDDED** is set, as their corresponding sheet display hierarchy effects are mutually conflicting.<br>3. For a sheet launched with [openBindSheet](../arkts-apis-uicontext-uicontext.md#openbindsheet12), if a valid target ID is not provided, **SheetMode.EMBEDDED** cannot be set, and the default value **SheetMode.OVERLAY** is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| scrollSizeMode<sup>12+</sup> | [ScrollSizeMode](#scrollsizemode12)   | No| Yes| Content update mode of the sheet when it is scrolled.<br>Default value: **ScrollSizeMode.FOLLOW_DETENT**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| keyboardAvoidMode<sup>13+</sup> | [SheetKeyboardAvoidMode](#sheetkeyboardavoidmode13) | No| Yes| How the sheet avoids the soft keyboard when it is brought up.<br> Default value: **TRANSLATE_AND_SCROLL**<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| enableHoverMode<sup>14+</sup>              | boolean | No| Yes  | Whether to respond when the device is in semi-folded mode.<br>Default value: **false**, meaning not to enable the hover mode.<br> Default value for 2-in-1 devices: **true**<br>**NOTE**<br>The bottom and popup sheets do not respond when the device is in semi-folded mode. The subwindow mode does not support the semi-folded mode.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| hoverModeArea<sup>14+</sup>              | [HoverModeAreaType](#hovermodeareatype14) | No| Yes  | Display area of the dialog box in hover mode.<br>Default value: **HoverModeAreaType.BOTTOM_SCREEN**<br> Default value for 2-in-1 devices: **HoverModeAreaType.TOP_SCREEN**<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| radius<sup>15+</sup> | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) \| [BorderRadiuses](ts-types.md#borderradiuses9) \| [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12) | No| Yes| Corner radius of the sheet.<br>To deliver the optimal experience, use the same radius for the four corners.<br>Default value: **32vp**<br>**NOTE**<br>1. The corner radius is displayed based on the set value. If it is not set, the default value is used. The bottom sheet does not display the bottom two corners, even if they are set.<br>2. If different corner radii are set for the four corners and one of the values is invalid, the corner pertaining to the invalid value is reset to the default value, while the other corners retain their set values. If a uniform corner radius is set for all four corners and the value is invalid, all four corners are reset to the default value.<br>3. When the corner radius is set as a percentage, the width of the sheet is used as the reference.<br>4. If the corner radius is greater than half the width of the sheet, it is set to half the width of the sheet.<br>5. If the height of the sheet is too small and the corner radius is set too large, it may cause display issues.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| detentSelection<sup>15+</sup>         <br>| [SheetSize](#sheetsize) \| [Length](ts-types.md#length) | No| Yes   | Initial detent (position) for non-gesture switching.<br>Default value: **detents[0]**<br>**NOTE**<br>1. The value must be within the range of the **detents** array. If the value is outside this range, this API has no effect.<br>2. When **SheetSize.FIT_CONTENT** is used, this API has no effect.<br>3. Avoid calling this API when gesture-based detent switching is used.<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| placement<sup>18+</sup> | [Placement](ts-appendix-enums.md#placement8) | No| Yes| Display position of the sheet popup relative to the target.<br>Default value: **Placement.Bottom**<br>**NOTE**<br> 1. The system attempts to display the popup at the specified position if the popup fits within the window. If this is not feasible, it tries vertical flipping first, followed by a 90° horizontal rotation.<br>2. If the alignment causes the popup to exceed the window bounds, it will be adjusted horizontally or vertically until fully visible.<br>3. If none of the four directions can accommodate the popup, the behavior depends on the value of the **placementOnTarget** property:<br>(1) If the property value is **true**, the popup moves in the mirror direction of the specified placement until fully visible.<br>(2) If the property value is **false**, the system selects the direction that can fully display the popup width and has the most remaining height. It then adjusts the sheet height to fit this direction, ensuring that the popup is displayed while maintaining the alignment specified by the **placement** setting.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| placementOnTarget<sup>18+</sup> | boolean | No| Yes| Whether the sheet popup can overlap the target if none of the four directions can accommodate the popup.<br> Default value: **true**<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| effectEdge<sup>18+</sup> | number | No| Yes| Edge effect used when the boundary of the scrolling area in reached in the sheet. Single-edge activation is supported.<br>Default value: [EffectEdge](ts-container-scrollable-common.md#effectedge18).START \| [EffectEdge](ts-container-scrollable-common.md#effectedge18).END (that is, value **3**)<br>**NOTE**<br>1. Only start edge: [EffectEdge](ts-container-scrollable-common.md#effectedge18).START<br>2. Only end edge: [EffectEdge](ts-container-scrollable-common.md#effectedge18).END<br>3. Both edges: [EffectEdge](ts-container-scrollable-common.md#effectedge18).START \| [EffectEdge](ts-container-scrollable-common.md#effectedge18).END (that is, value **3**)<br>4. Neither edge: [EffectEdge](ts-container-scrollable-common.md#effectedge18).START & [EffectEdge](ts-container-scrollable-common.md#effectedge18).END (that is, value **0**)<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| showInSubWindow<sup>19+</sup> | boolean                                  | No| Yes   | Whether to show the sheet in a separate subwindow.<br>Default value: **false**.<br>**NOTE**<br>1. **true**: The sheet displays in a separate subwindow and can extend beyond application window bounds.<br>2. **false**: The sheet displays only within application window bounds.<br>3. To prevent disruptions to the normal behavior of associated components, do not nest multiple dialog boxes where **showInSubWindow** is set to **true**.<br>4. Avoid using picker components (such as **CalendarPicker**, **CalendarPickerDialog**, **DatePickerDialog**, **TextPickerDialog**, and **TimePickerDialog**) in the dialog box where **showInSubWindow** is set to **true**, as the dialog box may affect the behavior of these components.<br>5. This property cannot be dynamically changed when the sheet is displayed.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| enableFloatingDragBar<sup>20+</sup>              | boolean | No| Yes  | Whether to display drag bar in a floating style. **true** to display in a a floating style, **false** otherwise.<br>Default value: **false**.<br> **NOTE**<br>The floating style takes effect only when the drag bar is visible, and the floating drag bar does not occupy layout space.<br> This parameter is fixed at **false** when **title** uses [CustomBuilder](ts-types.md#custombuilder8).<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| modalTransition<sup>20+</sup> | [ModalTransition](#modaltransition) | No| Yes| Transition animation for full-screen sheet style.<br>Default value: **ModalTransition.DEFAULT**.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## SheetSize

Enumerates the sheet heights.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     | Value   | Description                        |
| ------------------------- | ---- | -------------------------------- |
| MEDIUM                    | 0    | The sheet height is half of the screen height.<br>**Atomic service API**: This API can be used in atomic services since API version 11.  |
| LARGE                     | 1    | The sheet height is almost the screen height.<br>**Atomic service API**: This API can be used in atomic services since API version 11.  |
| FIT_CONTENT<sup>11+</sup> | 2    | The sheet height automatically adapts to the content.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**NOTE**<br>**FIT_CONTENT**: The sheet height automatically adapts to the layout of the builder root node of the child component. In this scenario, the height of the root node of the builder cannot use the percentage. The layout of the root node cannot depend on each other.|

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
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No| Yes  | Background color of the sheet.<br>Default value: **Color.White**<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| onWillAppear<sup>12+</sup>        | () => void                                 | No| Yes | Callback for when the sheet is about to be displayed (before the animation starts). **Atomic service API**: This API can be used in atomic services since API version 12.|
| onAppear        | () => void                                 | No| Yes  | Callback for when the sheet is displayed (after the animation ends).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| onWillDisappear<sup>12+</sup>     | () => void                                 | No| Yes  | Callback for when the sheet is about to disappear (before the animation starts).<br>**NOTE**<br>Modifying state variables within the **onWillDisappear** function is not allowed, as it may lead to unstable component behavior. **Atomic service API**: This API can be used in atomic services since API version 12.|
| onDisappear     | () => void                                 | No| Yes  | Callback for when the sheet disappears (after the animation ends).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## ModalTransition

Enumeration of full-modal transition modes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value| Description          |
| ------- | ---- | -------- |
| NONE    | - | No transition animation for the modal.  |
| DEFAULT | - | Slide-up and slide-down animation for the modal. |
| ALPHA   | - | Opacity gradient animation for the modal.|

## SheetType<sup>11+</sup>

Enumerates the sheet styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description                                              |
| ------ | ---- | ------------------------------------------------------ |
| BOTTOM | 0    | Bottom sheet.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| CENTER | 1    | Center sheet.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| POPUP  | 2    | Popup sheet. The popup sheet cannot be dismissed with a pull-down gesture.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| SIDE<sup>20+</sup>   | 3    | Side-aligned sheet.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| CONTENT_COVER<sup>20+</sup>   | 4    | Full-screen sheet.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

**Side-aligned sheet behavior**:

1. Transition animation: By default, the sheet enters from the right and exits to the right. In right-to-left (RTL) locales, it enters from the left and exits to the left. Custom transitions are not supported.

2. No multi-position capability is supported, and the detents and detentSelection APIs are not supported. The APIs related to the control bar, such as the dragBar API, are not supported.

3. You can swipe up to interact with the bottom pop-up after the transition ends. However, you can only swipe right to close the side pop-up after the transition ends. In the mirror scenario, the capabilities are opposite.

4. The height cannot be customized. The default height is full screen.

5. The APIs for specifying other display layers are not supported, such as showInSubWindow = true and mode = SheetMode.EMBEDDED. The layer of the side pop-up is the same as that of SheetMode.OVERLAY. The side pop-up can be displayed only at the top layer of the current UIContext and above all pages. It is displayed at the same level as dialog boxes.

6. The capability of avoiding the hover state is not supported.

7. Default width specifications of the side style semi-modal pop-up:
   - If the [breakpoint](../../../../application-dev/ui/arkts-layout-development-grid-layout.md#breakpoints) is md, the default width is half of the window width.
   - If the [breakpoint](../../../../application-dev/ui/arkts-layout-development-grid-layout.md#breakpoints) is greater than md, the default width is 400 vp.


Interfaces Not Supported by the Side Pop-up Window Style
| Name            | Description             |
| --------------- |  --------------- |
| height          | The height supports only the full-screen height.|
| detents | No detent capability.| 
| dragBar         | DragBar is not supported. |
| onDetentsDidChange | No detent capability.|
| uiContext | The display level cannot be specified.|
| mode | The display level cannot be specified.|
| scrollSizeMode | No detent capability. |
| enableHoverMode  | The avoidance capability in the hover state is not supported.|
| hoverModeArea    | The avoidance capability in the hover state is not supported.|
| detentSelection | No detent capability.|
| placement | Only the bubble style is supported.|
| placementOnTarget | Only the bubble style is supported.|
| showInSubWindow | The display level cannot be specified.|

bindSheet full-screen modal style description:

1. The full-screen style covers the entire screen. The border, shadow, title bar, close button, and rounded corners are not supported.

2. The builder content is laid out in the secure area by default.

3. The full-screen style supports the system transition mode [ModalTransition](#modaltransition). The default value is ModalTransition.DEFAULT. Custom transition is not supported.

4. The detent capability is not supported, and the detents and detentSelection APIs are not supported.

5. Swipe up and down are not supported. Only swipe from the side is supported.

6. The width and height cannot be customized. The default width and height are full screen.

7. The APIs for specifying other display levels are not supported, for example, showInSubWindow = true and mode = SheetMode.EMBEDDED. The level of the full-screen pop-up window is the same as that of SheetMode.OVERLAY. The full-screen pop-up window can be displayed only at the top of the current UIContext and is located above all pages. The full-screen pop-up window is displayed at the same level as the pop-up window component.

8. By default, the soft keyboard is not avoided. You need to customize the avoidance of the soft keyboard.

9. The mask effect is not supported.


APIs not supported by bindSheet full-screen modal style
| Name            | Description             |
| --------------- |  --------------- |
| height          | The height supports only the full-screen height.|
| width           | The width supports only the full-screen width.|
| detents | No detent capability.|
| dragBar         | The scroll bar cannot be dragged. |
| onDetentsDidChange | No position control capability.|
| showClose          | The close button cannot be displayed.|
| title          | The title bar cannot be displayed.|
| uiContext | The display level cannot be specified.|
| mode | The display level cannot be specified.|
| scrollSizeMode | No position control capability. |
| keyboardAvoidMode | No capability of avoiding the soft keyboard. You need to customize the avoidance.|
| enableHoverMode  | No capability of avoiding the soft keyboard in the hover state.|
| hoverModeArea    | No capability of avoiding the soft keyboard in the hover state.|
| detentSelection | No position control capability.|
| showInSubWindow | The display level cannot be specified.|
| radius         | Rounded corners are not supported. |
| borderWidth         | The border width is not supported. |
| borderColor         | The border color is not supported. |
| borderStyle         | The border style is not supported. |
| shadow         | The shadow is not supported. |
| maskColor      | The overlay color is not supported. |
| enableOutsideInteractive | The interaction permission cannot be set. |
| effectEdge     | The edge bounce effect is not supported. |
| enableFloatingDragBar | The floating scroll bar is not supported. |
| onWillSpringBackWhenDismiss | No bounce effect. |

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
| subtitle | [ResourceStr](ts-types.md#resourcestr) | No  | Yes  | Subtitle of the sheet.|

## SheetMode<sup>12+</sup>

Enumerates the display layer modes of a sheet.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                     | Value  | Description                        |
| ------------------------- | ---- | -------------------------------- |
| OVERLAY                   | 0    | The sheet is displayed at the top of the window corresponding to the current **UIContext** instance, above all pages. It is displayed at the same level as dialog boxes.  |
| EMBEDDED                  | 1    | The sheet is displayed at the top of the current page.<br>**NOTE**<br>Currently, the sheet can only be mounted on a **Page** or **NavDestination** node, with priority given to the **NavDestination** node if it is present. This means that, the sheet can only be displayed at the top of these two types of pages.<br> In this mode, new pages can overlay the sheet, and when the user returns to the previous page, the sheet remains present without losing its content.<br> In this mode, you must ensure that the target page node, such as the **Page** node, has been attached to the tree before bringing up the sheet; otherwise, the sheet will not be able to be attached to the corresponding page node.|

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
| reason | [DismissReason](ts-universal-attributes-popup.md#dismissreason12) | No   | No   | Type of operation that causes the sheet to be dismissed.<br>**NOTE**<br> DismissReason.SLIDE takes effect only for the semi-modal side pop-up window and indicates that the user swipes right to exit. If the mirroring scenario is used, the user swipes left to exit.<br> DismissReason.SLIDE_DOWN takes effect for the semi-modal bottom pop-up window and center pop-up window and indicates that the user swipes down to exit.<br> The semi-modal bubble pop-up window does not support the swiping exit capability.|

## SpringBackAction<sup>12+</sup>

Controls the interactive spring back of a sheet before it is dismissed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type                                      | Read-Only  | Optional  | Description           |
| --------------- | ---------------------------------------- | ---- | ---- | ------------- |
| springBack | [Callback](./ts-types.md#callback12)\<void> | No   | No   | Callback to control the interactive spring back before the sheet is dismissed. |

## SheetKeyboardAvoidMode<sup>13+</sup>

Method for avoiding the soft keyboard when the semi-modal page activates the input method.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Value  | Description                        |
| ------------------------- | ---- | -------------------------------- |
| NONE | 0    | Disables keyboard avoidance for the sheet.<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| TRANSLATE_AND_RESIZE    | 1    | Lifts the sheet to avoid the keyboard;<br>if not enough, resizes the content.<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| RESIZE_ONLY    | 2    | Resizes the content to avoid the keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| TRANSLATE_AND_SCROLL    | 3    | Lifts the sheet to avoid the keyboard;<br>if not enough, scrolls the content.<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| POPUP_SHEET<sup>20+</sup>    | 4    | Sets the popup style of a semi-modal dialog box to avoid the soft keyboard.<br> 1. When the popup style dialog box cannot be displayed in the current position due to the size of the dialog box, the display position is adjusted according to the following rules: first, the dialog box is vertically flipped to avoid the soft keyboard, and then the dialog box is rotated 90 degrees horizontally to avoid the soft keyboard. The following uses the preset direction as the bottom as an example. The adjustment sequence is as follows: bottom, top, right, and left.<br>2. If the alignment causes the popup to exceed the window bounds, it will be adjusted horizontally or vertically until fully visible.<br>3. If the current popup style dialog box cannot be displayed in any of the four directions when the soft keyboard is avoided, the processing method complies with the placementOnTarget attribute set by the developer.<br>(1) If the property value is **true**, the popup moves in the mirror direction of the specified placement until fully visible.<br>(2) If the property value is **false**, the system selects the direction that can fully display the popup width and has the most remaining height. It then adjusts the sheet height to fit this direction, ensuring that the popup is displayed while maintaining the alignment specified by the **placement** setting.<br>4. If the semi-modal dialog box is not a follow-up style, it cannot avoid the soft keyboard.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

> **NOTE**
>
> When setting the POPUP_SHEET avoidance mode, the semi-modal dialog box avoids only the soft keyboard started by the text box component in the panel. In other scenarios, the semi-modal dialog box does not need to avoid the soft keyboard.
>

## Example
### Example 1: Setting Sheets with Different Heights

This example demonstrates how to set different heights for sheets using the **height** property.

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
            console.log("BindSheet onWillAppear.");
          },
          onAppear: () => {
            console.log("BindSheet onAppear.");
          },
          onWillDisappear: () => {
            console.log("BindSheet onWillDisappear.");
          },
          onDisappear: () => {
            console.log("BindSheet onDisappear.");
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

![en-us_sheet](figures/en-us_sheet1.gif)

### Example 2: Setting Three Different Height Detents

This example demonstrates how to use the **detents** property of **bindSheet** to set three different height detents for a sheet.
1. The drag bar is only effective when there are multiple height detents.
2. Unlike the **height** property, which can set different heights at different times, the **detents** property provides a gesture to switch between detent heights and is more suitable for fixed height intervals.
3. If the height range is uncertain or there may be more than three different heights, avoid using the **detents** property.

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

![en-us_sheet](figures/en-us_sheet2.gif)

### Example 3: Setting the Border Width and Color

This example demonstrates how to use the **borderWidth** and **borderColor** properties with **LocalizedEdgeWidths** and **LocalizedEdgeColors** types in **bindSheet**.

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

![en-us_sheet](figures/en-us_sheet3_ltr.png)

The following shows how the example is represented with right-to-left scripts.

![en-us_sheet](figures/en-us_sheet3_rtl.png)

### Example 4: Using Dismiss Callbacks

This example shows how to register **onWillDismiss** and **onWillSpringBackWhenDismiss** with **bindSheet**.

```ts
// xxx.ets
@Entry
@Component
struct bindSheetExample {
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
            if (dismissSheetAction.reason == DismissReason.SLIDE_DOWN) {
              dismissSheetAction.dismiss(); // Register the dismiss behavior.
            }
          }),

          onWillSpringBackWhenDismiss: ((SpringBackAction: SpringBackAction) => {
            // No springBack is registered, so the half-modal will not bounce back when swiped down.
            //SpringBackAction.springBack();
          }),
        })
    }
  }
}
```
![en-us_sheet](figures/en-us_sheet4.gif)

### Example 5: Setting the Content Update Mode

This example shows how to use **ScrollSizeMode.CONTINUOUS**, which continuously updates the content and is suitable for detents with multiple height settings.
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
      Button('BindSheet')
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
The sheet's content height is not updated until the user stops dragging and releases the sheet.

![en-us_sheet](figures/en-us_sheet5_ltr.gif)

The sheet's content height is updated in real time as the user drags the sheet.

![en-us_sheet](figures/en-us_sheet5_rtl.gif)

### Example 6: Configuring the Sheet to Resize to Avoid the Keyboard

This example demonstrates how to adjust the scrollable content within a sheet when the keyboard height changes by setting **SheetKeyboardAvoidMode** to **RESIZE_ONLY**.

```ts
//xxx.ets
import window from '@ohos.window';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct ListenKeyboardHeightChange {
  @State isShow: boolean = false;
  @State avoidMode: SheetKeyboardAvoidMode = SheetKeyboardAvoidMode.RESIZE_ONLY;
  scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6];
  windowClass: window.Window | undefined = undefined;

  aboutToAppear(): void {
    try {
      window.getLastWindow(this.getUIContext().getHostContext(), (err: BusinessError, data) => {
        const errCode: number = err.code;
        if (errCode) {
          console.error(`Failed to obtain the top window, Cause code: ${err.code}, message: ${err.message}`);
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
        ForEach(this.arr, (item: number) => {
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
![en-us_sheet](figures/en-us_sheet6.gif)

### Example 7: Setting the Corner Radius in a Mirrored Layout

This example demonstrates how to set different corner radii for a sheet in a mirrored layout. Typically, to avoid a poor visual experience, do not set different values.

In this example, the **radius** property of the sheet uses the LocalizedBorderRadiuses type.

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

![en-us_sheet](figures/en-us_sheet7_ltr.png)

The following shows how the example is represented with right-to-left scripts.

![en-us_sheet](figures/en-us_sheet7_rtl.png)

### Example 8: ImplementIng a Side-Style Sheet

This example implements a side-style sheet.

```ts
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct SheetSideExample {
  @State isShowSide: boolean = false;
  @State enableOutsideInteractive: boolean = false;
  @State borderWidths: LocalizedEdgeWidths | undefined = undefined;
  @State borderColors: Resource | undefined = undefined;
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16];

  @Builder
  sideBuilder() {
    Column() {
      ForEach(this.arr, (item: number) => {
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
      Text('Change the semi-modal interaction mode')
        .fontSize(22).fontColor(0xFFFFFF).fontWeight(FontWeight.Bold).textAlign(TextAlign.Center)
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
      Button("Half-Modal Popover - Side")
        .onClick(() => {
          this.isShowSide = true;
        })
        .fontSize(20)
        .margin(10)
        .bindSheet($$this.isShowSide, this.sideBuilder(), {
          title: { title: "SideSheet", subtitle: "Default width" },
          backgroundColor: Color.Grey,
          onWillAppear: () => {
            console.log("SideSheet onWillAppear.");
          },
          onAppear: () => {
            console.log("SideSheet onAppear.");
          },
          onWillDisappear: () => {
            console.log("SideSheet onWillDisappear.");
          },
          onDisappear: () => {
            console.log("SideSheet onDisappear.");
          },

          preferType: SheetType.SIDE,  // SheetType.SIDE
          blurStyle: BlurStyle.Regular,
          maskColor: "#4bffc62d", // Custom mask color
          enableOutsideInteractive: this.enableOutsideInteractive,

          borderWidth: this.borderWidths,
          borderColor: this.borderColors,

          onHeightDidChange: (height: number)=>{
            console.log("SideSheet height change:" + height);
          },
          onTypeDidChange: (type: SheetType) => {
            console.log("SideSheet type change:" + type);
          },
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```



### Example 9: ImplementIng a ContentCover-Style Sheet

This example demonstrates how to display the sheet in full-screen ContentCover mode.

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
          this.isShow = true
        })
        .fontSize(20)
        .margin(10)
        .bindSheet(this.isShow, this.myBuilder(), {
          modalTransition: ModalTransition.DEFAULT,
          preferType: SheetType.CONTENT_COVER,
          backgroundColor: '#ffd5d5d5',
          maskColor: '#ff707070',
          onWillAppear: () => {
            console.log("ContentCover onWillAppear.")
          },
          onAppear: () => {
            console.log("ContentCover onAppear.")
          },
          onWillDisappear: () => {
            console.log("ContentCover onWillDisappear.")
          },
          onDisappear: () => {
            console.log("ContentCover onDisappear.")
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
![en-us_sheet](figures/en-us_sheet9_content_cover.gif)
