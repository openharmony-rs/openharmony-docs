# NetPortStatesInfo

Describes the information about the TCP and UDP ports that are currently listened for by the system.

**Since:** 24

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## tcpPortStatesInfo

```TypeScript
tcpPortStatesInfo?: Array<TcpNetPortStatesInfo>
```

TCP information currently listened for by the system.

**Type:** Array&lt;[TcpNetPortStatesInfo](arkts-network-connection-tcpnetportstatesinfo-i.md)&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## udpPortStatesInfo

```TypeScript
udpPortStatesInfo?: Array<UdpNetPortStatesInfo>
```

UDP information currently listened for by the system.

**Type:** Array&lt;[UdpNetPortStatesInfo](arkts-network-connection-udpnetportstatesinfo-i.md)&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core
