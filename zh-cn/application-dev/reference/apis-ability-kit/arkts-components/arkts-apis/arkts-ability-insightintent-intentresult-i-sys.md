# IntentResult

```TypeScript
interface IntentResult<T>
```

意图执行的返回结果，支持[泛型类型](../../../quick-start/introduction-to-arkts.md#泛型类和接口)。

**起始版本：** 20

<!--Device-insightIntent-interface IntentResult<T>--><!--Device-insightIntent-interface IntentResult<T>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## interactionInfo

```TypeScript
interactionInfo?: InteractionInfo
```

意图执行完成后返回的交互信息。

**类型：** [InteractionInfo](arkts-ability-insightintent-interactioninfo-i-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IntentResult-interactionInfo?: InteractionInfo--><!--Device-IntentResult-interactionInfo?: InteractionInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
