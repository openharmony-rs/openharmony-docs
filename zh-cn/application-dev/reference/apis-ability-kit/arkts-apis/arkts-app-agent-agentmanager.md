# @ohos.app.agent.agentManager

agentManager模块提供Agent管理能力，支持AgentExtensionAbility的连接、断开连接等操作，支持LOW_CODE类型Agent的生命周期管理，支持AgentExtensionAbility与 ServiceExtensionAbility的连接管理，同时提供获取设备上的AgentCard信息。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace agentManager--><!--Device-unnamed-declare namespace agentManager-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [connectAgentExtensionAbility](arkts-ability-agentmanager-connectagentextensionability-f-sys.md) | 将当前调用方组件连接到 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)。通过返回的 [AgentProxy](arkts-ability-agentproxy-i-sys.md)与 [AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md)进行通信，以使用 AgentExtensionAbility对外提供的能力。 |
| [connectServiceExtensionAbility](arkts-ability-agentmanager-connectserviceextensionability-f-sys.md) | 将AgentExtensionAbility连接到ServiceExtensionAbility。若目标ServiceExtensionAbility可见，可直接连接；若不可见，需申请 `ohos.permission.START_INVISIBLE_ABILITY`权限；若目标ServiceExtensionAbility位于远程设备上，需申请 `ohos.permission.DISTRIBUTED_DATASYNC`权限。 |
| [deleteAgentCard](arkts-ability-agentmanager-deleteagentcard-f-sys.md) | 删除指定应用agentId对应的AgentCard。 |
| [disconnectAgentExtensionAbility](arkts-ability-agentmanager-disconnectagentextensionability-f-sys.md) | 断开与指定proxy的[AgentExtensionAbility](arkts-ability-app-agent-agentextensionability-agentextensionability-c.md) 的连接。 |
| [disconnectServiceExtensionAbility](arkts-ability-agentmanager-disconnectserviceextensionability-f-sys.md) | 断开AgentExtensionAbility与ServiceExtensionAbility的连接。 |
| [getAgentCardByAgentId](arkts-ability-agentmanager-getagentcardbyagentid-f-sys.md) | 获取指定应用agentId对应的AgentCard。使用Promise异步回调。 |
| [getAgentCardsByBundleName](arkts-ability-agentmanager-getagentcardsbybundlename-f-sys.md) | 获取指定应用的所有AgentCard。使用Promise异步回调。 |
| [getAllAgentCards](arkts-ability-agentmanager-getallagentcards-f-sys.md) | 获取设备上所有的AgentCard。使用Promise异步回调。 |
| [notifyLowCodeAgentComplete](arkts-ability-agentmanager-notifylowcodeagentcomplete-f-sys.md) | 通知指定的 LOW_CODE类 型的AgentCard关联的Agent生命周期已结束。 |
| [registerAgentCard](arkts-ability-agentmanager-registeragentcard-f-sys.md) | 注册AgentCard到系统中，使系统能够识别和调用对应的AgentExtensionAbility。 系统会根据类型对appInfo进行校验： - APP、LOW_CODE类型：校验bundle和ability是否存在，并验证ability是否为agent类型。 - ATOMIC_SERVICE类型：在原子化服务已安装时，校验ability是否存在，并验证ability是否为agent类型。 |
| [updateAgentCard](arkts-ability-agentmanager-updateagentcard-f-sys.md) | 更新系统中已存在的AgentCard信息，当[SemVer版本](https://semver.org/)不低于当前已存在的AgentCard时执行覆盖更新。当SemVer版本相同时，系统优先保存通过 [registerAgentCard](arkts-ability-agentmanager-registeragentcard-f-sys.md)或[updateAgentCard](arkts-ability-agentmanager-updateagentcard-f-sys.md)接口调用 时传入的AgentCard。 系统会根据类型对appInfo进行校验： - APP、LOW_CODE类型：校验bundle和ability是否存在，并验证ability是否为agent类型。 - ATOMIC_SERVICE类型：在原子化服务已安装时，校验ability是否存在，并验证ability是否为agent类型。 |
<!--DelEnd-->

