# SocketStateBase

```TypeScript
export interface SocketStateBase
```

Defines the status of the socket connection.

**Since:** 7

<!--Device-socket-export interface SocketStateBase--><!--Device-socket-export interface SocketStateBase-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## isBound

```TypeScript
isBound: boolean
```

Whether the connection is in the bound state. The value **true** indicates that the connection is in the bound state, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 7

<!--Device-SocketStateBase-isBound: boolean--><!--Device-SocketStateBase-isBound: boolean-End-->

**System capability:** SystemCapability.Communication.NetStack

## isClose

```TypeScript
isClose: boolean
```

Whether the connection is in the closed state. The value **true** indicates that the connection is in the closed state, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 7

<!--Device-SocketStateBase-isClose: boolean--><!--Device-SocketStateBase-isClose: boolean-End-->

**System capability:** SystemCapability.Communication.NetStack

## isConnected

```TypeScript
isConnected: boolean
```

Whether the connection is in the connected state. The value **true** indicates that the connection is in the connected state, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 7

<!--Device-SocketStateBase-isConnected: boolean--><!--Device-SocketStateBase-isConnected: boolean-End-->

**System capability:** SystemCapability.Communication.NetStack
