# BundleStatsInfo（系统接口）

FA模型的使用信息属性集合。

**起始版本：** 9

<!--Device-usageStatistics-interface BundleStatsInfo--><!--Device-usageStatistics-interface BundleStatsInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## abilityInFgTotalTime

```TypeScript
abilityInFgTotalTime?: number
```

应用在前台可见的总时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-abilityInFgTotalTime?: long--><!--Device-BundleStatsInfo-abilityInFgTotalTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## abilityPrevAccessTime

```TypeScript
abilityPrevAccessTime?: number
```

应用最后一次使用的时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-abilityPrevAccessTime?: long--><!--Device-BundleStatsInfo-abilityPrevAccessTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## abilityPrevSeenTime

```TypeScript
abilityPrevSeenTime?: number
```

应用最后一次在前台可见的时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-abilityPrevSeenTime?: long--><!--Device-BundleStatsInfo-abilityPrevSeenTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## abilitySeenTotalTime

```TypeScript
abilitySeenTotalTime?: number
```

应用在前台可见的总时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-abilitySeenTotalTime?: long--><!--Device-BundleStatsInfo-abilitySeenTotalTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex?: number
```

应用程序的索引。

**类型：** number

**起始版本：** 15

<!--Device-BundleStatsInfo-appIndex?: int--><!--Device-BundleStatsInfo-appIndex?: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

应用包名。

**类型：** string

**起始版本：** 9

<!--Device-BundleStatsInfo-bundleName?: string--><!--Device-BundleStatsInfo-bundleName?: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## fgAbilityAccessTotalTime

```TypeScript
fgAbilityAccessTotalTime?: number
```

应用在前台可见的总时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-fgAbilityAccessTotalTime?: long--><!--Device-BundleStatsInfo-fgAbilityAccessTotalTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## fgAbilityPrevAccessTime

```TypeScript
fgAbilityPrevAccessTime?: number
```

应用最后一次访问前台的时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-fgAbilityPrevAccessTime?: long--><!--Device-BundleStatsInfo-fgAbilityPrevAccessTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: number
```

用户id。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-id: int--><!--Device-BundleStatsInfo-id: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## infosBeginTime

```TypeScript
infosBeginTime?: number
```

BundleActiveInfo对象中第一条应用使用统计的记录时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-infosBeginTime?: long--><!--Device-BundleStatsInfo-infosBeginTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

## infosEndTime

```TypeScript
infosEndTime?: number
```

BundleActiveInfo对象中最后一条应用使用统计的记录时间，单位：ms。

**类型：** number

**起始版本：** 9

<!--Device-BundleStatsInfo-infosEndTime?: long--><!--Device-BundleStatsInfo-infosEndTime?: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

