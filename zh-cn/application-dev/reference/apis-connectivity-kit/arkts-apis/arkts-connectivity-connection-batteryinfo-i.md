# BatteryInfo

描述设备的电量信息。

只有支持特定电量信息AT（Attention）命令（包括：+XEVENT和IPHONEACCEV）的设备才支持上报有效的电量信息。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## batteryLevel

```TypeScript
batteryLevel: number
```

表示设备的电量值，单位：%。取值范围：0-100，表示电量百分比；如果该值为-1，表示没有电量信息。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## boxBatteryLevel

```TypeScript
boxBatteryLevel: number
```

若是蓝牙耳机设备类型，表示耳机仓的电量值，单位：%。取值范围：0-100，表示电量百分比；如果该值为-1，表示没有电量信息。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## boxChargeState

```TypeScript
boxChargeState: DeviceChargeState
```

若是蓝牙耳机设备类型，表示耳机仓的充电状态。

**类型：** [DeviceChargeState](arkts-connectivity-connection-devicechargestate-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## leftEarBatteryLevel

```TypeScript
leftEarBatteryLevel: number
```

若是蓝牙耳机设备类型，表示左侧耳机的电量值，单位：%。取值范围：0-100，表示电量百分比；如果该值为-1，表示没有电量信息。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## leftEarChargeState

```TypeScript
leftEarChargeState: DeviceChargeState
```

若是蓝牙耳机设备类型，表示左侧耳机的充电状态。

**类型：** [DeviceChargeState](arkts-connectivity-connection-devicechargestate-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rightEarBatteryLevel

```TypeScript
rightEarBatteryLevel: number
```

若是蓝牙耳机设备类型，表示右侧耳机的电量值，单位：%。取值范围：0-100，表示电量百分比；如果该值为-1，表示没有电量信息。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## rightEarChargeState

```TypeScript
rightEarChargeState: DeviceChargeState
```

若是蓝牙耳机设备类型，表示右侧耳机的充电状态。

**类型：** [DeviceChargeState](arkts-connectivity-connection-devicechargestate-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
