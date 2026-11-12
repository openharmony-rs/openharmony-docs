# FreezeState（系统接口）

```TypeScript
export enum FreezeState
```

枚举应用程序的冻结状态。

**起始版本：** 26.1.0

<!--Device-suspendManager-export enum FreezeState--><!--Device-suspendManager-export enum FreezeState-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

## ACTIVE

```TypeScript
ACTIVE = 0
```

应用处于激活状态。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FreezeState-ACTIVE = 0--><!--Device-FreezeState-ACTIVE = 0-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

## DOZE

```TypeScript
DOZE = 1
```

应用处于doze状态，进入冻结过程，但尚未完全冻结。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FreezeState-DOZE = 1--><!--Device-FreezeState-DOZE = 1-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

## FROZEN

```TypeScript
FROZEN = 2
```

应用处于冻结状态。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FreezeState-FROZEN = 2--><!--Device-FreezeState-FROZEN = 2-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。
