# FocusRule (System API)

```TypeScript
export type FocusRule = 'bypassSelf' | 'bypassSelfDescendants' |
'checkSelf' | 'checkSelfBypassDescendants'
```

Describes how to determine the focus capability of the starting node and its child nodes when searching for focusable nodes.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

| Type | Description |
| --- | --- |
| 'bypassSelf' | Skips the check on the starting node and only checks its child nodes. The value is fixed to the 'bypassSelf' string. |
| 'bypassSelfDescendants' | Skips the check on the starting node and all its child nodes. The value is fixed to the 'bypassSelfDescendants' string. |
| 'checkSelf' | Checks whether the starting node can gain focus first. If yes, uses it directly; if not, continues to check its child nodes. The value is fixed to the 'checkSelf' string. |
| 'checkSelfBypassDescendants' | Checks whether the starting node can gain focus first. If yes, uses it; if not, skips the check on all child nodes. The value is fixed to the 'checkSelfBypassDescendants' string. |
