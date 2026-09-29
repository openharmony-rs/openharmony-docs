# DatePickerComponentOptions

```TypeScript
export declare class DatePickerComponentOptions
```

Defines the options of the date and time picker component.

**Since:** 26.0.0

<!--Device-unnamed-export declare class DatePickerComponentOptions--><!--Device-unnamed-export declare class DatePickerComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: DateOptions
```

Date options.

**Type:** [DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentOptions-dateOptions?: DateOptions--><!--Device-DatePickerComponentOptions-dateOptions?: DateOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## displayMode

```TypeScript
displayMode?: DisplayMode
```

Display mode of the picker.

Default value: **DisplayMode.DATE**

**NOTE:** 

- **DATE**: Displays only the date using **dateOptions**. This value is applicable to scenarios where only the date  
needs to be selected, such as birthday selection and schedule date setting.  
- **TIME**: Displays only the time using **timeOptions**. This value is applicable to scenarios where only the time  
needs to be selected, such as alarm setting and reminder time setting.  
- **DATE_TIME**: Displays both the date and time, with **dateOptions** and **timeOptions** taking effect  
simultaneously. This value is applicable to scenarios where both the date and time need to be selected, such as event scheduling and meeting time setting.

**Type:** [DisplayMode](arkts-arkui-arkui-advanced-datepickercomponent-displaymode-e.md)

**Default:** DisplayMode.DATE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentOptions-displayMode?: DisplayMode--><!--Device-DatePickerComponentOptions-displayMode?: DisplayMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeOptions

```TypeScript
timeOptions?: TimeOptions
```

Time options.

**Type:** [TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DatePickerComponentOptions-timeOptions?: TimeOptions--><!--Device-DatePickerComponentOptions-timeOptions?: TimeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
