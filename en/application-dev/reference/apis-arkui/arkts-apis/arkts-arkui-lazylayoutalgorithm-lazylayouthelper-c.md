# LazyLayoutHelper

Helper class for lazy layout algorithm. Provides layout direction and view position information for lazy layout.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLazyLayoutDirection

```TypeScript
getLazyLayoutDirection(): LazyLayoutDirection
```

Get the lazy layout direction.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LazyLayoutDirection](arkts-arkui-lazylayoutalgorithm-lazylayoutdirection-e.md) | The lazy layout direction. |

## getViewEnd

```TypeScript
getViewEnd(): number
```

Get the end position of the visible view.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | The end position of the visible view.<br>Unit: px. |

## getViewStart

```TypeScript
getViewStart(): number
```

Get the start position of the visible view.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | The start position of the visible view.<br>Unit: px. |

## setAdjustedOffset

```TypeScript
setAdjustedOffset(offset: number): void
```

Set the adjusted offset for the lazy layout.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | The adjusted offset value to set.<br>Unit: px. |

## setChildrenInactive

```TypeScript
setChildrenInactive(children: number[]): void
```

Set children inactive.

If child components are generated via ForEach or Repeat without virtualScroll, they will not be displayed after being set to inactive. If child components are generated via LazyForEach or Repeat with virtualScroll, they will be destroyed or recycled after being set to inactive. LazyForEach and Repeat with virtualScroll only support consecutive active child components; setting a child component to inactive between two active child components will not take effect. Child components laid out outside the display area will be automatically set to inactive.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| children | number[] | Yes | The indices of child components to set inactive. |
