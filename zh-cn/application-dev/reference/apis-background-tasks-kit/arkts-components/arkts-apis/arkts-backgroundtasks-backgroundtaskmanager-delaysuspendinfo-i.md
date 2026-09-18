# DelaySuspendInfo

短时任务信息。

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## actualDelayTime

```TypeScript
actualDelayTime: number
```

应用实际申请的短时任务时间，单位：ms。<br>Unit:ms

**说明：** 申请时间最长为3分钟，低电量（[BatteryCapacityLevel](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-batteryinfo-batterycapacitylevel-e.md)为LEVEL_LOW）时最长为1分钟。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

## requestId

```TypeScript
requestId: number
```

短时任务的请求ID。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask
