# ResourceType (System API)

```TypeScript
export enum ResourceType
```

Enumerates the efficiency resource types.

**Since:** 9

<!--Device-backgroundTaskManager-export enum ResourceType--><!--Device-backgroundTaskManager-export enum ResourceType-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## AUDIO

```TypeScript
AUDIO = 1 << 6
```

Audio resource. Such type of resource prevents an application from being suspended when the application has an audio being played.

**Since:** 9

<!--Device-ResourceType-AUDIO = 1 << 6--><!--Device-ResourceType-AUDIO = 1 << 6-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## BLUETOOTH

```TypeScript
BLUETOOTH = 1 << 4
```

Bluetooth resource. Such type of resource ensures that an application in the suspended state can be woken up by Bluetooth-related events.

**Since:** 9

<!--Device-ResourceType-BLUETOOTH = 1 << 4--><!--Device-ResourceType-BLUETOOTH = 1 << 4-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## COMMON_EVENT

```TypeScript
COMMON_EVENT = 1 << 1
```

Common event resource. Such type of resource ensures that an application in the suspended state can receive common events.

**Since:** 9

<!--Device-ResourceType-COMMON_EVENT = 1 << 1--><!--Device-ResourceType-COMMON_EVENT = 1 << 1-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## CPU

```TypeScript
CPU = 1
```

CPU resource. Such type of resource prevents an application from being suspended.

**Since:** 9

<!--Device-ResourceType-CPU = 1--><!--Device-ResourceType-CPU = 1-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## GPS

```TypeScript
GPS = 1 << 5
```

GPS resource. Such type of resource ensures that an application in the suspended state can be woken up by GPS- related events.

**Since:** 9

<!--Device-ResourceType-GPS = 1 << 5--><!--Device-ResourceType-GPS = 1 << 5-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## RUNNING_LOCK

```TypeScript
RUNNING_LOCK = 1 << 7
```

RUNNING_LOCK resources are not proxied when the application is suspended.

**Since:** 10

<!--Device-ResourceType-RUNNING_LOCK = 1 << 7--><!--Device-ResourceType-RUNNING_LOCK = 1 << 7-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## SENSOR

```TypeScript
SENSOR = 1 << 8
```

Sensor callbacks are not intercepted.

**Since:** 10

<!--Device-ResourceType-SENSOR = 1 << 8--><!--Device-ResourceType-SENSOR = 1 << 8-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## TIMER

```TypeScript
TIMER = 1 << 2
```

Timer resource. Such type of resource ensures that an application in the suspended state can be woken up by system timers.

**Since:** 9

<!--Device-ResourceType-TIMER = 1 << 2--><!--Device-ResourceType-TIMER = 1 << 2-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

## WORK_SCHEDULER

```TypeScript
WORK_SCHEDULER = 1 << 3
```

Deferred task resource. Such type of resource provides a loose control policy for an application.

**Since:** 9

<!--Device-ResourceType-WORK_SCHEDULER = 1 << 3--><!--Device-ResourceType-WORK_SCHEDULER = 1 << 3-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.
