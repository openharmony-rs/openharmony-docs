# InlineStyleOptions

```TypeScript
declare class InlineStyleOptions extends CommonOptions
```

Defines the inline numeric counter attributes and events.

Inherits from [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md).

> **NOTE:** 
> 
> 1. **min** must be less than or equal to **max**. If **min** is greater than **max**, **max** is used.

**Inheritance/Implementation:** InlineStyleOptions extends [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: (value: number) => void
```

Callback invoked when the value changes, returning the current value. Use case: pass in this callback when you need to perform custom operations upon value changes (such as updating associated UI, logging, saving state, etc.).

**value**: current displayed value.

Default value: the callback is not triggered when the value changes.

If the value is **undefined**, the default value is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

## max

```TypeScript
max?: number
```

Maximum value of **Counter**.

Default value: **999**.

Value range: [min, +∞).

If the value exceeds the range (that is, the set value is less than **min**), **min** is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 999

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

Minimum value of **Counter**.

Default value: **0**.

Value range: (-∞, max].

If the value exceeds the range (that is, the set value is greater than **max**), **max** is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 0

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textWidth

```TypeScript
textWidth?: number
```

Width of the number text.

Default value: adaptive text width.

Value range: [0, +∞).

Unit: vp.

If the value exceeds the range (that is, the set value is less than 0), **0** is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 0

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: number
```

Initial value of **Counter**.

Default value: **0**.

Value range: [min, max], where **min** and **max** correspond to the minimum and maximum values of **Counter** respectively (the default value of **min** is **0** and **max** is **999**).

If the value exceeds the range, **min** is used when the value is less than **min**, and **max** is used when the value is greater than **max**.

**Type:** number

**Default:** 0

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
