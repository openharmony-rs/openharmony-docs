# CounterV2InlineStyleOptions

```TypeScript
declare class CounterV2InlineStyleOptions extends CounterV2CommonOptions
```

Defines the attributes and events of the inline number **CounterV2**.

> **NOTE:** 
> 
> **min** must be less than or equal to **max**. If **min** is greater than **max**, **max** is used.

**Inheritance/Implementation:** CounterV2InlineStyleOptions extends [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: OnInlineCounterV2Change
```

Callback triggered when the value changes. The callback parameter **value** indicates the currently displayed value.

Use scenario: Pass in this callback when you need to perform custom operations upon value changes (such as updating associated data, triggering service logic, or logging).

Default value: **undefined**, indicating that the callback is not triggered when the value changes.

If the value is **undefined**, the default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

Maximum value of **CounterV2**.

Default value: **999**

Value range: [min, +∞)

If the value exceeds the range (that is, the set value is less than **min**), **min** is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 999

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

Minimum value of **CounterV2**.

Default value: **0**

Value range: (-∞, max]

If the value exceeds the range (that is, the set value is greater than **max**), **max** is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textWidth

```TypeScript
textWidth?: number
```

Width of the number text.

Default value: adaptive text width.

Value range: [0, +∞)

Unit: vp

If the value exceeds the range (that is, the set value is less than 0), **0** is used.

If the value is **undefined**, the default value is used.

**Type:** number

**Default:** undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: number
```

Initial value of **CounterV2**.

Default value: **0**

Valid value range: [min, max], where **min** and **max** correspond to the minimum and maximum values of **CounterV2**, respectively.

If the value is **undefined**, the default value is used.

Boundary handling: If value is less than **min**, **min** is used. If value is greater than **max**, **max** is used.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
