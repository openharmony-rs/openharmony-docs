# TextCascadePickerRangeContent

```TypeScript
declare interface TextCascadePickerRangeContent
```

Defines the content for multi-column picker options.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## children

```TypeScript
children?: TextCascadePickerRangeContent[]
```

Linkage data.

**Type:** [TextCascadePickerRangeContent](arkts-arkui-textpicker-comp-textcascadepickerrangecontent-i.md)[]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string | Resource
```

Text information.

Note: Text truncation occurs when content exceeds column width.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
