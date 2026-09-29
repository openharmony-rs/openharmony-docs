# TextCascadePickerRangeContent

```TypeScript
declare interface TextCascadePickerRangeContent
```

Defines the content for multi-column picker options.

**Since:** 10

<!--Device-unnamed-declare interface TextCascadePickerRangeContent--><!--Device-unnamed-declare interface TextCascadePickerRangeContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## children

```TypeScript
children?: TextCascadePickerRangeContent[]
```

Linked data. Indicates the array of child options of the current data item, used to build the hierarchical structure of a multi-column linkage data picker. Each element of the array is of the [TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md) type, containing the text and children attributes, and supports multi-level nesting. Pass this parameter when the picker supports multi-level linkage; if it is not passed, the option has no child-level data.

**Type:** [TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md)[]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextCascadePickerRangeContent-children?: TextCascadePickerRangeContent[]--><!--Device-TextCascadePickerRangeContent-children?: TextCascadePickerRangeContent[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string | Resource
```

Text information.

**Note:** When the text length is greater than the column width, the text is truncated.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextCascadePickerRangeContent-text: string | Resource--><!--Device-TextCascadePickerRangeContent-text: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
