# TextPickerRangeContent

```TypeScript
declare interface TextPickerRangeContent
```

Defines the content for single-column picker options.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: string | Resource
```

Image resource. If the value is a string, such as **"/common/hello.png"**, it represents the path to the image.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: string | Resource
```

Text information.

An empty character string is used by default.

Note: Text truncation occurs when content exceeds column width.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Default:** ""

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
