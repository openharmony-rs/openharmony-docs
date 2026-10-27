# SystemEventAttributes (System API)

```TypeScript
export interface SystemEventAttributes
```

System event scenario attributes.

**Since:** 26.1.0

<!--Device-behaviorAwareness-export interface SystemEventAttributes--><!--Device-behaviorAwareness-export interface SystemEventAttributes-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## appId

```TypeScript
appId?: string
```

Application ID (for app-related events).

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-appId?: string--><!--Device-SystemEventAttributes-appId?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## appName

```TypeScript
appName?: string
```

Application name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-appName?: string--><!--Device-SystemEventAttributes-appName?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## batteryThreshold

```TypeScript
batteryThreshold?: number
```

Battery threshold. Unit: Percentage. The value must be an integer within [0,100]. Default value: The default value is 0.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-batteryThreshold?: int--><!--Device-SystemEventAttributes-batteryThreshold?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## bluetoothDeviceName

```TypeScript
bluetoothDeviceName?: string
```

Bluetooth device name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-bluetoothDeviceName?: string--><!--Device-SystemEventAttributes-bluetoothDeviceName?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## bluetoothDeviceType

```TypeScript
bluetoothDeviceType?: BluetoothDeviceType
```

Bluetooth device type. Default value: The default value is 0.

**Type:** [BluetoothDeviceType](arkts-multimodalawareness-behaviorawareness-bluetoothdevicetype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-bluetoothDeviceType?: BluetoothDeviceType--><!--Device-SystemEventAttributes-bluetoothDeviceType?: BluetoothDeviceType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## dailyDurationThreshold

```TypeScript
dailyDurationThreshold?: number
```

Daily usage duration threshold. Unit: Minute. The value must be an integer within [0,1440]. Default value: The default value is 0.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-dailyDurationThreshold?: int--><!--Device-SystemEventAttributes-dailyDurationThreshold?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## durationThreshold

```TypeScript
durationThreshold?: number
```

Single-use duration threshold. Unit: Minute. The value should be an integer. Default value: The default value is 0.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-durationThreshold?: int--><!--Device-SystemEventAttributes-durationThreshold?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## kind

```TypeScript
kind: 'systemEvent'
```

Discriminator field, fixed as 'systemEvent'.

**Type:** 'systemEvent'

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-kind: 'systemEvent'--><!--Device-SystemEventAttributes-kind: 'systemEvent'-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## level

```TypeScript
level?: number
```

Battery percentage. Unit: Percentage. The value must be an integer within [0,100]. Default value: The default value is 0.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-level?: int--><!--Device-SystemEventAttributes-level?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## packageName

```TypeScript
packageName?: string
```

Application package name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemEventAttributes-packageName?: string--><!--Device-SystemEventAttributes-packageName?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
