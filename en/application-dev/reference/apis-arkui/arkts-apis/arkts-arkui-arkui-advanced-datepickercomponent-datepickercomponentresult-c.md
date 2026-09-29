# DatePickerComponentResult

```TypeScript
export declare class DatePickerComponentResult
```

Defines the selection result of the date and time picker, including the year, month, day, hour, minute, and second selected by the user. It is used to pass the specific date and time values in the **onChange** and **onScrollStop** callbacks.

**Since:** 26.0.0

<!--Device-unnamed-export declare class DatePickerComponentResult--><!--Device-unnamed-export declare class DatePickerComponentResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## day

```TypeScript
day?: number
```

Day of the selected date.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentResult-day?: int--><!--Device-DatePickerComponentResult-day?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hour

```TypeScript
hour?: number
```

Hour of the selected time.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentResult-hour?: int--><!--Device-DatePickerComponentResult-hour?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minute

```TypeScript
minute?: number
```

Minute of the selected time.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentResult-minute?: int--><!--Device-DatePickerComponentResult-minute?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

Month index of the selected date, starting from 0. The value **0** indicates January, and **11** indicates December.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentResult-month?: int--><!--Device-DatePickerComponentResult-month?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## second

```TypeScript
second?: number
```

Second of the selected time.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentResult-second?: int--><!--Device-DatePickerComponentResult-second?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

Year of the selected date.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentResult-year?: int--><!--Device-DatePickerComponentResult-year?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
