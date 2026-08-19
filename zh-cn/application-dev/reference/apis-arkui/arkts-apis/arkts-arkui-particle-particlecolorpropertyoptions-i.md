# ParticleColorPropertyOptions

设置粒子颜色属性更新器配置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface ParticleColorPropertyOptions--><!--Device-unnamed-export interface ParticleColorPropertyOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distributionType

```TypeScript
distributionType?: DistributionType
```

粒子初始颜色随机值分布，允许用户选择颜色随机值生成的分布类型，支持均匀分布或正态（高斯）分布。 默认值：DistributionType.UNIFORM **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [DistributionType](arkts-arkui-particle-distributiontype-e.md)

**默认值：** DistributionType.UNIFORM

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleColorPropertyOptions-distributionType?: DistributionType--><!--Device-ParticleColorPropertyOptions-distributionType?: DistributionType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: ParticleTuple<ResourceColor, ResourceColor>
```

粒子初始颜色区间，粒子发射器生成粒子的初始颜色在range区间随机取值。 默认值：range:[Color.White,Color.White] **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleTuple](arkts-arkui-particletuple-t.md)&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md), [ResourceColor](arkts-arkui-resourcecolor-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleColorPropertyOptions-range: ParticleTuple<ResourceColor, ResourceColor>--><!--Device-ParticleColorPropertyOptions-range: ParticleTuple<ResourceColor, ResourceColor>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updater

```TypeScript
updater?: ParticleColorUpdaterOptions
```

颜色属性变化配置。颜色属性变化类型type有三类： 1、当type为ParticleUpdater.NONE，表示无变化，则config类型为 [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-t.md)[ParticleUpdater.NONE]。 2、type为ParticleUpdater.RANDOM，表示随机变化，则config类型为 [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-t.md)[ParticleUpdater.RANDOM]。 3、type为ParticleUpdater.CURVE,表示按动画曲线变化，则config类型为 [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-t.md)[ParticleUpdater.CURVE]。 默认值：type默认为 ParticleUpdater.NONE。 **说明：** 当type为ParticleUpdater.RANDOM或者ParticleUpdater.CURVE时，updater中颜色配置的优先级高于range中的颜色配置。在updater配置的动画时间周期内，以updater中的颜 色配置来变化；在updater配置的动画时间周期外，以range中的颜色配置来变化。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleColorUpdaterOptions](arkts-arkui-particle-particlecolorupdateroptions-i.md)

**默认值：** {type:UPDATER.NONE;config:undefined}

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleColorPropertyOptions-updater?: ParticleColorUpdaterOptions--><!--Device-ParticleColorPropertyOptions-updater?: ParticleColorUpdaterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

