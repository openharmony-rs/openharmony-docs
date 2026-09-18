# BadgeParamWithNumber

Inherits from [BadgeParam](arkts-arkui-badgeparam-i.md) and has all attributes of **BadgeParam**.

**Inheritance/Implementation:** BadgeParamWithNumber extends [BadgeParam](arkts-arkui-badgeparam-i.md)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: number
```

Number of notifications.

**NOTE:** 

If the value is less than or equal to 0 and less than the value of **maxCount**, no badge is displayed.

Value range: [-2147483648, 2147483647]. If the value is out of the range, 4294967296 is added or subtracted so that the value is within the range. If the value is not an integer, it is rounded off to the nearest integer. For example, 5.5 is rounded off to 5.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount?: number
```

Maximum number of messages. If the number of messages exceeds the maximum, only **maxCount+** is displayed. For example, if **maxCount** is 99, **99+** is displayed.

Default value: **99**

Value range: [-2147483648, 2147483647]. If the value is out of the range, 4294967296 is added or subtracted so that the value is within the range. If the value is not an integer, it is rounded off to the nearest integer. For example, 5.5 is rounded off to 5.

**Type:** number

**Default:** 99

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
