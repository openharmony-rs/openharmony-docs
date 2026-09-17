# FocusMoveResultCode (System API)

Enumerates the result codes returned by the focusable node query.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## NOT_SUPPORTED

```TypeScript
NOT_SUPPORTED = -1
```

Query is not supported.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SEARCH_SUCCESS

```TypeScript
SEARCH_SUCCESS = 0
```

The node is queried successfully.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SEARCH_SUCCESS_NEXT_BYPASS_DESCENDANTS

```TypeScript
SEARCH_SUCCESS_NEXT_BYPASS_DESCENDANTS = 1
```

The node query is successful. It is recommended to use the parameter bypassSelfDescendants in the next query to improve query efficiency.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SEARCH_FAILURE

```TypeScript
SEARCH_FAILURE = 2
```

Failed to query the node. The current page has no focusable node.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SEARCH_FAILURE_IN_CHILD_TREE

```TypeScript
SEARCH_FAILURE_IN_CHILD_TREE = 3
```

Failed to query the node. The current container has no focusable node.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SEARCH_FAILURE_LOST_NODE

```TypeScript
SEARCH_FAILURE_LOST_NODE = 4
```

Failed to query the node. The start node is not found.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SEARCH_NEXT

```TypeScript
SEARCH_NEXT = 5
```

The returned node is not focusable. Continue to query from the returned node.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## DOUBLE_CHECK_CHILD_PROPERTY

```TypeScript
DOUBLE_CHECK_CHILD_PROPERTY = 6
```

The returned node is not focusable. Continue to query from all descendants of the returned node.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## DOUBLE_CHECK_CHILD_PROPERTY_AND_GET_LAST

```TypeScript
DOUBLE_CHECK_CHILD_PROPERTY_AND_GET_LAST = 7
```

The returned node is not focusable. Continue to query from the last child node of the returned node.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## SEARCH_FAILURE_IN_SCROLL

```TypeScript
SEARCH_FAILURE_IN_SCROLL = 8
```

Failed to query the node in the scrollable component.

**Since:** 23

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
