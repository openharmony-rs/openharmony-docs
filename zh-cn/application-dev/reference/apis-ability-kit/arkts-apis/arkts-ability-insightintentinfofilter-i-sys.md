# InsightIntentInfoFilter（系统接口）

意图筛选器，描述目标意图的筛选条件，用于筛选设备上符合条件的意图。

**起始版本：** 23

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

目标意图所属的应用包名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## intentFlags

```TypeScript
intentFlags: number
```

意图信息（[InsightIntentInfo](arkts-ability-insightintentinfo-i-sys.md)）的标识，用于表示查询全量意图信息或者简要意图信息，取值可参考
[GetInsightIntentFlag](arkts-ability-getinsightintentflag-e-sys.md)。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## intentName

```TypeScript
intentName?: string
```

目标意图名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName?: string
```

目标意图所属的模块名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

目标意图所属的用户ID。

**说明：**

如果调用方应用的用户ID与目标意图所属的用户ID不同，则需要申请权限`ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS`。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

