# AppearSymbolEffect

```TypeScript
declare class AppearSymbolEffect extends SymbolEffect
```

Defines AppearSymbolEffect class, which inherits from **SymbolEffect**.

**Inheritance/Implementation:** AppearSymbolEffect extends [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md)

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
| scope | [EffectScope](arkts-arkui-symbolglyph-comp-effectscope-e.md) | No | Effect scope.<br>Default value: **EffectScope.LAYER** |

## scope

```TypeScript
scope?: EffectScope
```

Effect scope.

Default value: **EffectScope.LAYER**

**Type:** [EffectScope](arkts-arkui-symbolglyph-comp-effectscope-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
