# TextPickerOptions

```TypeScript
declare interface TextPickerOptions
```

Defines the configuration options of the text picker.

**Since:** 8

<!--Device-unnamed-declare interface TextPickerOptions--><!--Device-unnamed-declare interface TextPickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnWidths

```TypeScript
columnWidths?: LengthMetrics[]
```

Sets the width of each column.

Default value: the width of each column is equal, which is the component width divided by the number of columns.

**Note:** 

1. When the text length is greater than the column width, the text is truncated.
2. When an abnormal value is set, the default value is used.
3. Undefined and Null are supported, but Undefined[] and Null[] are not supported.
4. When the length of the columnWidths array does not match the actual number of columns, the column width values
beyond the number of columns are ignored; columns without a specified width evenly share the remaining available width of the component (the component width minus the sum of the specified column widths).

**Model restriction:** This API can be used only under the stage model.

**Atomic service API:** This API is supported in atomic services since API version 18.

**Type:** LengthMetrics[]

**Default:** Each column has equal width, calculated by dividing the total component width by the number of columns.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextPickerOptions-columnWidths?: LengthMetrics[]--><!--Device-TextPickerOptions-columnWidths?: LengthMetrics[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## range

```TypeScript
range: string[] | string[][]  | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]
```

Data selection list of the picker. It cannot be set to an empty array. If it is set to an empty array, nothing is displayed; if it dynamically changes to an empty array, the current normal value remains displayed.

**Note:** 

1. A single-column data picker uses the string[], Resource, or
[TextPickerRangeContent](arkts-arkui-textpicker-comp-textpickerrangecontent-i.md)[] type.
2. A multi-column non-linked data picker uses the string[][] type.
3. A multi-column linkage data picker uses the
[TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md)[] type.
4. The Resource type supports only
[strarray.json](../../../quick-start/resource-categories-and-access.md#resource-group-directories).
5. The type and number of columns of range cannot be dynamically modified.

**Atomic service API:** This API is supported in atomic services since API version 11.

**Type:** string[] &#124; string[][] &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [TextPickerRangeContent](arkts-arkui-textpicker-comp-textpickerrangecontent-i.md)[] &#124; [TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md)[]

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerOptions-range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]--><!--Device-TextPickerOptions-range: string[] | string[][] | Resource | TextPickerRangeContent[] | TextCascadePickerRangeContent[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: number[]
```

Sets the index of the selected item in the data selection list. The index starts from 0.

Default value: 0

**Note:** 

1. A single-column data picker uses the number type.
2. A multi-column non-linked data picker uses the number[] type, and the array length is the same as the number of
columns.
3. A multi-column linkage data picker uses the number[] type, and the array length is the same as the number of
levels.
4. Since API version 10, this parameter supports
[$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding variables.
5. If this attribute is not set or the set value is invalid, the default value is used.

**Atomic service API:** This API is supported in atomic services since API version 11.

**Type:** number[]

**Default:** 0

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerOptions-selected?: number | number[]--><!--Device-TextPickerOptions-selected?: number | number[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr[]
```

Sets the value of the selected item. Its priority is lower than that of selected.

Default value: the value of the first element in the data selection list.

**Note:** 

1. Since API version 10, this parameter supports
[$$](../../../ui/state-management/arkts-two-way-sync.md) two-way binding variables.
2. Since API version 20, the Resource type is supported.
3. This value is valid only when a text list is displayed. It is invalid when a list of images or a mixed list of
images and text is displayed.
4. A single-column data picker uses the [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) type.
5. A multi-column non-linked data picker uses the [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)[] type, and the array length is
the same as the number of columns.
6. A multi-column linkage data picker uses the [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)[] type, and the array length is
the same as the number of levels.
7. When neither selected nor value is set, or the selected value is invalid, the default value is used.

**Atomic service API:** This API is supported in atomic services since API version 11.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)[]

**Default:** 
- API versions 8 to 9: value of the first item

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerOptions-value?: ResourceStr | ResourceStr[]--><!--Device-TextPickerOptions-value?: ResourceStr | ResourceStr[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
