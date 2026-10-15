# LazyLayoutHelper

```TypeScript
export class LazyLayoutHelper
```

Lazy loading layout auxiliary class, which provides the layout direction and visible area position information.

**Since:** 26.0.0

<!--Device-unnamed-export class LazyLayoutHelper--><!--Device-unnamed-export class LazyLayoutHelper-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLazyLayoutDirection

```TypeScript
getLazyLayoutDirection(): LazyLayoutDirection
```

Obtains the lazy loading layout direction. This API can be used to determine whether to start layout from the beginning or end of the content in custom measurement.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyLayoutHelper-getLazyLayoutDirection(): LazyLayoutDirection--><!--Device-LazyLayoutHelper-getLazyLayoutDirection(): LazyLayoutDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LazyLayoutDirection](arkts-arkui-lazylayoutalgorithm-lazylayoutdirection-e.md) | Lazy loading layout direction. |

## getViewEnd

```TypeScript
getViewEnd(): number
```

Obtains the end position of the visible area. It can be used together with [getViewStart](#getviewstart) to determine the visible area range for custom measurement.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyLayoutHelper-getViewEnd(): int--><!--Device-LazyLayoutHelper-getViewEnd(): int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | End position of the visible area.<br>The unit is px. |

## getViewStart

```TypeScript
getViewStart(): number
```

Obtains the start position of the visible area. It can be used together with [getViewEnd](#getviewend) to determine the visible area range for custom measurement.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyLayoutHelper-getViewStart(): int--><!--Device-LazyLayoutHelper-getViewStart(): int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Start position of the visible area.<br>The unit is px. |

## setAdjustedOffset

```TypeScript
setAdjustedOffset(offset: number): void
```

Sets an adjusted offset for lazy loading.

When parameters such as the number of layout columns and spacing change, this API needs to be called to adjust the offset to keep the relative position of the first child component in the visible area unchanged.

Take the vertical layout as an example. When the layout direction is **LazyLayoutDirection.FORWARD**, the offset set by this API is the adjustment value of the upper boundary of the container. When the layout direction is **LazyLayoutDirection.BACKWARD**, the offset set by this API is the adjustment value of the lower boundary of the container.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyLayoutHelper-setAdjustedOffset(offset: int): void--><!--Device-LazyLayoutHelper-setAdjustedOffset(offset: int): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Adjusted offset. A positive value indicates that the position is adjusted towards the end of the content, and a negative value indicates that the position is adjusted towards the start of the content. The unit is px.<br>The value should be an integer. |

## setChildrenInactive

```TypeScript
setChildrenInactive(children: number[]): void
```

Sets a child component to the inactive state.

If a child component is generated through [ForEach](../arkts-components/arkts-arkui-foreach-comp-attribute.md#foreachattribute) or [Repeat](../arkts-components/arkts-arkui-repeat-comp.md) (with [virtualScroll](../arkts-components/arkts-arkui-repeat-comp-attribute.md#virtualscroll) disabled), it will not be displayed after being set to the inactive state.

If a child component is generated through [LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md) or [Repeat](../arkts-components/arkts-arkui-repeat-comp.md) (with [virtualScroll](../arkts-components/arkts-arkui-repeat-comp-attribute.md#virtualscroll) enabled), it will be destroyed or recycled after being set to the inactive state.

[LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md) or [Repeat](../arkts-components/arkts-arkui-repeat-comp.md) (with [virtualScroll](../arkts-components/arkts-arkui-repeat-comp-attribute.md#virtualscroll) enabled) supports only consecutive active child components. Setting a child component to the inactive state between two active child components does not take effect.

Child components outside the visible area are automatically set to the inactive state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyLayoutHelper-setChildrenInactive(children: int[]): void--><!--Device-LazyLayoutHelper-setChildrenInactive(children: int[]): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| children | number[] | Yes | Index array of child components to be set to the inactive state. An index must be a non-negative integer within the range [0, Total child components - 1]. The index outside this range does not take effect. |
