# DelaySuspendInfo

Defines the information about the transient task.

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## actualDelayTime

```TypeScript
actualDelayTime: number
```

Actual duration of the transient task requested by the application, in milliseconds. <br>Unit:ms

Note: The maximum duration of a transient task is 3 minutes in normal cases. In the case of a low battery ([BatteryCapacityLevel](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-batteryinfo-batterycapacitylevel-e.md) set to **LEVEL_LOW**), the maximum duration is decreased to 1 minute.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## requestId

```TypeScript
requestId: number
```

Request ID of the transient task.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask
