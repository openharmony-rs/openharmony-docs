# BadgeParamWithNumber

```TypeScript
declare interface BadgeParamWithNumber extends BadgeParam
```

BadgeParamWithNumber inherits from [BadgeParam](arkts-arkui-badge-comp-badgeparam-i.md) and has all the attributes of BadgeParam.

**Inheritance/Implementation:** BadgeParamWithNumber extends [BadgeParam](arkts-arkui-badge-comp-badgeparam-i.md)

**Since:** 7

<!--Device-unnamed-declare interface BadgeParamWithNumber extends BadgeParam--><!--Device-unnamed-declare interface BadgeParamWithNumber extends BadgeParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: number
```

Number of reminder messages.

**NOTE:** 

When the value is less than or equal to 0 and less than **maxCount**, the badge is not displayed.

Value range: [-2147483648, 2147483647]. If the value is out of range, 4294967296 is added to or subtracted from it to keep it within the range. If the value is not an integer, the decimal part is discarded, for example, 5.5 becomes 5.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BadgeParamWithNumber-count: number--><!--Device-BadgeParamWithNumber-count: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount?: number
```

Maximum number of messages. When the number exceeds the maximum, only **maxCount+** is displayed. For example, when **maxCount** is 99, `99+` is displayed.

Default value: **99**

Value range: [-2147483648, 2147483647]. If the value is out of range, 4294967296 is added to or subtracted from it to keep it within the range. If the value is not an integer, the decimal part is discarded, for example, 5.5 becomes 5.

**Type:** number

**Default:** 99

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BadgeParamWithNumber-maxCount?: number--><!--Device-BadgeParamWithNumber-maxCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
