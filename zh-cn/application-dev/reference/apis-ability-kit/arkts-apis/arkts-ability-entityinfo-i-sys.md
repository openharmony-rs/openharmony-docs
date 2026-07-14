# EntityInfo（系统接口）

EntityInfo继承自[IntentEntityDecoratorInfo](arkts-ability-intententitydecoratorinfo-i.md)，
用于描述
[@InsightIntentEntity](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)
装饰器定义的意图实体的信息。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## className

```TypeScript
readonly className: string
```

表示
[@InsightIntentEntity](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)
装饰器修饰的类名。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## entityCategory

```TypeScript
readonly entityCategory: string
```

表示意图实体类别。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## entityId

```TypeScript
readonly entityId: string
```

表示意图实体的ID。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## isQueryable

```TypeScript
readonly isQueryable?: boolean
```

实体是可查询的。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
readonly parameters: Record<string, Object>
```

表示意图实体参数的数据格式声明，用于意图调用时定义实体参数的数据格式。

**类型：** Record<string, Object>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## parentClassName

```TypeScript
readonly parentClassName: string
```

表示
[@InsightIntentEntity](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)
装饰器修饰的类的父类名。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## supportedQueryProperties

```TypeScript
readonly supportedQueryProperties?: string[]
```

支持查询属性。

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

