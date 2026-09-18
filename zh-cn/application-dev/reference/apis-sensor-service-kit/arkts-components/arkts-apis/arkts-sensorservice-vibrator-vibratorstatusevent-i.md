# VibratorStatusEvent

振动设备上线、下线状态事件信息。当马达设备上线或下线时，通过[vibrator.on](arkts-sensorservice-vibrator-on-f.md#onvibratorstatechange)回调传递此对象。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId: number
```

设备的ID。可用于[startVibration](arkts-sensorservice-vibrator-startvibration-f.md)和[stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md)等接口指定目标设备。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## isVibratorOnline

```TypeScript
isVibratorOnline: boolean
```

指示设备的上线和下线状态。true表示设备上线，可用于触发振动；false表示设备下线，此时该设备的振动不可用。

**类型：** boolean

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## timestamp

```TypeScript
timestamp: number
```

报告事件的时间戳。单位：ms（毫秒）。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## vibratorCount

```TypeScript
vibratorCount: number
```

设备上的马达的数量。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice
