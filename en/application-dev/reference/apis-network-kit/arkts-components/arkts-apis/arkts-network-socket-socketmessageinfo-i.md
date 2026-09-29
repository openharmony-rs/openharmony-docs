# SocketMessageInfo

```TypeScript
export interface SocketMessageInfo
```

Defines the socket connection information.

**Since:** 11

<!--Device-socket-export interface SocketMessageInfo--><!--Device-socket-export interface SocketMessageInfo-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## message

```TypeScript
message: ArrayBuffer
```

Received **message** event.

**Type:** ArrayBuffer

**Since:** 11

<!--Device-SocketMessageInfo-message: ArrayBuffer--><!--Device-SocketMessageInfo-message: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NetStack

## remoteInfo

```TypeScript
remoteInfo: SocketRemoteInfo
```

Socket connection information.

**Type:** [SocketRemoteInfo](arkts-network-socket-socketremoteinfo-i.md)

**Since:** 11

<!--Device-SocketMessageInfo-remoteInfo: SocketRemoteInfo--><!--Device-SocketMessageInfo-remoteInfo: SocketRemoteInfo-End-->

**System capability:** SystemCapability.Communication.NetStack
