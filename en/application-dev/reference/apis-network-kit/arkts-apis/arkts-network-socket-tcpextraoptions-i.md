# TCPExtraOptions

Defines other properties of the **TCPSocket** object. This object is inherited from [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md).

**Inheritance/Implementation:** TCPExtraOptions extends [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## keepAlive

```TypeScript
keepAlive?: boolean
```

Whether to keep the connection alive. The default value is **false**. The value **true** means to keep the connection alive, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## OOBInline

```TypeScript
OOBInline?: boolean
```

Whether to enable OOBInline. The default value is **false**. The value **true** means to enable OOBInline, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## socketLinger

```TypeScript
socketLinger?: {on: boolean, linger: number}
```

Socket linger.

- **on**: whether to enable socket linger. The value true means to enable socket linger and false means the  
opposite.  
- **linger**: linger time, in ms. The value ranges from **0** to **65535**.

Specify this parameter only when **on** is set to **true**.

**Type:** {on: boolean, linger: number}

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## tcpFastOpen

```TypeScript
tcpFastOpen?: boolean
```

Whether to enable TCP Fast Open (TFO) in the TCP socket connection. This function allows the client to carry data during the first handshake, reducing the connection setup delay and improving the performance in high-frequency short connection scenarios. The default value is **false**. **true**: yes; **false**: no.

Currently, this parameter can be configured only on the client.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## TCPNoDelay

```TypeScript
TCPNoDelay?: boolean
```

Whether to enable no-delay on the TCP socket connection. The default value is **false**. The value **true** means to enable no-delay on the TCP socket connection, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack
