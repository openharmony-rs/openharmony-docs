# SocketRemoteInfo

```TypeScript
export interface SocketRemoteInfo
```

Defines information about the socket connection.

**Since:** 7

<!--Device-socket-export interface SocketRemoteInfo--><!--Device-socket-export interface SocketRemoteInfo-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: string
```

Peer IP address.

**Type:** string

**Since:** 7

<!--Device-SocketRemoteInfo-address: string--><!--Device-SocketRemoteInfo-address: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## family

```TypeScript
family: 'IPv4' | 'IPv6'
```

Network protocol type.

- IPv4  
- IPv6

The default value is **IPv4**.

**Type:** 'IPv4' &#124; 'IPv6'

**Since:** 7

<!--Device-SocketRemoteInfo-family: 'IPv4' | 'IPv6'--><!--Device-SocketRemoteInfo-family: 'IPv4' | 'IPv6'-End-->

**System capability:** SystemCapability.Communication.NetStack

## port

```TypeScript
port: number
```

Port number. The value ranges from **0** to **65535**.

**Type:** number

**Since:** 7

<!--Device-SocketRemoteInfo-port: int--><!--Device-SocketRemoteInfo-port: int-End-->

**System capability:** SystemCapability.Communication.NetStack

## size

```TypeScript
size: number
```

Length of the server response message, in bytes.

**Type:** number

**Since:** 7

<!--Device-SocketRemoteInfo-size: int--><!--Device-SocketRemoteInfo-size: int-End-->

**System capability:** SystemCapability.Communication.NetStack
