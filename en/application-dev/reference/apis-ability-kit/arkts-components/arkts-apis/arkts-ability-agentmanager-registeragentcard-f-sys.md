# registerAgentCard (System API)

## Modules to Import

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## registerAgentCard

```TypeScript
function registerAgentCard(agentCard: AgentCard): Promise<void>
```

Registers an AgentCard. If `agentCard.type` is not specified, it defaults to `agentConstant.AgentCardType.APP`. When the type is `APP` or `LOW_CODE`, `appInfo` is validated, especially `bundleName` and `abilityName`. A maximum of 1000 AgentCards can be registered under one bundle.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MODIFY_AGENT_CARD

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agentCard | [AgentCard](arkts-ability-agentcard-i.md) | Yes | The AgentCard information to register. |

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
| [35600005](../errorcode-ability.md#35600005-the-specified-agentcard-version-is-invalid) | The specified AgentCard version is invalid. |
| [35600006](../errorcode-ability.md#35600006-the-specified-agentcard-has-already-been-registered) | The specified AgentCard has already been registered. Use updateAgentCard instead. |
| [35600008](../errorcode-ability.md#35600008-the-number-of-agentcards-in-the-same-application-reaches-the-limit) | The number of AgentCards in the bundle reaches the limit. |
