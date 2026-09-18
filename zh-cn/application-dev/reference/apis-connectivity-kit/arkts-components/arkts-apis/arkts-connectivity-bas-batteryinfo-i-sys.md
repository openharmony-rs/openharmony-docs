# BatteryInfo（系统接口）

描述设备的电量信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## batteryLevel

```TypeScript
batteryLevel: number
```

表示设备的电量值。取值范围为[-1, 100]，-1表示没有电量信息，单位: %。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: BluetoothAddress
```

表示远端设备的地址信息。

**类型：** BluetoothAddress

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
