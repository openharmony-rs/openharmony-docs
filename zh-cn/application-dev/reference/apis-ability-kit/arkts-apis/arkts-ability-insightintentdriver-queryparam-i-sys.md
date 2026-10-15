# QueryParam（系统接口）

```TypeScript
interface QueryParam
```

意图实体查询参数，用于筛选设备上符合条件的意图实体。

@typedef QueryParam

**起始版本：** 26.0.0

<!--Device-insightIntentDriver-interface QueryParam--><!--Device-insightIntentDriver-interface QueryParam-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

目标意图实体所属的应用包名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QueryParam-bundleName: string--><!--Device-QueryParam-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## className

```TypeScript
className: string
```

表示[@InsightIntentEntity](arkts-ability-app-ability-insightintentdecorator-insightintententity-d.md#insightintententity)修饰的目标意图实体的类名。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QueryParam-className: string--><!--Device-QueryParam-className: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## intentName

```TypeScript
intentName: string
```

目标意图实体所属的意图名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QueryParam-intentName: string--><!--Device-QueryParam-intentName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName: string
```

目标意图实体所属的模块名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QueryParam-moduleName: string--><!--Device-QueryParam-moduleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## queryEntityParam

```TypeScript
queryEntityParam: insightIntent.QueryEntityParam
```

意图实体查询参数，包含查询模式及查询条件，用于指定意图实体查询方式。

**类型：** [insightIntent.QueryEntityParam](arkts-ability-insightintent-queryentityparam-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QueryParam-queryEntityParam: insightIntent.QueryEntityParam--><!--Device-QueryParam-queryEntityParam: insightIntent.QueryEntityParam-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

目标意图实体所属的用户ID。

> **说明：** 
> 
> 如果调用方应用的用户ID与目标意图实体所属的用户ID不同，则需要申请权限ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QueryParam-userId?: int--><!--Device-QueryParam-userId?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
