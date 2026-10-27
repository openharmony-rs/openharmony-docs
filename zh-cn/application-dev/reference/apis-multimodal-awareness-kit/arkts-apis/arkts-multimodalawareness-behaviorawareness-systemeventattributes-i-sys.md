# SystemEventAttributes（系统接口）

```TypeScript
export interface SystemEventAttributes
```

系统事件类场景属性。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface SystemEventAttributes--><!--Device-behaviorAwareness-export interface SystemEventAttributes-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## appId

```TypeScript
appId?: string
```

应用 ID（用于应用相关事件）。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-appId?: string--><!--Device-SystemEventAttributes-appId?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## appName

```TypeScript
appName?: string
```

应用名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-appName?: string--><!--Device-SystemEventAttributes-appName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## batteryThreshold

```TypeScript
batteryThreshold?: number
```

电量阈值。单位：百分比。取值需为 [0,100] 范围内的整数。默认值：默认值为 0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-batteryThreshold?: int--><!--Device-SystemEventAttributes-batteryThreshold?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## bluetoothDeviceName

```TypeScript
bluetoothDeviceName?: string
```

蓝牙设备名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-bluetoothDeviceName?: string--><!--Device-SystemEventAttributes-bluetoothDeviceName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## bluetoothDeviceType

```TypeScript
bluetoothDeviceType?: BluetoothDeviceType
```

蓝牙设备类型。默认值：默认值为 0。

**类型：** [BluetoothDeviceType](arkts-multimodalawareness-behaviorawareness-bluetoothdevicetype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-bluetoothDeviceType?: BluetoothDeviceType--><!--Device-SystemEventAttributes-bluetoothDeviceType?: BluetoothDeviceType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## dailyDurationThreshold

```TypeScript
dailyDurationThreshold?: number
```

当日使用时长阈值。单位：分钟。取值需为 [0,1440] 范围内的整数。默认值：默认值为 0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-dailyDurationThreshold?: int--><!--Device-SystemEventAttributes-dailyDurationThreshold?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## durationThreshold

```TypeScript
durationThreshold?: number
```

单次使用时长阈值。单位：分钟。取值应为整数。默认值：默认值为 0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-durationThreshold?: int--><!--Device-SystemEventAttributes-durationThreshold?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## kind

```TypeScript
kind: 'systemEvent'
```

判别字段，固定为 'systemEvent'。

**类型：** 'systemEvent'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-kind: 'systemEvent'--><!--Device-SystemEventAttributes-kind: 'systemEvent'-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## level

```TypeScript
level?: number
```

电量百分比。单位：百分比。取值需为 [0,100] 范围内的整数。默认值：默认值为 0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-level?: int--><!--Device-SystemEventAttributes-level?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## packageName

```TypeScript
packageName?: string
```

应用包名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemEventAttributes-packageName?: string--><!--Device-SystemEventAttributes-packageName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
