# AgentCardType

Agent卡片的类型。

**起始版本：** 26.0.0

<!--Device-agentConstant-export enum AgentCardType--><!--Device-agentConstant-export enum AgentCardType-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## APP

```TypeScript
APP = 0
```

应用型Agent卡片，适用于传统安装应用，Agent能力随应用安装和卸载，需要用户主动安装应用后使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCardType-APP = 0--><!--Device-AgentCardType-APP = 0-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## ATOMIC_SERVICE

```TypeScript
ATOMIC_SERVICE = 1
```

原子化服务型Agent卡片，适用于免安装的原子化服务，Agent能力可以即用即离，无需预先安装，支持快速体验和分享。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AgentCardType-ATOMIC_SERVICE = 1--><!--Device-AgentCardType-ATOMIC_SERVICE = 1-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

