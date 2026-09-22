# RippleFieldOptions

```TypeScript
declare interface RippleFieldOptions
```

Defines ripple field options.

@interface RippleFieldOptions

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## amplitude

```TypeScript
amplitude?: number
```

The amplitude of the ripple field. The greater the amplitude, the stronger the force of the ripple field. Range of values:[0, +∞)

**Type:** number

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## attenuation

```TypeScript
attenuation?: number
```

The attenuation coefficient of the ripple field. The larger the attenuation coefficient, the faster the wave attenuates over time. Range of values:[0,1]

**Type:** number

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center?: PositionT<number>
```

The central point where the ripple field generates force. The top-left corner of the component is the origin of coordinates. The coordinate unit is vp.

**Type:** [PositionT](arkts-arkui-particle-comp-positiont-t.md)&lt;number&gt;

**Default:** {x:0,y:0}

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: FieldRegion
```

The region influenced by the ripple field.

**Type:** [FieldRegion](arkts-arkui-particle-comp-fieldregion-i.md)

**Default:** {shape:DisturbanceFieldShape.RECT,position:{x:0,y:0},size:{width:0,height:0}}

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wavelength

```TypeScript
wavelength?: number
```

Wavelength, which is the distance over which a wave cycle changes. The larger the wavelength, the slower the wave changes with distance, and the less pronounced the wave fluctiations. Range of values:[0, +∞)

**Type:** number

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## waveSpeed

```TypeScript
waveSpeed?: number
```

Wave speed. The greater the wave speed, the faster the wave changes over time, and the more pronounced the wave motion. Range of values:[0, +∞)

**Type:** number

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
