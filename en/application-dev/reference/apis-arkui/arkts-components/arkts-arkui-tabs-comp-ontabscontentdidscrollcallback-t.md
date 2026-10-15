# OnTabsContentDidScrollCallback

```TypeScript
declare type OnTabsContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void
```

Triggered when the **Tabs** is swiped.

> **NOTE:** 
> 
> - For example, when the index of the currently selected tab is 0, during a transition animation from page 0 to page 1, the callback is triggered for all pages within the viewport on every frame. When pages 0 and 1 are both in the viewport, the callback is triggered twice per frame. The first callback has **selectedIndex** as **0**, **index**as **0**, **position** as the ratio of how much page 0 has moved relative to its position before the animation started on the current frame, and **mainAxisLength** as the length of page 0 on the main axis. The second callback has **selectedIndex** as **0**, **index** as **1**, **position** as the ratio of how much page 1 has moved relative to page 0 before the animation started on the current frame, and **mainAxisLength** as the length of page 1 on the main axis.
> 
> - If the animation curve is a spring interpolation curve, during the transition animation from page 0 to page 1,due to the position and velocity when the user lifts their finger off the screen, animation may overshoot and slide past to page 2, then bounce back to page 1. Throughout this process, a callback is triggered for pages 1 and 2within the viewport on every frame.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-declare type OnTabsContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void--><!--Device-unnamed-declare type OnTabsContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedIndex | number | Yes | Index of the currently selected page. For example, when the index of the currently selected tab is 0, during a transition animation from page 0 to page 1, **selectedIndex** is **0** in every callback. |
| index | number | Yes | Index of the page within the viewport. For example, during page swiping, when pages 0 and 1 are both in the viewport, the callback is triggered twice per frame. The first callback has **index** as **0**, and the second callback has **index** as **1**. |
| position | number | Yes | Ratio of how much the page indicated by **index** has moved relative to the start position of the **Tabs** main axis (the start position of the page corresponding to **selectedIndex**). For example, in a horizontal **Tabs**, when the index of the currently selected tab is 0, during a transition animation from page 0 to page 1 by swiping left, if on a certain frame pages 0 and 1 occupy 30% and 70% of the viewport respectively, the callback is triggered twice on the current frame. The first callback has **position** as **-0.7**, indicating that page 0 is on the left of the start position of the **Tabs** main axis on the current frame, and the left edge of page 0 is 70% of the viewport away from the start position of the **Tabs** main axis, that is, page 0 has moved left by 70% of the viewport. The second callback has **position** as **0.3**, indicating that page 1 is on the right of the start position of the **Tabs** main axis on the current frame, and the left edge of page 1 is 30% of the viewport away from the start position of the **Tabs** main axis. In fact, page 1 has also moved left by 70% of the viewport. |
| mainAxisLength | number | Yes | Length of the page corresponding to **index** on the main axis, in vp. For example, if **index** is **0** in a callback and **mainAxisLength** is **360** in that callback, the length of page 0 on the main axis on the current frame is 360 vp. For a horizontal **Tabs**, this represents the page width; for a vertical **Tabs**, this represents the page height. |
