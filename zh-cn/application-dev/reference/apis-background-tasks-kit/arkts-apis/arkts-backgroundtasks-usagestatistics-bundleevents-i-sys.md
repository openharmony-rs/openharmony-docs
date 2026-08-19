# BundleEvents（系统接口）

FA模型的使用信息属性集合。

**起始版本：** 23

<!--Device-usageStatistics-interface BundleEvents--><!--Device-usageStatistics-interface BundleEvents-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## appGroup

```TypeScript
appGroup?: int
```

应用程序的使用优先级组。

**类型：** int

**起始版本：** 23

<!--Device-BundleEvents-appGroup?: int--><!--Device-BundleEvents-appGroup?: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

应用名称。

**类型：** string

**起始版本：** 23

<!--Device-BundleEvents-bundleName?: string--><!--Device-BundleEvents-bundleName?: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## eventId

```TypeScript
eventId?: int
```

应用事件类型。

**类型：** int

**起始版本：** 23

<!--Device-BundleEvents-eventId?: int--><!--Device-BundleEvents-eventId?: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## eventOccurredTime

```TypeScript
eventOccurredTime?: long
```

应用事件发生的时间戳，单位：ms。

**类型：** long

**起始版本：** 23

<!--Device-BundleEvents-eventOccurredTime?: long--><!--Device-BundleEvents-eventOccurredTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## indexOfLink

```TypeScript
indexOfLink?: string
```

快捷方式id。

**类型：** string

**起始版本：** 23

<!--Device-BundleEvents-indexOfLink?: string--><!--Device-BundleEvents-indexOfLink?: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## nameOfClass

```TypeScript
nameOfClass?: string
```

类名。

**类型：** string

**起始版本：** 23

<!--Device-BundleEvents-nameOfClass?: string--><!--Device-BundleEvents-nameOfClass?: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

