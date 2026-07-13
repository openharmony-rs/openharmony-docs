# ResourceType（系统接口）

能效资源类型。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## CPU

```TypeScript
CPU = 1
```

CPU资源，申请后应用进程不被挂起。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## COMMON_EVENT

```TypeScript
COMMON_EVENT = 1 << 1
```

公共事件资源，申请后应用进程被挂起后，可以收到公共事件。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## TIMER

```TypeScript
TIMER = 1 << 2
```

计时器，申请后应用进程被挂起后，Timer仍然可以唤醒应用。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## WORK_SCHEDULER

```TypeScript
WORK_SCHEDULER = 1 << 3
```

延迟任务资源，申请后延迟任务管控变宽松。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## BLUETOOTH

```TypeScript
BLUETOOTH = 1 << 4
```

蓝牙资源，申请后应用进程被挂起后，蓝牙相关事件仍然可以唤醒应用。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## GPS

```TypeScript
GPS = 1 << 5
```

GPS资源，申请后应用进程被挂起后，GPS相关事件可以唤醒应用。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## AUDIO

```TypeScript
AUDIO = 1 << 6
```

音频资源，有音频播放时对应的应用进程不被挂起。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## RUNNING_LOCK

```TypeScript
RUNNING_LOCK = 1 << 7
```

RUNNING_LOCK资源，申请后挂起状态不会代理RUNNING_BACKGROUND锁。

**起始版本：** 10

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

## SENSOR

```TypeScript
SENSOR = 1 << 8
```

申请后不拦截Sensor回调。

**起始版本：** 10

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**系统接口：** 此接口为系统接口。

