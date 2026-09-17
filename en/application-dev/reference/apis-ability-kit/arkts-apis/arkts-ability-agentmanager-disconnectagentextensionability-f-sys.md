# disconnectAgentExtensionAbility (System API)

## Modules to Import

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## disconnectAgentExtensionAbility

```TypeScript
function disconnectAgentExtensionAbility(proxy: AgentProxy): Promise<void>
```

Disconnects to an AgentExtensionAbility.

**Since:** 24

**Required permissions:** ohos.permission.CONNECT_AGENT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| proxy | [AgentProxy](arkts-ability-agentproxy-i-sys.md) | Yes | The agent proxy to disconnect. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
