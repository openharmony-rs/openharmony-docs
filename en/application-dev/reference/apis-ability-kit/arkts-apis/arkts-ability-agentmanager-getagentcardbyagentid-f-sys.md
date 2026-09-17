# getAgentCardByAgentId (System API)

## Modules to Import

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## getAgentCardByAgentId

```TypeScript
function getAgentCardByAgentId(bundleName: string, agentId: string): Promise<AgentCard>
```

Gets the AgentCard within specified agent id.

**Since:** 24

**Required permissions:** ohos.permission.GET_AGENT_CARD

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | The bundle name the AgentCard belongs to. |
| agentId | string | Yes | The agent id the AgentCard belongs to. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AgentCard](arkts-ability-agentcard-i.md)&gt; | Returns the specified AgentCard. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [18500001](../errorcode-ability.md#18500001-invalid-bundle-name) | The bundle does not exist or no patch has been applied. |
| [35600001](../errorcode-ability.md#35600001-the-specified-agentid-does-not-exist) | The specified agentId does not exist. |
