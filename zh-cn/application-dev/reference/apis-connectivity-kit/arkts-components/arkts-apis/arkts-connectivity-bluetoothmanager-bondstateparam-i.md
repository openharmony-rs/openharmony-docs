# BondStateParam

描述配对状态参数。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [BondStateParam](arkts-connectivity-connection-bondstateparam-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示要配对的设备ID。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [deviceId](arkts-connectivity-connection-bondstateparam-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## state

```TypeScript
state: BondState
```

表示配对设备的状态。

**类型：** [BondState](arkts-connectivity-bluetoothmanager-bondstate-e.md)

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [state](arkts-connectivity-connection-bondstateparam-i.md#state)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
