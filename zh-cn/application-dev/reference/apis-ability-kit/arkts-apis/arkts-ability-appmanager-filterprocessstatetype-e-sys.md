# FilterProcessStateType（系统接口）

表示要监听的进程状态，该类型为枚举。可配合[AppStateFilter]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_过滤想要监听的进程状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-appManager-export enum FilterProcessStateType--><!--Device-appManager-export enum FilterProcessStateType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## CREATE

```TypeScript
CREATE = 1 << 0
```

进程刚创建完成，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state取值 为0的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterProcessStateType-CREATE = 1 << 0--><!--Device-FilterProcessStateType-CREATE = 1 << 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## FOREGROUND

```TypeScript
FOREGROUND = 1 << 1
```

进程处于前台，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state取值为 2的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterProcessStateType-FOREGROUND = 1 << 1--><!--Device-FilterProcessStateType-FOREGROUND = 1 << 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## BACKGROUND

```TypeScript
BACKGROUND = 1 << 2
```

进程处于后台，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state取值为 4的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterProcessStateType-BACKGROUND = 1 << 2--><!--Device-FilterProcessStateType-BACKGROUND = 1 << 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## DESTROY

```TypeScript
DESTROY = 1 << 3
```

进程已终止，对应\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中state取值为5 的状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterProcessStateType-DESTROY = 1 << 3--><!--Device-FilterProcessStateType-DESTROY = 1 << 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

