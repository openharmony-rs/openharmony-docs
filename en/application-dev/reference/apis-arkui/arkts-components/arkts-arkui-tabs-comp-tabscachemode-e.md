# TabsCacheMode

```TypeScript
declare enum TabsCacheMode
```

Enumerates the caching modes for child components.

**Since:** 19

<!--Device-unnamed-declare enum TabsCacheMode--><!--Device-unnamed-declare enum TabsCacheMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CACHE_BOTH_SIDE

```TypeScript
CACHE_BOTH_SIDE = 0
```

Cache the currently displayed child component and the child components on both sides. For example, if **cachedMaxCount** is set to **n**, up to 2n+1 child components will be cached.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-TabsCacheMode-CACHE_BOTH_SIDE = 0--><!--Device-TabsCacheMode-CACHE_BOTH_SIDE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CACHE_LATEST_SWITCHED

```TypeScript
CACHE_LATEST_SWITCHED = 1
```

Cache the currently displayed child component and the most recently switched child component. For example, if **cachedMaxCount** is set to **n**, up to n+1 child components will be cached.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-TabsCacheMode-CACHE_LATEST_SWITCHED = 1--><!--Device-TabsCacheMode-CACHE_LATEST_SWITCHED = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
