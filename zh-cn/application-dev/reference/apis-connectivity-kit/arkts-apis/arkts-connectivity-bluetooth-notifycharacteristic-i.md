# NotifyCharacteristic

描述server端特征值变化时发送的特征通知参数定义。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [NotifyCharacteristic](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

特定特征（characteristic）的UUID，例如：00002a11-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [characteristicUuid](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#characteristicuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## characteristicValue

```TypeScript
characteristicValue: ArrayBuffer
```

特征对应的二进制值。

**类型：** ArrayBuffer

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [characteristicValue](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#characteristicvalue)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## confirm

```TypeScript
confirm: boolean
```

如果是notification则对端回复确认设置为true，如果是indication则对端不需要回复确认设置为false。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [confirm](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#confirm)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

特定服务（service）的UUID，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceUuid](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md#serviceuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
