# WebSocketOpenInfo

```TypeScript
export interface WebSocketOpenInfo
```

The result for open info of a WebSocket connection.

**Since:** 26.0.0

<!--Device-webSocket-export interface WebSocketOpenInfo--><!--Device-webSocket-export interface WebSocketOpenInfo-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## message

```TypeScript
message: string
```

result message.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WebSocketOpenInfo-message: string--><!--Device-WebSocketOpenInfo-message: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## protocol

```TypeScript
protocol?: string
```

Negotiated protocol.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WebSocketOpenInfo-protocol?: string--><!--Device-WebSocketOpenInfo-protocol?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## status

```TypeScript
status: number
```

result status.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WebSocketOpenInfo-status: int--><!--Device-WebSocketOpenInfo-status: int-End-->

**System capability:** SystemCapability.Communication.NetStack
