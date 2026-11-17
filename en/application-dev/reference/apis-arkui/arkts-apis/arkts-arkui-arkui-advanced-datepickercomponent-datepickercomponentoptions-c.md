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

## itemTextStyle

```TypeScript
itemTextStyle?: PickerComponentTextStyle
```

Text style of all items. When both selectedTextStyle and itemTextStyle are set, itemTextStyle applies to items other than the selected item. Default value: {color: $r('sys.color.font_primary'), font: {size: '14vp' (when the number of displayed columns is 6 or greater) or '16vp' (otherwise), weight: FontWeight.Normal}, overflow: TextOverflow.Clip}.

**Type:** [PickerComponentTextStyle](../arkts-components/arkts-arkui-common-comp-pickercomponenttextstyle-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DatePickerComponentOptions-itemTextStyle?: PickerComponentTextStyle--><!--Device-DatePickerComponentOptions-itemTextStyle?: PickerComponentTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedTextStyle

```TypeScript
selectedTextStyle?: PickerComponentTextStyle
```

Text style of the selected item. Default value: {color: $r('sys.color.font_primary'), font: {size: '14vp' (when the number of displayed columns is 6 or greater) or '16vp' (otherwise), weight: FontWeight.Normal}, overflow: TextOverflow.Clip}.

**Type:** [PickerComponentTextStyle](../arkts-components/arkts-arkui-common-comp-pickercomponenttextstyle-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DatePickerComponentOptions-selectedTextStyle?: PickerComponentTextStyle--><!--Device-DatePickerComponentOptions-selectedTextStyle?: PickerComponentTextStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectionIndicator

```TypeScript
selectionIndicator?: PickerIndicatorStyle
```

Style of the selected item indicator. Default value: {type: PickerIndicatorType.BACKGROUND, strokeWidth: {value: 2, unit: LengthUnit.px}, dividerColor: 'sys.color.comp_divider', startMargin: {value: 0, unit: LengthUnit.px}, endMargin: {value: 0, unit: LengthUnit.px}, borderRadius: {value: 12, unit: LengthUnit.vp}, backgroundColor: 'sys.color.comp_background_tertiary'}

**Type:** [PickerIndicatorStyle](../arkts-components/arkts-arkui-uipickercomponent-comp-pickerindicatorstyle-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DatePickerComponentOptions-selectionIndicator?: PickerIndicatorStyle--><!--Device-DatePickerComponentOptions-selectionIndicator?: PickerIndicatorStyle-End-->

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
