# BreakStrategy

```TypeScript
enum BreakStrategy
```

Enumerates the text break strategies.

**Since:** 12

<!--Device-text-enum BreakStrategy--><!--Device-text-enum BreakStrategy-End-->

**System capability:** SystemCapability.Graphics.Drawing

## GREEDY

```TypeScript
GREEDY = 0
```

Fills the current line as much as possible without adding hyphens.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-BreakStrategy-GREEDY = 0--><!--Device-BreakStrategy-GREEDY = 0-End-->

**System capability:** SystemCapability.Graphics.Drawing

## HIGH_QUALITY

```TypeScript
HIGH_QUALITY = 1
```

Optimizes layout and may add hyphens when necessary.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-BreakStrategy-HIGH_QUALITY = 1--><!--Device-BreakStrategy-HIGH_QUALITY = 1-End-->

**System capability:** SystemCapability.Graphics.Drawing

## BALANCED

```TypeScript
BALANCED = 2
```

Ensures consistent line width in a paragraph, adding hyphens if needed.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-BreakStrategy-BALANCED = 2--><!--Device-BreakStrategy-BALANCED = 2-End-->

**System capability:** SystemCapability.Graphics.Drawing
