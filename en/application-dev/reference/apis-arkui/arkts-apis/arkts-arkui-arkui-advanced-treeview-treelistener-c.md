# TreeListener

```TypeScript
export declare class TreeListener
```

Defines a listener for the tree view component, which can be bound to the tree view component to listen for node changes of the tree. The same listener cannot control multiple tree view components. The listener internally maintains the mapping between event types and callback functions. When a user performs a node operation on the TreeView, the TreeView notifies the listener to trigger the corresponding callback function, and the developer can obtain node information in the callback and perform service processing.

**Since:** 10

<!--Device-unnamed-export declare class TreeListener--><!--Device-unnamed-export declare class TreeListener-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## off

```TypeScript
off(type: TreeListenType, callback?: (callbackParam: CallbackParam) => void): void
```

Cancels listening. Listening must be registered before it can be canceled. The same listener cannot control multiple tree view components.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeListener-off(type: TreeListenType, callback?: (callbackParam: CallbackParam) => void): void--><!--Device-TreeListener-off(type: TreeListenType, callback?: (callbackParam: CallbackParam) => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | Yes | Type of the listening event, used to specify the listening event to cancel. |
| callback | (callbackParam: CallbackParam) =&gt; void | No | Callback invoked when the corresponding listening event is triggered. Default value: **undefined**. When this parameter is passed, the listener for the corresponding node information is canceled; when not passed, all node information listeners of this type are canceled. |

## on

```TypeScript
on(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void
```

Registers a listener for tree view node events. After successful registration, the callback function is triggered when the corresponding event occurs on a node. The same listener cannot control multiple tree view components.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeListener-on(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void--><!--Device-TreeListener-on(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | Yes | Type of the listening event, used to specify the listening event to register. |
| callback | (callbackParam: CallbackParam) =&gt; void | Yes | Callback invoked when the corresponding listening event is triggered. The callback parameter **callbackParam** contains information such as **currentNodeId**, **parentNodeId**, and **childIndex**. |

## once

```TypeScript
once(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void
```

Registers a one-time listening for tree view node events. After successful registration, the callback function is triggered when the corresponding event occurs on a node for the first time, and the listening is automatically removed after triggering. The same listener cannot control multiple tree view components.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeListener-once(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void--><!--Device-TreeListener-once(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | Yes | Type of the listening event, used to specify the listening event to register. |
| callback | (callbackParam: CallbackParam) =&gt; void | Yes | Callback invoked when the corresponding listening event is triggered. The callback parameter **callbackParam** contains information such as **currentNodeId**, **parentNodeId**, and **childIndex**. |
