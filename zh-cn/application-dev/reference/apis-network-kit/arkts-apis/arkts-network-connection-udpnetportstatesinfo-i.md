# UdpNetPortStatesInfo

UDP端口状态信息。

**起始版本：** 24

<!--Device-connection-export interface UdpNetPortStatesInfo--><!--Device-connection-export interface UdpNetPortStatesInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## udpLocalIp

```TypeScript
udpLocalIp: string
```

UDP网络本地IP地址。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UdpNetPortStatesInfo-udpLocalIp: string--><!--Device-UdpNetPortStatesInfo-udpLocalIp: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## udpLocalPort

```TypeScript
udpLocalPort: int
```

UDP网络本地端口，取值范围[0, 65535]。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UdpNetPortStatesInfo-udpLocalPort: int--><!--Device-UdpNetPortStatesInfo-udpLocalPort: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## udpPid

```TypeScript
udpPid: int
```

监听该UDP端口的进程PID。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UdpNetPortStatesInfo-udpPid: int--><!--Device-UdpNetPortStatesInfo-udpPid: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## udpUid

```TypeScript
udpUid: int
```

监听该UDP端口的用户UID。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UdpNetPortStatesInfo-udpUid: int--><!--Device-UdpNetPortStatesInfo-udpUid: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

