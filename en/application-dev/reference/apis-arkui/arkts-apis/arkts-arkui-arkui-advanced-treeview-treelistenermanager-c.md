# TreeListenerManager

```TypeScript
export declare class TreeListenerManager
```

Defines a listener manager for the tree view component, which can obtain a listener instance and bind it to the tree view component for managing node listening of the tree. The same listener cannot control multiple tree view components.

**Since:** 10

<!--Device-unnamed-export declare class TreeListenerManager--><!--Device-unnamed-export declare class TreeListenerManager-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## getInstance

```TypeScript
static getInstance(): TreeListenerManager
```

Obtains a **TreeListenerManager** singleton object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeListenerManager-static getInstance(): TreeListenerManager--><!--Device-TreeListenerManager-static getInstance(): TreeListenerManager-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TreeListenerManager](arkts-arkui-arkui-advanced-treeview-treelistenermanager-c.md) | treeListenerManager instance |

## getTreeListener

```TypeScript
getTreeListener(): TreeListener
```

Obtains a listener.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TreeListenerManager-getTreeListener(): TreeListener--><!--Device-TreeListenerManager-getTreeListener(): TreeListener-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TreeListener](arkts-arkui-arkui-advanced-treeview-treelistener-c.md) | treeListener object |
