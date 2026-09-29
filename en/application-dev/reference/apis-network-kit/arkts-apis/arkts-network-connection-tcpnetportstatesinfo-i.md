# TcpNetPortStatesInfo

```TypeScript
export interface TcpNetPortStatesInfo
```

Describes the TCP port state information.

**Since:** 24

<!--Device-connection-export interface TcpNetPortStatesInfo--><!--Device-connection-export interface TcpNetPortStatesInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## tcpLocalIp

```TypeScript
tcpLocalIp: string
```

Local IP address of the TCP network.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-TcpNetPortStatesInfo-tcpLocalIp: string--><!--Device-TcpNetPortStatesInfo-tcpLocalIp: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## tcpLocalPort

```TypeScript
tcpLocalPort: number
```

Local port of the TCP network. The value range is [0, 65535].

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-TcpNetPortStatesInfo-tcpLocalPort: int--><!--Device-TcpNetPortStatesInfo-tcpLocalPort: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## tcpPid

```TypeScript
tcpPid: number
```

PID of the process that listens for the TCP port.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-TcpNetPortStatesInfo-tcpPid: int--><!--Device-TcpNetPortStatesInfo-tcpPid: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## tcpRemoteIp

```TypeScript
tcpRemoteIp: string
```

Remote IP address of the TCP network.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-TcpNetPortStatesInfo-tcpRemoteIp: string--><!--Device-TcpNetPortStatesInfo-tcpRemoteIp: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## tcpRemotePort

```TypeScript
tcpRemotePort: number
```

Remote port of the TCP network. The value range is [0, 65535].

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-TcpNetPortStatesInfo-tcpRemotePort: int--><!--Device-TcpNetPortStatesInfo-tcpRemotePort: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## tcpState

```TypeScript
tcpState: TcpState
```

TCP network status.

**Type:** [TcpState](arkts-network-connection-tcpstate-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-TcpNetPortStatesInfo-tcpState: TcpState--><!--Device-TcpNetPortStatesInfo-tcpState: TcpState-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## tcpUid

```TypeScript
tcpUid: number
```

UID of the user who listens for the TCP port.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-TcpNetPortStatesInfo-tcpUid: int--><!--Device-TcpNetPortStatesInfo-tcpUid: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
