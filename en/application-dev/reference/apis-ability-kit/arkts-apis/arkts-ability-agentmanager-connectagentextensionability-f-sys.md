# connectAgentExtensionAbility (System API)

## Modules to Import

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## connectAgentExtensionAbility

```TypeScript
function connectAgentExtensionAbility(want: Want, agentId: string,
    callback: AgentExtensionConnectCallback): Promise<AgentProxy>
```

Connects to an AgentExtensionAbility.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECT_AGENT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates the want info to connect. |
| agentId | string | Yes | The agent id to connect. |
| callback | [AgentExtensionConnectCallback](arkts-ability-agentextensionconnectcallback-i-sys.md) | Yes | The callback of connection. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AgentProxy](arkts-ability-agentproxy-i-sys.md)&gt; | The promise to get AgentProxy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by enterprise device management (EDM). |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |
| [35600001](../errorcode-ability.md#35600001-the-specified-agentid-does-not-exist) | The specified agentId does not exist. |
| [35600003](../errorcode-ability.md#35600003-maximum-caller-connections-reached) | Maximum connections from the same caller have been reached. Please disconnect at least one agent extension beforehand. |
| [35600007](../errorcode-ability.md#35600007-the-specified-low_code-agent-has-been-triggered-and-has-not-completed-its-workflow) | The specified LOW_CODE agent is already active and is not yet completed. |
