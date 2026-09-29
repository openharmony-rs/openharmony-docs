# RectWidthStyle

```TypeScript
enum RectWidthStyle
```

Enumerates the rectangle width styles.

**Since:** 12

<!--Device-text-enum RectWidthStyle--><!--Device-text-enum RectWidthStyle-End-->

**System capability:** SystemCapability.Graphics.Drawing

## TIGHT

```TypeScript
TIGHT = 0
```

If **letterSpacing** is not set, the rectangle conforms tightly to the text it contains. However, if **letterSpacing** is set, a gap is introduced between the rectangle and text.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-RectWidthStyle-TIGHT = 0--><!--Device-RectWidthStyle-TIGHT = 0-End-->

**System capability:** SystemCapability.Graphics.Drawing

## MAX

```TypeScript
MAX = 1
```

The rectangle's width is extended to align with the widest rectangle across all lines.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-RectWidthStyle-MAX = 1--><!--Device-RectWidthStyle-MAX = 1-End-->

**System capability:** SystemCapability.Graphics.Drawing
