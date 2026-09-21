# DateStyleOptions

```TypeScript
declare class DateStyleOptions extends CommonOptions
```

Defines the attributes and events of the inline date counter.

Inherits from [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md).

**Inheritance/Implementation:** DateStyleOptions extends [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onDateChange

```TypeScript
onDateChange?: (date: DateData) => void
```

Callback invoked when the date changes to return the current date. Use case: Pass in this callback when you need to perform custom operations (such as updating associated UI, logging, saving state, etc.) upon date changes.

**date**: currently displayed date value.

Default value: no callback is triggered.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | [DateData](arkts-arkui-arkui-advanced-counter-datedata-c.md) | Yes |  |

## day

```TypeScript
day?: number
```

Initial day of the inline date type.

Default value: **1**.

Value range: [1, 31].

**Note:** The specific value range of days in each month is determined by the actual number of days in that month.

If the value is out of the range, the default value is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

Initial month of the inline date type.

Default value: **1**.

Value range: [1, 12].

If the value is out of the range, the default value is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

Initial year of the inline date type.

Default value: **1**.

Value range: [1, 5000].

If the value is out of the range, the default value is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
