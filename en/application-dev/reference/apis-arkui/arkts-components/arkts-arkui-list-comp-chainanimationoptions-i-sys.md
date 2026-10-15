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

Conduction coefficient of the chained linkage animation effect, which controls the influence range of the linkage. The value range is [0,1]. The larger the value, the more list items are affected by the chained linkage. If the value is out of range, the default value is used.

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

Damping of the chained linkage animation effect, which controls the oscillation decay speed.

Value range: (0, +∞). The larger the value, the faster the animation decays and the fewer the oscillations; the smaller the value, the more likely the animation is to oscillate. If the value is set to a value less than or equal to 0, the current value remains unchanged; if it has never been set, the default value is used.

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

Edge effect of the chained linkage animation effect, which controls how the spacing changes after the list scrolls to the edge. **DEFAULT** presents directional stretching and rebound feedback, and **STRETCH** presents synchronous stretching feedback of all list items.

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

Intensity of the chained linkage animation effect, which controls the displacement amplitude of list items in the chained linkage. The value range is [0,1]. The larger the value, the greater the displacement amplitude of list items in the chained linkage. If the value is out of range, the default value is used.

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

Maximum spacing of the chained linkage animation effect.

Unit: same as **Length**. If the value is less than the spacing between list items (**space**), the spacing between list items is used.

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

Minimum spacing of the chained linkage animation effect.

Unit: same as **Length**. If the value is less than 0, 0 is used; if the value is greater than the spacing between list items (**space**), the spacing between list items is used.

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

Stiffness of the chained linkage animation effect, which controls the rebound speed and animation hardness.

Value range: (0, +∞). The larger the value, the faster the rebound speed and the harder the animation; the smaller the value, the softer the animation. If the value is set to a value less than or equal to 0, the current value remains unchanged; if it has never been set, the default value is used.

**Type:** number

**Default:** 228

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainAnimationOptions-stiffness?: number--><!--Device-ChainAnimationOptions-stiffness?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
