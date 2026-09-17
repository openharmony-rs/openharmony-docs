# AgentHostProxy

The proxy object of the connected party for the AgentExtensionAbility, used to send messages to the connected party, etc.

@interface AgentHostProxy

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## authorize

```TypeScript
authorize(handshakeData: string): void
```

Send authentication to an agent service host.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

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

Send data to an agent service host.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Indicates the data to send. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-failed-to-send-ipc-messages) | Failed to send the IPC message. |
