# ReplaceSymbolEffect

Defines ReplaceSymbolEffect class, which inherits from **SymbolEffect**.

**Inheritance/Implementation:** ReplaceSymbolEffect extends [SymbolEffect](arkts-arkui-symboleffect-c.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(scope?: EffectScope)
```

A constructor used to create an **AppearSymbolEffect** instance, which comes with an appear animation effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-effectscope-e.md) | No | Effect scope.<br>Default value: **EffectScope.LAYER** |

## constructor

```TypeScript
constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)
```

A constructor used to create a **ReplaceSymbolEffect** instance, which comes with a replace animation effect. The replace effect type can be specified.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-effectscope-e.md) | No | Effect scope.<br>Default value: **EffectScope.LAYER** |
| replaceType | [ReplaceEffectType](arkts-arkui-replaceeffecttype-e.md) | No | Replacement effect type.<br>Default value: **ReplaceEffectType.SEQUENTIAL** |

## replaceType

```TypeScript
replaceType?: ReplaceEffectType
```

Replacement effect type.

Default value: **ReplaceEffectType.SEQUENTIAL**.

**Type:** [ReplaceEffectType](arkts-arkui-replaceeffecttype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scope

```TypeScript
scope?: EffectScope
```

Effect scope.

Default value: **EffectScope.LAYER**

**Type:** [EffectScope](arkts-arkui-effectscope-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
