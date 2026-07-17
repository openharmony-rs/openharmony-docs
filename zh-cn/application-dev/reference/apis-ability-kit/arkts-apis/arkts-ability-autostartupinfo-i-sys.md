# AutoStartupInfo（系统接口）

定义开机自启动应用组件信息。

**起始版本：** 11

<!--Device-unnamed-export interface AutoStartupInfo--><!--Device-unnamed-export interface AutoStartupInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityName

```TypeScript
abilityName: string
```

应用程序的Ability名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-abilityName: string--><!--Device-AutoStartupInfo-abilityName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityTypeName

```TypeScript
abilityTypeName?: string
```

应用程序的Ability类型。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-abilityTypeName?: string--><!--Device-AutoStartupInfo-abilityTypeName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## appCloneIndex

```TypeScript
appCloneIndex?: number
```

分身应用索引。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-appCloneIndex?: int--><!--Device-AutoStartupInfo-appCloneIndex?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用程序的Bundle名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-bundleName: string--><!--Device-AutoStartupInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## canUserModify

```TypeScript
readonly canUserModify?: boolean
```

表示是否允许开发者修改此应用的开机自启动状态，true表示允许，false表示不允许。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-readonly canUserModify?: boolean--><!--Device-AutoStartupInfo-readonly canUserModify?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName?: string
```

应用程序的Module名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-moduleName?: string--><!--Device-AutoStartupInfo-moduleName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## setterUserId

```TypeScript
readonly setterUserId?: number
```

设置者的用户ID，记录了将当前应用设置为开机自启动的用户ID。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-readonly setterUserId?: int--><!--Device-AutoStartupInfo-readonly setterUserId?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
readonly userId?: number
```

应用程序所属的用户ID，用于区分同一设备上不同用户账号下的应用。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoStartupInfo-readonly userId?: int--><!--Device-AutoStartupInfo-readonly userId?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

