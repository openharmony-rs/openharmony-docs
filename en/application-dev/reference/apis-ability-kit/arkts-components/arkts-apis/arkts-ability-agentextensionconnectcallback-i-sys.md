# AgentExtensionConnectCallback (System API)

Agent extension connect callback.

@interface AgentExtensionConnectCallback

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## onAuth

```TypeScript
onAuth(handshakeData: string): void
```

Called back when authentication is received.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handshakeData | string | Yes | Indicates the received handshake data. |

## onData

```TypeScript
onData(data: string): void
```

Called back when data is received.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Indicates the received data. |

## onDisconnect

```TypeScript
onDisconnect(): void
```

The callback interface was disconnected successfully.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
