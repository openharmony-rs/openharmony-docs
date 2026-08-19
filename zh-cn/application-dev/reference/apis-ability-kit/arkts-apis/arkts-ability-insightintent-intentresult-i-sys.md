# IntentResult

意图执行的返回结果，支持泛型类型。

**起始版本：** 26.0.0

<!--Device-insightIntent-interface IntentResult--><!--Device-insightIntent-interface IntentResult-End-->

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

<!--Device-IntentResult-interactionInfo?: InteractionInfo--><!--Device-IntentResult-interactionInfo?: InteractionInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

