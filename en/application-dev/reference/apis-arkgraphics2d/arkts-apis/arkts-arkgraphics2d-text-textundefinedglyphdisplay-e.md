# TextUndefinedGlyphDisplay

```TypeScript
enum TextUndefinedGlyphDisplay
```

Enumerates the modes for displaying undefined text glyphs.

**Since:** 20

<!--Device-text-enum TextUndefinedGlyphDisplay--><!--Device-text-enum TextUndefinedGlyphDisplay-End-->

**System capability:** SystemCapability.Graphics.Drawing

## USE_DEFAULT

```TypeScript
USE_DEFAULT = 0
```

Follows the internal .notdef glyph design of the font, which can be an empty box, space, or custom symbol.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-TextUndefinedGlyphDisplay-USE_DEFAULT = 0--><!--Device-TextUndefinedGlyphDisplay-USE_DEFAULT = 0-End-->

**System capability:** SystemCapability.Graphics.Drawing

## USE_TOFU

```TypeScript
USE_TOFU = 1
```

Always uses explicit tofu blocks to replace undefined glyphs, overriding the default behavior of fonts. It is suitable for debugging missing characters or forcing a uniform display of missing symbols.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-TextUndefinedGlyphDisplay-USE_TOFU = 1--><!--Device-TextUndefinedGlyphDisplay-USE_TOFU = 1-End-->

**System capability:** SystemCapability.Graphics.Drawing
