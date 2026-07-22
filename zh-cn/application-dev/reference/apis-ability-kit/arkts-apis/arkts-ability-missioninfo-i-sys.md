# MissionInfo（系统接口）

表示任务的详细信息，可以通过[getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md#getmissioninfo)获取。

**起始版本：** 8

<!--Device-unnamed-export interface MissionInfo--><!--Device-unnamed-export interface MissionInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## abilityState

```TypeScript
abilityState: number
```

表示此任务的能力状态。

**类型：** number

**起始版本：** 10

<!--Device-MissionInfo-abilityState: int--><!--Device-MissionInfo-abilityState: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## continuable

```TypeScript
continuable: boolean
```

表示任务是否可以迁移。返回true表示可以迁移，返回false表示不可迁移。

**类型：** boolean

**起始版本：** 8

<!--Device-MissionInfo-continuable: boolean--><!--Device-MissionInfo-continuable: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## iconPath

```TypeScript
iconPath: string
```

表示任务的图标路径。

**类型：** string

**起始版本：** 8

<!--Device-MissionInfo-iconPath: string--><!--Device-MissionInfo-iconPath: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## label

```TypeScript
label: string
```

表示任务的标签。

**类型：** string

**起始版本：** 8

<!--Device-MissionInfo-label: string--><!--Device-MissionInfo-label: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## lockedState

```TypeScript
lockedState: boolean
```

表示锁定状态。返回true表示锁定状态，返回false表示未锁定状态。

**类型：** boolean

**起始版本：** 8

<!--Device-MissionInfo-lockedState: boolean--><!--Device-MissionInfo-lockedState: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## missionId

```TypeScript
missionId: number
```

表示任务ID。

**类型：** number

**起始版本：** 8

<!--Device-MissionInfo-missionId: int--><!--Device-MissionInfo-missionId: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## runningState

```TypeScript
runningState: number
```

表示运行状态。

**类型：** number

**起始版本：** 8

<!--Device-MissionInfo-runningState: int--><!--Device-MissionInfo-runningState: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp: string
```

表示任务的最近创建或更新时间。

**类型：** string

**起始版本：** 8

<!--Device-MissionInfo-timestamp: string--><!--Device-MissionInfo-timestamp: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## unclearable

```TypeScript
unclearable: boolean
```

表示任务是否可以被用户手动删除。返回true表示可以被用户手动删除，返回false表示不可被用户手动删除。

**类型：** boolean

**起始版本：** 10

<!--Device-MissionInfo-unclearable: boolean--><!--Device-MissionInfo-unclearable: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want: Want
```

表示任务的Want信息。

**类型：** Want

**起始版本：** 8

<!--Device-MissionInfo-want: Want--><!--Device-MissionInfo-want: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

