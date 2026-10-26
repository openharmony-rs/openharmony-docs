# VibratorInfo

```TypeScript
interface VibratorInfo
```

Defines the vibrator information.

**Since:** 19

<!--Device-vibrator-interface VibratorInfo--><!--Device-vibrator-interface VibratorInfo-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId: number
```

Device ID.

**Type:** number

**Since:** 19

<!--Device-VibratorInfo-deviceId: int--><!--Device-VibratorInfo-deviceId: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## deviceName

```TypeScript
deviceName: string
```

Device name.

**Type:** string

**Since:** 19

<!--Device-VibratorInfo-deviceName: string--><!--Device-VibratorInfo-deviceName: string-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## isHdHapticSupported

```TypeScript
isHdHapticSupported: boolean
```

Whether HD vibration is supported. The value **true** indicates that HD vibration is supported, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 19

<!--Device-VibratorInfo-isHdHapticSupported: boolean--><!--Device-VibratorInfo-isHdHapticSupported: boolean-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## isLocalVibrator

```TypeScript
isLocalVibrator: boolean
```

Whether the device is a local device. The value **true** indicates that the device is a local device, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 19

<!--Device-VibratorInfo-isLocalVibrator: boolean--><!--Device-VibratorInfo-isLocalVibrator: boolean-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## isSupportIntensity

```TypeScript
isSupportIntensity?: boolean
```

Indicates whether vibration intensity adjustment is supported. The value **true** indicates that vibration intensity adjustment is supported, and the value **false** indicates that vibration intensity adjustment is not supported. Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-VibratorInfo-isSupportIntensity?: boolean--><!--Device-VibratorInfo-isSupportIntensity?: boolean-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## vibratorId

```TypeScript
vibratorId: number
```

Vibrator ID.

**Type:** number

**Since:** 19

<!--Device-VibratorInfo-vibratorId: int--><!--Device-VibratorInfo-vibratorId: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
