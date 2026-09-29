# LocalSocketMessageInfo

```TypeScript
export interface LocalSocketMessageInfo
```

Defines the data received by the client over a local socket connection.

**Since:** 11

<!--Device-socket-export interface LocalSocketMessageInfo--><!--Device-socket-export interface LocalSocketMessageInfo-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: string
```

Local socket connection address.

**Type:** string

**Since:** 11

<!--Device-LocalSocketMessageInfo-address: string--><!--Device-LocalSocketMessageInfo-address: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## message

```TypeScript
message: ArrayBuffer
```

Data received.

**Type:** ArrayBuffer

**Since:** 11

<!--Device-LocalSocketMessageInfo-message: ArrayBuffer--><!--Device-LocalSocketMessageInfo-message: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NetStack

## size

```TypeScript
size: number
```

Data length.

**Type:** number

**Since:** 11

<!--Device-LocalSocketMessageInfo-size: int--><!--Device-LocalSocketMessageInfo-size: int-End-->

**System capability:** SystemCapability.Communication.NetStack
