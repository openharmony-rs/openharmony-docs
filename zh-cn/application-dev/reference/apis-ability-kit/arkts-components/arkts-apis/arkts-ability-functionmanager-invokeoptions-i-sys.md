# InvokeOptions（系统接口）

Function调用的可选参数。包含Function调用时的应用上下文信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { functionManager } from '@kit.AbilityKit';
```

## context

```TypeScript
context?: Context
```

执行Function调用时的应用上下文信息。<br>说明：目前仅支持[UIAbilityContext](arkts-ability-uiabilitycontext-c.md)。

**类型：** [Context](arkts-ability-context-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
