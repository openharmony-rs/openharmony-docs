# FrameNode

Provides APIs for creating a specific type of FrameNode, which can be mounted through the basic API of the FrameNode and be displayed using a placeholder container.

When **typeNode** is used to create Text, Image, Select, or Toggle nodes, if the UI instance corresponding to the input [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) is destroyed, this API returns an invalid FrameNode that cannot be properly mounted or displayed.

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [typeNode](arkts-arkui-typenode-n.md) | Provides APIs for creating a specific type of FrameNode, which can be mounted through the basic API of the FrameNode and be displayed using a placeholder container. |

### Classes

| Name | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | **FrameNode** represents an entity node in the component tree. It can be used by a [NodeController](arkts-arkui-nodecontroller-c.md) to mount a BuilderNode (that holds the FrameNode) to a NodeContainer or mount a [RenderNode](arkts-arkui-rendernode-c.md) to another FrameNode.&lt;!--RP2--&gt;&lt;!--RP2End--&gt; |
| [NodeAdapter](arkts-arkui-framenode-nodeadapter-c.md) | Provides lazy loading capabilities for FrameNode data, implementing LazyForEach API functionality. |

### Interfaces

| Name | Description |
| --- | --- |
| [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | Provides options for configuring or querying the cross-language access permissions for a FrameNode. For example, for nodes created using ArkTS, this API can control whether non-ArkTS languages are allowed to access or modify the attributes of these nodes. |
| [InteractionEventBindingInfo](arkts-arkui-framenode-interactioneventbindinginfo-i.md) | Describes the binding state of interaction events on components. When querying reveals an interaction event bound to the current node, this object provides detailed event binding information. |
| [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | Describes the layout constraints of the component. |
| [TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md) | Extends [FrameNode](arkts-arkui-framenode-c.md) to define a FrameNode with specific type constraints. |

### Enums

| Name | Description |
| --- | --- |
| [ChildrenCountMode](arkts-arkui-framenode-childrencountmode-e.md) | Enumerates the modes of counting child nodes. |
| [ExpandMode](arkts-arkui-framenode-expandmode-e.md) | Enumerates the expansion mode of child nodes. |
| [UIState](arkts-arkui-framenode-uistate-e.md) | Enumerates polymorphic style states, which are used to process polymorphic styles. |

### Types

| Name | Description |
| --- | --- |
| [UIStatesChangeHandler](arkts-arkui-uistateschangehandler-t.md) | Defines the callback triggered when the UI state changes. Defines the callback triggered on UI state changes. It receives the current [UIState](arkts-arkui-framenode-uistate-e.md) value when triggered. The parameter represents **UIState** enumerated values or their bitwise combinations. |
