# BLEDescriptor

```TypeScript
interface BLEDescriptor
```

描述descriptor的接口参数定义 。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BLEDescriptor](arkts-connectivity-bluetoothmanager-bledescriptor-i.md)

<!--Device-bluetooth-interface BLEDescriptor--><!--Device-bluetooth-interface BLEDescriptor-End-->

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

**替代接口：** [characteristicUuid](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#characteristicuuid)

<!--Device-BLEDescriptor-characteristicUuid: string--><!--Device-BLEDescriptor-characteristicUuid: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

描述符（descriptor）的UUID，例如：00002902-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [descriptorUuid](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#descriptoruuid)

<!--Device-BLEDescriptor-descriptorUuid: string--><!--Device-BLEDescriptor-descriptorUuid: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptorValue

```TypeScript
descriptorValue: ArrayBuffer
```

描述符对应的二进制值。

**类型：** ArrayBuffer

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [descriptorValue](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#descriptorvalue)

<!--Device-BLEDescriptor-descriptorValue: ArrayBuffer--><!--Device-BLEDescriptor-descriptorValue: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

特定服务（service）的UUID，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceUuid](arkts-connectivity-bluetoothmanager-bledescriptor-i.md#serviceuuid)

<!--Device-BLEDescriptor-serviceUuid: string--><!--Device-BLEDescriptor-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
