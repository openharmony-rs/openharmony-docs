# ChainAnimationOptions (System API)

```TypeScript
declare interface ChainAnimationOptions
```

Defines a collection of chain animation effect attributes, used to set the maximum spacing, minimum spacing, animation intensity, conduction coefficient, edge effect, stiffness, and damping of the list. When the list requires fine-grained control over the chained linkage elastic effect, different animation feels can be achieved by adjusting the parameters in this object.

**Since:** 10

<!--Device-unnamed-declare interface ChainAnimationOptions--><!--Device-unnamed-declare interface ChainAnimationOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## conductivity

```TypeScript
conductivity?: number
```

Conductivity of chain animation.

**Type:** number

**Default:** 0.7

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-conductivity?: number--><!--Device-ChainAnimationOptions-conductivity?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## damping

```TypeScript
damping?: number
```

Damping of chain spring.

**Type:** number

**Default:** 30

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-damping?: number--><!--Device-ChainAnimationOptions-damping?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeEffect

```TypeScript
edgeEffect?: ChainEdgeEffect
```

Edge effect of chain animation.

**Type:** [ChainEdgeEffect](arkts-arkui-list-comp-chainedgeeffect-e-sys.md)

**Default:** ChainEdgeEffect.DEFAULT

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-edgeEffect?: ChainEdgeEffect--><!--Device-ChainAnimationOptions-edgeEffect?: ChainEdgeEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## intensity

```TypeScript
intensity?: number
```

Intensity of chain animation.

**Type:** number

**Default:** 0.3

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-intensity?: number--><!--Device-ChainAnimationOptions-intensity?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## maxSpace

```TypeScript
maxSpace: Length
```

Maximum space for chain animation. <br>Unit: same as **Length**.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-maxSpace: Length--><!--Device-ChainAnimationOptions-maxSpace: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## minSpace

```TypeScript
minSpace: Length
```

Minimum space for chain animation. <br>Unit: same as **Length**.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-minSpace: Length--><!--Device-ChainAnimationOptions-minSpace: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## stiffness

```TypeScript
stiffness?: number
```

Stiffness of chain spring.

**Type:** number

**Default:** 228

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-stiffness?: number--><!--Device-ChainAnimationOptions-stiffness?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
