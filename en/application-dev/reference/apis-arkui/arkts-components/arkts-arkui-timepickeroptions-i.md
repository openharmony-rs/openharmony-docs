# TimePickerOptions

Describes the parameters of the time picker.

Property modifications made to **TimePickerOptions** during the **TimePicker** scrolling process may not take effect.

The **Date** object is used to handle dates and time. It can be used in the following ways:

**Method 1**: new Date()

Obtains the current system date and time.

**Method 2**: new Date(value: number | string)

**Method 3**: new Date(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?: number, ms?: number)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

End time of the time picker.

Default value: **Date(0, 0, 0, 23, 59, 59)**.

**NOTE:** 

1. Only the hour and minute values take effect.
2. If **end** is set and is not the default value, **loop** does not take effect.

**Type:** Date

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## format

```TypeScript
format?: TimePickerFormat
```

Time format.

Default value: **TimePickerFormat.HOUR_MINUTE**

**Type:** [TimePickerFormat](arkts-arkui-timepickerformat-e.md)

**Default:** HOUR_MINUTE

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Time of the selected item.

Default value: current system time

Since API version 10, this parameter supports two-way binding through [&#36;&#36;](../../../ui/state-management/arkts-two-way-sync.md).

**Type:** Date

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Start time of the time picker.

Default value: **Date(0, 0, 0, 0, 0, 0)**

**NOTE:** 

1. Only the hour and minute values take effect.
2. If **start** is set and is not the default value, **loop** does not take effect.

**Type:** Date

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
