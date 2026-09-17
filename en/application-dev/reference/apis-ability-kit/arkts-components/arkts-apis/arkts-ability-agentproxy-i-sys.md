# AgentProxy (System API)

The proxy object of the AgentExtensionAbility, used to send messages to the AgentExtensionAbility, etc.

@interface AgentProxy

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## authorize

```TypeScript
authorize(handshakeData: string): void
```

Send authentication to the AgentExtensionAbility.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handshakeData | string | Yes | Indicates the handshake data to send. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-failed-to-send-ipc-messages) | Failed to send the IPC message. |

## sendData

```TypeScript
sendData(data: string): void
```

Send data to the AgentExtensionAbility.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Indicates the data to send. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-failed-to-send-ipc-messages) | Failed to send the IPC message. |
