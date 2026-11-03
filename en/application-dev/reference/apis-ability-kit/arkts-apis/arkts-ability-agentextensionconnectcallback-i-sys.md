# AgentExtensionConnectCallback (System API)

```TypeScript
export interface AgentExtensionConnectCallback
```

Developers can use the callback APIs provided by AgentExtensionConnectCallback to receive data and security authentication requests sent by the server, and to detect the disconnection of the AgentExtensionAbility server.

> **NOTE:** 
> 
> - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module are system APIs.
> - The APIs of this module can be used only in the stage model.

**Since:** 24

<!--Device-unnamed-export interface AgentExtensionConnectCallback--><!--Device-unnamed-export interface AgentExtensionConnectCallback-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## onAuth

```TypeScript
onAuth(handshakeData: string): void
```

Receives the security authentication callback from the AgentExtensionAbility server.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AgentExtensionConnectCallback-onAuth(handshakeData: string): void--><!--Device-AgentExtensionConnectCallback-onAuth(handshakeData: string): void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handshakeData | string | Yes | Security authentication data received from the AgentExtensionAbility server side. |

## onData

```TypeScript
onData(data: string): void
```

Receives data from the AgentExtensionAbility server.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AgentExtensionConnectCallback-onData(data: string): void--><!--Device-AgentExtensionConnectCallback-onData(data: string): void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Data received from the server-side AgentExtensionAbility. |

## onDisconnect

```TypeScript
onDisconnect(): void
```

Called when the connection to the AgentExtensionAbility server is disconnected.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AgentExtensionConnectCallback-onDisconnect(): void--><!--Device-AgentExtensionConnectCallback-onDisconnect(): void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
