# Particle

定义Particle组件。

## Particle

```TypeScript
Particle(particles: Particles<
      PARTICLE,
      COLOR_UPDATER,
      OPACITY_UPDATER,
      SCALE_UPDATER,
      ACC_SPEED_UPDATER,
      ACC_ANGLE_UPDATER,
      SPIN_UPDATER
    >)
```

create a particle array.

Anonymous Object Rectification.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| particles | [Particles](arkts-arkui-particles-i.md)&lt;PARTICLE, COLOR_UPDATER, OPACITY_UPDATER, SCALE_UPDATER, ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER, SPIN_UPDATER&gt; | 是 | Array of particles. |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccelerationOptions](arkts-arkui-accelerationoptions-i.md) | 粒子加速度配置。 |
| [DisturbanceFieldOptions](arkts-arkui-disturbancefieldoptions-i.md) | 设置粒子扰动场参数。 |
| [EmitterOptions](arkts-arkui-emitteroptions-i.md) | 粒子发射器的配置。 |
| [EmitterParticleOptions](arkts-arkui-emitterparticleoptions-i.md) | 粒子配置。 |
| [EmitterProperty](arkts-arkui-emitterproperty-i.md) | 设置发射器属性。 |
| [FieldRegion](arkts-arkui-fieldregion-i.md) | 用于设置粒子场的区域信息。 |
| [ImageParticleParameters](arkts-arkui-imageparticleparameters-i.md) | 设置图片选项。 |
| [ParticleAnnulusRegion](arkts-arkui-particleannulusregion-i.md) | 用于设置环形发射器区域的配置信息。 |
| [ParticleColorOptions](arkts-arkui-particlecoloroptions-i.md) | 颜色变化方式为随机变化的时候，在区间内随机生成一个差值。r、g、b、a四个颜色通道每秒分别使用差值叠加当前颜色值，生成目标颜色值。实现颜色随机变化的效果。 |
| [ParticleColorPropertyOptions](arkts-arkui-particlecolorpropertyoptions-i.md) | 设置粒子颜色属性更新器配置。 |
| [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-i.md) | 设置粒子颜色属性更新器的配置。 |
| [ParticleColorUpdaterOptions](arkts-arkui-particlecolorupdateroptions-i.md) | 颜色属性变化配置。 |
| [ParticleConfigs](arkts-arkui-particleconfigs-i.md) | 设置粒子配置项。 |
| [ParticleOptions](arkts-arkui-particleoptions-i.md) | 设置粒子参数。 |
| [ParticlePropertyAnimation](arkts-arkui-particlepropertyanimation-i.md) | 设置粒子属性生命周期。 |
| [ParticlePropertyOptions](arkts-arkui-particlepropertyoptions-i.md) | 设置粒子属性选项。 |
| [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md) | 设置粒子属性更新器配置。 |
| [Particles](arkts-arkui-particles-i.md) | 粒子动画的集合。 |
| [ParticleUpdaterOptions](arkts-arkui-particleupdateroptions-i.md) | 属性变化配置。 |
| [PointParticleParameters](arkts-arkui-pointparticleparameters-i.md) | 设置粒子半径。 |
| [RippleFieldOptions](arkts-arkui-ripplefieldoptions-i.md) | 用于描述粒子波动场信息的参数。 |
| [VelocityFieldOptions](arkts-arkui-velocityfieldoptions-i.md) | 用于描述粒子速度场信息的参数。 |
| [VelocityOptions](arkts-arkui-velocityoptions-i.md) | 粒子速度配置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ParticleTuple](arkts-arkui-particletuple-t.md) | 粒子元组，表示定义动画参数配置值对的类型。 |
| [PositionT](arkts-arkui-positiont-t.md) | 用于设置或返回组件的位置。 |
| [SizeT](arkts-arkui-sizet-t.md) | 定义Size类型。 |
| [Vector2T](arkts-arkui-vector2t-t.md) | 定义Vector2T类型。其中Vector2T类型包含x和y两个属性值。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DistributionType](arkts-arkui-distributiontype-e.md) | 初始颜色随机值分布类型。 |
| [DisturbanceFieldShape](arkts-arkui-disturbancefieldshape-e.md) | 扰动场形状。 |
| [ParticleEmitterShape](arkts-arkui-particleemittershape-e.md) | 粒子发射器形状。 |
| [ParticleType](arkts-arkui-particletype-e.md) | 粒子类型。 |
| [ParticleUpdater](arkts-arkui-particleupdater-e.md) | 粒子变化类型。 |

## 示例

```TypeScript
### 示例1（圆形初始化粒子）

描述粒子动画基础用法，通过圆形初始化粒子。


```

```TypeScript
### 示例2（图片初始化粒子）

描述粒子动画基础用法，通过图片初始化粒子。该示例同时配置两种不同的图片粒子，展示多粒子类型组合效果。


```

```TypeScript
### 示例3（粒子扰动场的干扰下运动轨迹发生变化）

演示粒子在扰动场干扰下运动轨迹变化的效果。


```

```TypeScript
### 示例4（调整粒子发射器位置）

通过emitter()调整粒子发射器的位置。


```

```TypeScript
### 示例5（环形发射器创建）

该示例演示如何创建环形发射器，粒子在整个圆环范围内（起始角度0到结束角度360）静态发射。


```

```TypeScript
### 示例6（环形发射器更新）

描述粒子动画环形发射器更新的基础用法。


```

```TypeScript
### 示例7（设置波动场和速度场）

从API version 22开始，支持设置粒子波动场和速度场。该示例演示如何通过rippleFields接口设置粒子波动场，产生类似波纹扩散的效果。通过velocityFields接口设置粒子速度场，使粒子在原有速度的基础上叠加速度场指定的速度。
```
