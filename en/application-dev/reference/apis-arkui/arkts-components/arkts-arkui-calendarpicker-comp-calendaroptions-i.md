# CalendarOptions

```TypeScript
declare interface CalendarOptions
```

Describes the parameters of the calendar picker.

## Rules for Setting start and end

| Scenario | Description |  
| -------- | ------------------------------------------------------------ |  
| The start date is later than the end date. | Both start and end dates are invalid, and the selected date is the default value. |

| The selected date is earlier than the start date. | The selected date is set as the start date. |  
| The selected date is later than the end date. | The selected date is set as the end date. |  
| The start date is later than the current system date, and the selected date is not set. | The selected date is set as the start date. |

| The end date is earlier than the current system date, and the selected date is not set. | The selected date is set as the end date. |

| The set date is in invalid format, for example, **1999-13-32**.| The start or end date setting is invalid,and the selected date is the default value.|

**Since:** 10

<!--Device-unnamed-declare interface CalendarOptions--><!--Device-unnamed-declare interface CalendarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disabledDateRange

```TypeScript
disabledDateRange?: DateRange[]
```

Disabled date range. If this parameter is not passed, no date is disabled.

**NOTE:** 

1. If the start date or end date within a date range is invalid or is not set, the entire date range does not
take effect.
2. If the end date is earlier than the start date within a date range, the entire date range does not take
effect.
3. When users select a date and adjust it with the up or down arrow keys, the system skips over all dates in
the disabled date range.

**Type:** [DateRange](arkts-arkui-common-comp-daterange-i.md)[]

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-CalendarOptions-disabledDateRange?: DateRange[]--><!--Device-CalendarOptions-disabledDateRange?: DateRange[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

End date.

Default value: **Date('5000-12-31')**.

Value range: [Date('0001-01-01'), Date('5000-12-31')].

Note: If the start date is later than the end date, both the settings of **start** and **end** are invalid, and the selected date is the default value. For details, see [Rules for setting start and end](#rules-for-setting-start-and-end).

**Type:** Date

**Default:** Date('5000-12-31')

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CalendarOptions-end?: Date--><!--Device-CalendarOptions-end?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hintRadius

```TypeScript
hintRadius?: number | Resource
```

Background style of the selected state in the calendar picker.

Value range: [0.0, 16.0]

Unit: vp.

Default value: **16.0** (the background is a circle).

**NOTE:** 

If the value of **hintRadius** is **0.0**, the background is a rectangle with square corners. If the value of **hintRadius** is within the range (0.0, 16.0), the background is a rectangle with rounded corners. If the value of **hintRadius** is **16.0**, the background is a circle. If the value of **hintRadius** is a negative number or greater than **16.0**, the default value **16.0** is used.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** 16.0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CalendarOptions-hintRadius?: number | Resource--><!--Device-CalendarOptions-hintRadius?: number | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Date of the selected item. This parameter is passed when the selected date needs to be preset. If the date does not need to be preset, the current system date is used. If the value is not set or does not comply with the date format specifications, the default value will be used. For details about the relationship between the selected date and the **start** and **end** parameters, see [Rules for setting start and end](#rules-for-setting-start-and-end).

Default value: current system date

Value range: [Date('0001-01-01'), Date('5000-12-31')].

**Type:** Date

**Default:** current system date

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CalendarOptions-selected?: Date--><!--Device-CalendarOptions-selected?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Start date.

Default value: **Date('0001-01-01')**

Value range: [Date('0001-01-01'), Date('5000-12-31')].

Note: If the start date is later than the end date, both the settings of **start** and **end** are invalid, and the selected date is the default value. For details, see [Rules for setting start and end](#rules-for-setting-start-and-end).

**Type:** Date

**Default:** Date('0001-01-01')

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CalendarOptions-start?: Date--><!--Device-CalendarOptions-start?: Date-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
