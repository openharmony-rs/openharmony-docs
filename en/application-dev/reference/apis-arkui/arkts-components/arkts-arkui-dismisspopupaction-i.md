# DismissPopupAction

Provides information about the dismissal of the popup.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

Callback for dismissing the popup. This API is called only when the popup needs to be dismissed.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

Reason why the popup is dismissed.

**Type:** [DismissReason](arkts-arkui-dismissreason-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
