# ParticleUpdaterOptions

颜色属性变化配置。
> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-interface ParticleUpdaterOptions<TYPE, UPDATER extends ParticleUpdater>--><!--Device-unnamed-interface ParticleUpdaterOptions<TYPE, UPDATER extends ParticleUpdater>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## config

```TypeScript
config: ParticlePropertyUpdaterConfigs<TYPE>[UPDATER]
```

属性变化配置。属性变化类型type有三类：

1、当type为ParticleUpdater.NONE，表示无变化，则config类型为[ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.NONE]。

2、当type为ParticleUpdater.RANDOM，表示变化类型为随机变化，则config类型为[ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.RANDOM]。

3、当type为ParticleUpdater.CURVE，表示变化类型为曲线变化，则config类型为[ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.CURVE]。

**类型：** ParticlePropertyUpdaterConfigs&lt;TYPE&gt;[UPDATER]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleUpdaterOptions-config: ParticlePropertyUpdaterConfigs<TYPE>[UPDATER]--><!--Device-ParticleUpdaterOptions-config: ParticlePropertyUpdaterConfigs<TYPE>[UPDATER]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: UPDATER
```

表示颜色属性变化类型。

默认值：type默认为ParticleUpdater.NONE。

**类型：** UPDATER

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleUpdaterOptions-type: UPDATER--><!--Device-ParticleUpdaterOptions-type: UPDATER-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

