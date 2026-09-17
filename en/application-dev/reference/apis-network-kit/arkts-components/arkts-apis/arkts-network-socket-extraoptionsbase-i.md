# ExtraOptionsBase

Defines base properties of the **LocalSocket** object.

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## receiveBufferSize

```TypeScript
receiveBufferSize?: number
```

Size of the RX buffer, in bytes. The value ranges from 0 to 262144. If this parameter is left unspecified or the unspecified value exceeds the value range, the default value **8192** is used.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## reuseAddress

```TypeScript
reuseAddress?: boolean
```

Whether to reuse addresses. The value **true** means to reuse addresses, and the value **false** means the opposite.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## sendBufferSize

```TypeScript
sendBufferSize?: number
```

Size of the TX buffer, in bytes. The value ranges from 0 to 262144. If this parameter is left unspecified or the unspecified value exceeds the value range, the default value **8192** is used.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

## socketTimeout

```TypeScript
socketTimeout?: number
```

Timeout duration of the local socket connection, in ms.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack
