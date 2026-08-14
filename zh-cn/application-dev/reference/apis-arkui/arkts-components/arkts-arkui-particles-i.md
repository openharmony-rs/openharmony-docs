# Particles

粒子动画的集合。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-interface Particles--><!--Device-unnamed-interface Particles-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## particles

```TypeScript
particles: Array<
    ParticleOptions<
      PARTICLE,
      COLOR_UPDATER,
      OPACITY_UPDATER,
      SCALE_UPDATER,
      ACC_SPEED_UPDATER,
      ACC_ANGLE_UPDATER,
      SPIN_UPDATER
    >
  >
```

粒子动画的集合。每个粒子动画（[ParticleOptions](arkts-arkui-particleoptions-i.md#ParticleOptions)）包含粒子发射，同时可配置粒子的颜色、透明度、大小、速度、加速度与旋转速度，详见 [ParticleOptions](arkts-arkui-particleoptions-i.md#ParticleOptions)属性说明。

**类型：** Array&lt;[ParticleOptions](arkts-arkui-particleoptions-i.md)&lt;PARTICLE, COLOR_UPDATER, OPACITY_UPDATER, SCALE_UPDATER, ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER, SPIN_UPDATER&gt;&gt;

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Particles-particles: Array<    ParticleOptions<      PARTICLE,      COLOR_UPDATER,      OPACITY_UPDATER,      SCALE_UPDATER,      ACC_SPEED_UPDATER,      ACC_ANGLE_UPDATER,      SPIN_UPDATER    >  >--><!--Device-Particles-particles: Array<    ParticleOptions<      PARTICLE,      COLOR_UPDATER,      OPACITY_UPDATER,      SCALE_UPDATER,      ACC_SPEED_UPDATER,      ACC_ANGLE_UPDATER,      SPIN_UPDATER    >  >-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

