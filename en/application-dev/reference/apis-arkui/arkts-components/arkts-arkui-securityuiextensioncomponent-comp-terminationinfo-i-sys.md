# TerminationInfo (System API)

```TypeScript
declare interface TerminationInfo
```

Defines the result returned when the started **UIExtensionAbility** exits normally.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## code

```TypeScript
code: number
```

Result code returned when the **UIExtensionAbility** exits. The value **0** indicates that the **UIExtensionAbility** exits normally, and a non-zero value indicates that the **UIExtensionAbility** exits abnormally. The meaning of the result code is defined by the **UIExtensionAbility** that is started. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## want

```TypeScript
want?: import('../api/@ohos.app.ability.Want').default
```

Data returned when the **UIExtensionAbility** exits.

**Type:** import('../api/@ohos.app.ability.Want').default

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
