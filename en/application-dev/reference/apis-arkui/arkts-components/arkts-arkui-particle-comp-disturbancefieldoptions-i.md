# DisturbanceFieldOptions

```TypeScript
declare interface DisturbanceFieldOptions
```

Defines particle disturbance Field params.

@interface DisturbanceFieldOptions

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## feather

```TypeScript
feather?: number
```

Feather value, which represents the degree of attenuation from the center of the field to its edges. The value is an integer ranging from 0 to 100. A value of 0 indicates that the field is rigid, and all particles within its range are repelled. The higher the feather value, the more gradual the field becomes, resulting in more particles close to the center point appearing within the field's range.

Default value: **0**.

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## noiseAmplitude

```TypeScript
noiseAmplitude?: number
```

Noise amplitude, which indicates the range of noise fluctuations. The greater the amplitude, the greater the difference between the noises. The value is greater than or equal to 0.

Default value: **1**.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## noiseFrequency

```TypeScript
noiseFrequency?: number
```

Noise frequency. The higher the frequency, the finer the noise. The value is greater than or equal to 0.

Default value: **1**.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## noiseScale

```TypeScript
noiseScale?: number
```

Noise scale, used to control the overall size of the noise pattern. The value is greater than or equal to 0.

Default value: **1**.

**Type:** number

**Default:** 1

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

Position of the field.

Default value: {x:0, y:0}.

Value range of **x** and **y**: (-∞, +∞).

**Type:** [PositionT](arkts-arkui-particle-comp-positiont-t.md)&lt;number&gt;

**Default:** {x:0,y:0}

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: DisturbanceFieldShape
```

Shape of the field.

Default value: **DisturbanceFieldShape.RECT**

**Type:** [DisturbanceFieldShape](arkts-arkui-particle-comp-disturbancefieldshape-e.md)

**Default:** DisturbanceFieldShape.RECT

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

Size of the field.

Default value: {width:0, height:0}.

Value range of **width** and **height**: [0, +∞).

**Type:** [SizeT](arkts-arkui-particle-comp-sizet-t.md)&lt;number&gt;

**Default:** {width:0,height:0}

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strength

```TypeScript
strength?: number
```

Field strength, which indicates the intensity of the repulsive force from the center outward. The default value is **0**. Positive values indicate a repulsive force directed outward, while negative values indicate an attractive force directed inward.

Value range: (-∞, +∞).

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
