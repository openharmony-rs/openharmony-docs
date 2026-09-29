# ScrollBarOptions

```TypeScript
declare interface ScrollBarOptions
```

Parameters of the **ScrollBar** component.

> **NOTE:** 
> 
> - The ScrollBar component is used to display and control the scroll position of the bound scrollable component.When child components are set, the child component serves as a custom scrollbar slider and moves with the scroll position of the scrollable component.
> 
> - The scrollbar component is bound to the scrollable component through a Scroller, and they can be linked only when their directions are the same. A scrollable component can be bound to multiple ScrollBar components, while a ScrollBar component can be bound to only one scrollable component.
> 
> - Since API version 12, the ScrollBar component supports displaying a scrollbar in the default style when it has no child nodes.
> 
> - The visibility of the ScrollBar component is set through BarState. The component automatically adjusts opacity based on the BarState setting to control visibility. Therefore, the [opacity](arkts-arkui-common-comp-commonmethod-c.md#opacity-1) attribute set for the ScrollBar component does not take effect.

**Since:** 8

<!--Device-unnamed-declare interface ScrollBarOptions--><!--Device-unnamed-declare interface ScrollBarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: ScrollBarDirection
```

Scrollbar direction in which scrollable components scroll.<br>Default value: **ScrollBarDirection.Vertical**

**Type:** [ScrollBarDirection](arkts-arkui-scrollbar-comp-scrollbardirection-e.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollBarOptions-direction?: ScrollBarDirection--><!--Device-ScrollBarOptions-direction?: ScrollBarDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller: Scroller
```

Scroller, which can be bound to scrollable components for scrolling control.

**Type:** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollBarOptions-scroller: Scroller--><!--Device-ScrollBarOptions-scroller: Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: BarState
```

Scrollbar state.<br>Default value: **BarState.Auto**

**Type:** [BarState](../arkts-apis/arkts-arkui-barstate-e.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollBarOptions-state?: BarState--><!--Device-ScrollBarOptions-state?: BarState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
