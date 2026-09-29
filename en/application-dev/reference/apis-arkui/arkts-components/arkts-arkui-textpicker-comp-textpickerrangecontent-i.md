# TextPickerRangeContent

```TypeScript
declare interface TextPickerRangeContent
```

Defines the content for single-column picker options.

**Since:** 10

<!--Device-unnamed-declare interface TextPickerRangeContent--><!--Device-unnamed-declare interface TextPickerRangeContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: string | Resource
```

Image resource. When **icon** is of the string type, it indicates the path of the image, for example, "/common/ hello.png"; when **icon** is of the Resource type, it indicates a resource reference.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerRangeContent-icon: string | Resource--><!--Device-TextPickerRangeContent-icon: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: string | Resource
```

Text information.

Default value: empty string

**Note:** 

1. When this attribute is not set, the default value is used.
2. When the text length is greater than the column width, the text is truncated.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** ""

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerRangeContent-text?: string | Resource--><!--Device-TextPickerRangeContent-text?: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
