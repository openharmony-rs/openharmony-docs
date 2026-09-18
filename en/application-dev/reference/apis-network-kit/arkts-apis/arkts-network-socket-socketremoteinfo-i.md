# SocketRemoteInfo

Defines information about the socket connection.

**Since:** 7

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

**System capability:** SystemCapability.Communication.NetStack

## port

```TypeScript
port: number
```

Port number. The value ranges from **0** to **65535**.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## size

```TypeScript
size: number
```

Length of the server response message, in bytes.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack
