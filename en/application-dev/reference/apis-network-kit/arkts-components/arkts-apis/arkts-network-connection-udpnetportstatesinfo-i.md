# UdpNetPortStatesInfo

Describes the UDP port state information.

**Since:** 24

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## udpLocalIp

```TypeScript
udpLocalIp: string
```

Local IP address of the UDP network.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## udpLocalPort

```TypeScript
udpLocalPort: number
```

Local port of the UDP network. The value range is [0, 65535].

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## udpPid

```TypeScript
udpPid: number
```

PID of the process that listens for the UDP port.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## udpUid

```TypeScript
udpUid: number
```

UID of the user who listens for the UDP port.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core
