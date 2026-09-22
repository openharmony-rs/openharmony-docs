# AgentExtensionAbility

```TypeScript
declare class AgentExtensionAbility extends ExtensionAbility
```

The class of agent extension ability. This class cannot be used in Harmony Archive(HAR).

@extends ExtensionAbility

**Inheritance/Implementation:** AgentExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 24

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { AgentExtensionAbility } from '@kit.AbilityKit';
```

## onAuth

```TypeScript
onAuth(proxy: AgentHostProxy, handshakeData: string): void
```

The system triggers this callback when the AgentExtensionAbility receives a security authentication request sent by the client. The server can process the received security authentication request in this callback, and use [AgentHostProxy.authorize](arkts-ability-agenthostproxy-i.md#authorize) to send a security authentication request to the client.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| proxy | [AgentHostProxy](arkts-ability-agenthostproxy-i.md) | Yes | Indicates the agent service host proxy. |
| handshakeData | string | Yes | Indicates the received handshake data. |

## onConnect

```TypeScript
onConnect(want: Want, proxy: AgentHostProxy): void
```

Called back when an agent extension is connected to an ability.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates connection information about the AgentExtensionAbility. |
| proxy | [AgentHostProxy](arkts-ability-agenthostproxy-i.md) | Yes | Indicates the agent service host proxy. |

## onCreate

```TypeScript
onCreate(want: Want): void
```

The system triggers this callback when an AgentExtensionAbility instance is created. Developers can perform initialization logic (such as defining variables and loading resources) in this callback.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information, including the ability name and bundle name. |

## onData

```TypeScript
onData(proxy: AgentHostProxy, data: string): void
```

The system triggers this callback when the AgentExtensionAbility receives data sent by the client. The server can use [AgentHostProxy.sendData](arkts-ability-agenthostproxy-i.md#senddata) to send data to the client in this callback.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| proxy | [AgentHostProxy](arkts-ability-agenthostproxy-i.md) | Yes | Indicates the agent service host proxy. |
| data | string | Yes | Indicates the received data. |

## onDestroy

```TypeScript
onDestroy(): void
```

Called back before an agent service extension is destroyed.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## onDisconnect

```TypeScript
onDisconnect(want: Want, proxy: AgentHostProxy): void
```

Called back when ability connected to an agent service extension is disconnected.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates disconnection information about the agent service extension. |
| proxy | [AgentHostProxy](arkts-ability-agenthostproxy-i.md) | Yes | Indicates the agent service host proxy. |

## context

```TypeScript
context: AgentExtensionContext
```

Context of the AgentExtensionAbility.

**Type:** [AgentExtensionContext](arkts-ability-agentextensioncontext-c.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AgentRuntime.Core
