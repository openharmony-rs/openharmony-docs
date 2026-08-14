# ParticlePropertyOptions

设置粒子属性选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ParticlePropertyOptions--><!--Device-unnamed-export interface ParticlePropertyOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: ParticleTuple<double, double>
```

粒子初始属性值区间，粒子发射器生成粒子的属性值在range区间随机取值。 **说明：**各项属性的非法输入取默认值，当最大值小于最小值的时候取默认区间。TYPE为number。 不同属性的默认值不同： 1、opacity属性：range:[1.0,1.0]，取值范围为[0, 1]，默认值为1.0。 2、scale属性：range:[1.0,1.0]，取值范围为[0, 10000]，默认值为1.0。 3、acceleration加速度speed属性：range:[0.0,0.0]，取值范围为[0, 10000]，默认值为0.0。 4、acceleration加速度angle属性：range:[0.0,0.0]，取值范围为[-10000, 10000]，默认值为0.0。 5、spin属性：range:[0.0,0.0]，取值范围为[-10000, 10000]，默认值为0.0。

**类型：** [ParticleTuple](arkts-arkui-particletuple-t.md)&lt;double, double&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticlePropertyOptions-range: ParticleTuple<double, double>--><!--Device-ParticlePropertyOptions-range: ParticleTuple<double, double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updater

```TypeScript
updater?: ParticleUpdaterOptions
```

属性变化配置。属性变化类型type有三类： 1、当type为ParticleUpdater.NONE，表示无变化，则config类型为 [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-t.md#ParticlePropertyUpdaterConfigs)[ParticleUpdater.NONE]。 2、当type为ParticleUpdater.RANDOM，表示变化类型为随机变化，则config类型为 [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-t.md#ParticlePropertyUpdaterConfigs)[ParticleUpdater.RANDOM]。 3、当type为ParticleUpdater.CURVE，表示变化类型为曲线变化，则config类型为 [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-t.md#ParticlePropertyUpdaterConfigs)[ParticleUpdater.CURVE] 默认值：type默认为ParticleUpdater.NONE。

**类型：** [ParticleUpdaterOptions](arkts-arkui-particle-particleupdateroptions-i.md)

**默认值：** {type:UPDATER.NONE;config:undefined}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParticlePropertyOptions-updater?: ParticleUpdaterOptions--><!--Device-ParticlePropertyOptions-updater?: ParticleUpdaterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

