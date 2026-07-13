# WorkInfo

延迟任务的具体信息, 用于设置延迟任务的触发条件等。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## abilityName

```TypeScript
abilityName: string
```

包内ability名称。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## batteryLevel

```TypeScript
batteryLevel?: number
```

电量。

取值范围：[0, 100]

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## batteryStatus

```TypeScript
batteryStatus?: BatteryStatus
```

电池状态。

**类型：** BatteryStatus

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## bundleName

```TypeScript
bundleName: string
```

延迟任务所在应用的包名。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## chargerType

```TypeScript
chargerType?: ChargingType
```

充电类型。

**类型：** ChargingType

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## earliestStartTime

```TypeScript
earliestStartTime?: number
```

任务首次执行时间距离任务申请时间的间隔，单位：ms，默认为0，范围大于等于0。
取值范围为全体整数。

**类型：** number

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## idleWaitTime

```TypeScript
idleWaitTime?: number
```

空闲等待时间，单位：ms。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## isCharging

```TypeScript
isCharging?: boolean
```

是否充电，默认为false。

- true表示充电触发延迟任务回调。
- false表示不充电触发延迟任务回调。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## isDeepIdle

```TypeScript
isDeepIdle?: boolean
```

是否要求设备进入空闲状态，默认为false。

- true表示需要。
- false表示不需要。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## isPersisted

```TypeScript
isPersisted?: boolean
```

注册的延迟任务是否可保存在系统中，默认为false。

- true表示可保存，即系统重启后，任务可恢复。
- false表示不可保存。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## isRepeat

```TypeScript
isRepeat?: boolean
```

是否循环任务，默认为false。

- true表示循环任务。
- false表示非循环任务。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## networkType

```TypeScript
networkType?: NetworkType
```

网络类型。

**类型：** NetworkType

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## parameters

```TypeScript
parameters?: Record<string, number | number | string | boolean>
```

携带参数信息。

**类型：** Record<string, number | number | string | boolean>

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## repeatCount

```TypeScript
repeatCount?: number
```

循环次数。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## repeatCycleTime

```TypeScript
repeatCycleTime?: number
```

循环间隔，单位：ms。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## storageRequest

```TypeScript
storageRequest?: StorageRequest
```

存储状态。

**类型：** StorageRequest

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## workId

```TypeScript
workId: number
```

延迟任务ID。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

