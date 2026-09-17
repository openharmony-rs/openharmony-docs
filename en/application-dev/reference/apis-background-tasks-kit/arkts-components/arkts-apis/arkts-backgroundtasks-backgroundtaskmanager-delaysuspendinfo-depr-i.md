# DelaySuspendInfo

Provides the information about the suspension delay.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [DelaySuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-delaysuspendinfo-i.md)

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## Modules to Import

```TypeScript
```

## actualDelayTime

```TypeScript
actualDelayTime: number
```

Actual suspension delay duration of the application, in milliseconds.

The default duration is 180000 when the battery level is higher than or equal to the broadcast low battery level and 60000 when the battery level is lower than the broadcast low battery level.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** DelaySuspendInfo

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## requestId

```TypeScript
requestId: number
```

ID of the suspension delay request.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** DelaySuspendInfo

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask
