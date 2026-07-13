# EfficiencyResourcesRequest（系统接口）

能效资源申请参数。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## cpuLevel

```TypeScript
cpuLevel?: EfficiencyResourcesCpuLevel
```

指定CPU级别，能效资源类型resourceTypes为CPU时该参数用于指定CPU资源大小，系统会在负载空闲时间（例如灭屏场景）分配指定的CPU资源给应用。

**类型：** EfficiencyResourcesCpuLevel

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## isApply

```TypeScript
isApply: boolean
```

申请或释放资源。

- true表示申请资源。
- false表示释放部分资源。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## isPersist

```TypeScript
isPersist?: boolean
```

是否永久持有资源，默认为false。

- true表示永久持有
- false表示有限时间内持有。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## isProcess

```TypeScript
isProcess?: boolean
```

进程或应用申请，默认为false。

- true表示进程申请。
- false表示应用申请。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## reason

```TypeScript
reason: string
```

申请资源原因。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## resourceTypes

```TypeScript
resourceTypes: number
```

申请的资源类型。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## timeOut

```TypeScript
timeOut: number
```

资源使用时间，单位：ms。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

