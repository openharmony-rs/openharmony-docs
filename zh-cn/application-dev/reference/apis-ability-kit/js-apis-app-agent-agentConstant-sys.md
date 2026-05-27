# @ohos.app.agent.agentConstant (Agent常量)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangxuguang-huawei-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

agentConstant模块提供Agent相关的常量。

> **说明：**
>
> 本模块首批接口从API版本26.0.0开始支持。
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口均为系统接口。

## 导入模块

```ts
import { agentConstant } from '@kit.AbilityKit';
```

## agentConstant.AgentCardType

Agent卡片的类型。

**原子化服务API**：从API版本26.0.0开始，该枚举支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

| 名称      | 值   | 说明                   |
| --------- | ---- | ---------------------- |
| LOW_CODE  | 2    | 低代码型Agent卡片，仅系统应用可使用，适用于系统应用提供的快速构建和部署的智能体能力，支持通过可视化配置或简单脚本快速创建Agent，无需编写完整代码，降低Agent开发门槛。     |