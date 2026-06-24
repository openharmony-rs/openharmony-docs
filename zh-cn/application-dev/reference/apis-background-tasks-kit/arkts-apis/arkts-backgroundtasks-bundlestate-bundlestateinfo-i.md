# BundleStateInfo

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## merge

```TypeScript
merge(toMerge: BundleStateInfo): void
```

Merges a specified {@link BundleActiveInfo} object with this {@link BundleActiveInfo} object.
The bundle name of both objects must be the same.

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toMerge | BundleStateInfo | 是 | Indicates the { |

## abilityInFgTotalTime

```TypeScript
abilityInFgTotalTime?: number
```

The total duration, in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## abilityPrevAccessTime

```TypeScript
abilityPrevAccessTime?: number
```

The last time when the application was accessed, in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## abilityPrevSeenTime

```TypeScript
abilityPrevSeenTime?: number
```

The last time when the application was visible in the foreground, in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## abilitySeenTotalTime

```TypeScript
abilitySeenTotalTime?: number
```

The total duration when the application was visible in the foreground, in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## bundleName

```TypeScript
bundleName?: string
```

The bundle name of the application.

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## fgAbilityAccessTotalTime

```TypeScript
fgAbilityAccessTotalTime?: number
```

The total duration when the foreground application was accessed, in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## fgAbilityPrevAccessTime

```TypeScript
fgAbilityPrevAccessTime?: number
```

The last time when the foreground application was accessed, in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## id

```TypeScript
id: number
```

The identifier of BundleStateInfo.

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## infosBeginTime

```TypeScript
infosBeginTime?: number
```

The time of the first bundle usage record in this {@code BundleActiveInfo} object,
in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## infosEndTime

```TypeScript
infosEndTime?: number
```

The time of the last bundle usage record in this {@code BundleActiveInfo} object,
in milliseconds.
<br> Unit:ms

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

