# DateMode

DateMode enum defines the mode of the date picker.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DATE

```TypeScript
DATE = 0
```

Date displays three columns: year, month, and day.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## YEAR_AND_MONTH

```TypeScript
YEAR_AND_MONTH = 1
```

Date displays two columns: year and month.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MONTH_AND_DAY

```TypeScript
MONTH_AND_DAY = 2
```

Defines a mode that displays the date as month and day. In this mode, when the month changes from December to January, the year does not increment; when the month changes from January to December, the year does not decrement. The year remains unchanged at its current setting.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
