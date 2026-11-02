# AgentProxy (System API)

```TypeScript
export interface AgentProxy
```

AgentProxy is used to send data or security authentication requests from the client to the AgentExtensionAbility server.

> **NOTE:** 
> 
> - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module are all system APIs.
> - The APIs of this module can be used only in the stage model.
> - The APIs of this module must be used in the main thread. They cannot be used in child threads such as Worker and TaskPool.

**Since:** 24

<!--Device-unnamed-export interface AgentProxy--><!--Device-unnamed-export interface AgentProxy-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## authorize

```TypeScript
authorize(handshakeData: string): void
```

The client calls this API to send a security authentication request to the AgentExtensionAbility server.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AgentProxy-authorize(handshakeData: string): void--><!--Device-AgentProxy-authorize(handshakeData: string): void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handshakeData | string | Yes | Security authentication data to be sent to the AgentExtensionAbility server. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-failed-to-send-ipc-messages) | Failed to send the IPC message. |

## sendData

```TypeScript
sendData(data: string): void
```

The client calls this API to send data to the AgentExtensionAbility server.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AgentProxy-sendData(data: string): void--><!--Device-AgentProxy-sendData(data: string): void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Data to be sent to the AgentExtensionAbility server. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [35600002](../errorcode-ability.md#35600002-failed-to-send-ipc-messages) | Failed to send the IPC message. |
