# TreeListenerManagerV2

```TypeScript
export declare class TreeListenerManagerV2
```

Defines the listener manager of the tree view component, which is used to manage changes to tree view listeners. Bind this object to the tree view component before use. The same listener manager cannot control multiple tree view components. This manager is designed in singleton mode. Obtain the globally unique instance through **getInstance**, and then obtain the listener instance through **getTreeListener**.

**Since:** 26.0.0

<!--Device-unnamed-export declare class TreeListenerManagerV2--><!--Device-unnamed-export declare class TreeListenerManagerV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## getInstance

```TypeScript
static getInstance(): TreeListenerManagerV2
```

Obtains the singleton object of the tree view component listener manager.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerManagerV2-static getInstance(): TreeListenerManagerV2--><!--Device-TreeListenerManagerV2-static getInstance(): TreeListenerManagerV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TreeListenerManagerV2](arkts-arkui-arkui-advanced-treeviewv2-treelistenermanagerv2-c.md) | Singleton object of the listener manager of the tree view component. |

## getTreeListener

```TypeScript
getTreeListener(): TreeListenerV2
```

Obtains a tree view listener instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TreeListenerManagerV2-getTreeListener(): TreeListenerV2--><!--Device-TreeListenerManagerV2-getTreeListener(): TreeListenerV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TreeListenerV2](arkts-arkui-arkui-advanced-treeviewv2-treelistenerv2-c.md) | Tree view listener instance, used to register or unregister event listeners for node click, add, delete, modify, and move operations of the tree view. |
