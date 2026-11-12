# WebSocketOpenInfo

```TypeScript
export interface WebSocketOpenInfo
```

Detailed information after a WebSocket connection is successfully established.

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

Status information returned by the server. It corresponds to the **status** field. For example, when **status=101** is set, this field returns "Switching Protocols".

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WebSocketOpenInfo-message: string--><!--Device-WebSocketOpenInfo-message: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## protocol

```TypeScript
protocol?: string
```

Negotiated protocol returned by the server.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WebSocketOpenInfo-protocol?: string--><!--Device-WebSocketOpenInfo-protocol?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## status

```TypeScript
status: number
```

Status code returned by the server. For example, 101 indicates that the connection is successfully established and upgraded to the WebSocket protocol.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WebSocketOpenInfo-status: int--><!--Device-WebSocketOpenInfo-status: int-End-->

**System capability:** SystemCapability.Communication.NetStack
