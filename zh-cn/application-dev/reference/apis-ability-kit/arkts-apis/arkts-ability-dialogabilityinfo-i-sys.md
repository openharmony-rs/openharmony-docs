# DialogAbilityInfo（系统接口）

提供会话组件信息，包括包名、模块名、组件名等信息。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityIconId

```TypeScript
abilityIconId: number
```

表示Ability图标ID。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityLabelId

```TypeScript
abilityLabelId: number
```

表示Ability标签ID。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityName

```TypeScript
abilityName: string
```

表示组件名。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex: number
```

表示应用的分身索引。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleIconId

```TypeScript
bundleIconId: number
```

表示Bundle图标ID。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleLabelId

```TypeScript
bundleLabelId: number
```

表示Bundle标签ID。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

表示包名。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## codePath

```TypeScript
codePath?: string
```

表示应用程序的安装目录。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## installSource

```TypeScript
installSource?: string
```

表示应用程序的安装来源，支持的取值如下：

- pre-installed：表示首次开机时安装的预置应用。
- ota：表示系统升级时新增的预置应用。
- recovery：表示用户卸载后又手动恢复的预置应用。
- bundleName：表示由此包名对应的应用安装。该bundleName代表变量，以实际值为准。
- unknown：表示应用安装来源未知。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName: string
```

表示模块名。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## multiAppMode

```TypeScript
multiAppMode: MultiAppMode
```

表示应用的多开模式。

**类型：** MultiAppMode

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## visible

```TypeScript
visible: boolean
```

表示Ability是否可见。true表示Ability可见，false表示Ability不可见。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

