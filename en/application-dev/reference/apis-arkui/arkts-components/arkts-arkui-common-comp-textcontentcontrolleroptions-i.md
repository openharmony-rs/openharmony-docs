# TextContentControllerOptions

```TypeScript
declare interface TextContentControllerOptions
```

Provides configuration options for text insertion operations in text input components.

**Since:** 15

<!--Device-unnamed-declare interface TextContentControllerOptions--><!--Device-unnamed-declare interface TextContentControllerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

Position to insert text. Value range: [0, text length]. If the value is out of range, it is automatically corrected to a valid boundary position.

**Note:** 

Pass this parameter when text needs to be inserted at a specified position (rather than at the end). If not passed, text is inserted at the end by default.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextContentControllerOptions-offset?: number--><!--Device-TextContentControllerOptions-offset?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
