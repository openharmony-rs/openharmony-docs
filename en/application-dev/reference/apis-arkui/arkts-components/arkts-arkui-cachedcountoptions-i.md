# CachedCountOptions

Describes the configuration options for child components to be preloaded.

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## independent

```TypeScript
independent?: boolean
```

Whether to calculate [cachedCount](arkts-arkui-swiper-comp-attribute.md#cachedcount) by group.

**true**: **cachedCount** is calculated based on the actual number of child components, not by group.

**false**: If **displayCount.swipeByGroup=true**, **cachedCount** is calculated by group. Otherwise, it is calculated based on the actual number of child components.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
