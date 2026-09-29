# HierarchicalSymbolEffect

```TypeScript
declare class HierarchicalSymbolEffect extends SymbolEffect
```

Inherits from **SymbolEffect**.

**Inheritance/Implementation:** HierarchicalSymbolEffect extends [SymbolEffect](arkts-arkui-symbolglyph-comp-symboleffect-c.md)

**Since:** 12

<!--Device-unnamed-declare class HierarchicalSymbolEffect extends SymbolEffect--><!--Device-unnamed-declare class HierarchicalSymbolEffect extends SymbolEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(fillStyle?: EffectFillStyle)
```

A constructor used to create a **HierarchicalSymbolEffect** instance, which comes with a hierarchical animation effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-HierarchicalSymbolEffect-constructor(fillStyle?: EffectFillStyle)--><!--Device-HierarchicalSymbolEffect-constructor(fillStyle?: EffectFillStyle)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillStyle | [EffectFillStyle](arkts-arkui-symbolglyph-comp-effectfillstyle-e.md) | No | Animation mode. For the specific enumeration values and descriptions, see EffectFillStyle Enumeration Description.<br>Default value: EffectFillStyle.CUMULATIVE |

## fillStyle

```TypeScript
fillStyle?: EffectFillStyle
```

Animation mode.

Default value: EffectFillStyle.CUMULATIVE

**Type:** [EffectFillStyle](arkts-arkui-symbolglyph-comp-effectfillstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-HierarchicalSymbolEffect-fillStyle?: EffectFillStyle--><!--Device-HierarchicalSymbolEffect-fillStyle?: EffectFillStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
