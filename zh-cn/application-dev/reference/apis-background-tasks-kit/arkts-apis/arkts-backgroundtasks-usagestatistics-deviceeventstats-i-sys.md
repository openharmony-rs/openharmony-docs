# DeviceEventStats（系统接口）

FA模型的使用信息属性集合。

**起始版本：** 9

<!--Device-usageStatistics-interface DeviceEventStats--><!--Device-usageStatistics-interface DeviceEventStats-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## count

```TypeScript
count: number
```

应用通知次数或者系统事件触发次数。

**类型：** number

**起始版本：** 9

<!--Device-DeviceEventStats-count: int--><!--Device-DeviceEventStats-count: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId: number
```

应用事件类型。

**类型：** number

**起始版本：** 9

<!--Device-DeviceEventStats-eventId: int--><!--Device-DeviceEventStats-eventId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

通知应用包名或者系统事件名。

**类型：** string

**起始版本：** 9

<!--Device-DeviceEventStats-name: string--><!--Device-DeviceEventStats-name: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

