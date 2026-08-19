# TcpNetPortStatesInfo

TCP端口状态信息。

**起始版本：** 24

<!--Device-connection-export interface TcpNetPortStatesInfo--><!--Device-connection-export interface TcpNetPortStatesInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## tcpLocalIp

```TypeScript
tcpLocalIp: string
```

TCP网络本地IP地址。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpNetPortStatesInfo-tcpLocalIp: string--><!--Device-TcpNetPortStatesInfo-tcpLocalIp: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## tcpLocalPort

```TypeScript
tcpLocalPort: int
```

TCP网络本地端口，取值范围[0, 65535]。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpNetPortStatesInfo-tcpLocalPort: int--><!--Device-TcpNetPortStatesInfo-tcpLocalPort: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## tcpPid

```TypeScript
tcpPid: int
```

监听该TCP端口的进程PID。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpNetPortStatesInfo-tcpPid: int--><!--Device-TcpNetPortStatesInfo-tcpPid: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## tcpRemoteIp

```TypeScript
tcpRemoteIp: string
```

TCP网络远程IP地址。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpNetPortStatesInfo-tcpRemoteIp: string--><!--Device-TcpNetPortStatesInfo-tcpRemoteIp: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## tcpRemotePort

```TypeScript
tcpRemotePort: int
```

TCP网络远程端口，取值范围[0, 65535]。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpNetPortStatesInfo-tcpRemotePort: int--><!--Device-TcpNetPortStatesInfo-tcpRemotePort: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## tcpState

```TypeScript
tcpState: TcpState
```

TCP网络状态。

**类型：** [TcpState](arkts-network-connection-tcpstate-e.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpNetPortStatesInfo-tcpState: TcpState--><!--Device-TcpNetPortStatesInfo-tcpState: TcpState-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## tcpUid

```TypeScript
tcpUid: int
```

监听该TCP端口的用户UID。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TcpNetPortStatesInfo-tcpUid: int--><!--Device-TcpNetPortStatesInfo-tcpUid: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

