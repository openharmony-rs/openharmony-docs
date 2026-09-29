# ExpandMode

```TypeScript
export enum ExpandMode
```

Enumerates the expansion mode of child nodes.

**Since:** 15

<!--Device-unnamed-export enum ExpandMode--><!--Device-unnamed-export enum ExpandMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NOT_EXPAND

```TypeScript
NOT_EXPAND = 0
```

The child nodes of the current FrameNode are not expanded. If the FrameNode contains [LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md) child nodes, the child nodes of the current FrameNode are not expanded when the child nodes on the main node tree are being obtained. The child node sequence numbers are calculated based on the child nodes on the main node tree.

Application scenario: Only expanded child nodes on the main node tree need to be obtained without triggering expansion.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ExpandMode-NOT_EXPAND = 0--><!--Device-ExpandMode-NOT_EXPAND = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EXPAND

```TypeScript
EXPAND = 1
```

The child nodes of the current FrameNode are expanded. If the FrameNode contains [LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md) child nodes, the child nodes of the current FrameNode are expanded when all child nodes are being obtained. The child node sequence numbers are calculated based on all child nodes.

Application scenario: All child nodes, including lazy loading ones, need to be obtained.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ExpandMode-EXPAND = 1--><!--Device-ExpandMode-EXPAND = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAZY_EXPAND

```TypeScript
LAZY_EXPAND = 2
```

The child nodes of the current FrameNode are expanded on demand. If the FrameNode contains [LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md) child nodes, the child nodes of the current FrameNode are not expanded when the child nodes on the main node tree are being obtained, and are expanded when the child nodes not on the main node tree are being obtained. The child node sequence numbers are calculated based on all child nodes.

Application scenario: Child nodes on both the main node tree and non-main node tree need to be obtained on demand.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ExpandMode-LAZY_EXPAND = 2--><!--Device-ExpandMode-LAZY_EXPAND = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAZY_NOT_EXPAND

```TypeScript
LAZY_NOT_EXPAND = 3
```

The child nodes of the current FrameNode are not expanded. If the FrameNode contains [LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md) child nodes, already expanded child nodes can be returned directly. When obtaining unexpanded child nodes, only the node at the corresponding position is created without expanding all child nodes. The child node sequence numbers are calculated based on all child nodes.

Application scenario: Child nodes need to be obtained precisely by position without batch expansion of lazy loading child nodes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExpandMode-LAZY_NOT_EXPAND = 3--><!--Device-ExpandMode-LAZY_NOT_EXPAND = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
