# DateMode

```TypeScript
export declare enum DateMode
```

Enumerates the modes of the date picker.

**Since:** 26.0.0

<!--Device-unnamed-export declare enum DateMode--><!--Device-unnamed-export declare enum DateMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DATE

```TypeScript
DATE = 0
```

Three columns: year, month, and day.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DateMode-DATE = 0--><!--Device-DateMode-DATE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## YEAR_AND_MONTH

```TypeScript
YEAR_AND_MONTH = 1
```

Two columns: year and month.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DateMode-YEAR_AND_MONTH = 1--><!--Device-DateMode-YEAR_AND_MONTH = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MONTH_AND_DAY

```TypeScript
MONTH_AND_DAY = 2
```

Two columns: month and day. In this mode, the year is specified by **selected** and remains unchanged; if **selected** is not specified, the current system year is used. When the month changes from December to January, the year does not increment. When the month changes from January to December, the year does not decrement. When scrolling through months causes the day to exceed the valid range, the day is automatically adjusted to the last day of that month.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DateMode-MONTH_AND_DAY = 2--><!--Device-DateMode-MONTH_AND_DAY = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
