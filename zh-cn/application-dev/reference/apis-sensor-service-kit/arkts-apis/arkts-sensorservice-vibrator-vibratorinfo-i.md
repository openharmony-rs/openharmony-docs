# VibratorInfo

表示查询的马达信息。通过[vibrator.getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md)返回此对象，用于获取设备马达能力和选择合适的马达触发振动。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
```

## deviceId

```TypeScript
deviceId: number
```

设备ID。可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) 和[stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md)等接口指定目标设备。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## deviceName

```TypeScript
deviceName: string
```

设备名称。

**类型：** string

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## isHdHapticSupported

```TypeScript
isHdHapticSupported: boolean
```

是否支持高清振动。true表示支持高清振动，可使用VibrateFromFile和VibrateFromPattern类型触发振动；false表示不支持，使用自定义振动类型可能效果不佳。

**类型：** boolean

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 查询是否支持高清振动
  let ret = vibrator.isHdHapticSupported();
  console.info(`The query result is ${ret}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

## isLocalVibrator

```TypeScript
isLocalVibrator: boolean
```

是否为本地设备。true表示本地设备，可直接触发振动；false表示远程设备，需在分布式场景下使用。

**类型：** boolean

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## vibratorId

```TypeScript
vibratorId: number
```

马达ID。可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) 和[stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md)等接口指定目标马达。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice
