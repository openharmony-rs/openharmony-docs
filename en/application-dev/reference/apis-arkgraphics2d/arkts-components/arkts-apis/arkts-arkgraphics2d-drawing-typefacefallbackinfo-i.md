# TypefaceFallbackInfo

```TypeScript
interface TypefaceFallbackInfo
```

Defines the typeface fallback info structure for a run of glyphs that share the same fallback typeface.

**Since:** 26.0.1

<!--Device-drawing-interface TypefaceFallbackInfo--><!--Device-drawing-interface TypefaceFallbackInfo-End-->

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## glyphIds

```TypeScript
glyphIds: Array<number>
```

The glyph ID array for this run.

**Type:** Array&lt;number&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-TypefaceFallbackInfo-glyphIds: Array<number>--><!--Device-TypefaceFallbackInfo-glyphIds: Array<number>-End-->

**System capability:** SystemCapability.Graphics.Drawing

## typeface

```TypeScript
typeface: Typeface
```

The typeface matched for this run of glyphs.

**Type:** [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-TypefaceFallbackInfo-typeface: Typeface--><!--Device-TypefaceFallbackInfo-typeface: Typeface-End-->

**System capability:** SystemCapability.Graphics.Drawing
