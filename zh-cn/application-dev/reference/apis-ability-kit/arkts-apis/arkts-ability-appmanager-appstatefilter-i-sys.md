# AppStateFilter（系统接口）

应用生命周期变化事件的过滤器，可作为 [on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的参数用 于筛选所需监听的应用生命周期变化事件。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-appManager-export interface AppStateFilter--><!--Device-appManager-export interface AppStateFilter-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityStateTypes

```TypeScript
abilityStateTypes?: int
```

表示要监听的Ability状态。取值范围是： - 0：表示不监听任何Ability状态。 - \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中枚举的按位或运算组合：例如 "appManager.FilterAbilityStateType.CREATE | appManager.FilterAbilityStateType.FOREGROUND" ，表示同时监听Ability的创建状态和前台状态。 - 如果该项不设置，则默认监听所有的Ability状态。

**类型：** int

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-AppStateFilter-abilityStateTypes?: int--><!--Device-AppStateFilter-abilityStateTypes?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## appStateTypes

```TypeScript
appStateTypes?: int
```

表示要监听的应用状态。 取值范围是： - 0：表示不监听任何应用状态。 - \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中枚举的按位或运算组合：例如 "appManager.FilterAppStateType.CREATE | appManager.FilterAppStateType.FOREGROUND" ，表示同时监听应用的创建状态和前台状态。 - 如果该项不设置，则默认监听所有的应用状态。

**类型：** int

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-AppStateFilter-appStateTypes?: int--><!--Device-AppStateFilter-appStateTypes?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleTypes

```TypeScript
bundleTypes?: int
```

表示要监听的应用类型。取值范围是： - 0：表示不监听任何类型的应用。 - \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中枚举的按位或运算组合：例如 "appManager.FilterBundleType.APP | appManager.FilterBundleType.ATOMIC\_SERVICE" ，表示同时监听应用和原子化服务的生命周期变化事件。 - 如果该项不设置，则默认监听所有的应用类型。

**类型：** int

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-AppStateFilter-bundleTypes?: int--><!--Device-AppStateFilter-bundleTypes?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## callbacks

```TypeScript
callbacks?: int
```

表示要监听的回调函数。取值范围是： - 0：表示不监听任何回调函数。 - \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中枚举的按位或运算组合：例如 "appManager.FilterCallback.ON\_ABILITY\_STATE\_CHANGED | appManager.FilterCallback.ON\_PROCESS\_STATE\_CHANGED" ，表示同时监听 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ 和 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ 。 - 如果该项不设置，则默认监听\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_中对应的所有回调函数。

**类型：** int

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-AppStateFilter-callbacks?: int--><!--Device-AppStateFilter-callbacks?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## processStateTypes

```TypeScript
processStateTypes?: int
```

表示要监听的进程状态。取值范围是： - 0：表示不监听任何进程状态。 - \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中枚举的按位或运算组合：例如 "appManager.FilterProcessStateType.CREATE | appManager.FilterProcessStateType.FOREGROUND" ，表示同时监听进程的创建状态和前台状态。 - 如果该项不设置，则默认监听所有的进程状态。

**类型：** int

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-AppStateFilter-processStateTypes?: int--><!--Device-AppStateFilter-processStateTypes?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

