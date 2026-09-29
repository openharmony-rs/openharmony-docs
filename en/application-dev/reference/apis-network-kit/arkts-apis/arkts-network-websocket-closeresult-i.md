# CloseResult

```TypeScript
export interface CloseResult
```

Represents the result obtained from the **close** event reported when the WebSocket connection is closed.

**Since:** 10

<!--Device-webSocket-export interface CloseResult--><!--Device-webSocket-export interface CloseResult-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## code

```TypeScript
code: number
```

Error code for closing the connection.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-CloseResult-code: int--><!--Device-CloseResult-code: int-End-->

**System capability:** SystemCapability.Communication.NetStack

## reason

```TypeScript
reason: string
```

Error cause for closing the connection.

**Type:** string

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-CloseResult-reason: string--><!--Device-CloseResult-reason: string-End-->

**System capability:** SystemCapability.Communication.NetStack
