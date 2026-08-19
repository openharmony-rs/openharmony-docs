# AgentExtensionAbility

AgentExtensionAbility继承自[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)，提供智能体扩展能力，包括智能体 服务的创建、销毁、连接、断开的生命周期回调接口，以及接收客户端所发送数据和安全认证的回调接口。 本文将AgentExtensionAbility组件提供方称为服务端，将AgentExtensionAbility组件使用方称为客户端。 > **说明：** > > 本模块接口不支持在[har](../../../quick-start/har-package.md)包中使用。

**继承/实现关系：** AgentExtensionAbility extends ExtensionAbility

**起始版本：** 24

<!--Device-unnamed-declare class AgentExtensionAbility--><!--Device-unnamed-declare class AgentExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## 导入模块

```TypeScript
import { AgentExtensionAbility } from '@kit.AbilityKit';
```

## onAgentInvoked

```TypeScript
onAgentInvoked(agentId: string): void
```

当LOW_CODE 类型的Agent被成功调用时触发，用于执行初始化操作（如从云端下载资源、加载配置等）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AgentExtensionAbility-onAgentInvoked(agentId: string): void--><!--Device-AgentExtensionAbility-onAgentInvoked(agentId: string): void-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agentId | string | 是 | 低代码类型的Agent的ID。 |

