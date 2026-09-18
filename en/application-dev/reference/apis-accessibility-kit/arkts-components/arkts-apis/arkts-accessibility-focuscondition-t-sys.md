# FocusCondition (System API)

```TypeScript
export type FocusCondition = 'forward' | 'backward' |
'findLast' | 'getForwardScrollAncestor' | 'getBackwardScrollAncestor' | 'getScrollableAncestor'
```

Describes the method for querying focusable nodes.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

| Type | Description |
| --- | --- |
| 'forward' | The next focusable node after the current node. The value is fixed to the 'forward'string. |
| 'backward' | The previous focusable node before the current node. The value is fixed to the 'backward'string. |
| 'findLast' | The last node among the child nodes of the starting node. The value is fixed to the 'findLast' string. |
| 'getForwardScrollAncestor' | The scrollable parent component that supports forward scrolling. The value is fixed to the 'getForwardScrollAncestor' string. |
| 'getBackwardScrollAncestor' | The scrollable parent component that supports backward scrolling. The value is fixed to the 'getBackwardScrollAncestor' string. |
| 'getScrollableAncestor' | The scrollable parent component that supports scrolling in any direction. The value is fixed to the 'getScrollableAncestor' string. |
