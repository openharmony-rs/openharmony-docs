# DismissSheetAction

```TypeScript
declare interface DismissSheetAction
```

Component sheet dismiss

**Since:** 12

<!--Device-unnamed-declare interface DismissSheetAction--><!--Device-unnamed-declare interface DismissSheetAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

Callback for dismissing the sheet. Call this API when you need to exit the page.

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DismissSheetAction-dismiss: Callback<void>--><!--Device-DismissSheetAction-dismiss: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

Returns the operation type for exiting the current semi-modal page.

**Note:** 

DismissReason.SLIDE takes effect only for the side popup style of the semi-modal page, indicating exit by swiping right. In a mirrored scenario, it indicates exit by swiping left.

DismissReason.SLIDE_DOWN takes effect for the bottom popup style and center popup style of the semi-modal page, indicating exit by swiping down.

The bubble popup style of the semi-modal page does not support swipe-to-exit.

**Type:** [DismissReason](arkts-arkui-common-comp-dismissreason-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DismissSheetAction-reason: DismissReason--><!--Device-DismissSheetAction-reason: DismissReason-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
