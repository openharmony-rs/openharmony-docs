# EffectInfo

查询的预置效果信息。通过[vibrator.getEffectInfoSync](arkts-sensorservice-vibrator-geteffectinfosync-f.md)返回此对象，用于判断预置振动效果是否受指定设备的指定马达支持。

**起始版本：** 23

<!--Device-vibrator-interface EffectInfo--><!--Device-vibrator-interface EffectInfo-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## isEffectSupported

```TypeScript
isEffectSupported: boolean
```

预置效果是否受支持。true表示支持该预置振动效果，可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) ；false表示不支持，使用该effectId触发振动可能效果不佳。

**类型：** boolean

**起始版本：** 23

<!--Device-EffectInfo-isEffectSupported: boolean--><!--Device-EffectInfo-isEffectSupported: boolean-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

