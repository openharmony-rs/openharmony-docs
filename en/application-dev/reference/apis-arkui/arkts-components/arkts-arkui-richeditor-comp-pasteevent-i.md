# PasteEvent

```TypeScript
declare interface PasteEvent
```

Defines a user paste event.

**Since:** 11

<!--Device-unnamed-declare interface PasteEvent--><!--Device-unnamed-declare interface PasteEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## preventDefault

```TypeScript
preventDefault?: Callback<void>
```

Prevents the system default paste event.

When omitted, the system default paste behavior is executed.

**Type:** Callback&lt;void&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PasteEvent-preventDefault?: Callback<void>--><!--Device-PasteEvent-preventDefault?: Callback<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
