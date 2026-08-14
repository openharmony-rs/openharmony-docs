# Particle

Defines Particle Component.

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

create a particle array. Anonymous Object Rectification.

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ParticleInterface-<    PARTICLE extends ParticleType,    COLOR_UPDATER extends ParticleUpdater,    OPACITY_UPDATER extends ParticleUpdater,    SCALE_UPDATER extends ParticleUpdater,    ACC_SPEED_UPDATER extends ParticleUpdater,    ACC_ANGLE_UPDATER extends ParticleUpdater,    SPIN_UPDATER extends ParticleUpdater  >(particles: Particles<      PARTICLE,      COLOR_UPDATER,      OPACITY_UPDATER,      SCALE_UPDATER,      ACC_SPEED_UPDATER,      ACC_ANGLE_UPDATER,      SPIN_UPDATER    >): ParticleAttribute--><!--Device-ParticleInterface-<    PARTICLE extends ParticleType,    COLOR_UPDATER extends ParticleUpdater,    OPACITY_UPDATER extends ParticleUpdater,    SCALE_UPDATER extends ParticleUpdater,    ACC_SPEED_UPDATER extends ParticleUpdater,    ACC_ANGLE_UPDATER extends ParticleUpdater,    SPIN_UPDATER extends ParticleUpdater  >(particles: Particles<      PARTICLE,      COLOR_UPDATER,      OPACITY_UPDATER,      SCALE_UPDATER,      ACC_SPEED_UPDATER,      ACC_ANGLE_UPDATER,      SPIN_UPDATER    >): ParticleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| particles | [Particles](arkts-arkui-particles-i.md)&lt;PARTICLE, COLOR_UPDATER, OPACITY_UPDATER, SCALE_UPDATER, ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER, SPIN_UPDATER&gt; | 是 | Array of particles. |

## 汇总

- [AccelerationOptions](arkts-arkui-accelerationoptions-i.md)
- [DisturbanceFieldOptions](arkts-arkui-disturbancefieldoptions-i.md)
- [EmitterOptions](arkts-arkui-emitteroptions-i.md)
- [EmitterParticleOptions](arkts-arkui-emitterparticleoptions-i.md)
- [EmitterProperty](arkts-arkui-emitterproperty-i.md)
- [FieldRegion](arkts-arkui-fieldregion-i.md)
- [ImageParticleParameters](arkts-arkui-imageparticleparameters-i.md)
- [ParticleAnnulusRegion](arkts-arkui-particleannulusregion-i.md)
- [ParticleColorOptions](arkts-arkui-particlecoloroptions-i.md)
- [ParticleColorPropertyOptions](arkts-arkui-particlecolorpropertyoptions-i.md)
- [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-i.md)
- [ParticleColorUpdaterOptions](arkts-arkui-particlecolorupdateroptions-i.md)
- [ParticleConfigs](arkts-arkui-particleconfigs-i.md)
- [ParticleOptions](arkts-arkui-particleoptions-i.md)
- [ParticlePropertyAnimation](arkts-arkui-particlepropertyanimation-i.md)
- [ParticlePropertyOptions](arkts-arkui-particlepropertyoptions-i.md)
- [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md)
- [Particles](arkts-arkui-particles-i.md)
- [ParticleUpdaterOptions](arkts-arkui-particleupdateroptions-i.md)
- [PointParticleParameters](arkts-arkui-pointparticleparameters-i.md)
- [RippleFieldOptions](arkts-arkui-ripplefieldoptions-i.md)
- [VelocityFieldOptions](arkts-arkui-velocityfieldoptions-i.md)
- [VelocityOptions](arkts-arkui-velocityoptions-i.md)
- [ParticleTuple](arkts-arkui-particletuple-t.md)
- [PositionT](arkts-arkui-positiont-t.md)
- [SizeT](arkts-arkui-sizet-t.md)
- [Vector2T](arkts-arkui-vector2t-t.md)
- [DistributionType](arkts-arkui-distributiontype-e.md)
- [DisturbanceFieldShape](arkts-arkui-disturbancefieldshape-e.md)
- [ParticleEmitterShape](arkts-arkui-particleemittershape-e.md)
- [ParticleType](arkts-arkui-particletype-e.md)
- [ParticleUpdater](arkts-arkui-particleupdater-e.md)
