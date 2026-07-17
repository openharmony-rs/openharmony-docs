# ParticlePropertyOptions

设置粒子属性选项。

**起始版本：** 10

<!--Device-unnamed-interface ParticlePropertyOptions<TYPE, UPDATER extends ParticleUpdater>--><!--Device-unnamed-interface ParticlePropertyOptions<TYPE, UPDATER extends ParticleUpdater>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: ParticleTuple<TYPE, TYPE>
```

粒子初始属性值区间，粒子发射器生成粒子的属性值在range区间随机取值。

**说明**

各项属性的非法输入取默认值，当最大值小于最小值的时候取默认区间。TYPE为number。

不同属性的默认值不同：

1、opacity属性：range:[1.0,1.0]，取值范围为[0, 1]，默认值为1.0。

2、scale属性：range:[1.0,1.0]，取值范围为[0, 10000]，默认值为1.0。

3、acceleration加速度speed属性：range:[0.0,0.0]，取值范围为[0, 10000]，默认值为0.0。

4、acceleration加速度angle属性：range:[0.0,0.0]，取值范围为[-10000, 10000]，默认值为0.0。

5、spin属性：range:[0.0,0.0]，取值范围为[-10000, 10000]，默认值为0.0。

**类型：** ParticleTuple<TYPE, TYPE>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticlePropertyOptions-range: ParticleTuple<TYPE, TYPE>--><!--Device-ParticlePropertyOptions-range: ParticleTuple<TYPE, TYPE>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updater

```TypeScript
updater?: ParticleUpdaterOptions<TYPE, UPDATER>
```

属性变化配置。属性变化类型type有三类：

1、当type为ParticleUpdater.NONE，表示无变化，则config类型为[ParticlePropertyUpdaterConfigs](arkts-arkui-particle-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.NONE]。

2、当type为ParticleUpdater.RANDOM，表示变化类型为随机变化，则config类型为[ParticlePropertyUpdaterConfigs](arkts-arkui-particle-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.RANDOM]。

3、当type为ParticleUpdater.CURVE，表示变化类型为曲线变化，则config类型为[ParticlePropertyUpdaterConfigs](arkts-arkui-particle-particlepropertyupdaterconfigs-i.md)[ParticleUpdater.CURVE]

默认值：type默认为ParticleUpdater.NONE。

**类型：** ParticleUpdaterOptions<TYPE, UPDATER>

**默认值：** {type:UPDATER.NONE;config:ParticlePropertyUpdaterConfigs<UPDATER.NONE>[UPDATER.NONE]}

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticlePropertyOptions-updater?: ParticleUpdaterOptions<TYPE, UPDATER>--><!--Device-ParticlePropertyOptions-updater?: ParticleUpdaterOptions<TYPE, UPDATER>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

