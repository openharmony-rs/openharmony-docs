# EmitterProperty

```TypeScript
interface EmitterProperty
```

Sets the emitter attributes.

**Since:** 12

<!--Device-unnamed-interface EmitterProperty--><!--Device-unnamed-interface EmitterProperty-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## annulusRegion

```TypeScript
annulusRegion?: ParticleAnnulusRegion
```

Ring emitter parameters. This parameter takes effect only when the shape of the emitter corresponding to the **index** is annulus. For a annulus emitter, **position** and **size** do not take effect.

**Atomic service API:** This API is supported in atomic services since API version 20.

**Type:** [ParticleAnnulusRegion](arkts-arkui-particle-comp-particleannulusregion-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-EmitterProperty-annulusRegion?: ParticleAnnulusRegion--><!--Device-EmitterProperty-annulusRegion?: ParticleAnnulusRegion-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emitRate

```TypeScript
emitRate?: number
```

Emission rate of the emitter, that is, the number of particles emitted per second.

If this parameter is not passed, the current emission rate is retained. If the passed value is less than 0, the default value 5 is used. An **emitRate** value greater than 5000 may have a significant impact on performance and a sharp drop in frame rate. It is recommended to set this parameter to a value less than 5000.

**Atomic service API:** This API is supported in atomic services since API version 12.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EmitterProperty-emitRate?: number--><!--Device-EmitterProperty-emitRate?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index, rounded to an integer, which specifies the corresponding emitter by the array index of the emitter in the initialization parameters. The default value is 0 for an invalid value.

**Atomic service API:** This API is supported in atomic services since API version 12.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EmitterProperty-index: number--><!--Device-EmitterProperty-index: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

Emitter position. Only the number type is supported.

If this parameter is not passed, the current emitter position is retained. Two valid parameters must be passed. If either of them is invalid, **position** does not take effect. When the shape of the emitter corresponding to the **index** is annulus (**ANNULUS**), **position** does not take effect.

Value range of x and y: (-∞, +∞).

**Atomic service API:** This API is supported in atomic services since API version 12.

**Type:** [PositionT](arkts-arkui-particle-comp-positiont-t.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EmitterProperty-position?: PositionT<number>--><!--Device-EmitterProperty-position?: PositionT<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

Size of the emitter. Only the number type is supported.

If this parameter is not passed, the current emitter size is retained. Two valid parameters greater than 0 must be passed. If either of them is invalid, **size** does not take effect. When the shape of the emitter corresponding to the index is annulus (**ANNULUS**), **size** does not take effect.

**Atomic service API:** This API is supported in atomic services since API version 12.

**Type:** [SizeT](arkts-arkui-particle-comp-sizet-t.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EmitterProperty-size?: SizeT<number>--><!--Device-EmitterProperty-size?: SizeT<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
