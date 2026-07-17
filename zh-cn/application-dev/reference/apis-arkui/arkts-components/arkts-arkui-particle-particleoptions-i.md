# ParticleOptions

设置粒子参数。

**起始版本：** 10

<!--Device-unnamed-interface ParticleOptions<  PARTICLE extends ParticleType,  COLOR_UPDATER extends ParticleUpdater,  OPACITY_UPDATER extends ParticleUpdater,  SCALE_UPDATER extends ParticleUpdater,  ACC_SPEED_UPDATER extends ParticleUpdater,  ACC_ANGLE_UPDATER extends ParticleUpdater,  SPIN_UPDATER extends ParticleUpdater>--><!--Device-unnamed-interface ParticleOptions<  PARTICLE extends ParticleType,  COLOR_UPDATER extends ParticleUpdater,  OPACITY_UPDATER extends ParticleUpdater,  SCALE_UPDATER extends ParticleUpdater,  ACC_SPEED_UPDATER extends ParticleUpdater,  ACC_ANGLE_UPDATER extends ParticleUpdater,  SPIN_UPDATER extends ParticleUpdater>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## acceleration

```TypeScript
acceleration?: AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>
```

粒子加速度配置。

**说明**：

speed表示加速度大小，angle表示加速度方向（单位为角度）。

默认值：{ speed:{range:[0.0,0.0]},angle:{range:[0.0,0.0]} }

**类型：** AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>

**默认值：** {speed:{range:[0,0]};angle:{range:[0,0]}}

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleOptions-acceleration?: AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>--><!--Device-ParticleOptions-acceleration?: AccelerationOptions<ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ParticleColorPropertyOptions<COLOR_UPDATER>
```

粒子颜色配置。

**说明**：

默认值：{ range:[Color.White,Color.White] } 。图片粒子不支持设置颜色。

**类型：** ParticleColorPropertyOptions<COLOR_UPDATER>

**默认值：** {range:['#FFFFFF','#FFFFFF']}

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleOptions-color?: ParticleColorPropertyOptions<COLOR_UPDATER>--><!--Device-ParticleOptions-color?: ParticleColorPropertyOptions<COLOR_UPDATER>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## emitter

```TypeScript
emitter: EmitterOptions<PARTICLE>
```

粒子发射器配置。

**类型：** EmitterOptions<PARTICLE>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleOptions-emitter: EmitterOptions<PARTICLE>--><!--Device-ParticleOptions-emitter: EmitterOptions<PARTICLE>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity?: ParticlePropertyOptions<number, OPACITY_UPDATER>
```

粒子透明度配置。

默认值：{ range:[1.0,1.0] }

**类型：** ParticlePropertyOptions<number, OPACITY_UPDATER>

**默认值：** {range:[1.0,1.0]}

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleOptions-opacity?: ParticlePropertyOptions<number, OPACITY_UPDATER>--><!--Device-ParticleOptions-opacity?: ParticlePropertyOptions<number, OPACITY_UPDATER>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: ParticlePropertyOptions<number, SCALE_UPDATER>
```

粒子大小配置。

默认值：{ range:[1.0,1.0] }

**类型：** ParticlePropertyOptions<number, SCALE_UPDATER>

**默认值：** {range:[1.0,1.0]}

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleOptions-scale?: ParticlePropertyOptions<number, SCALE_UPDATER>--><!--Device-ParticleOptions-scale?: ParticlePropertyOptions<number, SCALE_UPDATER>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spin

```TypeScript
spin?: ParticlePropertyOptions<number, SPIN_UPDATER>
```

粒子自旋角度配置。

默认值：{range:[0.0,0.0]}

方向：正数表示顺时针旋转，负数表示逆时针旋转。

**类型：** ParticlePropertyOptions<number, SPIN_UPDATER>

**默认值：** {range:[0,0]}

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleOptions-spin?: ParticlePropertyOptions<number, SPIN_UPDATER>--><!--Device-ParticleOptions-spin?: ParticlePropertyOptions<number, SPIN_UPDATER>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity?: VelocityOptions
```

粒子速度配置。

**说明**：

speed表示速度大小。angle表示速度的方向（单位为角度），以元素几何中心为坐标原点，水平方向为X轴，正数表示顺时针方向旋转角度。

默认值：{ speed:[0.0,0.0],angle:[0.0,0.0] }

**类型：** VelocityOptions

**默认值：** {speed:[0,0];angle:[0,0]}

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleOptions-velocity?: VelocityOptions--><!--Device-ParticleOptions-velocity?: VelocityOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

