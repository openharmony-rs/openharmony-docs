# DatePickerMode

```TypeScript
declare enum DatePickerMode
```

Enumerates date display modes.

**Since:** 18

<!--Device-unnamed-declare enum DatePickerMode--><!--Device-unnamed-declare enum DatePickerMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DATE

```TypeScript
DATE = 0
```

Three-column display: year, month, and day.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerMode-DATE = 0--><!--Device-DatePickerMode-DATE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MONTH_AND_DAY

```TypeScript
MONTH_AND_DAY = 2
```

Two-column display: month and day.

In this mode, the year remains unchanged and takes the value specified by the **selected** parameter. If **selected** is not specified, the current system year is used. When scrolling the month causes the date to exceed the valid range, the date is automatically adjusted to the last day of the month.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerMode-MONTH_AND_DAY = 2--><!--Device-DatePickerMode-MONTH_AND_DAY = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## YEAR_AND_MONTH

```TypeScript
YEAR_AND_MONTH = 1
```

Two-column display: year and month.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerMode-YEAR_AND_MONTH = 1--><!--Device-DatePickerMode-YEAR_AND_MONTH = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
