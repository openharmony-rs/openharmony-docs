# DismissDialogAction

Provides information about the action to dismiss the dialog box.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dismiss

```TypeScript
dismiss: Callback<void>
```

Callback for dismissing the dialog box. This API is called only when the dialog box needs to be exited.

**Type:** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

Reason why the dialog box cannot be dismissed. You must specify whether to close the dialog box for each of the listed actions.

**Type:** [DismissReason](../arkts-components/arkts-arkui-dismissreason-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
