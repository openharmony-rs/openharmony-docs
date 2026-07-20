# IntentDecoratorInfo

意图装饰器的通用属性，用于定义意图的基本信息（包括意图名称、意图版本号）。适用于本模块的所有装饰器。

> **说明：**  
>  
> 如果根据schema与intentVersion字段，在标准意图列表存在匹配的标准意图，系统会将intentName、domain、llmDescription、keywords、parameters、result字段均设置为标准  
> 意图的相应字段值。

**起始版本：** 20

<!--Device-unnamed-declare interface IntentDecoratorInfo--><!--Device-unnamed-declare interface IntentDecoratorInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentFunction, InsightIntentForm, InsightIntentLink, InsightIntentEntity, LinkParamCategory, InsightIntentPage, InsightIntentEntry, InsightIntentFunctionMethod } from '@kit.AbilityKit';
```

## displayDescription

```TypeScript
displayDescription?: string
```

表示显示给用户的意图描述。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-displayDescription?: string--><!--Device-IntentDecoratorInfo-displayDescription?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## displayName

```TypeScript
displayName: string
```

表示显示给用户的意图名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-displayName: string--><!--Device-IntentDecoratorInfo-displayName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## domain

```TypeScript
domain: string
```

表示意图垂域，用于将意图按垂直领域分类（例如：视频、音乐、游戏），取值范围参见[各垂域的智慧分发特性列表](https://developer.huawei.com/consumer/cn/doc/service/intents-ai-distribution-characteristic-0000001901922213#section2656133582215)中的垂域字段。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-domain: string--><!--Device-IntentDecoratorInfo-domain: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## icon

```TypeScript
icon?: ResourceStr
```

表示意图图标，用于在AI入口显示。

- 当取值为字符串类型时，表示图标读取网络资源。  
- 当取值为[Resource](../../reference/apis-localization-kit/js-apis-resource-manager.md)时，表示图标读取本地资源。

**类型：** ResourceStr

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-icon?: ResourceStr--><!--Device-IntentDecoratorInfo-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## intentName

```TypeScript
intentName: string
```

表示意图名称，是意图的唯一标识。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-intentName: string--><!--Device-IntentDecoratorInfo-intentName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## intentVersion

```TypeScript
intentVersion: string
```

表示意图版本号。当意图能力演进时，可通过版本号进行区分和管理。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-intentVersion: string--><!--Device-IntentDecoratorInfo-intentVersion: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## keywords

```TypeScript
keywords?: string[]
```

表示意图的搜索关键字。

**类型：** string[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-keywords?: string[]--><!--Device-IntentDecoratorInfo-keywords?: string[]-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## llmDescription

```TypeScript
llmDescription?: string
```

表示意图的功能，用于大型语言模型理解该意图。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-llmDescription?: string--><!--Device-IntentDecoratorInfo-llmDescription?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示意图参数的数据格式声明，用于意图调用时定义入参的数据格式。取值参见[各垂域意图Schema](https://developer.huawei.com/consumer/cn/doc/service/intents-schema-0000001901962713)

**类型：** Record&lt;string, Object&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-parameters?: Record<string, Object>--><!--Device-IntentDecoratorInfo-parameters?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## result

```TypeScript
result?: Record<string, Object>
```

表示意图调用返回结果的数据格式声明，用于定义意图调用返回结果的数据格式。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-result?: Record<string, Object>--><!--Device-IntentDecoratorInfo-result?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## schema

```TypeScript
schema?: string
```

表示接入的标准意图的名称。开发者[接入标准意图](docroot://application-models/insight-intent-definition.md#接入标准意图)时，需要配置该字段，[创建自定义意图](docroot://application-models/insight-intent-definition.md#创建自定义意图)时，无需配置该字段。标准意图列表参见[附录：标准意图接入规范](docroot://application-models/insight-intent-access-specifications.md)。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-IntentDecoratorInfo-schema?: string--><!--Device-IntentDecoratorInfo-schema?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

