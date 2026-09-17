# ChildrenCountMode

Enumerates the modes of counting child nodes.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALL_EXPAND

```TypeScript
ALL_EXPAND = 0
```

Counting all child node after expansion. When a lazy loading node (for example, LazyForEach) is encountered, the node is expanded and the number of all child nodes is returned.

Whether to expand lazy loading nodes: yes

Application scenario: A node needs to be expanded and the number of all child nodes needs to be returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ONLY_EXPANDED

```TypeScript
ONLY_EXPANDED = 1
```

Counting currently expanded child nodes. Lazy loading nodes are not expanded, and only the number of currently expanded child nodes is returned. Lazy loading nodes that are not expanded are not included in the count.

Whether to expand lazy loading nodes: yes

Application scenario: Only the number of expanded child nodes needs to be queried.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALL_NOT_EXPAND

```TypeScript
ALL_NOT_EXPAND = 2
```

Counting all child nodes. Lazy loading nodes are not expanded, but the total number of potential child nodes (including both expanded and unexpanded lazy loading nodes) is returned. This counting mode provides the total number of potential child nodes without triggering any expansion.

Whether to expand lazy loading nodes: yes

Application scenario: This counting mode is used when the total number of all child nodes needs to be obtained. Unlike **ALL_EXPAND**, this mode does not expand child nodes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
