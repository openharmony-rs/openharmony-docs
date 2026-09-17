# BLEConnectChangedState

描述Gatt profile连接状态。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [BLEConnectionChangeState](arkts-connectivity-ble-bleconnectionchangestate-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示远端设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [deviceId](arkts-connectivity-ble-bleconnectionchangestate-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

表示BLE连接状态的枚举。

**类型：** [ProfileConnectionState](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md)

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [state](arkts-connectivity-ble-bleconnectionchangestate-i.md#state)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
