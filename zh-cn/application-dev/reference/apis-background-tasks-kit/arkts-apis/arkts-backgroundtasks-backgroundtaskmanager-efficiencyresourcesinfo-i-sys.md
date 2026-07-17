# EfficiencyResourcesInfo（系统接口）

能效资源信息。

**起始版本：** 20

<!--Device-backgroundTaskManager-interface EfficiencyResourcesInfo--><!--Device-backgroundTaskManager-interface EfficiencyResourcesInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## cpuLevel

```TypeScript
cpuLevel?: EfficiencyResourcesCpuLevel
```

指定CPU级别，能效资源类型resourceTypes为CPU时该参数用于指定CPU资源大小，系统会在负载空闲时间（例如灭屏场景）分配指定的CPU资源给应用。

**类型：** EfficiencyResourcesCpuLevel

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EfficiencyResourcesInfo-cpuLevel?: EfficiencyResourcesCpuLevel--><!--Device-EfficiencyResourcesInfo-cpuLevel?: EfficiencyResourcesCpuLevel-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## isForProcess

```TypeScript
isForProcess: boolean
```

进程或应用申请，取值为true表示进程申请。取值为false表示应用申请。

**类型：** boolean

**起始版本：** 20

<!--Device-EfficiencyResourcesInfo-isForProcess: boolean--><!--Device-EfficiencyResourcesInfo-isForProcess: boolean-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## isPersistent

```TypeScript
isPersistent: boolean
```

是否永久持有资源，默认为false。取值为true表示永久持有。取值为false表示有限时间内持有。

**类型：** boolean

**起始版本：** 20

<!--Device-EfficiencyResourcesInfo-isPersistent: boolean--><!--Device-EfficiencyResourcesInfo-isPersistent: boolean-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## pid

```TypeScript
pid: number
```

应用进程的PID。

**类型：** number

**起始版本：** 20

<!--Device-EfficiencyResourcesInfo-pid: int--><!--Device-EfficiencyResourcesInfo-pid: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## reason

```TypeScript
reason: string
```

申请资源原因。

**类型：** string

**起始版本：** 20

<!--Device-EfficiencyResourcesInfo-reason: string--><!--Device-EfficiencyResourcesInfo-reason: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## resourceTypes

```TypeScript
resourceTypes: number
```

能效资源类型。

**类型：** number

**起始版本：** 20

<!--Device-EfficiencyResourcesInfo-resourceTypes: int--><!--Device-EfficiencyResourcesInfo-resourceTypes: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## timeout

```TypeScript
timeout: number
```

超时时间，单位：ms。

**类型：** number

**起始版本：** 20

<!--Device-EfficiencyResourcesInfo-timeout: int--><!--Device-EfficiencyResourcesInfo-timeout: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

应用的UID。

**类型：** number

**起始版本：** 20

<!--Device-EfficiencyResourcesInfo-uid: int--><!--Device-EfficiencyResourcesInfo-uid: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

