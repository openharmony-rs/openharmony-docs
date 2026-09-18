# HierarchicalSymbolEffect

Defines HierarchicalSymbolEffect class, which inherits from **SymbolEffect**.

**Inheritance/Implementation:** HierarchicalSymbolEffect extends [SymbolEffect](arkts-arkui-symboleffect-c.md)

**Since:** 12

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillStyle | [EffectFillStyle](arkts-arkui-effectfillstyle-e.md) | No | Effect fill style.<br>Default value: **EffectFillStyle.CUMULATIVE** |

## fillStyle

```TypeScript
fillStyle?: EffectFillStyle
```

Effect fill style.

Default value: **EffectFillStyle.CUMULATIVE**

**Type:** [EffectFillStyle](arkts-arkui-effectfillstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
