# TreeListenerManager

Implements a **TreeListenerManager** object, which can be bound to a **TreeView** component to listen for changes of tree nodes. One **TreeListenerManager** object can be bound to only one tree view component.

**Since:** 10

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TreeListener](arkts-arkui-arkui-advanced-treeview-treelistener-c.md) | treeListener object |
