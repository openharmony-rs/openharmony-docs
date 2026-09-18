# DescriptorReadReq

描述server端订阅后收到的描述符读请求事件参数结构。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [DescriptorReadRequest](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md)

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

**替代接口：** [characteristicUuid](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md#characteristicuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

表示描述符（descriptor）的UUID，例如：00002902-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [descriptorUuid](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md#descriptoruuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

表示发送描述符读请求的远端设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deviceId](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

表示读描述符数据的起始位置。例如：k表示从第k个字节开始读，server端回复响应时需填写相同的offset。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [offset](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md#offset)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

特定服务（service）的UUID，例如：00001888-0000-1000-8000-00805f9b34fb。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [serviceUuid](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md#serviceuuid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

表示读请求的传输ID，server端回复响应时需填写相同的传输ID。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [transId](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md#transid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
