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

## code

```TypeScript
code: int
```

意图执行返回的错误码，由开发者定义。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IntentResult-code: int--><!--Device-IntentResult-code: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: T
```

意图执行返回的结果，通常会包含需要返回给系统入口的数据。

**类型：** T

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IntentResult-result?: T--><!--Device-IntentResult-result?: T-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

