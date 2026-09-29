# StateChangeParam

```TypeScript
interface StateChangeParam
```

描述profile状态改变参数。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [StateChangeParam](arkts-connectivity-baseprofile-statechangeparam-i.md)

<!--Device-bluetoothManager-interface StateChangeParam--><!--Device-bluetoothManager-interface StateChangeParam-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示蓝牙设备地址。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [deviceId](arkts-connectivity-baseprofile-statechangeparam-i.md#deviceid)

<!--Device-StateChangeParam-deviceId: string--><!--Device-StateChangeParam-deviceId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: ProfileConnectionState
```

表示蓝牙设备的profile连接状态。

**类型：** [ProfileConnectionState](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md)

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [state](arkts-connectivity-baseprofile-statechangeparam-i.md#state)

<!--Device-StateChangeParam-state: ProfileConnectionState--><!--Device-StateChangeParam-state: ProfileConnectionState-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
