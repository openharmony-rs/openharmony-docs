# LineSpacingOptions

```TypeScript
declare interface LineSpacingOptions
```

Configures the line spacing of text and whether it applies only between lines.

**Since:** 20

<!--Device-unnamed-declare interface LineSpacingOptions--><!--Device-unnamed-declare interface LineSpacingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onlyBetweenLines

```TypeScript
onlyBetweenLines?: boolean
```

Whether the line spacing of the text takes effect only between lines.

When set to true, the line spacing applies only between lines, with no extra line spacing above the first line or below the last line. When set to false, line spacing exists both above the first line and below the last line.

Default value: false

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-LineSpacingOptions-onlyBetweenLines?: boolean--><!--Device-LineSpacingOptions-onlyBetweenLines?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
