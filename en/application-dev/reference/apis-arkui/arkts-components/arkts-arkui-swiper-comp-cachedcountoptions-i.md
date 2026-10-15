# CachedCountOptions

```TypeScript
declare interface CachedCountOptions
```

Describes the configuration options for child components to be preloaded.

**Since:** 24

<!--Device-unnamed-declare interface CachedCountOptions--><!--Device-unnamed-declare interface CachedCountOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## independent

```TypeScript
independent?: boolean
```

Whether [cachedCount](arkts-arkui-swiper-comp-attribute.md#cachedcount3) is calculated based on the actual number of child components.

When set to **true**, **cachedCount** is calculated based on the actual number of child components instead of by group.

When set to **false**, if **displayCount.swipeByGroup** is **true**, **cachedCount** is calculated by group; otherwise, it is calculated based on the actual number of child components.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

<!--Device-CachedCountOptions-independent?: boolean--><!--Device-CachedCountOptions-independent?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

Whether to draw nodes within the preloading range.

**true**: yes.

**false**: no.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

<!--Device-CachedCountOptions-isShown?: boolean--><!--Device-CachedCountOptions-isShown?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
