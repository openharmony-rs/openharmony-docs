# IntentEntityDecoratorInfo

用于描述[@InsightIntentEntity](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)装饰器支持的参数。

**起始版本：** 20

<!--Device-unnamed-declare interface IntentEntityDecoratorInfo--><!--Device-unnamed-declare interface IntentEntityDecoratorInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentFunction, InsightIntentForm, InsightIntentLink, InsightIntentEntity, LinkParamCategory, InsightIntentPage, InsightIntentEntry, InsightIntentFunctionMethod } from '@kit.AbilityKit';
```

## entityCategory

```TypeScript
entityCategory: string
```

表示意图实体类别。可以基于意图实体类别对意图实体进行归类

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentEntityDecoratorInfo-entityCategory: string--><!--Device-IntentEntityDecoratorInfo-entityCategory: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示意图实体的数据格式声明。用于定义意图实体的数据格式。

**类型：** Record<string, Object>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentEntityDecoratorInfo-parameters?: Record<string, Object>--><!--Device-IntentEntityDecoratorInfo-parameters?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## supportedQueryProperties

```TypeScript
supportedQueryProperties?: string[]
```

支持的查询属性。

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IntentEntityDecoratorInfo-supportedQueryProperties?: string[]--><!--Device-IntentEntityDecoratorInfo-supportedQueryProperties?: string[]-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

