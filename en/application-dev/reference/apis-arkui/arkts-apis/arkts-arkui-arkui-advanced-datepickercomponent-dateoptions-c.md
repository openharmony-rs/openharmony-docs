# DateOptions

```TypeScript
export declare class DateOptions extends CommonOptions
```

Defines the options of the date picker.

This API inherits from [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md).

**Inheritance/Implementation:** DateOptions extends [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)

**Since:** 26.0.0

<!--Device-unnamed-export declare class DateOptions extends CommonOptions--><!--Device-unnamed-export declare class DateOptions extends CommonOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## lunar

```TypeScript
lunar?: boolean
```

Whether to display the lunar calendar.

- **true**: The lunar calendar is displayed. This is applicable to scenarios where the traditional lunar calendar  
is required, such as traditional festivals, lunar birthdays, and lunar anniversaries.  
- **false**: The lunar calendar is not displayed. This is applicable to scenarios where the Gregorian calendar is  
used.

Default value: **false**

**NOTE:** 

This attribute takes effect only in the simplified Chinese and traditional Chinese language environments. It has no effect in other language environments.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DateOptions-lunar?: boolean--><!--Device-DateOptions-lunar?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DateMode
```

Mode of the date picker.

Default value: DateMode.DATE

**Type:** [DateMode](arkts-arkui-arkui-advanced-datepickercomponent-datemode-e.md)

**Default:** DateMode.DATE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DateOptions-mode?: DateMode--><!--Device-DateOptions-mode?: DateMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
