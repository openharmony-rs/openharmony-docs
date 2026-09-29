# LineHeightStyle

```TypeScript
enum LineHeightStyle
```

Enumerates the line height scaling base.

**Since:** 21

<!--Device-text-enum LineHeightStyle--><!--Device-text-enum LineHeightStyle-End-->

**System capability:** SystemCapability.Graphics.Drawing

## FONT_SIZE

```TypeScript
FONT_SIZE = 0
```

Uses the font size as the scaling base. The line height is calculated as follows: [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).fontSize * [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).heightScale.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-LineHeightStyle-FONT_SIZE = 0--><!--Device-LineHeightStyle-FONT_SIZE = 0-End-->

**System capability:** SystemCapability.Graphics.Drawing

## FONT_HEIGHT

```TypeScript
FONT_HEIGHT = 1
```

Uses the font height as the scaling base. The line height is calculated as follows: the height of the shaped glyph * [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).heightScale.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-LineHeightStyle-FONT_HEIGHT = 1--><!--Device-LineHeightStyle-FONT_HEIGHT = 1-End-->

**System capability:** SystemCapability.Graphics.Drawing
