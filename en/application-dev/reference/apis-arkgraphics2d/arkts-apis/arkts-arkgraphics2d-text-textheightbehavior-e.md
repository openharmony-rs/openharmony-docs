# TextHeightBehavior

```TypeScript
enum TextHeightBehavior
```

Enumerates the text height modifier patterns.

**Since:** 12

<!--Device-text-enum TextHeightBehavior--><!--Device-text-enum TextHeightBehavior-End-->

**System capability:** SystemCapability.Graphics.Drawing

## ALL

```TypeScript
ALL = 0x0
```

Allows the first line of the paragraph to rise and the last line to drop.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-TextHeightBehavior-ALL = 0x0--><!--Device-TextHeightBehavior-ALL = 0x0-End-->

**System capability:** SystemCapability.Graphics.Drawing

## DISABLE_FIRST_ASCENT

```TypeScript
DISABLE_FIRST_ASCENT = 0x1
```

Prevents the first line of a paragraph from rising.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-TextHeightBehavior-DISABLE_FIRST_ASCENT = 0x1--><!--Device-TextHeightBehavior-DISABLE_FIRST_ASCENT = 0x1-End-->

**System capability:** SystemCapability.Graphics.Drawing

## DISABLE_LAST_ASCENT

```TypeScript
DISABLE_LAST_ASCENT = 0x2
```

Prevents the last line of a paragraph from dropping.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-TextHeightBehavior-DISABLE_LAST_ASCENT = 0x2--><!--Device-TextHeightBehavior-DISABLE_LAST_ASCENT = 0x2-End-->

**System capability:** SystemCapability.Graphics.Drawing

## DISABLE_ALL

```TypeScript
DISABLE_ALL = 0x1 | 0x2
```

Prevents the first line of the paragraph to rise and the last line to drop.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-TextHeightBehavior-DISABLE_ALL = 0x1 | 0x2--><!--Device-TextHeightBehavior-DISABLE_ALL = 0x1 | 0x2-End-->

**System capability:** SystemCapability.Graphics.Drawing
