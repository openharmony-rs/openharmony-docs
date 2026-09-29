# CalendarPickerDialog

```TypeScript
declare class CalendarPickerDialog
```

Tapping a date opens a calendar picker dialog, where you can select a date. It is suitable for scenarios requiring date selection within an app, such as schedule management, booking systems, and form filling.

**Since:** 10

<!--Device-unnamed-declare class CalendarPickerDialog--><!--Device-unnamed-declare class CalendarPickerDialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: CalendarDialogOptions): void
```

Displays a calendar picker dialog box for the user to select a date.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CalendarPickerDialog-static show(options?: CalendarDialogOptions): void--><!--Device-CalendarPickerDialog-static show(options?: CalendarDialogOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CalendarDialogOptions](arkts-arkui-calendarpicker-comp-calendardialogoptions-i.md) | No | Parameters for configuring the calendar picker dialog box. If this parameter is not set, the dialog box cannot be displayed. |
