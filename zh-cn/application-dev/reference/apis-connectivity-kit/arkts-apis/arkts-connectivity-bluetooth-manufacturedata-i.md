# ManufactureData

描述BLE广播数据包的内容。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ManufactureData](arkts-connectivity-bluetoothmanager-manufacturedata-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## manufactureId

```TypeScript
manufactureId: number
```

表示制造商的ID，由蓝牙SIG分配。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [manufactureId](arkts-connectivity-bluetoothmanager-manufacturedata-i.md#manufactureid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## manufactureValue

```TypeScript
manufactureValue: ArrayBuffer
```

表示制造商发送的制造商数据。

**类型：** ArrayBuffer

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [manufactureValue](arkts-connectivity-bluetoothmanager-manufacturedata-i.md#manufacturevalue)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
