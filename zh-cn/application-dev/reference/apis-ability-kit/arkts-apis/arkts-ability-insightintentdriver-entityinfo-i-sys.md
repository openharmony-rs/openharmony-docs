# EntityInfo（系统接口）

EntityInfo继承自[IntentEntityDecoratorInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_， 用于描述 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 装饰器定义的意图实体的信息。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-insightIntentDriver-interface EntityInfo--><!--Device-insightIntentDriver-interface EntityInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## className

```TypeScript
readonly className: string
```

表示 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 装饰器修饰的类名。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntityInfo-readonly className: string--><!--Device-EntityInfo-readonly className: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## entityCategory

```TypeScript
readonly entityCategory: string
```

表示意图实体类别。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntityInfo-readonly entityCategory: string--><!--Device-EntityInfo-readonly entityCategory: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## entityId

```TypeScript
readonly entityId: string
```

表示意图实体的ID。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntityInfo-readonly entityId: string--><!--Device-EntityInfo-readonly entityId: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## isQueryable

```TypeScript
readonly isQueryable?: boolean
```

实体是可查询的。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntityInfo-readonly isQueryable?: boolean--><!--Device-EntityInfo-readonly isQueryable?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
readonly parameters: Record<string, Object>
```

表示意图实体参数的数据格式声明，用于意图调用时定义实体参数的数据格式。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntityInfo-readonly parameters: Record<string, Object>--><!--Device-EntityInfo-readonly parameters: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## parentClassName

```TypeScript
readonly parentClassName: string
```

表示 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 装饰器修饰的类的父类名。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntityInfo-readonly parentClassName: string--><!--Device-EntityInfo-readonly parentClassName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## supportedQueryProperties

```TypeScript
readonly supportedQueryProperties?: string[]
```

支持查询属性。

**类型：** string[]

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EntityInfo-readonly supportedQueryProperties?: string[]--><!--Device-EntityInfo-readonly supportedQueryProperties?: string[]-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

