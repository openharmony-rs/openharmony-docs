# InsightIntentInfo（系统接口）

意图信息，表示设备中意图的具体参数配置。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName: string
```

表示应用包名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## developType

```TypeScript
readonly developType?: DevelopType
```

表示意图的开发方式。

**类型：** DevelopType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## displayDescription

```TypeScript
readonly displayDescription: string
```

表示在意图框架中显示的意图描述。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## displayName

```TypeScript
readonly displayName: string
```

表示在意图框架中显示的意图名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## domain

```TypeScript
readonly domain: string
```

表示意图垂域，用于将意图按垂直领域分类（例如：视频、音乐、游戏），取值范围参见
[各垂域的智慧分发特性列表](https://developer.huawei.com/consumer/cn/doc/service/intents-ai-distribution-characteristic-0000001901922213#section2656133582215)
中的垂域字段。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## entities

```TypeScript
readonly entities: Array<EntityInfo>
```

表示意图包含的实体信息。

**类型：** Array<EntityInfo>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## icon

```TypeScript
readonly icon: string
```

表示意图图标。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## intentName

```TypeScript
readonly intentName: string
```

表示意图名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## intentType

```TypeScript
readonly intentType: InsightIntentType
```

表示通过意图装饰器定义的意图类型。

**说明：**

对于使用配置文件开发的意图，该字段返回值默认为[@InsightIntentEntry](./js-apis-app-ability-InsightIntentDecorator.md#insightintententry)类
型装饰器。

**类型：** InsightIntentType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## intentVersion

```TypeScript
readonly intentVersion: string
```

意图版本号，当意图能力演进时，可通过版本号进行区分和管理。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## keywords

```TypeScript
readonly keywords: string[]
```

表示意图的搜索关键字。

**类型：** string[]

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## llmDescription

```TypeScript
readonly llmDescription: string
```

表示意图的功能，用于大型语言模型理解该意图。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
readonly moduleName: string
```

表示模块名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
readonly parameters: Record<string, Object>
```

表示意图参数的数据格式声明，用于意图调用时定义入参的数据格式。

**类型：** Record<string, Object>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## result

```TypeScript
readonly result: Record<string, Object>
```

表示意图调用返回的结果。

**类型：** Record<string, Object>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## schema

```TypeScript
readonly schema: string
```

标准意图名称，如果在标准意图列表中存在schema与intentVersion字段均匹配的意图，则按照标准意图处理。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## subIntentInfo

```TypeScript
readonly subIntentInfo: LinkIntentInfo | PageIntentInfo | FunctionIntentInfo | FormIntentInfo | EntryIntentInfo
```

表示特定意图装饰器的意图信息。

**说明：**

对于使用配置文件开发的意图，该字段返回值默认为[EntryIntentInfo](#entryintentinfo20)。

**类型：** LinkIntentInfo | PageIntentInfo | FunctionIntentInfo | FormIntentInfo | EntryIntentInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## subIntentInfoForConfiguration

```TypeScript
readonly subIntentInfoForConfiguration?: SubIntentInfoForConfiguration
```

表示使用配置文件开发的意图的特有信息。

**类型：** SubIntentInfoForConfiguration

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

