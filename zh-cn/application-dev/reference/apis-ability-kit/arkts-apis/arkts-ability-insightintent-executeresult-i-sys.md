# ExecuteResult

意图执行的返回结果。

**起始版本：** 23

<!--Device-insightIntent-interface ExecuteResult--><!--Device-insightIntent-interface ExecuteResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
import { insightIntentDriver } from '@kit.AbilityKit';
import { insightIntentProvider } from '@kit.AbilityKit';
```

## interactionInfo

```TypeScript
interactionInfo?: InteractionInfo
```

意图执行完成后返回的交互信息。

**类型：** [InteractionInfo](arkts-ability-insightintent-interactioninfo-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecuteResult-interactionInfo?: InteractionInfo--><!--Device-ExecuteResult-interactionInfo?: InteractionInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

