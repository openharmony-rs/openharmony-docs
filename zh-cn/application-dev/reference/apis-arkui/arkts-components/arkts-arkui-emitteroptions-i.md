# EmitterOptions

粒子发射器的配置。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## annulusRegion

```TypeScript
annulusRegion?: ParticleAnnulusRegion
```

环形发射器参数。需要发射器形状为环形（即shape参数为ParticleEmitterShape.ANNULUS）时才生效，且对于环形发射器，形状信息必须通过annulusRegion参数指定，position和size不生效。

**类型：** ParticleAnnulusRegion

**默认值：** {innerRadius:LengthMetrics.vp(0),outerRadius:LengthMetrics.vp(0)}

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## emitRate

```TypeScript
emitRate?: number
```

发射器发射速率（即每秒发射粒子数）。 默认值：5，小于0时取默认值5。emitRate值超过5000时会极大影响性能，建议设置参数小于5000。

**类型：** number

**默认值：** 5

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## particle

```TypeScript
particle: EmitterParticleOptions<PARTICLE>
```

粒子配置。

-type表示粒子类型，可以选择图片或者是点。

-config表示对应类型的配置。

-config类型和type值有关联：

1. 如果type为ParticleType.POINT，则config类型为[PointParticleParameters](arkts-arkui-pointparticleparameters-i.md) 。
2. 如果type为ParticleType.IMAGE，则config类型为[ImageParticleParameters](arkts-arkui-imageparticleparameters-i.md) 。

-count表示发射的粒子总数，count取值>=-1，当count为-1表示粒子总数无限大。

-lifetime表示单个粒子的生命周期，默认值1000（即1000ms，1s），lifetime>=-1，当lifetime为-1表示粒子生命周期无限大。当lifetime<-1，取默认值。

**说明**：如果不需要动画一直播放，建议不要将生命周期设置为-1，可能对性能造成较大影响。

lifetimeRange表示粒子生命周期取值范围，设置lifetimeRange后粒子的生命周期为[lifetime-lifetimeRange, lifetime+lifetimeRange]中间的一个随机整数。
lifetimeRange默认值为0，取值范围为[0, +∞）。设置为负值时取默认值。

**类型：** EmitterParticleOptions<PARTICLE>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: ParticleTuple<Dimension, Dimension>
```

发射器位置（距离组件左上角的位置。第一个参数为x方向上的相对偏移，第二个参数为y轴方向相对偏移。）

默认值：`[0.0, 0.0]`

**类型：** ParticleTuple<Dimension, Dimension>

**默认值：** [0,0]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shape

```TypeScript
shape?: ParticleEmitterShape
```

发射器形状。

默认值：ParticleEmitterShape.RECTANGLE

**类型：** ParticleEmitterShape

**默认值：** ParticleEmitterShape.RECTANGLE

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ParticleTuple<Dimension, Dimension>
```

发射窗口的大小。第一个参数为发射器宽，第二个参数为发射器高。

默认值：`['100%','100%']`(即发射窗口占满Particle组件)

**类型：** ParticleTuple<Dimension, Dimension>

**默认值：** ['100%','100%']

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

