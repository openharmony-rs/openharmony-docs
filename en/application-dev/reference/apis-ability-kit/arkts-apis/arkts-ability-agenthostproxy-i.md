# AgentHostProxy

```TypeScript
export interface AgentHostProxy
```

AgentHostProxy is used to send data or security authentication requests from the AgentExtensionAbility server to the client.

> **NOTE:** 
> 
> - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.
> - The APIs of this module must be used in the main thread. They are not supported in subthreads such as Worker and TaskPool.

**Since:** 24

<!--Device-unnamed-export interface AgentHostProxy--><!--Device-unnamed-export interface AgentHostProxy-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## authorize

```TypeScript
authorize(handshakeData: string): void
```

Sends a security authentication request from the AgentExtensionAbility server to the client.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-AgentHostProxy-authorize(handshakeData: string): void--><!--Device-AgentHostProxy-authorize(handshakeData: string): void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handshakeData | string | Yes | Security authentication data to be sent to the client. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-failed-to-send-ipc-messages) | Failed to send the IPC message. |

## sendData

```TypeScript
sendData(data: string): void
```

Sends data from the AgentExtensionAbility server to the client.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-AgentHostProxy-sendData(data: string): void--><!--Device-AgentHostProxy-sendData(data: string): void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Data to be sent to the client of AgentExtensionAbility. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-failed-to-send-ipc-messages) | Failed to send the IPC message. |
