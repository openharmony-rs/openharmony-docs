# FilterAppStateType（系统接口）

表示要监听的应用状态，该类型为枚举。可配合[AppStateFilter]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_过滤想要监听的应用状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-appManager-export enum FilterAppStateType--><!--Device-appManager-export enum FilterAppStateType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## CREATE

```TypeScript
CREATE = 1 << 0
```

应用正在初始化，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state 取值为0的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAppStateType-CREATE = 1 << 0--><!--Device-FilterAppStateType-CREATE = 1 << 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## FOREGROUND

```TypeScript
FOREGROUND = 1 << 1
```

应用位于前台，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state取 值为2的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAppStateType-FOREGROUND = 1 << 1--><!--Device-FilterAppStateType-FOREGROUND = 1 << 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## BACKGROUND

```TypeScript
BACKGROUND = 1 << 2
```

应用位于后台，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state取 值为4的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAppStateType-BACKGROUND = 1 << 2--><!--Device-FilterAppStateType-BACKGROUND = 1 << 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## DESTROY

```TypeScript
DESTROY = 1 << 3
```

应用已退出，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state取值 为5的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAppStateType-DESTROY = 1 << 3--><!--Device-FilterAppStateType-DESTROY = 1 << 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

