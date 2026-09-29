# DescriptorWriteReq

```TypeScript
interface DescriptorWriteReq
```

描述server端订阅后收到的描述符写请求事件参数结构。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [DescriptorWriteRequest](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md)

<!--Device-bluetooth-interface DescriptorWriteReq--><!--Device-bluetooth-interface DescriptorWriteReq-End-->

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

**替代接口：** [characteristicUuid](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#characteristicuuid)

<!--Device-DescriptorWriteReq-characteristicUuid: string--><!--Device-DescriptorWriteReq-characteristicUuid: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

表示描述符（descriptor）的UUID，例如：00002902-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [descriptorUuid](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#descriptoruuid)

<!--Device-DescriptorWriteReq-descriptorUuid: string--><!--Device-DescriptorWriteReq-descriptorUuid: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

表示发送描述符写请求的远端设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deviceId](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#deviceid)

<!--Device-DescriptorWriteReq-deviceId: string--><!--Device-DescriptorWriteReq-deviceId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## isPrep

```TypeScript
isPrep: boolean
```

表示写请求是否立即执行。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isPrep](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#isprep)

<!--Device-DescriptorWriteReq-isPrep: boolean--><!--Device-DescriptorWriteReq-isPrep: boolean-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## needRsp

```TypeScript
needRsp: boolean
```

表示是否要给client端回复响应。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [needRsp](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#needrsp)

<!--Device-DescriptorWriteReq-needRsp: boolean--><!--Device-DescriptorWriteReq-needRsp: boolean-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

表示写描述符数据的起始位置。例如：k表示从第k个字节开始写，server端回复响应时需填写相同的offset。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [offset](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#offset)

<!--Device-DescriptorWriteReq-offset: number--><!--Device-DescriptorWriteReq-offset: number-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

特定服务（service）的UUID，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceUuid](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#serviceuuid)

<!--Device-DescriptorWriteReq-serviceUuid: string--><!--Device-DescriptorWriteReq-serviceUuid: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

表示写请求的传输ID，server端回复响应时需填写相同的传输ID。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [transId](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#transid)

<!--Device-DescriptorWriteReq-transId: number--><!--Device-DescriptorWriteReq-transId: number-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

表示写入的描述符二进制数据。

**类型：** ArrayBuffer

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [value](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#value)

<!--Device-DescriptorWriteReq-value: ArrayBuffer--><!--Device-DescriptorWriteReq-value: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
