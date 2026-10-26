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

## hideYear

```TypeScript
hideYear?: boolean
```

Whether to enable the "hide year" option.

- **true**: A "----" option is appended after the [end](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md) year. The user can select "----" to  
indicate that the specific year is not relevant. This is applicable to scenarios that do not require a specific year, such as birthdays and anniversaries.  
- **false**: The "----" option is not displayed. The year column shows only the specific years within the  
range of [start](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md) and [end](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md).

**NOTE:** 

1. This attribute takes effect only when [displayMode](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentoptions-c.md) is  
**DisplayMode.DATE** or **DisplayMode.DATE_TIME** and [mode](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md) is **DateMode.DATE** or **DateMode.YEAR_AND_MONTH**.
2. When this attribute is **true**, the user can still scroll to select a specific year. The "----" option and
specific years can be switched freely.
3. This attribute supports runtime dynamic switching. When the value changes, the year column is updated
accordingly.

Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DateOptions-hideYear?: boolean--><!--Device-DateOptions-hideYear?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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
