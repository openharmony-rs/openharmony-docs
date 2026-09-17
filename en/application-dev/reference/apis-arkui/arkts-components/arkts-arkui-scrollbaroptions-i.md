# ScrollBarOptions

Parameters of the **ScrollBar** component.

> **NOTE:** 
> 
> - The **ScrollBar** component defines the behavior style of the scrollable area, and its child nodes define the behavior style of the scrollbar.
> 
> - This component is bound to a scrollable component through **scroller**, and can be used to scroll the scrollable component only when their directions are the same. The **ScrollBar** component can be bound to only one scrollable component, and vice versa.
> 
> - Since API version 12, the **ScrollBar** component displays a default scrollbar style when without child nodes.
> 
> - The visibility of the **ScrollBar** component is set through **BarState**. The component automatically adjusts
> **opacity** based on the **BarState** setting to control its visibility. Therefore, setting the
> opacity attribute for the **ScrollBar**
> component does not take effect.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: ScrollBarDirection
```

Scrollbar direction in which scrollable components scroll.<br>Default value: **ScrollBarDirection.Vertical**

**Type:** [ScrollBarDirection](arkts-arkui-scrollbardirection-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller: Scroller
```

Scroller, which can be bound to scrollable components for scrolling control.

**Type:** [Scroller](arkts-arkui-scroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: BarState
```

Scrollbar state.<br>Default value: **BarState.Auto**

**Type:** [BarState](../arkts-apis/arkts-arkui-barstate-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
