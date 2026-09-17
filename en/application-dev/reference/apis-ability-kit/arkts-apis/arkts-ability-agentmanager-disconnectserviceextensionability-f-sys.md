# disconnectServiceExtensionAbility (System API)

## Modules to Import

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## disconnectServiceExtensionAbility

```TypeScript
function disconnectServiceExtensionAbility(context: AgentExtensionContext, connectId: number): Promise<void>
```

Disconnects an AgentExtensionAbility from a ServiceExtensionAbility, in contrast to [connectServiceExtensionAbility](arkts-ability-agentmanager-connectserviceextensionability-f-sys.md).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [AgentExtensionContext](arkts-ability-agentextensioncontext-c.md) | Yes | The context of the current agent extension ability. |
| connectId | number | Yes | The connection id returned by connectServiceExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
