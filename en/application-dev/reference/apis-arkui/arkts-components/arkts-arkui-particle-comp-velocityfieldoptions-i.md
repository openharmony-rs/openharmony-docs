# VelocityFieldOptions

```TypeScript
declare interface VelocityFieldOptions
```

Parameter used to describe the velocity field of particles.

@interface VelocityFieldOptions

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: FieldRegion
```

The region influenced by the velocity field.

**Type:** [FieldRegion](arkts-arkui-particle-comp-fieldregion-i.md)

**Default:** {shape:DisturbanceFieldShape.RECT,position:{x:0,y:0},size:{width:0,height:0}}

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity?: Vector2T<number>
```

The velocity values in each direction of the velocity field. Particles only acquire this velocity when within the range of the velocity field; once they leave the range of the velocity field, they are no longer influenced by it and do not gain this additional velocity.

**Type:** [Vector2T](arkts-arkui-particle-comp-vector2t-t.md)&lt;number&gt;

**Default:** {x:0,y:0}

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
