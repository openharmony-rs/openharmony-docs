# DragInteractionOptions

```TypeScript
declare interface DragInteractionOptions
```

Interaction behavior for the floating preview image

**Since:** 12

<!--Device-unnamed-declare interface DragInteractionOptions--><!--Device-unnamed-declare interface DragInteractionOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultAnimationBeforeLifting

```TypeScript
defaultAnimationBeforeLifting?: boolean
```

Whether to enable the default press animation (scale-down) during long-press lift phase. **true** to enable, **false** otherwise.

Default value: **false**.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DragInteractionOptions-defaultAnimationBeforeLifting?: boolean--><!--Device-DragInteractionOptions-defaultAnimationBeforeLifting?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableEdgeAutoScroll

```TypeScript
enableEdgeAutoScroll?: boolean
```

Whether to trigger automatic scrolling when users drag to the edges of a scrollable container.

**true**: Trigger automatic scrolling.

**false**: Do not trigger automatic scrolling.

Default value: **true**

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DragInteractionOptions-enableEdgeAutoScroll?: boolean--><!--Device-DragInteractionOptions-enableEdgeAutoScroll?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Whether to enable haptic feedback during dragging.

**true**: Enable haptic feedback during dragging.

**false**: Disable haptic feedback during dragging. This parameter is effective only for previews with masks (configured using [bindContextMenu](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu2)).

Note: The settings take effect only when the application has the **ohos.permission.VIBRATE** permission and the user has enabled haptic feedback.

Default value: **false**

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DragInteractionOptions-enableHapticFeedback?: boolean--><!--Device-DragInteractionOptions-enableHapticFeedback?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isLiftingDisabled

```TypeScript
isLiftingDisabled?: boolean
```

Whether to disable the lift animation effect during dragging.

**true**: Disable the lifting effect during dragging.

**false**: Enable the lifting effect during dragging.

With the value **true**, only the custom menu preview (set using [bindContextMenu](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu1)), also known as the long-press preview, is displayed if both the long-press preview and drag preview are configured.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-DragInteractionOptions-isLiftingDisabled?: boolean--><!--Device-DragInteractionOptions-isLiftingDisabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isMultiSelectionEnabled

```TypeScript
isMultiSelectionEnabled?: boolean
```

Whether to enable multi-select clustering during drag operations. **true** to enable, **false** otherwise. This parameter takes effect only for the [grid items](arkts-arkui-griditem-comp.md) and [list items](arkts-arkui-listitem-comp.md) in the [Grid](arkts-arkui-grid-comp.md) and [List](arkts-arkui-list-comp.md) containers.

When this feature is enabled, child components cannot be dragged individually. Preview priority: string in [dragPreview](arkts-arkui-common-comp-commonmethod-c.md#dragpreview1) &gt; PixelMap in **dragPreview**  
> component snapshot. Builder previews not supported.

This parameter is incompatible with bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu12) using **isShown** parameter.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DragInteractionOptions-isMultiSelectionEnabled?: boolean--><!--Device-DragInteractionOptions-isMultiSelectionEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
