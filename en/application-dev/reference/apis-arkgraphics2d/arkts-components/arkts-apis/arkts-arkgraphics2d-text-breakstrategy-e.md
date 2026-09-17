# BreakStrategy

Enumerates the text break strategies.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## GREEDY

```TypeScript
GREEDY = 0
```

Fills the current line as much as possible without adding hyphens.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## HIGH_QUALITY

```TypeScript
HIGH_QUALITY = 1
```

Optimizes layout and may add hyphens when necessary.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## BALANCED

```TypeScript
BALANCED = 2
```

Ensures consistent line width in a paragraph, adding hyphens if needed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
