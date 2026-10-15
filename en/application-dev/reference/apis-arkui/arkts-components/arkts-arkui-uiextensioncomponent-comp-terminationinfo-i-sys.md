# TerminationInfo (System API)

```TypeScript
declare interface TerminationInfo
```

Triggered when the started UIExtensionAbility exits properly by calling **terminateSelfWithResult** or **terminateSelf**.

**Since:** 12

<!--Device-unnamed-declare interface TerminationInfo--><!--Device-unnamed-declare interface TerminationInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## code

```TypeScript
code: number
```

Result code returned when the launched **UIExtensionAbility** exits. The result code is determined by the data passed in when `terminateSelfWithResult` or `terminateSelf` is called.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-TerminationInfo-code: number--><!--Device-TerminationInfo-code: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

Data returned when the launched **UIExtensionAbility** exits. The default value is **undefined**.

**Type:** import('../api/@ohos.app.ability.Want').default

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default--><!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
