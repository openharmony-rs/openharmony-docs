# DisturbanceFieldOptions

```TypeScript
declare interface DisturbanceFieldOptions
```

Sets the parameters of the disturbance field.

**Since:** 12

<!--Device-unnamed-declare interface DisturbanceFieldOptions--><!--Device-unnamed-declare interface DisturbanceFieldOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## feather

```TypeScript
feather?: number
```

Feathering value, which indicates the degree of attenuation from the center of the field to the field edge. It is an integer ranging from 0 to 100. The value **0** indicates that the field is a rigid body, and all particles within the range are repelled. A larger feathering value indicates a greater degree of easing of the field, and more particles close to the center appear within the field range. If the value is set to negative or greater than 100, the default value is used. If the value is set to a non-integer, it is truncated to an integer.

Default value: **0**.

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-feather?: number--><!--Device-DisturbanceFieldOptions-feather?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## noiseAmplitude

```TypeScript
noiseAmplitude?: number
```

Noise amplitude, which indicates the fluctuation range of the noise value. A larger amplitude indicates a larger fluctuation range. The value must be greater than or equal to 0.

Default value: **1**. If a negative value is passed in, the default value **1** is used.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-noiseAmplitude?: number--><!--Device-DisturbanceFieldOptions-noiseAmplitude?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## noiseFrequency

```TypeScript
noiseFrequency?: number
```

Noise frequency. A larger frequency indicates finer noise. The value must be greater than or equal to 0.

Default value: **1**. If a negative value is passed in, the default value **1** is used.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-noiseFrequency?: number--><!--Device-DisturbanceFieldOptions-noiseFrequency?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## noiseScale

```TypeScript
noiseScale?: number
```

Noise scale, used to control the overall size of the noise pattern. The value must be greater than or equal to 0.

Default value: **1**. If a negative value is passed in, the default value **1** is used.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-noiseScale?: number--><!--Device-DisturbanceFieldOptions-noiseScale?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

Position of the field, in vp.

Default value: **{x:0, y:0}**.

Value range of x and y: (-∞, +∞).

**Type:** [PositionT](arkts-arkui-particle-comp-positiont-t.md)&lt;number&gt;

**Default:** {x:0,y:0}

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-position?: PositionT<number>--><!--Device-DisturbanceFieldOptions-position?: PositionT<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: DisturbanceFieldShape
```

Shape of the field.

The default value is **DisturbanceFieldShape.RECT**.

**Type:** [DisturbanceFieldShape](arkts-arkui-particle-comp-disturbancefieldshape-e.md)

**Default:** DisturbanceFieldShape.RECT

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-shape?: DisturbanceFieldShape--><!--Device-DisturbanceFieldOptions-shape?: DisturbanceFieldShape-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

Size of the field, in vp.

Default value: **{width:0, height:0}**.

Value range of **width** and **height**: [0, +∞).

**Type:** [SizeT](arkts-arkui-particle-comp-sizet-t.md)&lt;number&gt;

**Default:** {width:0,height:0}

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-size?: SizeT<number>--><!--Device-DisturbanceFieldOptions-size?: SizeT<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strength

```TypeScript
strength?: number
```

Field strength, which indicates the strength of the repulsive force from the center of the field outward. Default value: **0**. A positive value indicates that the repulsive force points outward, and a negative value indicates an attractive force pointing inward.

Value range: (-∞, +∞).

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DisturbanceFieldOptions-strength?: number--><!--Device-DisturbanceFieldOptions-strength?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
