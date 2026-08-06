# BundleStateInfo

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-bundleState-interface BundleStateInfo--><!--Device-bundleState-interface BundleStateInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## merge

```TypeScript
merge(toMerge: BundleStateInfo): void
```

Merges a specified \_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ object with this \_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ object. The bundle name of both objects must be the same.

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-merge(toMerge: BundleStateInfo): void--><!--Device-BundleStateInfo-merge(toMerge: BundleStateInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toMerge | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the { |

## abilityInFgTotalTime

```TypeScript
abilityInFgTotalTime?: number
```

The total duration, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-abilityInFgTotalTime?: number--><!--Device-BundleStateInfo-abilityInFgTotalTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## abilityPrevAccessTime

```TypeScript
abilityPrevAccessTime?: number
```

The last time when the application was accessed, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-abilityPrevAccessTime?: number--><!--Device-BundleStateInfo-abilityPrevAccessTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## abilityPrevSeenTime

```TypeScript
abilityPrevSeenTime?: number
```

The last time when the application was visible in the foreground, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-abilityPrevSeenTime?: number--><!--Device-BundleStateInfo-abilityPrevSeenTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## abilitySeenTotalTime

```TypeScript
abilitySeenTotalTime?: number
```

The total duration when the application was visible in the foreground, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-abilitySeenTotalTime?: number--><!--Device-BundleStateInfo-abilitySeenTotalTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## bundleName

```TypeScript
bundleName?: string
```

The bundle name of the application.

**类型：** string

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-bundleName?: string--><!--Device-BundleStateInfo-bundleName?: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## fgAbilityAccessTotalTime

```TypeScript
fgAbilityAccessTotalTime?: number
```

The total duration when the foreground application was accessed, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-fgAbilityAccessTotalTime?: number--><!--Device-BundleStateInfo-fgAbilityAccessTotalTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## fgAbilityPrevAccessTime

```TypeScript
fgAbilityPrevAccessTime?: number
```

The last time when the foreground application was accessed, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-fgAbilityPrevAccessTime?: number--><!--Device-BundleStateInfo-fgAbilityPrevAccessTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## id

```TypeScript
id: number
```

The identifier of BundleStateInfo.

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-id: number--><!--Device-BundleStateInfo-id: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## infosBeginTime

```TypeScript
infosBeginTime?: number
```

The time of the first bundle usage record in this {@code BundleActiveInfo} object, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-infosBeginTime?: number--><!--Device-BundleStateInfo-infosBeginTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## infosEndTime

```TypeScript
infosEndTime?: number
```

The time of the last bundle usage record in this {@code BundleActiveInfo} object, in milliseconds. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ Unit:ms

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-BundleStateInfo-infosEndTime?: number--><!--Device-BundleStateInfo-infosEndTime?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

