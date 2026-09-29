# BounceSymbolEffect

```TypeScript
declare class BounceSymbolEffect extends SymbolEffect
```

Inherits from **SymbolEffect**.

**Inheritance/Implementation:** BounceSymbolEffect extends [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md)

**Since:** 12

<!--Device-unnamed-declare class BounceSymbolEffect extends SymbolEffect--><!--Device-unnamed-declare class BounceSymbolEffect extends SymbolEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(scope?: EffectScope, direction?: EffectDirection)
```

A constructor used to create a **BounceSymbolEffect** instance, which comes with a bounce animation effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BounceSymbolEffect-constructor(scope?: EffectScope, direction?: EffectDirection)--><!--Device-BounceSymbolEffect-constructor(scope?: EffectScope, direction?: EffectDirection)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-symbolglyph-comp-effectscope-e.md) | No | Animation scope. For details about the specific enumeration values and descriptions, see EffectScope Enumeration Description.<br>Default value: EffectScope.LAYER |
| direction | [EffectDirection](arkts-arkui-symbolglyph-comp-effectdirection-e.md) | No | Animation direction. For details about the specific enumeration values and descriptions, see EffectDirection Enumeration Description.<br>Default value: EffectDirection.DOWN |

## direction

```TypeScript
direction?: EffectDirection
```

Animation direction. For details about the specific enumeration values and descriptions, see EffectDirection Enumeration Description.

Default value: EffectDirection.DOWN

**Type:** [EffectDirection](arkts-arkui-symbolglyph-comp-effectdirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BounceSymbolEffect-direction?: EffectDirection--><!--Device-BounceSymbolEffect-direction?: EffectDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scope

```TypeScript
scope?: EffectScope
```

Animation scope. For details about the specific enumeration values and descriptions, see EffectScope Enumeration Description.

Default value: EffectScope.LAYER

**Type:** [EffectScope](arkts-arkui-symbolglyph-comp-effectscope-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BounceSymbolEffect-scope?: EffectScope--><!--Device-BounceSymbolEffect-scope?: EffectScope-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
