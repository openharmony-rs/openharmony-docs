# updateAgentCard (System API)

## Modules to Import

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## updateAgentCard

```TypeScript
function updateAgentCard(agentCard: AgentCard): Promise<void>
```

Updates the AgentCard within specified agent id.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MODIFY_AGENT_CARD

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agentCard | [AgentCard](arkts-ability-agentcard-i.md) | Yes | The AgentCard information to update. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [18500001](../errorcode-ability.md#18500001-invalid-bundle-name) | The bundle does not exist or no patch has been applied. |
| [35600001](../errorcode-ability.md#35600001-the-specified-agentid-does-not-exist) | The specified agentId does not exist. |
| [35600004](../errorcode-ability.md#35600004-the-specified-agentcard-version-is-older-than-the-current-version) | The specified AgentCard version is older than the current version. |
| [35600005](../errorcode-ability.md#35600005-the-specified-agentcard-version-is-invalid) | The specified AgentCard version is invalid. |
