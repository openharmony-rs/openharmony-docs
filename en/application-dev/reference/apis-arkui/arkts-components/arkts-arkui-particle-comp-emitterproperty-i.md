# EmitterProperty

```TypeScript
interface EmitterProperty
```

Defines the emitter property.

@interface EmitterProperty

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## annulusRegion

```TypeScript
annulusRegion?: ParticleAnnulusRegion
```

the description of the annulus region. This parameter is valid only for emitter whose shape is annulus.

**Type:** [ParticleAnnulusRegion](arkts-arkui-particle-comp-particleannulusregion-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emitRate

```TypeScript
emitRate?: number
```

Emit rate, that is, the number of particles emitted per second.

If no value is passed in, the current emit rate is retained. If a value less than 0 is passed in, the default value **5** is used. The **emitRate** value can significantly impact performance when it exceeds 5000; you are advised to set it to be less than 5000.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the emitter based on the index array of the emitters in the initialization parameters. The value is rounded to the nearest whole number. The default value **0** is used in case of exceptions.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

Array of emitter positions. Only the number type is supported.

If no value is passed in, the current emitter position is retained. Two valid values must be passed in; if either is an invalid value, **position** will not take effect.

Value range of **x** and **y**: (-∞, +∞).

**Type:** [PositionT](arkts-arkui-particle-comp-positiont-t.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

Size of the emit window. Only the number type is supported.

If no value is passed in, the current emitter window size is retained. Two valid values greater than 0 must be passed in; if either is an invalid value, **size** will not take effect.

**Type:** [SizeT](arkts-arkui-particle-comp-sizet-t.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
