# CloseResult

Represents the result obtained from the **close** event reported when the WebSocket connection is closed.

**Since:** 10

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## reason

```TypeScript
reason: string
```

Error cause for closing the connection.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack
