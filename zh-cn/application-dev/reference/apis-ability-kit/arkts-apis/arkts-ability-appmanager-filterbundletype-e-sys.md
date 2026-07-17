# FilterBundleType（系统接口）

表示要监听的的应用类型，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的应用类型。

**起始版本：** 21

<!--Device-appManager-export enum FilterBundleType--><!--Device-appManager-export enum FilterBundleType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## APP

```TypeScript
APP = 1 << 0
```

应用。

**起始版本：** 21

<!--Device-FilterBundleType-APP = 1 << 0--><!--Device-FilterBundleType-APP = 1 << 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## ATOMIC_SERVICE

```TypeScript
ATOMIC_SERVICE = 1 << 1
```

原子化服务。

**起始版本：** 21

<!--Device-FilterBundleType-ATOMIC_SERVICE = 1 << 1--><!--Device-FilterBundleType-ATOMIC_SERVICE = 1 << 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

