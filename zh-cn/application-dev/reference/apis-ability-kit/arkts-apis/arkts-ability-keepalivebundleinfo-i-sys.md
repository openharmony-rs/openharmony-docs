# KeepAliveBundleInfo（系统接口）

定义应用保活信息，可以通过[getKeepAliveBundles](arkts-ability-getkeepalivebundles-f-sys.md#getkeepalivebundles-1)或
[getKeepAliveAppServiceExtensions](arkts-ability-getkeepaliveappserviceextensions-f-sys.md#getkeepaliveappserviceextensions-1)获取。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## allowUserToCancel

```TypeScript
allowUserToCancel?: boolean
```

表示是否允许用户取消保活。true表示允许，false表示不允许。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

Bundle名称。

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## setter

```TypeScript
setter: KeepAliveSetter
```

表示应用保活设置者类型。

**类型：** KeepAliveSetter

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## setterUserId

```TypeScript
setterUserId?: number
```

应用保活设置者的用户ID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: KeepAliveAppType
```

表示被保活应用的应用类型。

**类型：** KeepAliveAppType

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

