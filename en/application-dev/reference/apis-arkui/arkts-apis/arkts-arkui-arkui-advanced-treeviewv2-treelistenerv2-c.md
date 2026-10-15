# TreeListenerV2

```TypeScript
export declare class TreeListenerV2
```

Defines the listener of the tree view component, which is used to listen for changes to tree view nodes. Bind this object to a tree view component before use. A single tree view listener cannot control multiple tree view components. This listener provides two event registration modes: **on** and **once**. The **on** method continuously listens for events until canceled, while the **once** method listens once and then is automatically destroyed. After use, call **offNodeClick**, **offNodeAdd**, and other methods to cancel listening when the component is destroyed, to avoid memory leaks.

**Since:** 26.0.0

<!--Device-unnamed-export declare class TreeListenerV2--><!--Device-unnamed-export declare class TreeListenerV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## offNodeAdd

```TypeScript
offNodeAdd(callback?: OnChangedCallback): void
```

Unregisters the node add event listener. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-offNodeAdd(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeAdd(callback?: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No | Callback for the node addition event. If this parameter is passed in, the corresponding listener is canceled; otherwise, all node addition listeners are canceled. |

## offNodeClick

```TypeScript
offNodeClick(callback?: OnChangedCallback): void
```

Unregisters the node click event listener. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-offNodeClick(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeClick(callback?: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No | Callback for the node click event. If this parameter is passed, the corresponding listener is removed; otherwise, all node click listeners are removed. |

## offNodeDelete

```TypeScript
offNodeDelete(callback?: OnChangedCallback): void
```

Unregisters from the node deletion event. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-offNodeDelete(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeDelete(callback?: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No | Callback for the node deletion event. If this parameter is passed, the corresponding listener is unregistered; otherwise, all node deletion listeners are unregistered. |

## offNodeModify

```TypeScript
offNodeModify(callback?: OnChangedCallback): void
```

Unregisters the node modification event listener. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-offNodeModify(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeModify(callback?: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No | Callback for the node modification event. If this parameter is passed, the corresponding listener is canceled; otherwise, all node modification listeners are canceled. |

## offNodeMove

```TypeScript
offNodeMove(callback?: OnChangedCallback): void
```

Unregisters the node move event listener. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-offNodeMove(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeMove(callback?: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | No | Callback for the node move event. If this parameter is passed in, the corresponding listener is unregistered; otherwise, all node move listeners are unregistered. |

## onceNodeAdd

```TypeScript
onceNodeAdd(callback: OnChangedCallback): void
```

Registers a node add event listener, which is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onceNodeAdd(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeAdd(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback for the node addition event. |

## onceNodeClick

```TypeScript
onceNodeClick(callback: OnChangedCallback): void
```

Registers a node click event listener, which is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onceNodeClick(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeClick(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback for the node click event. |

## onceNodeDelete

```TypeScript
onceNodeDelete(callback: OnChangedCallback): void
```

Registers a node deletion event listener. The listener is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onceNodeDelete(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeDelete(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback for the node deletion event. |

## onceNodeModify

```TypeScript
onceNodeModify(callback: OnChangedCallback): void
```

Registers a node modification event listener, which is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onceNodeModify(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeModify(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback for the node modification event. |

## onceNodeMove

```TypeScript
onceNodeMove(callback: OnChangedCallback): void
```

Registers a node move event listener that is automatically destroyed after being triggered once. Node move is triggered by drag operations. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onceNodeMove(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeMove(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback for the node move event. |

## onNodeAdd

```TypeScript
onNodeAdd(callback: OnChangedCallback): void
```

Registers a listener for the node addition event, which takes effect continuously. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onNodeAdd(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeAdd(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback invoked when a node is added. |

## onNodeClick

```TypeScript
onNodeClick(callback: OnChangedCallback): void
```

Registers a listener for the node click event, which takes effect continuously. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onNodeClick(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeClick(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback invoked when a node is clicked. |

## onNodeDelete

```TypeScript
onNodeDelete(callback: OnChangedCallback): void
```

Registers a listener for the node deletion event, which takes effect continuously. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onNodeDelete(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeDelete(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback invoked when a node is deleted. |

## onNodeModify

```TypeScript
onNodeModify(callback: OnChangedCallback): void
```

Registers a listener for the node modification event, which takes effect continuously. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onNodeModify(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeModify(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback for the node modification event. |

## onNodeMove

```TypeScript
onNodeMove(callback: OnChangedCallback): void
```

Registers a node move event listener that takes effect continuously. Node move is triggered by drag operations. This API uses a callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerV2-onNodeMove(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeMove(callback: OnChangedCallback): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | Yes | Callback invoked when a node is moved. |
