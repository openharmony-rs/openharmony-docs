# @ohos.app.agent.agentConstant (Agent常量)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangxuguang-huawei-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

agentConstant模块提供Agent相关的常量。

**起始版本：** 26.0.0

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

## 导入模块

```ts
import { agentConstant } from '@kit.AbilityKit';
```

## agentConstant.AgentCardType

Agent卡片的类型。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API(仅ArkTS-Dyn)**：从API版本26.0.0开始，该枚举支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**ArkTS-Dyn起始版本**：26.0.0

**ArkTS-Sta起始版本**：26.0.0

| 名称      | 值   | 说明                   |
| --------- | ---- | ---------------------- |
| APP       | 0    | 应用型Agent卡片，适用于传统安装应用，Agent能力随应用一起安装和卸载，需要用户主动安装应用后才能使用。       |
| ATOMIC_SERVICE | 1 | 原子化服务型Agent卡片，适用于免安装的原子化服务，Agent能力可以即用即离，无需预先安装，支持快速体验和分享。  |