# DismissSheetAction

```TypeScript
declare interface DismissSheetAction
```

Component sheet dismiss

@interface DismissSheetAction

**Since:** 12

<!--Device-unnamed-declare interface DismissSheetAction--><!--Device-unnamed-declare interface DismissSheetAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

Defines sheet dismiss function

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

Dismiss reason type.

**Type:** [DismissReason](arkts-arkui-common-comp-dismissreason-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DismissSheetAction-reason: DismissReason--><!--Device-DismissSheetAction-reason: DismissReason-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
