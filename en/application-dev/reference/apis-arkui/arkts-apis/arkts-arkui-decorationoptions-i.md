# DecorationOptions

```TypeScript
declare interface DecorationOptions
```

Provides additional configuration options for the text decoration line style.

**Since:** 20

<!--Device-unnamed-declare interface DecorationOptions--><!--Device-unnamed-declare interface DecorationOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableMultiType

```TypeScript
enableMultiType?: boolean
```

Whether to enable the display of multiple decoration lines.

Default value: **undefined**. The value **true** enables it, and **false** or **undefined** disables it.

All decoration lines to be displayed must have this option enabled. In the intersection area of these decoration lines, the multi-decoration-line effect is displayed, and the style, color, and thickness of the last set decoration line are used.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DecorationOptions-enableMultiType?: boolean--><!--Device-DecorationOptions-enableMultiType?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
