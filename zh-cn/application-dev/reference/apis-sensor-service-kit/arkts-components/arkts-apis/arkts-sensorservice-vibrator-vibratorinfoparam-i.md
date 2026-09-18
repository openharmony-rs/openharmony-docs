# VibratorInfoParam

设备上马达的参数。用于指定需要查询或控制的设备和马达信息。默认情况下，VibratorInfoParam默认为查询或控制本地全部马达。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId?: number
```

设备的ID。默认值：-1，表示本地设备。使用场景：在多设备场景下需指定远程设备时设置此参数；不填此参数时默认控制本地设备。从API version 19开始，设备ID可通过[getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md)或[on](arkts-sensorservice-vibrator-on-f.md#onvibratorstatechange)查询获取。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

## vibratorId

```TypeScript
vibratorId?: number
```

马达ID。默认值：0，表示该设备的全部马达。使用场景：在多马达设备上需指定特定马达时设置此参数；不填此参数时默认控制该设备的全部马达。从API version 19开始，马达ID可通过[getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md)或[on](arkts-sensorservice-vibrator-on-f.md#onvibratorstatechange)查询获取。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice
