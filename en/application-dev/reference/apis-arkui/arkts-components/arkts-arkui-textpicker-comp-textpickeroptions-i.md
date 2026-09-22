# TextPickerOptions

```TypeScript
declare interface TextPickerOptions
```

Defines the configuration options of the text picker.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnWidths

```TypeScript
columnWidths?: LengthMetrics[]
```

Custom widths for each column.

Default value: Each column has equal width, calculated by dividing the total component width by the number of columns.

**NOTE:** 

1. Text truncation occurs when content exceeds column width.
2. Invalid values are treated as the default value.
3. Individual array elements can be **Undefined** or **Null**, but the entire array cannot be **Undefined[]**
or **Null[]**.

**Type:** LengthMetrics[]

**Default:** Each column has equal width, calculated by dividing the total component width by the number of columns.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: string[] | string[][]  | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]
```

Data selection range of the picker. This parameter cannot be set to an empty array. If it is set to an empty array, no value is displayed. If it is dynamically changed to an empty array, the current valid value remains displayed.

**NOTE:** 

1. Single-column pickers: string[], Resource,
or [TextPickerRangeContent](arkts-arkui-textpicker-comp-textpickerrangecontent-i.md)[]
2. Multi-column independent pickers: string[][]
3. Multi-column cascading pickers: [TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md)[]
4. The Resource type supports only [strarray.json]
(../../../quick-start/resource-categories-and-access.md#resource-group-directories).
5. The type and number of columns in the range cannot be dynamically modified.

**Type:** string[] &#124; string[][] &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [TextPickerRangeContent](arkts-arkui-textpicker-comp-textpickerrangecontent-i.md)[] &#124; [TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md)[]

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: number[]
```

Index of the selected item in the data list. The index is zero-based.

Default value: **0**

**NOTE:** 

1. Single-column pickers: number
2. Multi-column pickers: number[]
3. Since API version 10, this parameter supports two-way binding through
[$$](../../../ui/state-management/arkts-two-way-sync.md).

**Type:** number[]

**Default:** 0

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr[]
```

Value of the selected item. The priority of this parameter is lower than that of **selected**.

Default value: value of the first item in the data list.

**NOTE:** 

1. Since API version 10, this parameter supports two-way binding through
[$$](../../../ui/state-management/arkts-two-way-sync.md).
2. The Resource type is supported since API version 20.
3. This parameter works only when the picker contains text only.
It does not work when the picker contains images or mixed content.
4. Single-column pickers: [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)
5. Multi-column pickers: [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)[]

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)[]

**Default:** 
- API versions 8 to 9: value of the first item

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
