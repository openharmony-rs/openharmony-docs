# ExpandMode

Enumerates the expansion mode of child nodes.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NOT_EXPAND

```TypeScript
NOT_EXPAND = 0
```

The child nodes of the current FrameNode are not expanded. If the FrameNode contains LazyForEach child nodes, the child nodes are not expanded when the nodes in the main tree are being obtained. The child node sequence numbers are calculated based on the nodes in the main tree.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EXPAND

```TypeScript
EXPAND = 1
```

The child nodes of the current FrameNode are expanded. If the FrameNode contains LazyForEach child nodes, all child nodes are expanded when being obtained. The child node sequence numbers are calculated based on all child nodes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAZY_EXPAND

```TypeScript
LAZY_EXPAND = 2
```

The child nodes of the current FrameNode are expanded on demand. If the FrameNode contains LazyForEach child nodes, the child nodes are not expanded when the nodes in the main tree are being obtained, but are expanded when nodes not in the main tree are being obtained. The child node sequence numbers are calculated based on all child nodes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAZY_NOT_EXPAND

```TypeScript
LAZY_NOT_EXPAND = 3
```

The child nodes of the current FrameNode are not expanded. If the FrameNode contains LazyForEach child nodes, expanded child nodes can be obtained directly. To obtain the child nodes that are not expanded, only the nodes at the corresponding positions are created, and all child nodes are not expanded. The child node sequence numbers are calculated based on all child nodes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
