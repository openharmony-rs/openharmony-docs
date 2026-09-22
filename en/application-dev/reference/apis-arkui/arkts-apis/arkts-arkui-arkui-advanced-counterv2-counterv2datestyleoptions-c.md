# CounterV2DateStyleOptions

```TypeScript
declare class CounterV2DateStyleOptions extends CounterV2CommonOptions
```

Defines the attributes and events of the inline date **CounterV2**.

**Inheritance/Implementation:** CounterV2DateStyleOptions extends [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## onDateChange

```TypeScript
onDateChange?: OnDateCounterV2ChangeCallback
```

Callback invoked when the date changes. The parameter **date** indicates the currently displayed date value.

Use scenario: Pass in this callback when you need to perform custom operations (such as updating associated data, triggering business logic, and logging) when the date changes.

Default value: **undefined**, indicating that this callback is not triggered.

If the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## day

```TypeScript
day?: number
```

Initial day of the inline date type.

Default value: **1**

Value range: [1, 31]

It must be a valid date. For example, if **month** is **2**, passing **30** for **day** is treated as an invalid value and the default value will be used.

If the value is out of the range, the default value is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

Initial month of the inline date type.

Default value: **1**

Value range: [1, 12]

If the value is out of the range, the default value is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

Initial year of the inline date type.

Default value: **1**

Value range: [1, 5000]

If the value is out of the range, the default value is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 1

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
