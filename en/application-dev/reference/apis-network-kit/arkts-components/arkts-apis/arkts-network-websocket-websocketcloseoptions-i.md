# WebSocketCloseOptions

Defines the optional parameters carried in the request for closing a WebSocket connection.

**Since:** 6

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## code

```TypeScript
code?: number
```

Error code. Set this parameter based on the actual situation. The value must be a positive integer ranging from 1 000 to 1015. If no error code is specified or the input value is not within the preceding range, the code will be set to the default value **1000**.

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## reason

```TypeScript
reason?: string
```

Error cause. Set this parameter based on the actual situation. If no reason value is specified, the reason value is set to the default value **CLOSE_NORMAL**.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack
