# WordBreak

Enumerates the word break types.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## NORMAL

```TypeScript
NORMAL = 0
```

Default mode that break words based on language-specific conventions.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## BREAK_ALL

```TypeScript
BREAK_ALL = 1
```

Allows breaks within any character in non-CJK text. (CJK means Chinese, Japanese, and Korean.) This value is suitable for Asian text that contains some non-Asian text. For example, it can be used to break consecutive English characters.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## BREAK_WORD

```TypeScript
BREAK_WORD = 2
```

For non-CJK text, breaks lines between any two characters. If a line contains break points (such as whitespace characters), the line breaks at the break points first to keep words intact. If the entire line has no break points, the line breaks between any two characters. For CJK text, this strategy behaves the same as NORMAL.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## BREAK_HYPHEN

```TypeScript
BREAK_HYPHEN = 3
```

Attempts to break words at the end of a line using a hyphen. If a hyphen cannot be added, it behaves like **BREAK_WORD**.

When using this word break strategy, you need to use the `locale` attribute in [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md) to define the language environment, which affects the word break effect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
