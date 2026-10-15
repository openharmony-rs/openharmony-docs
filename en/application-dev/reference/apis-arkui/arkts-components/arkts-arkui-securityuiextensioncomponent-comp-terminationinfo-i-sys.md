# TerminationInfo (System API)

```TypeScript
declare interface TerminationInfo
```

Defines the result returned when the started **UIExtensionAbility** exits normally.

**Since:** 26.0.0

<!--Device-unnamed-declare interface TerminationInfo--><!--Device-unnamed-declare interface TerminationInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## code

```TypeScript
code: number
```

Result code returned when the launched **UIExtensionAbility** exits. The value **0** indicates normal exit, and a non-zero value indicates abnormal exit. The specific meaning of the result code is defined by the launched **UIExtensionAbility**.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TerminationInfo-code: int--><!--Device-TerminationInfo-code: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

Data returned when the launched **UIExtensionAbility** exits. This field is empty if no data is returned.

**Type:** import('../api/@ohos.app.ability.Want').default

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default--><!--Device-TerminationInfo-want?: import('../api/@ohos.app.ability.Want').default-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
