# ParticleColorUpdaterOptions

颜色属性变化配置。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface ParticleColorUpdaterOptions--><!--Device-unnamed-export interface ParticleColorUpdaterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticleColorPropertyUpdaterConfigs
```

颜色属性变化类型type有三类： 1、当type为ParticleUpdater.NONE，表示无变化，则config类型为 [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-t.md)[ParticleUpdater.NONE]。 2、type为ParticleUpdater.RANDOM，表示随机变化，则config类型为 [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-t.md)[ParticleUpdater.RANDOM]。 3、type为ParticleUpdater.CURVE,表示按动画曲线变化，则config类型为 [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-t.md)[ParticleUpdater.CURVE]。 **说明：** 当type为ParticleUpdater.RANDOM或者ParticleUpdater.CURVE时，updater中颜色配置的优先级高于range中的颜色配置。在updater配置的动画时间周期内，以updater中的颜 色配置来变化；在updater配置的动画时间周期外，以range中的颜色配置来变化。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleColorUpdaterOptions-config: ParticleColorPropertyUpdaterConfigs--><!--Device-ParticleColorUpdaterOptions-config: ParticleColorPropertyUpdaterConfigs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: ParticleUpdater
```

表示颜色属性变化类型。 默认值：type默认为 ParticleUpdater.NONE。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleUpdater](arkts-arkui-particle-particleupdater-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticleColorUpdaterOptions-type: ParticleUpdater--><!--Device-ParticleColorUpdaterOptions-type: ParticleUpdater-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

