# FilterAbilityStateType（系统接口）

表示要监听的Ability状态，该类型为枚举。可配合[AppStateFilter]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_过滤想要监听的Ability状态。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-appManager-export enum FilterAbilityStateType--><!--Device-appManager-export enum FilterAbilityStateType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## CREATE

```TypeScript
CREATE = 1 << 0
```

Ability正在创建中，对应 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的 ABILITY\_STATE\_CREATE。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAbilityStateType-CREATE = 1 << 0--><!--Device-FilterAbilityStateType-CREATE = 1 << 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## FOREGROUND

```TypeScript
FOREGROUND = 1 << 1
```

Ability处于前台，对应 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的 ABILITY\_STATE\_FOREGROUND。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAbilityStateType-FOREGROUND = 1 << 1--><!--Device-FilterAbilityStateType-FOREGROUND = 1 << 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## BACKGROUND

```TypeScript
BACKGROUND = 1 << 2
```

Ability处于后台，对应 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的 ABILITY\_STATE\_BACKGROUND。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAbilityStateType-BACKGROUND = 1 << 2--><!--Device-FilterAbilityStateType-BACKGROUND = 1 << 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## DESTROY

```TypeScript
DESTROY = 1 << 3
```

Ability已经销毁，对应 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的 ABILITY\_STATE\_TERMINATED。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

<!--Device-FilterAbilityStateType-DESTROY = 1 << 3--><!--Device-FilterAbilityStateType-DESTROY = 1 << 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

