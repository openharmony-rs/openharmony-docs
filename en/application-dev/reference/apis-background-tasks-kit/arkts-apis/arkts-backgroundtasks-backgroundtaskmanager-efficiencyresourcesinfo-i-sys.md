# EfficiencyResourcesInfo (System API)

Defines the efficiency resource information.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## cpuLevel

```TypeScript
cpuLevel?: EfficiencyResourcesCpuLevel
```

CPU level. If **resourceTypes** is set to **CPU**, this parameter specifies the CPU resource size. The system allocates the specified CPU resources to the application during the idle time of load (for example, when the screen is off).

**Type:** [EfficiencyResourcesCpuLevel](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcescpulevel-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## isForProcess

```TypeScript
isForProcess: boolean
```

Whether the resource is requested by a process or an application. The value **true** indicates that the resource is requested by a process. The value **false** indicates that the resource is requested by an application.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## isPersistent

```TypeScript
isPersistent: boolean
```

Whether the resource is permanently held. The default value is **false**. The value **true** indicates the resource is permanently held. The value **false** indicates that the resource is held within a limited time.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## pid

```TypeScript
pid: number
```

Application PID.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## reason

```TypeScript
reason: string
```

Reason for requesting the resource.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## resourceTypes

```TypeScript
resourceTypes: number
```

Enumerates the efficiency resource types.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## timeout

```TypeScript
timeout: number
```

Timeout, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

Application UID.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.
