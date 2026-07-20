# IntentEntity

意图实体结构体定义，用于定义意图执行过程中涉及的关键信息对象，包括意图参数和意图执行结果等。

开发者通过继承该类来定义意图实体，继承类需使用[@InsightIntentEntity](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)装饰。

**起始版本：** 20

<!--Device-insightIntent-interface IntentEntity--><!--Device-insightIntent-interface IntentEntity-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## entityId

```TypeScript
entityId: string
```

意图实体的ID。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentEntity-entityId: string--><!--Device-IntentEntity-entityId: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

