# BundleStatsInfo (System API)

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## abilityInFgTotalTime

```TypeScript
abilityInFgTotalTime?: number
```

The total duration, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## abilityPrevAccessTime

```TypeScript
abilityPrevAccessTime?: number
```

The last time when the application was accessed, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## abilityPrevSeenTime

```TypeScript
abilityPrevSeenTime?: number
```

The last time when the application was visible in the foreground, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## abilitySeenTotalTime

```TypeScript
abilitySeenTotalTime?: number
```

The total duration, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex?: number
```

The app index of the application.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName?: string
```

The bundle name of the application.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## fgAbilityAccessTotalTime

```TypeScript
fgAbilityAccessTotalTime?: number
```

The total duration, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## fgAbilityPrevAccessTime

```TypeScript
fgAbilityPrevAccessTime?: number
```

The last time when the foreground application was accessed, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## id

```TypeScript
id: number
```

The identifier of BundleStatsInfo.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## infosBeginTime

```TypeScript
infosBeginTime?: number
```

The time of the first bundle usage record in this `BundleActiveInfo` object, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

## infosEndTime

```TypeScript
infosEndTime?: number
```

The time of the last bundle usage record in this `BundleActiveInfo` object, in milliseconds. <br> Unit:ms

**Type:** number

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.
