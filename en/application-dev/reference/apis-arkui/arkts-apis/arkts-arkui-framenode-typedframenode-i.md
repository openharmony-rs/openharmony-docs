# TypedFrameNode

```TypeScript
export interface TypedFrameNode<C, T> extends FrameNode
```

Extends [FrameNode](arkts-arkui-framenode-c.md) to define a FrameNode with specific type constraints. It supports various component types such as **Text**, **Image**, **Button**, and **Column**, and is suitable for scenarios where component nodes of specific types need to be dynamically created through code.

**Inheritance/Implementation:** TypedFrameNode extends [FrameNode](arkts-arkui-framenode-c.md)

**Since:** 12

<!--Device-unnamed-export interface TypedFrameNode<C, T> extends FrameNode--><!--Device-unnamed-export interface TypedFrameNode<C, T> extends FrameNode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## attribute

```TypeScript
readonly attribute: T
```

Obtains the attribute setting object of the corresponding component to set or update its common and private attributes.

**Type:** T

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TypedFrameNode-readonly attribute: T--><!--Device-TypedFrameNode-readonly attribute: T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
initialize: C
```

Passes construction parameters for creating a component, used to set or update the component's initial values.

**Type:** C

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TypedFrameNode-initialize: C--><!--Device-TypedFrameNode-initialize: C-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
