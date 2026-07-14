# AccelerationOptions

粒子加速度配置。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: ParticlePropertyOptions<number, ACC_ANGLE_UPDATER>
```

表示加速度方向（单位为角度）。

默认值：{range:[0.0,0.0]}

**类型：** ParticlePropertyOptions<number, ACC_ANGLE_UPDATER>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed?: ParticlePropertyOptions<number, ACC_SPEED_UPDATER>
```

表示加速度大小。

默认值：{range:[0.0,0.0]}

**类型：** ParticlePropertyOptions<number, ACC_SPEED_UPDATER>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

