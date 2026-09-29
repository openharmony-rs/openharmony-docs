# ExtraOptionsBase

```TypeScript
export interface ExtraOptionsBase
```

Defines base properties of the **LocalSocket** object.

**Since:** 7

<!--Device-socket-export interface ExtraOptionsBase--><!--Device-socket-export interface ExtraOptionsBase-End-->

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

<!--Device-ExtraOptionsBase-receiveBufferSize?: int--><!--Device-ExtraOptionsBase-receiveBufferSize?: int-End-->

**System capability:** SystemCapability.Communication.NetStack

## reuseAddress

```TypeScript
reuseAddress?: boolean
```

Whether to reuse addresses. The value **true** means to reuse addresses, and the value **false** means the opposite.

**Type:** boolean

**Since:** 7

<!--Device-ExtraOptionsBase-reuseAddress?: boolean--><!--Device-ExtraOptionsBase-reuseAddress?: boolean-End-->

**System capability:** SystemCapability.Communication.NetStack

## sendBufferSize

```TypeScript
sendBufferSize?: number
```

Size of the TX buffer, in bytes. The value ranges from 0 to 262144. If this parameter is left unspecified or the unspecified value exceeds the value range, the default value **8192** is used.

**Type:** number

**Since:** 7

<!--Device-ExtraOptionsBase-sendBufferSize?: int--><!--Device-ExtraOptionsBase-sendBufferSize?: int-End-->

**System capability:** SystemCapability.Communication.NetStack

## socketTimeout

```TypeScript
socketTimeout?: number
```

Timeout duration of the local socket connection, in ms.

**Type:** number

**Since:** 7

<!--Device-ExtraOptionsBase-socketTimeout?: int--><!--Device-ExtraOptionsBase-socketTimeout?: int-End-->

**System capability:** SystemCapability.Communication.NetStack
