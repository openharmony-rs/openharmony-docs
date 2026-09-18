# StateChangeParam

描述profile状态改变参数。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [StateChangeParam](arkts-connectivity-bluetoothmanager-statechangeparam-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示蓝牙设备地址。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deviceId](arkts-connectivity-bluetoothmanager-statechangeparam-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

表示蓝牙设备的profile连接状态。

**类型：** [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [state](arkts-connectivity-bluetoothmanager-statechangeparam-i.md#state)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
