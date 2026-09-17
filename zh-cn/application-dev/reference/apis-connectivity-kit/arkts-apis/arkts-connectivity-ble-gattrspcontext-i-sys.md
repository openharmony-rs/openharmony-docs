# GattRspContext（系统接口）

client端调用[writeCharacteristicValueWithContext](arkts-connectivity-ble-gattclientdevice-i-sys.md#writecharacteristicvaluewithcontext)等接口并接收到server端的回复消息后，蓝牙子系统上报给应用的信息。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## timestamp

```TypeScript
timestamp: number
```

本端接收到对端GATT回复消息的时间点，格式为微秒级的UNIX时间戳。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
