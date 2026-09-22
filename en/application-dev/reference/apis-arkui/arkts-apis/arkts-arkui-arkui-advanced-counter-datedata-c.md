# DateData

```TypeScript
declare class DateData
```

Defines date attributes and methods, including year, month, and day.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(year: number, month: number, day: number)
```

DateData constructor for initializing date objects.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| year | number | Yes | Year of the inline date type. Value range: [1, 5000]. |
| month | number | Yes | Month of the inline date type. Value range: [1, 12]. |
| day | number | Yes | Day of the inline date type. Value range: [1, 31]. The specific value is determined by the actual number of days in the month. |

## toString

```TypeScript
toString(): string
```

Returns the current date value in the string format, which is **YYYY-MM-DD**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Current date. |

## day

```TypeScript
day: number
```

Day of the inline date type. Value range: [1, 31]. The specific value is determined by the actual number of days in the month.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month: number
```

Month of the inline date type. Value range: [1, 12].

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year: number
```

Year of the inline date type. Value range: [1, 5000].

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
