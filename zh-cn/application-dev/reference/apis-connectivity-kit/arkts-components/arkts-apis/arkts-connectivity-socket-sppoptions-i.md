# SppOptions

描述套接字的配置参数。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## psm

```TypeScript
psm?: number
```

协议/服务多路复用器值，用于标识特定的服务数据传输通道。不填写该参数时默认值为-1。

对于客户端：

SppType设置为SPP_RFCOMM时，该参数不填。SppType设置为SPP_L2CAP_BLE或SPP_L2CAP时，需和服务端的psm值保持一致。

对于服务端：

SppType设置为SPP_RFCOMM时，该参数不填。SppType设置为SPP_L2CAP_BLE时，psm值必须由系统自动分配，有效值范围为[0x01, 0xFF]。SppType设置为SPP_L2CAP时，psm值可以主动设置或蓝牙子系统分配，若为主动设置，其有效范围为[0x01, 0xFFFF]，并且需要满足低位字节最低位必须为1，高位字节最低位必须为0；若为蓝牙子系统分配，该参数不填，可以通过[socket.getL2capPsm](arkts-connectivity-socket-getl2cappsm-f.md)接口获取psm值。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## secure

```TypeScript
secure: boolean
```

是否是安全通道。true表示是安全通道，false表示非安全通道。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## type

```TypeScript
type: SppType
```

蓝牙套接字链路类型。

**类型：** [SppType](arkts-connectivity-socket-spptype-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## uuid

```TypeScript
uuid: string
```

RFCOMM套接字链路类型的服务UUID，例如"00001101-0000-1000-8000-00805F9B34FB"。

建议开发者使用自定义的服务UUID（可通过工具函数[util.generateRandomUUID](../../apis-arkts/arkts-apis/arkts-arkts-util-generaterandomuuid-f.md)生成），也可以使用标准协议定义的Serial Port UUID服务(00001101-0000-1000-8000-00805F9B34FB)。SppType设置为SPP_RFCOMM时该参数必选。SppType设置为SPP_L2CAP或SPP_L2CAP_BLE时设置为空字符串。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core
