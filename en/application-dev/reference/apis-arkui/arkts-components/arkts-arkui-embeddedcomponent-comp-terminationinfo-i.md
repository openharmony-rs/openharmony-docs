# TerminationInfo

```TypeScript
declare interface TerminationInfo
```

Provides the result returned by the started **EmbeddedUIExtensionAbility**.

**Since:** 12

<!--Device-unnamed-declare interface TerminationInfo--><!--Device-unnamed-declare interface TerminationInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## code

```TypeScript
code: number
```

Result code returned when the EmbeddedUIExtensionAbility exits. The result code is determined by the data passed when terminateSelfWithResult or terminateSelf is called.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TerminationInfo-code: number--><!--Device-TerminationInfo-code: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

Data returned when the EmbeddedUIExtensionAbility exits.

**Type:** import('../api/@ohos.app.ability.Want').default

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default--><!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
