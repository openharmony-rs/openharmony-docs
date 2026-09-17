# CalendarOptions

Describes the parameters of the calendar picker.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disabledDateRange

```TypeScript
disabledDateRange?: DateRange[]
```

Disabled date range.

**NOTE:** 

1. If the start date or end date within a date range is invalid or is not set,
the entire date range does not take effect.
2. If the end date is earlier than the start date within a date range, the entire date range does not take effect.
3. When users select a date and adjust it with the up or down arrow keys,
the system skips over all dates in the disabled date range.

**Type:** [DateRange](arkts-arkui-daterange-i.md)[]

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

End date.

Default value: **Date('5000-12-31')**.

Value range: [Date('0001-01-01'), Date('5000-12-31')].

**Type:** Date

**Default:** Date('5000-12-31')

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hintRadius

```TypeScript
hintRadius?: number | Resource
```

Style of the background of the selected state.

Value range: [0.0, 16.0]

Unit: vp.

Default value: **16.0** (the background is a circle).

**NOTE:** 

If the value is **0.0**, the background is a right-angled rectangle. If the value is in the (0.0, 16.0) range, the background is a rounded rectangle. If the value is a negative number or greater than 16.0, the default value **16.0** is used, which means the background is a circle.

**Type:** number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** 16.0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Date of the selected item. If the value is not set or does not comply with the date format specifications, the default value will be used.

Default value: current system date

Value range: [Date('0001-01-01'), Date('5000-12-31')].

**Type:** Date

**Default:** current system date

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Start date.

Default value: **Date('0001-01-01')**

Value range: [Date('0001-01-01'), Date('5000-12-31')].

**Type:** Date

**Default:** Date('0001-01-01')

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
