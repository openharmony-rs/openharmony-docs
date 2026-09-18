# ServerResponse

描述server端回复client端读/写请求的响应参数结构。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [ServerResponse](arkts-connectivity-ble-serverresponse-i.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

表示远端设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [deviceId](arkts-connectivity-ble-serverresponse-i.md#deviceid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

表示请求的读/写起始位置，与订阅的读/写请求事件携带的offset保持一致。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [offset](arkts-connectivity-ble-serverresponse-i.md#offset)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## status

```TypeScript
status: number
```

表示响应的状态，设置为0即可，表示正常。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [status](arkts-connectivity-ble-serverresponse-i.md#status)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

表示请求的传输ID，与订阅的读/写请求事件携带的ID保持一致。

**类型：** number

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [transId](arkts-connectivity-ble-serverresponse-i.md#transid)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

表示回复响应的二进制数据。

**类型：** ArrayBuffer

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [value](arkts-connectivity-ble-serverresponse-i.md#value)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
