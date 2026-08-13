# EmitterParticleOptions

粒子配置。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface EmitterParticleOptions--><!--Device-unnamed-export interface EmitterParticleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticleConfigs
```

表示对应类型的配置。 config类型和type值有关联： 1. 如果type为ParticleType.POINT，则config类型为[PointParticleParameters](arkts-arkui-particle-pointparticleparameters-i.md#PointParticleParameters) 。 2. 如果type为ParticleType.IMAGE，则config类型为[ImageParticleParameters](arkts-arkui-particle-imageparticleparameters-i.md#ImageParticleParameters) 。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleConfigs](arkts-arkui-particleconfigs-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterParticleOptions-config: ParticleConfigs--><!--Device-EmitterParticleOptions-config: ParticleConfigs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: int
```

表示发射的粒子总数，count取值>=-1,当count为-1表示粒子总数无限大。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterParticleOptions-count: int--><!--Device-EmitterParticleOptions-count: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lifetime

```TypeScript
lifetime?: int
```

表示单个粒子的生命周期，默认值1000（即1000ms，1s），lifetime>=-1。当lifetime为-1表示粒子生命周期无限大。当lifetime<-1，取默认值。 **说明：**如果不需要动画一直播放，建议不要将生命周期设置为-1，可能对性能造成较大影响。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** int

**默认值：** 1000

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterParticleOptions-lifetime?: int--><!--Device-EmitterParticleOptions-lifetime?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lifetimeRange

```TypeScript
lifetimeRange?: int
```

表示粒子生命周期取值范围，设置lifetimeRange后粒子的生命周期为[lifetime-lifetimeRange, lifetime+lifetimeRange]中间的一个随机整数。lifetimeRange默认值为 0，取值范围为0到正无穷。设置为负值时取默认值。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** int

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterParticleOptions-lifetimeRange?: int--><!--Device-EmitterParticleOptions-lifetimeRange?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: ParticleType
```

表示粒子类型，可以选择图片或者是点。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleType](arkts-arkui-particle-particletype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterParticleOptions-type: ParticleType--><!--Device-EmitterParticleOptions-type: ParticleType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

