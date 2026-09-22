# CounterV2DateData

```TypeScript
declare class CounterV2DateData
```

Defines common date attributes and methods, including year, month, and day.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(year: number, month: number, day: number)
```

Constructor of **CounterV2DateData**, used to initialize a date object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| year | number | Yes | Year of the inline date type. Value range: [1, 5000]. If the value is out of the range, the default value is used. |
| month | number | Yes | Month of the inline date type. Value range: [1, 12]. If the value is out of the range, the default value is used. |
| day | number | Yes | Day of the inline date type. Value range: [1, 31]. It must be a valid date. For example, if **month** is **2**, passing **30** for **day** is treated as an invalid value and the default value will be used. If the value is out of the range, the default value is used. |

## toString

```TypeScript
toString(): string
```

Returns the current date value in the string format, which is **YYYY-MM-DD**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Date string in the **YYYY-MM-DD** format, for example, **2024-01-15**. |

## day

```TypeScript
day: number
```

Day of the inline date type.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month: number
```

Month of the inline date type.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year: number
```

Year of the inline date type.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
