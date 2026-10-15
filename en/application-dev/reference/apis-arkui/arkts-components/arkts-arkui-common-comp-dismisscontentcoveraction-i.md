# DismissContentCoverAction

```TypeScript
declare interface DismissContentCoverAction
```

Component content cover dismiss

**Since:** 12

<!--Device-unnamed-declare interface DismissContentCoverAction--><!--Device-unnamed-declare interface DismissContentCoverAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

Callback invoked when the full-screen modal page is closed. This method must be called in the onWillDismiss callback to close the full-screen modal page. If it is not called, the full-screen modal page remains open.

**Type:** [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DismissContentCoverAction-dismiss: Callback<void>--><!--Device-DismissContentCoverAction-dismiss: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

Type of operation that triggers the dismiss of the modal.

**Type:** [DismissReason](arkts-arkui-common-comp-dismissreason-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DismissContentCoverAction-reason: DismissReason--><!--Device-DismissContentCoverAction-reason: DismissReason-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
