# CallbackParam

```TypeScript
export interface CallbackParam
```

Declare CallbackParam.

**Since:** 10

<!--Device-unnamed-export interface CallbackParam--><!--Device-unnamed-export interface CallbackParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## childIndex

```TypeScript
childIndex?: number
```

Index of the child node under the parent node, used to identify the position of the child node in the parent node's child list.

Value range: greater than or equal to -1, where -1 indicates an invalid index or no child node.

Default value: **-1**

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CallbackParam-childIndex?: number--><!--Device-CallbackParam-childIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId: number
```

ID of the current child node.

The value must be greater than or equal to 0.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CallbackParam-currentNodeId: number--><!--Device-CallbackParam-currentNodeId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: number
```

ID of the current parent node.

The value must be greater than or equal to -1.

Default value: **-1**

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CallbackParam-parentNodeId?: number--><!--Device-CallbackParam-parentNodeId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
