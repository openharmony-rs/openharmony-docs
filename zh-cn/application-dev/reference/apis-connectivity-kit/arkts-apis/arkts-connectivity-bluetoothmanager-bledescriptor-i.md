# BLEDescriptor

描述descriptor的接口参数定义。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

特定特征（characteristic）的UUID，例如：00002a11-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [characteristicUuid](arkts-connectivity-ble-bledescriptor-i.md#characteristicuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

描述符（descriptor）的UUID，例如：00002902-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [descriptorUuid](arkts-connectivity-ble-bledescriptor-i.md#descriptoruuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptorValue

```TypeScript
descriptorValue: ArrayBuffer
```

描述符对应的二进制值。

**类型：** ArrayBuffer

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [descriptorValue](arkts-connectivity-ble-bledescriptor-i.md#descriptorvalue)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

特定服务（service）的UUID，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [serviceUuid](arkts-connectivity-ble-bledescriptor-i.md#serviceuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
