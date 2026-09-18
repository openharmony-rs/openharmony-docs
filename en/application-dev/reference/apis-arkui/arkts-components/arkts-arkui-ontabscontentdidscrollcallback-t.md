# OnTabsContentDidScrollCallback

```TypeScript
declare type OnTabsContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void
```

Defines the callback triggered when content in the **Tabs** component scrolls.  
> **NOTE:** 
> 
> - For example, when the index of the currently selected tab page is **0**, during a transition animation from page 0 to page 1, the callback is triggered for all pages within the viewport on every frame. When pages 0 and 1 are both in the viewport, the callback is triggered twice per frame. The first callback has **selectedIndex** as **0**,
> **index** as **0**, **position** as the ratio of how much page 0 has moved relative to its position before the
> animation started on the current frame, and **mainAxisLength** as the length of page 0 on the main axis. The second
> callback has **selectedIndex** as **0**, **index** as **1**, **position** as the ratio of how much page 1 has moved
> relative to page 0 before the animation started on the current frame, and **mainAxisLength** as the length of page
> 1 on the main axis.
> 
> - If the animation curve is a spring interpolation curve, during the transition animation from page 0 to page 1,due to the position and velocity when the user lifts their finger off the screen, animation may overshoot and slide past to page 2, then bounce back to page 1. Throughout this process, a callback is triggered for pages 1 and 2within the viewport on every frame.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedIndex | number | Yes | Index of the currently selected page. For example, if the index of the currently selected tab page is **0**, the value of **selectedIndex** in each callback is **0** during the animation of switching from page 0 to page 1. |
| index | number | Yes | Index of a page in the viewport. For example, if there are two pages (page 0 and page 1) in the viewport during page transition, the callback is triggered twice in each frame. In the first callback, the index is 0. In the second callback, the index is 1. |
| position | number | Yes | Position of the page specified by **index** relative to the start position of the **Tabs** main axis (start position of the page corresponding to **selectedIndex**). For example, in a horizontal **Tabs** component, with the currently selected tab index being 0, if a frame occurs where page 0 occupies 30% of the viewport and page 1 occupies 70%, two callbacks will be triggered for that frame during the animation from page 0 to page 1 (switching left). In the first callback, the value of **position** is **-0.7**, indicating that page 0 in the current frame is on the left of the start position of the main axis of **Tabs**, and its left edge is 70% of the viewport away from the starting position (meaning page 0 has moved left by 70% of the viewport). In the second callback, the value of **position** is **0.3**, indicating that page 1 in the current frame is on the right of the start position of the main axis of **Tabs**, and its left edge is 30% of the viewport away from the starting position (meaning page 1 has moved left by 70% of the viewport). |
| mainAxisLength | number | Yes | Length of the page specified by **index** along the main axis, in vp. For example, if the index of a callback is **0** and the **mainAxisLength** of this callback is **360**, the length of page 0 of the current frame in the main axis direction is 360 vp. This parameter indicates the page width for horizontal tabs, and the page height for vertical tabs. |
