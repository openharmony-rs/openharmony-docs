# DecorationOptions

```TypeScript
declare interface DecorationOptions
```

Provides additional configuration options for the text decoration line style.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableMultiType

```TypeScript
enableMultiType?: boolean
```

Whether to enable the display of multiple decoration lines.

Default value: **undefined**. **true**: Enable the display of multiple decoration lines. **false** or **undefined**: Disable the display of multiple decoration lines.

To display all decoration lines, this option must be enabled. The overlapping area of multiple decoration lines will show a combined effect, with the style, color, and thickness consistent with the last decoration line.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
