# ReplaceSymbolEffect

```TypeScript
declare class ReplaceSymbolEffect extends SymbolEffect
```

Inherits from **SymbolEffect**.

**Inheritance/Implementation:** ReplaceSymbolEffect extends [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md)

**Since:** 12

<!--Device-unnamed-declare class ReplaceSymbolEffect extends SymbolEffect--><!--Device-unnamed-declare class ReplaceSymbolEffect extends SymbolEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(scope?: EffectScope)
```

A constructor used to create a **ReplaceSymbolEffect** instance, which comes with a replace animation effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope)--><!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-symbolglyph-comp-effectscope-e.md) | No | Animation scope. For details about the specific enumeration values and descriptions, see EffectScope Enumeration Description.<br>Default value: EffectScope.LAYER |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)
```

A constructor used to create a **ReplaceSymbolEffect** instance, which comes with a replace animation effect. The replace effect type can be specified.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)--><!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-symbolglyph-comp-effectscope-e.md) | No | Animation scope.<br>Default value: EffectScope.LAYER |
| replaceType | [ReplaceEffectType](arkts-arkui-symbolglyph-comp-replaceeffecttype-e.md) | No | Replacement animation type.<br>Default value: ReplaceEffectType.SEQUENTIAL |

## replaceType

```TypeScript
replaceType?: ReplaceEffectType
```

Replacement Animation Type. For details about the specific enumeration values and descriptions, see ReplaceEffectType Enumeration Description.

Default value: ReplaceEffectType.SEQUENTIAL

**Type:** [ReplaceEffectType](arkts-arkui-symbolglyph-comp-replaceeffecttype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-ReplaceSymbolEffect-replaceType?: ReplaceEffectType--><!--Device-ReplaceSymbolEffect-replaceType?: ReplaceEffectType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scope

```TypeScript
scope?: EffectScope
```

Animation Scope. For details about the specific enumeration values and descriptions, see EffectScope Enumeration Description.

Default value: EffectScope.LAYER

**Type:** [EffectScope](arkts-arkui-symbolglyph-comp-effectscope-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ReplaceSymbolEffect-scope?: EffectScope--><!--Device-ReplaceSymbolEffect-scope?: EffectScope-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
