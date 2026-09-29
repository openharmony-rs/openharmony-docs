# FrameNode

Provides APIs for creating a specific type of FrameNode, which can be mounted through the basic API of the FrameNode and be displayed using a placeholder container. It is suitable for scenarios where component nodes of specific types need to be dynamically created through code and custom-mounted.

When **typeNode** is used to create [Text](../arkts-components/arkts-arkui-text-comp.md), [Image](../arkts-components/arkts-arkui-image-comp.md), [Select](../arkts-components/arkts-arkui-select-comp.md), or [Toggle](../arkts-components/arkts-arkui-toggle-comp.md) nodes, if the UI instance corresponding to the input [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) is destroyed, this API returns an invalid FrameNode that cannot be properly mounted or displayed.

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [typeNode](arkts-arkui-typenode-n.md) | Provides APIs for creating a specific type of FrameNode, which can be mounted through the basic API of the FrameNode and be displayed using a placeholder container. It is suitable for scenarios where component nodes of specific types need to be dynamically created through code and custom-mounted. |

### Classes

| Name | Description |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | **FrameNode** represents an entity node in the component tree, supporting capabilities such as node tree operations, custom drawing and layout, position query, and animation. It can be used by a [NodeController](arkts-arkui-nodecontroller-c.md) to mount a [BuilderNode](arkts-arkui-buildernode-c.md) (that holds the FrameNode) to a [NodeContainer](../arkts-components/arkts-arkui-nodecontainer-comp-attribute.md#nodecontainerattribute) or mount a [RenderNode](arkts-arkui-rendernode-c.md) to another FrameNode. It is suitable for scenarios where component node trees need to be dynamically created and managed through code, enabling flexible UI composition and custom rendering requirements that cannot be directly met by declarative components. |
| [NodeAdapter](arkts-arkui-framenode-nodeadapter-c.md) | Provides lazy loading capabilities for FrameNode data, implementing API functionality through [LazyForEach](../arkts-components/arkts-arkui-lazyforeach-comp.md). It is suitable for scenarios such as long lists where node data needs to be loaded on demand, improving rendering performance and reducing memory usage. |

### Interfaces

| Name | Description |
| --- | --- |
| [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | Provides options for configuring or querying the cross-language access permissions for a FrameNode. For example, for nodes created using ArkTS, this API can control whether non-ArkTS languages are allowed to access or modify the attributes of these nodes. |
| [InteractionEventBindingInfo](arkts-arkui-framenode-interactioneventbindinginfo-i.md) | Describes the binding state of interaction events on components. When querying reveals an interaction event bound to the current node, this object provides detailed event binding information. |
| [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | Describes the layout constraints of the component. |
| [TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md) | Extends [FrameNode](arkts-arkui-framenode-c.md) to define a FrameNode with specific type constraints. It supports various component types such as **Text**, **Image**, **Button**, and **Column**, and is suitable for scenarios where component nodes of specific types need to be dynamically created through code. |

### Types

| Name | Description |
| --- | --- |
| [UIStatesChangeHandler](arkts-arkui-uistateschangehandler-t.md) | Defines the callback triggered when the UI state changes. It receives the current [UIState](arkts-arkui-framenode-uistate-e.md) value when triggered. The parameter represents **UIState** enumerated values or their bitwise combinations. |

### Enums

| Name | Description |
| --- | --- |
| [ChildrenCountMode](arkts-arkui-framenode-childrencountmode-e.md) | Enumerates the modes of counting child nodes. |
| [ExpandMode](arkts-arkui-framenode-expandmode-e.md) | Enumerates the expansion mode of child nodes. |
| [UIState](arkts-arkui-framenode-uistate-e.md) | Enumerates polymorphic style states, which are used to process polymorphic styles. |
