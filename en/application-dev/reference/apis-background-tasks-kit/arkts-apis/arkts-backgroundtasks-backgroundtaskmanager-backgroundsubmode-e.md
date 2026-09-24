# BackgroundSubMode

```TypeScript
export enum BackgroundSubMode
```

Defines the subtype of a continuous task.

**Since:** 16

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## CAR_KEY

```TypeScript
CAR_KEY = 1
```

Car key.

**NOTE:** 

1. The car key subtype takes effect only when a continuous task of the BLUETOOTH_INTERACTION type is requested.
2. Continuous tasks of this type cannot be updated through the [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) API.

**Since:** 16

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
