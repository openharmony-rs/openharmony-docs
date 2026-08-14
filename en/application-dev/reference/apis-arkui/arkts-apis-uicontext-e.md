# Enums

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

This section provides enumeration types related to UIContext, which are used to configure scenarios such as keyboard avoidance, dynamic frame rate scenes, node rendering states, gesture listening, custom keyboard continuation, and text selection clearing policies.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## KeyboardAvoidMode<sup>11+</sup>

Enumerates the modes in which the layout responds when the keyboard is displayed.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description      |
| ------ | ---- | ---------- |
| OFFSET | 0    | Offset mode.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| RESIZE | 1    | Resize mode.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| OFFSET_WITH_CARET<sup>14+</sup> | 2 | Offset mode that also triggers avoidance when the input box cursor position changes.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| RESIZE_WITH_CARET<sup>14+</sup> | 3 | Resize mode that also triggers avoidance when the input box cursor position changes.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|
| NONE<sup>14+</sup>  | 4 | No keyboard avoidance.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|

## SwiperDynamicSyncSceneType<sup>12+</sup>

Enumerates the dynamic sync scene types.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value  | Description                  |
| -------- | ---- | ---------------------- |
| GESTURE | 0   | Gesture operation.|
| ANIMATION | 1   | Animation transition.|

## MarqueeDynamicSyncSceneType<sup>14+</sup>

Enumerates the dynamic sync scene types for the **Marquee** component.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value  | Description                  |
| -------- | ---- | ---------------------- |
| ANIMATION | 1   | Animation transition.|

## NodeRenderState<sup>20+</sup>

Enumerates node rendering states.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value|Description|
| -------- | ------- | -------- |
| ABOUT_TO_RENDER_IN | 0 | The node has been mounted to the rendering tree and will typically be rendered in the next frame and become visible to the user. However, a node being rendered does not necessarily mean that it is visible.|
| ABOUT_TO_RENDER_OUT | 1 | The node has been removed from the rendering tree and will generally not be rendered in the next frame. Users will no longer see this node.|

## GestureActionPhase<sup>20+</sup>

Enumerates triggering phases of gesture callbacks, corresponding to the action callbacks defined in **gesture.d.ts**. However, different gesture types support different phases (for example, **SwipeGesture** only includes the **WILL_START** enumerated value).

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description      |
| ------ | ---- | ---------- |
| WILL_START | 0 | The gesture has been successfully recognized by the system, and the **onActionStart** or **onAction** callback will be triggered immediately. If the gesture is bound to **onActionStart**, the callback is triggered at **onActionStart**. If the gesture is bound to **onAction**, the callback is triggered at **onAction**. If both are bound, the callback is triggered at **onActionStart** with priority. If neither is bound, no callback will be triggered. Containers with built-in gesture callbacks (such as scrollable containers) support the **onActionStart** or **onAction** callback triggering mechanism by default. For these containers, callbacks can be triggered without explicit binding.|
| WILL_END | 1 | The gesture has been determined to be in an ended state (typically occurring when the user lifts their finger to terminate the interaction). The **onActionEnd** callback will be triggered immediately, but the gesture must be explicitly bound to **onActionEnd**. Containers with built-in gesture callbacks (such as scrolling containers) support gesture end status determination by default. The **onActionEnd** callback can be triggered without explicit binding.|

## GestureListenerType<sup>20+</sup>

Enumerates the types of gestures to be listened for.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description      |
| ------ | ---- | ---------- |
| TAP | 0 | Tap gesture.|
| LONG_PRESS | 1 | Long press gesture.|
| PAN | 2 | Pan gesture.|
| PINCH | 3 | Pinch gesture.|
| SWIPE | 4 | Swipe gesture.|
| ROTATION | 5 | Rotation gesture.|

## ResolveStrategy<sup>22+</sup>

Enumerates resolution strategies for **UIContext** objects.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description      |
| ------ | ---- | ---------- |
| CALLING_SCOPE | 0 | Obtain the UIContext of the current calling scope.|
| LAST_FOCUS | 1 | Obtain the UIContext of the instance that most recently switched to the focused state.|
| MAX_INSTANCE_ID | 2 | Obtain the UIContext of the instance with the largest instance ID.|
| UNIQUE | 3 | Obtain the UIContext of the unique UI instance (when only one UI instance exists).|
| LAST_FOREGROUND | 4 | Obtain the UIContext of the instance that most recently switched to the foreground.|
| UNDEFINED | 5 | Obtain a UIContext with an ambiguous calling scope.|

## CustomKeyboardContinueFeature<sup>23+</sup>

Sets whether the custom keyboard remains persistent during input field switches.

When enabled, the customer keyboard will remain displayed without being dismissed and re-launched during input field switches.

When disabled, the customer keyboard will dismiss and re-launch during input field switches.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction:** This API can be used only in the stage model.

| Name  | Value  | Description      |
| ------ | ---- | ---------- |
| ENABLED | 0 | The custom keyboard remains persistent.|
| DISABLED | 1 | The custom keyboard does not remain persistent.|

## TextSelectionClearPolicy

Enumerates text selection clearing policies.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction:** This API can be used only in the stage model.

| Name  | Value  | Description      |
| ------ | ---- | ---------- |
| KEEP_SELECTED_TEXT_ON_EXTERNAL_TOUCH | 0 | When the user touches outside the text component, the text selection and handles are retained.|
| CLEAR_SELECTED_TEXT_ON_EXTERNAL_TOUCH | 1 | When the user touches outside the text component, the text selection and handles are cleared.|
