# DateOptions

DateOptions defines options for the date picker.

Inherits from [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md).

**Inheritance/Implementation:** DateOptions extends [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## lunar

```TypeScript
lunar?: boolean
```

Specifies whether to display as lunar calendar.

- true: Display as lunar calendar.  
- false: Do not display as lunar calendar.

Default value: false

**Description**:

This only takes effect in Simplified Chinese and Traditional Chinese language environments. In other language environments, setting this property has no effect.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DateMode
```

Defines the mode of the date picker.

Default value: DateMode.DATE

**Type:** [DateMode](arkts-arkui-arkui-advanced-datepickercomponent-datemode-e.md)

**Default:** DateMode.DATE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
