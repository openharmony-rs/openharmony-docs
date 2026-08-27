# MissionInfo（系统接口）

表示任务的详细信息，可以通过 [getMissionInfo](arkts-ability-missionmanager-getmissioninfo-f-sys.md) 获取。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## abilityState

```TypeScript
abilityState: number
```

表示此任务的能力状态。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## continuable

```TypeScript
continuable: boolean
```

表示任务是否可以迁移。返回true表示可以迁移，返回false表示不可迁移。

**类型：** boolean

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## iconPath

```TypeScript
iconPath: string
```

表示任务的图标路径。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## label

```TypeScript
label: string
```

表示任务的标签，用于在任务列表中显示的任务名称。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## lockedState

```TypeScript
lockedState: boolean
```

表示锁定状态。返回true表示锁定状态，返回false表示未锁定状态。

**类型：** boolean

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## missionId

```TypeScript
missionId: number
```

表示任务ID。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## runningState

```TypeScript
runningState: number
```

表示运行状态。0表示启用，任务活跃有效，对应的Ability正在运行或可恢复到前台；-1表示未启用，任务已关闭、销毁或不可恢复。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp: string
```

表示任务的最近创建或更新时间。单位：ns

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## unclearable

```TypeScript
unclearable: boolean
```

表示任务是否可以被用户手动删除。返回true表示可以被用户手动删除，返回false表示不可被用户手动删除。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want: Want
```

表示任务的Want信息。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 8

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。
