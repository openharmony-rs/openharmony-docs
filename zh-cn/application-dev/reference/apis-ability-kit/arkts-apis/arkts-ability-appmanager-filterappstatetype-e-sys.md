# FilterAppStateType（系统接口）

表示要监听的应用状态，该类型为枚举。可配合[AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md)过滤想要监听的应用状态。

**起始版本：** 21

<!--Device-appManager-export enum FilterAppStateType--><!--Device-appManager-export enum FilterAppStateType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## CREATE

```TypeScript
CREATE = 1 << 0
```

应用正在初始化，对应[AppStateData](../../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#属性)中state取值为0的状态。

**起始版本：** 21

<!--Device-FilterAppStateType-CREATE = 1 << 0--><!--Device-FilterAppStateType-CREATE = 1 << 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## FOREGROUND

```TypeScript
FOREGROUND = 1 << 1
```

应用位于前台，对应[AppStateData](../../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#属性)中state取值为2的状态。

**起始版本：** 21

<!--Device-FilterAppStateType-FOREGROUND = 1 << 1--><!--Device-FilterAppStateType-FOREGROUND = 1 << 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## BACKGROUND

```TypeScript
BACKGROUND = 1 << 2
```

应用位于后台，对应[AppStateData](../../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#属性)中state取值为4的状态。

**起始版本：** 21

<!--Device-FilterAppStateType-BACKGROUND = 1 << 2--><!--Device-FilterAppStateType-BACKGROUND = 1 << 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## DESTROY

```TypeScript
DESTROY = 1 << 3
```

应用已退出，对应[AppStateData](../../../../reference/apis-ability-kit/js-apis-inner-application-appStateData.md#属性)中state取值为5的状态。

**起始版本：** 21

<!--Device-FilterAppStateType-DESTROY = 1 << 3--><!--Device-FilterAppStateType-DESTROY = 1 << 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

