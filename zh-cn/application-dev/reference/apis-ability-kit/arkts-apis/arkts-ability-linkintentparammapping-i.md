# LinkIntentParamMapping

LinkIntentParamMapping是
[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)
装饰器的意图参数和uri信息的映射。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramCategory

```TypeScript
paramCategory?: LinkParamCategory
```

表示意图参数类别。

若意图参数类别取值为[LINK](#linkparamcategory)，系统获取paramName字段对应的意图参数映射名称，并将该意图参数映射名称拼接到uri链接的末尾(以键值对的形式key=value，key为意图参数映射名
称，value为意图参数值)。

若意图参数类别为[WANT](#linkparamcategory)，系统获取paramName字段对应的意图参数映射名称，并将该意图参数映射名称及取值通过[Want](./js-apis-app-ability-want.md)
的parameters字段进行传递。

**类型：** LinkParamCategory

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramMappingName

```TypeScript
paramMappingName?: string
```

表示意图参数映射名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## paramName

```TypeScript
paramName: string
```

表示意图参数的名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

