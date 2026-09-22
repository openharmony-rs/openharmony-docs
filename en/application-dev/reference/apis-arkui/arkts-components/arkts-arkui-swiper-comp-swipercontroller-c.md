# SwiperController

```TypeScript
declare class SwiperController
```

Implements the controller for the **Swiper** component. Bind this object to a **Swiper** component to control page turning and other functionalities.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(index: number, useAnimation?: boolean)
```

Goes to a specified page.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target page in the **Swiper** component.<br>**NOTE:** <br>If the value specified is less than 0 or greater than the maximum page index, the value **0** is used. |
| useAnimation | boolean | No | Whether to use an animation for when the target page is reached. The value **true** means to use an animation, and **false** means the opposite.<br>Default value: **false** |

<a id="changeindex-1"></a>

## changeIndex

```TypeScript
changeIndex(index: number, animationMode?: SwiperAnimationMode | boolean)
```

Moves to a specific page.

> **NOTE:** 
> 
> This API itself supports jumping without animation (set **animationMode** to **false** or
> **SwiperAnimationMode.NO_ANIMATION**). Avoid starting an animation with **changeIndex** and then interrupt it
> with **finishAnimation** to achieve animation-free jumping.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target page in the **Swiper** component.<br>**NOTE:** <br>If the value specified is less than 0 or greater than the maximum page index, the value **0** is used. |
| animationMode | [SwiperAnimationMode](arkts-arkui-swiper-comp-swiperanimationmode-e.md) &#124; boolean | No | Animation mode for moving to the specified page.<br> Default value: **SwiperAnimationMode.NO_ANIMATION**<br> **NOTE:** <br>The value **true** is equivalent to **SwiperAnimationMode.DEFAULT_ANIMATION**, which means to use the default animation. The value **false** is equivalent to **SwiperAnimationMode.NO_ANIMATION**, which means to use no animation. |

## constructor

```TypeScript
constructor()
```

A constructor used to create a **SwiperController** object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fakeDragBy

```TypeScript
fakeDragBy(offset: number): boolean
```

Sets the drag distance of drag simulation.

> **NOTE:** 
> 
> - The drag distance of drag simulation depends on the layout. You are advised to call this API before the layout,so that the drag effect can be displayed after the current frame layout. If this API is called multiple times before the layout, only the drag distance passed in the last call takes effect during the current frame layout.
> 
> - In the loop scenario where [loop](arkts-arkui-swiper-comp-attribute.md#loop) is set to **true**, if the drag distance of drag simulation is greater than the total layout length, the drag distance will be adjusted to the distance required to drag just far enough to display the first child node (when dragging toward the start of the layout) or the last child node (when dragging toward the end of the layout).
> 
> - The [onGestureSwipe](arkts-arkui-swiper-comp-attribute.md#ongestureswipe) and [onContentWillScroll](arkts-arkui-swiper-comp-attribute.md#oncontentwillscroll) events are not triggered during the drag. The [customContentTransition](arkts-arkui-swiper-comp-attribute.md#customcontenttransition) event is triggered before the layout.Since the actual drag distance may be adjusted during the layout, if the passed drag distance is too large, the returned node display information may be inconsistent with the layout result when the event is triggered.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | The drag distance to simulate the drag.<br> A positive number indicates that the layout is dragged to the start point. A negative number indicates dragging towards the end point of the layout. <br>Unit: vp.   - Drag distance of drag simulation.<br>A positive number indicates dragging towards the   start point of the layout, and a negative number indicates dragging towards the end point of the layout. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether to consume the passed drag distance.<br>**true** means to consume any passed drag distance; **false** means not to consume the passed drag distance because it is not in the drag simulation or has been dragged to the boundary. <br>If the drag distance is set to **0**, it cannot be consumed. |

## finishAnimation

```TypeScript
finishAnimation(callback?: VoidCallback)
```

Stops an animation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | No | Callback invoked when the animation stops.<br>**Since:** 18 |

## isFakeDragging

```TypeScript
isFakeDragging(): boolean
```

Obtains whether drag simulation is enabled.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the drag simulation is enabled.<br>**true** indicates that drag simulation is enabled; **false** indicates the opposite. |

## preloadItems

```TypeScript
preloadItems(indices: Optional<Array<number>>): Promise<void>
```

Preloads child nodes for **Swiper**. After this API is called, all specified child nodes will be loaded at once. Therefore, for performance considerations, it is recommended that you load child nodes in batches. This API uses a promise to return the result.

If the **SwiperController** object is not bound to any **Swiper** component, any attempt to call APIs on it will result in a JavaScript exception, together with the error code 100004. Therefore, you are advised to use **try-catch** to handle potential exceptions when calling APIs on **SwiperController**.

When combining with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) and custom components, be aware that [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) only retains custom components within the cache range. Components outside this range are removed. Therefore, make sure the indexes of nodes to be preloaded via this API are within the cache range to avoid issues.

> **NOTE:** 
> 
> **preloadItems** of **Swiper** needs to be called after **Swiper** is created. You are advised to control the
> first preloading in the [onAppear](arkts-arkui-common-comp-commonmethod-c.md#onappear) lifecycle of **Swiper**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indices | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Array&lt;number&gt;&gt; | Yes | Array of indexes of the child nodes to preload. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter invalid. Possible causes:<br> 1. The parameter type is not Array&lt;number&gt;. <br> 2. The parameter is an empty array. <br> 3. The parameter contains an invalid index. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to component. |

## showNext

```TypeScript
showNext()
```

Turns to the next page. The page turning includes a transition animation, with the duration set by the [duration](arkts-arkui-swiper-comp-attribute.md#duration) attribute of the **Swiper** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showPrevious

```TypeScript
showPrevious()
```

Turns to the previous page. The page turning includes a transition animation, with the duration set by the [duration](arkts-arkui-swiper-comp-attribute.md#duration) attribute of the **Swiper** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startFakeDrag

```TypeScript
startFakeDrag(): boolean
```

Enables drag simulation.

> **NOTE:** 
> 
> - If the **Swiper** component is dragged using real gestures or the drag simulation is enabled, the API returns
> **false**, indicating that the operation fails.
> 
> - Simulated drag cannot trigger nested scrolling.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether to enable drag simulation.<br>**true** if enabled; **false** the opposite |

## stopFakeDrag

```TypeScript
stopFakeDrag(): boolean
```

Disables drag simulation.

> **NOTE:** 
> 
> After drag simulation is enabled, it will end if a real drag gesture is received.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether drag simulation is disabled.<br>**true** indicates that drag simulation is disabled successfully; **false** indicates the opposite. |
