# CommonOptions

```TypeScript
export declare class CommonOptions
```

CommonOptions defines common options for the date time picker.

> **Description:**
> 
> - For Date usage, refer to [TimePickerOptions](../../../reference/apis-arkui/arkui-ts/ts-basic-components-timepicker.md#timepickeroptions)。
> 
> - The text size of DatePickerComponent changes based on the total number of columns displayed. When the number of columns is 6 or more, the text size is 14vp; in other cases, it is 16vp. When the component width is too narrow,text may be truncated.
> 
> - When parameters are omitted or set to undefined, default values are used.
> 
> - In [DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md), setting start, end, and selected only takes effect for the date part (year,month, day). In [TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md), setting start, end, and selected only takes effect for the time part (hour, minute, second).

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

Enables or disables haptic feedback.

Default value: true

- true: Enable haptic feedback.  
- false: Disable haptic feedback.

**Description**:

1. When set to true, its effectiveness depends on whether the system's hardware supports it.
2. To enable haptic feedback, you need to configure the requestPermissions field in the project's
[module.json5](../../../quick-start/module-configuration-file.md) to enable vibration permission, as follows:

"requestPermissions": [{"name": "ohos.permission.VIBRATE"}]

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

End date or time of the picker.

Default value: Date(2100, 12, 31, 23, 59, 59)

Value range: [Date(0, 0, 1, 0, 0, 0), Date(10000, 11, 31,23, 59, 59)]

**Description:**

When end is set to a valid value, loop does not take effect.

**Type:** Date

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: boolean
```

Sets whether to enable loop mode.

- true: Enable loop mode.  
- false: Disable loop mode.

Default value: true

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<DatePickerComponentResult>
```

Callback triggered after date or time is selected.

**Type:** Callback&lt;[DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<DatePickerComponentResult>
```

Callback triggered when a picker item is selected and scrolling stops.

**Type:** Callback&lt;[DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

Selected date. Default value is the current system date or time.

**Type:** Date

**Default:** current system date or time

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

Start date or time of the picker.

Default value: Date(1970, 0, 1, 0, 0, 0)

Value range: [Date(0, 0, 1, 0, 0, 0), Date(10000, 11, 31,23, 59, 59)]

**Description:**

When start is set to a valid value, loop does not take effect.

**Type:** Date

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
