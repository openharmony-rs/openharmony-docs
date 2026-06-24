# KeepAliveAppType（系统接口）

```TypeScript
export enum KeepAliveAppType
```

表示被保活应用的应用类型。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## ALL

```TypeScript
ALL = 0
```

三方应用和系统应用。此选项只能作为[getKeepAliveBundles](arkts-ability-appmanager-getkeepalivebundles-f-sys.md#getKeepAliveBundles-1)接口的入参被调用。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## THIRD_PARTY

```TypeScript
THIRD_PARTY = 1
```

三方应用。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## SYSTEM

```TypeScript
SYSTEM = 2
```

系统应用。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

