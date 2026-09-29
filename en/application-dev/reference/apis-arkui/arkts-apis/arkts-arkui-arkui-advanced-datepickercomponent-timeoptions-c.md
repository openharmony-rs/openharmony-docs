# TimeOptions

```TypeScript
export declare class TimeOptions extends CommonOptions
```

Defines the options of the time picker.

This API inherits from [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md).

> **NOTE:** 
> 
> If the **start** or **end** parameter is set to a valid value, the **loop** parameter will not take effect. For
> details, see the parameter description of [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md).

**Inheritance/Implementation:** TimeOptions extends [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)

**Since:** 26.0.0

<!--Device-unnamed-export declare class TimeOptions extends CommonOptions--><!--Device-unnamed-export declare class TimeOptions extends CommonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## format

```TypeScript
format?: TimeFormat
```

Format of the time picker.

Default value: **TimeFormat.HOUR_MINUTE**

**Type:** [TimeFormat](arkts-arkui-arkui-advanced-datepickercomponent-timeformat-e.md)

**Default:** TimeFormat.HOUR_MINUTE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TimeOptions-format?: TimeFormat--><!--Device-TimeOptions-format?: TimeFormat-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

Whether to display time in 24-hour format.

- **true**: The time is displayed in 24-hour format, applicable to international applications and professional  
scenarios that require precise time expression (such as healthcare, transportation, and military).  
- **false**: The time is displayed in 12-hour format, applicable to daily application scenarios targeting general  
users, which better aligns with users' everyday reading habits.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TimeOptions-useMilitaryTime?: boolean--><!--Device-TimeOptions-useMilitaryTime?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
