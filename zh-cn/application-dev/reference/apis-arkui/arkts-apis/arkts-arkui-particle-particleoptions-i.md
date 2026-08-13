# ParticleOptions

设置粒子参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ParticleOptions--><!--Device-unnamed-export interface ParticleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## acceleration

```TypeScript
acceleration?: AccelerationOptions
```

粒子加速度配置。 **说明：** speed表示加速度大小，angle表示加速度方向（单位为角度）。 默认值：{ speed:{range:[0.0,0.0]},angle:{range:[0.0,0.0]} }

**类型：** [AccelerationOptions](arkts-arkui-particle-accelerationoptions-i.md)

**默认值：** {speed:{range:[0,0]};angle:{range:[0,0]}}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleOptions-acceleration?: AccelerationOptions--><!--Device-ParticleOptions-acceleration?: AccelerationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ParticleColorPropertyOptions
```

粒子颜色配置。 **说明：** 默认值：{ range:[Color.White,Color.White] } 。图片粒子不支持设置颜色。

**类型：** [ParticleColorPropertyOptions](arkts-arkui-particle-particlecolorpropertyoptions-i.md)

**默认值：** {range:['#FFFFFF','#FFFFFF']}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleOptions-color?: ParticleColorPropertyOptions--><!--Device-ParticleOptions-color?: ParticleColorPropertyOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## emitter

```TypeScript
emitter: EmitterOptions
```

粒子发射器配置。

**类型：** [EmitterOptions](arkts-arkui-particle-emitteroptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleOptions-emitter: EmitterOptions--><!--Device-ParticleOptions-emitter: EmitterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity?: ParticlePropertyOptions
```

粒子透明度配置。 默认值：{ range:[1.0,1.0] }

**类型：** [ParticlePropertyOptions](arkts-arkui-particle-particlepropertyoptions-i.md)

**默认值：** {range:[1.0,1.0]}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleOptions-opacity?: ParticlePropertyOptions--><!--Device-ParticleOptions-opacity?: ParticlePropertyOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: ParticlePropertyOptions
```

粒子大小配置。 默认值：{ range:[1.0,1.0] }

**类型：** [ParticlePropertyOptions](arkts-arkui-particle-particlepropertyoptions-i.md)

**默认值：** {range:[1.0,1.0]}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleOptions-scale?: ParticlePropertyOptions--><!--Device-ParticleOptions-scale?: ParticlePropertyOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spin

```TypeScript
spin?: ParticlePropertyOptions
```

粒子自旋角度配置。 默认值：{range:[0.0,0.0]} 方向：正数表示顺时针旋转，负数表示逆时针旋转。

**类型：** [ParticlePropertyOptions](arkts-arkui-particle-particlepropertyoptions-i.md)

**默认值：** {range:[0,0]}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleOptions-spin?: ParticlePropertyOptions--><!--Device-ParticleOptions-spin?: ParticlePropertyOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity?: VelocityOptions
```

粒子速度配置。 **说明：** speed表示速度大小。angle表示速度的方向（单位为角度），以元素几何中心为坐标原点，水平方向为X轴，正数表示顺时针方向旋转角度。 默认值：{ speed:[0.0,0.0],angle:[0.0,0.0] }

**类型：** [VelocityOptions](arkts-arkui-particle-velocityoptions-i.md)

**默认值：** {speed:[0,0];angle:[0,0]}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleOptions-velocity?: VelocityOptions--><!--Device-ParticleOptions-velocity?: VelocityOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

