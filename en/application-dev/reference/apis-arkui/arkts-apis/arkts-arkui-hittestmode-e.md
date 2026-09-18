# HitTestMode

Sets the response logic and node blocking rules for the hit test.

> **NOTE:** 
> 
> When multiple nodes in a **Stack** component have overlapping touch areas, if the touch point hits a child
> component of the topmost node, only the topmost node will undergo hit testing by default. In this case, touch
> testing for lower-layer nodes can only be triggered by setting the
> [hitTestBehavior](../arkts-components/arkts-arkui-commonmethod-c.md#hittestbehavior) of the topmost node to **HitTestMode.Transparent**.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## Default

```TypeScript
Default
```

Default hit test mode. The node itself and its child nodes respond to the hit test, but block the hit test of sibling nodes. It does not affect the hit test of ancestor nodes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## Block

```TypeScript
Block
```

The node itself responds to the hit test and blocks the hit test of child nodes, sibling nodes, and ancestor nodes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## Transparent

```TypeScript
Transparent
```

Both the node itself and its child nodes respond to the hit test and do not block the hit test of sibling nodes and ancestor nodes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## None

```TypeScript
None
```

The node itself does not respond to the hit test and does not block the hit test of child nodes, sibling nodes, and ancestor nodes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## BLOCK_HIERARCHY

```TypeScript
BLOCK_HIERARCHY
```

The node itself and its child nodes respond to the hit test, preventing all sibling nodes and parent nodes with lower priority from participating in the hit test.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

## BLOCK_DESCENDANTS

```TypeScript
BLOCK_DESCENDANTS
```

The node itself does not respond to the hit test, and all its descendants (children, grandchildren, and more) also do not respond to the hit test. It does not affect the hit test of ancestor nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.
