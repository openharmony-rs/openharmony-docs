# ClickEffect

```TypeScript
declare interface ClickEffect
```

Defines the click effect.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## level

```TypeScript
level: ClickEffectLevel
```

Click feedback effect of the component.

Default value: **ClickEffectLevel.LIGHT**

**NOTE:** 

When **level** is **undefined** or **null**, **ClickEffect** uses the effect corresponding to **ClickEffectLevel.LIGHT** with a scaling ratio as described below.

**Type:** [ClickEffectLevel](../arkts-apis/arkts-arkui-clickeffectlevel-e.md)

**Default:** ClickEffectLevel.LIGHT

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: number
```

Custom scaling ratio for fine-tuning the click feedback effect.

**NOTE:** 

The default value varies depending on the value of **level**:

**ClickEffectLevel.LIGHT**: **0.90**

**ClickEffectLevel.MIDDLE** or **ClickEffectLevel.HEAVY**: **0.95**

**undefined** or **null** (treated as **ClickEffectLevel.LIGHT**): **0.90**

When **scale** is set to **undefined** or **null**, the default scaling ratio for the current **level** is used.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
