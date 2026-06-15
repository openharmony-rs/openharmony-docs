# AgentExtensionContext (智能体扩展组件上下文)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

AgentExtensionContext模块是[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)的上下文环境，继承自[ExtensionContext](js-apis-inner-application-extensionContext.md)。

AgentExtensionContext为开发者提供访问当前[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)智能体所配置的[AgentCard](js-apis-inner-application-AgentCard.md)信息的能力。

> **说明：**
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口仅可在Stage模型下使用。
> - 在本文档的示例中，通过`this.context`来获取`AgentExtensionContext`，其中`this`代表继承自`AgentExtensionAbility`的实例。

## 导入模块

```ts
import { common } from '@kit.AbilityKit';
```

## AgentExtensionContext

### 属性

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| agentCard | [AgentCard](js-apis-inner-application-AgentCard.md) | 否 | 否 | 当前[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)所配置的[AgentCard](js-apis-inner-application-AgentCard.md#agentcard-1)信息。 |

**示例：**

```ts
import { AgentExtensionAbility, common } from '@kit.AbilityKit';

export default class AgentExtension extends AgentExtensionAbility {
  onCreate(): void {
    let tmpContext: common.AgentExtensionContext = this.context; // 获取AgentExtensionContext
    console.info(`agentCard info data: ${JSON.stringify(tmpContext.agentCard)}.`);
  }
}
```
