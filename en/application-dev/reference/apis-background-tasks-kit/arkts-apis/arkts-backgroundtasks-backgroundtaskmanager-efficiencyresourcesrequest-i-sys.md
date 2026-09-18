# EfficiencyResourcesRequest (System API)

Describes the parameters for requesting efficiency resources.

**Since:** 9

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

## isApply

```TypeScript
isApply: boolean
```

Whether the request is used to apply for resources.

- **true**: The request is used to apply for resources.  
- **false**: The request is used to release resources.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## isPersist

```TypeScript
isPersist?: boolean
```

Whether the resource is permanently held. The default value is **false**.

- **true**: The resource is permanently held.  
- **false**: The resource is held for a limited period of time.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## isProcess

```TypeScript
isProcess?: boolean
```

Whether the request is initiated by a process. The default value is **false**.

- **true**: The request is initiated by a process.  
- **false**: The request is initiated by an application.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## reason

```TypeScript
reason: string
```

Reason for requesting the resource.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## resourceTypes

```TypeScript
resourceTypes: number
```

Type of the resource to request.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## timeOut

```TypeScript
timeOut: number
```

Duration for which the resource will be used, in milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.
