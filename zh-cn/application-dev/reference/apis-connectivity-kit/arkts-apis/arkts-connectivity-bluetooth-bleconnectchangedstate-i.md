# BLEConnectChangedState

描述Gatt profile连接状态 。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BLEConnectChangedState](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示远端设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deviceId](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

表示BLE连接状态的枚举。

**类型：** [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [state](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md#state)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
