# CallbackParamV2

```TypeScript
export interface CallbackParamV2
```

Defines the node callback parameter API, used to pass parameter information of node event callbacks.

**Since:** 26.0.0

<!--Device-unnamed-export interface CallbackParamV2--><!--Device-unnamed-export interface CallbackParamV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## childIndex

```TypeScript
childIndex?: number
```

Child index.

Value range: greater than or equal to -1.

Default value: **-1**

Valid only in the node move event, indicating the position index after the move.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CallbackParamV2-childIndex?: number--><!--Device-CallbackParamV2-childIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId: number
```

ID of the current node.

Value range: greater than or equal to 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CallbackParamV2-currentNodeId: number--><!--Device-CallbackParamV2-currentNodeId: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: number
```

ID of the current parent node.

Value range: greater than or equal to -1.

Default value: **-1**

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CallbackParamV2-parentNodeId?: number--><!--Device-CallbackParamV2-parentNodeId?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
