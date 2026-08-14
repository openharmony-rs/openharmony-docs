# EffectInfo

查询的预置效果信息。通过[vibrator.getEffectInfoSync](arkts-sensorservice-vibrator-geteffectinfosync-f.md#getEffectInfoSync)返回此对象，用于判断预置振动效果是否受指定设备的指定马达支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-interface EffectInfo--><!--Device-vibrator-interface EffectInfo-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## isEffectSupported

```TypeScript
isEffectSupported: boolean
```

预置效果是否受支持。true表示支持该预置振动效果，可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) ；false表示不支持，使用该effectId触发振动可能效果不佳。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-EffectInfo-isEffectSupported: boolean--><!--Device-EffectInfo-isEffectSupported: boolean-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

