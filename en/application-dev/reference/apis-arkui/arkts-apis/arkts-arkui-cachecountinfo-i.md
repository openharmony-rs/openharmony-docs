# CacheCountInfo

```TypeScript
declare interface CacheCountInfo
```

Defines the number of cached items.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount: number
```

Maximum number of cached items. When the actual number of cached items exceeds this value, redundant items are recycled or released. The system loads items to reach the maximum count when the UI is idle (no animations or user interactions). Values less than **minCount** are clamped to **minCount**. Value range: [**minCount**, +∞).

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minCount

```TypeScript
minCount: number
```

Minimum number of cached items. When the actual number of cached items is lower than this value, cached items are loaded during idle intervals between scrolling animation frames. Values less than 0 are clamped to **1**. Value range: [0, +∞).

**Type:** number

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
