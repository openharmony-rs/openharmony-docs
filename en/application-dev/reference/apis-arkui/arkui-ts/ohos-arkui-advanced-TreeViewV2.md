# TreeViewV2

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangrunsen-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ca610c3b31eac2a84ffac21a107ce522b473feb1 translatedAt=2026-08-21T02:21:46.006Z pushedAt=2026-08-21T07:13:34.528Z -->

The **TreeViewV2** component is displayed as a list in a hierarchical manner, which is suitable for displaying nested structures. It has parent nodes and child nodes, can be expanded or collapsed, and supports node addition, deletion, modification, drag-and-drop movement, custom icons, event listening, and context menus.

It is used in productivity apps, such as the side navigation bars in memos, emails, and galleries. It is suitable for scenarios that require displaying and managing hierarchical data and supporting node interaction operations.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can more flexibly control the data and state of the tree view through this component, achieving more efficient UI refresh.

> **NOTE**
>
> - This module's APIs can only be used in the stage model.
>
> - If [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) are set for **TreeViewV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and mount the universal attributes or universal events on \_\_Common\_\_, rather than directly applying them to **TreeViewV2** itself. This may cause the set universal attributes or universal events to not take effect or behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events on **TreeViewV2**.

**Since**: 26.0.0

## Modules to Import

```ts
import { TreeViewV2 } from '@kit.ArkUI';
```

## Child Components

Not supported

## TreeViewV2

TreeViewV2({ treeControllerV2: TreeControllerV2 })

The **TreeViewV2** component is a list displayed in a hierarchical manner, used to display components in a tree structure. It supports node addition, deletion, modification, drag-and-drop movement, custom icons, event listening, and context menus, and is suitable for scenarios where hierarchical data needs to be displayed and managed.

**Since**: 26.0.0

**Decorator:** @ComponentV2

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Mandatory | Decorator | Description |
| -------- | -------- | -------- | -------- | -------- |
| treeControllerV2 | [TreeControllerV2](#treecontrollerv2) | Yes | @Param | Controller of the tree view nodes, used to control the node information of the tree. After being bound to the tree view component, it can be used to add, delete, and modify nodes. The same controller cannot control multiple tree view components. |

## TreeControllerV2

Controller of the tree view component, used to control the node information of the tree. Bind this object to the tree view component before use. The same controller cannot control multiple tree view components.

### addNode

addNode(nodeParam?: NodeParamV2): TreeControllerV2

Adds a child node to the tapped node. After the node is added, you must call [buildDone()](#builddone) to trigger the saving of tree information; otherwise, the added node will not be displayed in the tree view. Chained calls are supported, for example, **addNode().addNode().buildDone()**.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| nodeParam | [NodeParamV2](#nodeparamv2) | No | Node information, used to specify the attributes of the node to be added. If this parameter is not passed, a node titled "New Folder" is added under the currently selected node. |

**Return value** 

| Type                              | Description                 |
| --------------------------------- | -------------------- |
| [TreeControllerV2](#treecontrollerv2) | Controller of the tree view component, used to chain other tree view control methods. |

### removeNode

removeNode(): void

Deletes the tapped node.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

### modifyNode

modifyNode(): void

Modifies the tapped node.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

### buildDone

buildDone(): void

Builds the tree view. After all nodes are added, this method must be called to trigger the saving of tree information. This API uses a two-phase build mode: first add nodes to the memory through **addNode**, and then call this method to save the node information in a unified manner and render it into the tree view. If this method is not called, the added nodes will not be displayed in the tree view.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

### refreshNode

refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void

Locates the parent node based on the passed **parentId**, and updates the subtitle of the parent node (**parentSubTitle**) and the subtitle of the current node (**currentSubtitle**).

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| parentId | number | Yes | ID of the parent node.<br />Value range: greater than or equal to -1.<br />If a value less than -1 is passed, the node is invalid. |
| parentSubTitle | [ResourceStr](ts-types.md#resourcestr) | Yes | Subtitle of the parent node, used to update the subtitle displayed on the parent node. |
| currentSubtitle | [ResourceStr](ts-types.md#resourcestr) | Yes | Subtitle of the current node, used to update the subtitle displayed on the current node. |

## NodeParamV2

Defines the node parameter API, which is used to configure the properties of a tree node.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read Only | Optional | Description                                                                                                                                               |
| -------- | -------- |---|---|--------------------------------------------------------------------------------------------------------------------------------------------------|
| parentNodeId | number | No | Yes | Parent node ID.<br />Value range: greater than or equal to -1.<br />Default value: **-1**, which is the root node ID. If the value is less than -1, the node is invalid and is not displayed in the tree view. |
| currentNodeId | number | No | Yes | Current child node ID.<br />Value range: greater than or equal to -1.<br />It cannot be the root node ID or null; otherwise, an exception is thrown. Two identical **currentNodeId** values cannot be set.<br />Default value: **-1**, which means the node ID is not specified and is automatically assigned by the system. |
| isFolder | boolean | No | Yes | Whether the node is a folder. The value **true** indicates a directory node that can contain child nodes (used when a parent node that can be expanded is required); the value **false** indicates a leaf node that cannot contain child nodes (used when a non-expandable terminal node is required). If this parameter is not passed, the default value **false** (leaf node) is used.                                                         |
| icon | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Icon used to customize the default icon of the node. Pass this parameter when a custom icon needs to be specified for the node. If it is not passed, the node displays the system default icon. When **symbolIconStyle** is also set, only the symbol icon is displayed and **icon** does not take effect.<br/>Default value: empty string, which means no custom icon is displayed. |
| symbolIconStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol icon style used to set the system symbol icon. Pass this parameter when a system symbol icon is required (for example, when consistency with the system style and dynamic color support are needed). If it is not passed, the icon specified by the **icon** parameter is used. Its display priority is higher than that of icon. When both **symbolIconStyle** and **icon** are set, only the symbol icon is displayed.<br/>Default value: **undefined**, which means no Symbol icon is displayed.                  |
| selectedIcon | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Selected icon used to customize the icon displayed when the node is selected. Pass this parameter when an icon different from the default state needs to be displayed in the node selection state. If it is not passed, the node displays the same icon as in the unselected state after being selected. When **symbolSelectedIconStyle** is also set, only the symbol selected icon is displayed and **selectedIcon** does not take effect.<br/>Default value: empty string, which means no custom selected icon is displayed when the node is selected. |
| symbolSelectedIconStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol selected icon style used to set the system Symbol icon when the node is selected. Pass this parameter when a system symbol icon is required as the selected icon (for example, when consistency with the system style and dynamic color support are needed). If it is not passed, the node displays the same icon as in the unselected state after being selected. Its priority is higher than that of **selectedIcon**. When both **symbolSelectedIconStyle** and **selectedIcon** are set, only the symbol selected icon is displayed.<br/>Default value: **undefined** |
| editIcon | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Edit icon used to customize the icon displayed when the node enters the editing state. Pass this parameter when an icon different from the default state needs to be displayed in the node editing state. If it is not passed, the node displays the same icon as in the non-editing state in the editing state. When **symbolEditIconStyle** is also set, only the symbol edit icon is displayed and **editIcon** does not take effect.<br/>Default value: empty string, which means no custom edit icon is displayed in the editing state. |
| symbolEditIconStyle | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No | Yes | Symbol edit icon style used to set the system symbol icon in the node editing state. Pass this parameter when a system symbol icon is required as the edit icon (for example, when consistency with the system style and dynamic color support are needed). If it is not passed, the node displays the same icon as in the non-editing state in the editing state. Its priority is higher than that of **editIcon**. When both **symbolEditIconStyle** and **editIcon** are set, only the symbol edit icon is displayed.<br/>Default value: **undefined**   |
| primaryTitle | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Primary title.<br/>Default value: empty string, which means no primary title is displayed.                           |
| secondaryTitle | [ResourceStr](ts-types.md#resourcestr) | No | Yes | Secondary title.<br/>Default value: empty string, which means no secondary title is displayed.                         |
| container | [OnContainerCallback](#oncontainercallback) | No | Yes | Right-click child component container bound to the node. The child component is decorated by **@Builder**. Pass this parameter when a right-click menu or custom right-click operation needs to be provided for the node. If it is not passed, the node does not display a right-click menu.<br/>Default value: **() => void**, which means no right-click child component container is bound. |

## TreeListenerManagerV2

Defines the listener manager of the tree view component, which is used to manage changes to tree view listeners. Bind this object to the tree view component before use. The same listener manager cannot control multiple tree view components. This manager is designed in singleton mode. Obtain the globally unique instance through **getInstance**, and then obtain the listener instance through **getTreeListener**.

### getInstance

static getInstance(): TreeListenerManagerV2

Obtains the singleton object of the tree view component listener manager.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Return value**

| Type              | Description               |
| --------------- |------------------|
| [TreeListenerManagerV2](#treelistenermanagerv2) | Singleton object of the listener manager of the tree view component. |

### getTreeListener

getTreeListener(): TreeListenerV2

Obtains a tree view listener instance.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Return value**

| Type           | Description         |
| ------------ |------------|
| [TreeListenerV2](#treelistenerv2) | Tree view listener instance, used to register or unregister event listeners for node click, add, delete, modify, and move operations of the tree view. |

## TreeListenerV2

Defines the listener of the tree view component, which is used to listen for changes to tree view nodes. Bind this object to a tree view component before use. A single tree view listener cannot control multiple tree view components. This listener provides two event registration modes: **on** and **once**. The **on** method continuously listens for events until canceled, while the **once** method listens once and then is automatically destroyed. After use, call **offNodeClick**, **offNodeAdd**, and other methods to cancel listening when the component is destroyed, to avoid memory leaks.

### onNodeClick

onNodeClick(callback: OnChangedCallback): void

Registers a listener for the node click event, which takes effect continuously. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback invoked when a node is clicked. |

### onceNodeClick

onceNodeClick(callback: OnChangedCallback): void

Registers a node click event listener, which is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback for the node click event. |

### offNodeClick

offNodeClick(callback?: OnChangedCallback): void

Unregisters the node click event listener. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | No | Callback for the node click event. If this parameter is passed, the corresponding listener is removed; otherwise, all node click listeners are removed. |

### onNodeAdd

onNodeAdd(callback: OnChangedCallback): void

Registers a listener for the node addition event, which takes effect continuously. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback invoked when a node is added. |

### onceNodeAdd

onceNodeAdd(callback: OnChangedCallback): void

Registers a node add event listener, which is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback for the node addition event. |

### offNodeAdd

offNodeAdd(callback?: OnChangedCallback): void

Unregisters the node add event listener. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | No | Callback for the node addition event. If this parameter is passed in, the corresponding listener is canceled; otherwise, all node addition listeners are canceled. |

### onNodeDelete

onNodeDelete(callback: OnChangedCallback): void

Registers a listener for the node deletion event, which takes effect continuously. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback invoked when a node is deleted. |

### onceNodeDelete

onceNodeDelete(callback: OnChangedCallback): void

Registers a node deletion event listener. The listener is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback for the node deletion event. |

### offNodeDelete

offNodeDelete(callback?: OnChangedCallback): void

Unregisters from the node deletion event. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | No | Callback for the node deletion event. If this parameter is passed, the corresponding listener is unregistered; otherwise, all node deletion listeners are unregistered. |

### onNodeModify

onNodeModify(callback: OnChangedCallback): void

Registers a listener for the node modification event, which takes effect continuously. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback for the node modification event. |

### onceNodeModify

onceNodeModify(callback: OnChangedCallback): void

Registers a node modification event listener, which is automatically destroyed after being triggered once. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback for the node modification event. |

### offNodeModify

offNodeModify(callback?: OnChangedCallback): void

Unregisters the node modification event listener. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | No | Callback for the node modification event. If this parameter is passed, the corresponding listener is canceled; otherwise, all node modification listeners are canceled. |

### onNodeMove

onNodeMove(callback: OnChangedCallback): void

Registers a node move event listener that takes effect continuously. Node move is triggered by drag operations. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback invoked when a node is moved. |

### onceNodeMove

onceNodeMove(callback: OnChangedCallback): void

Registers a node move event listener that is automatically destroyed after being triggered once. Node move is triggered by drag operations. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | Yes | Callback for the node move event. |

### offNodeMove

offNodeMove(callback?: OnChangedCallback): void

Unregisters the node move event listener. This API uses a callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

**Parameters**

| Name  | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | [OnChangedCallback](#onchangedcallback) | No | Callback for the node move event. If this parameter is passed in, the corresponding listener is unregistered; otherwise, all node move listeners are unregistered. |

## OnChangedCallback

type OnChangedCallback = (callbackParam: CallbackParamV2) => void

Defines the node event callback function.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type      | Mandatory | Description                                            |
| :------ |:--------| :- | :-------------------------------------------------- |
| callbackParam | [CallbackParamV2](#callbackparamv2) | Yes  | Node callback parameter, used to pass the parameter information of the node event callback. |

## CallbackParamV2

Defines the node callback parameter API, used to pass parameter information of node event callbacks.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

| Name | Type | Read Only | Optional | Description |
| -------- | -------- |---|---|------------------------------------------|
| currentNodeId | number | No | No | ID of the current node.<br />Value range: greater than or equal to 0. |
| parentNodeId | number | No | Yes | ID of the current parent node.<br />Value range: greater than or equal to -1.<br />Default value: **-1** |
| childIndex | number | No | Yes | Child index.<br />Value range: greater than or equal to -1.<br />Default value: **-1**<br />Valid only in the node move event, indicating the position index after the move. |

## OnContainerCallback

type OnContainerCallback = () => void

Defines a container callback function type, which is used to define child component callbacks bound to tree nodes.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences:** The actual device types supported by this API (phone, PC/2-in-1 device, tablet, and TV) are fewer than those supported by its system capability (phone, PC/2-in-1 device, tablet, TV, and wearable). Due to hardware capability restrictions, calling this API on wearables results in a runtime exception indicating that the API is undefined.

## Events

The [universal events](ts-component-general-events.md) are not supported.

## Example

### Example 1: Configuring a Tree View

Since API version 26.0.0, the following example supports adding, deleting, and renaming nodes in a tree view through the controller API of the tree view component.

```ts
import {
  TreeControllerV2,
  TreeListenerV2,
  TreeListenerManagerV2,
  NodeParamV2,
  TreeViewV2,
  CallbackParamV2
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct TreeViewV2Demo {
  // Create a tree view controller.
  private treeControllerV2: TreeControllerV2 = new TreeControllerV2();
  // Create a tree view listener.
  private treeListenerV2: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  // Record the ID of the currently clicked node.
  @Local clickNodeId: number = 0;

  // Cancel all listeners when the component is destroyed.
  aboutToDisappear(): void {
    this.treeListenerV2.offNodeClick();
    this.treeListenerV2.offNodeAdd();
    this.treeListenerV2.offNodeDelete();
    this.treeListenerV2.offNodeModify();
    this.treeListenerV2.offNodeMove();
  }

  // Register listeners and build the tree structure when the component is initialized.
  aboutToAppear(): void {
    // Register the node click listener.
    this.treeListenerV2.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node add listener.
    this.treeListenerV2.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node delete listener.
    this.treeListenerV2.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node move listener.
    this.treeListenerV2.onceNodeMove((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
      console.info(`Node moved to index: ${callbackParam.childIndex}`);
    })

    let normalResource: Resource = $r('sys.media.ohos_ic_normal_white_grid_folder');
    let selectedResource: Resource = $r('sys.media.ohos_ic_public_select_all');
    let editResource: Resource = $r('sys.media.ohos_ic_public_edit');

    let nodeParam: NodeParamV2 = {
      parentNodeId: -1,
      currentNodeId: 1,
      isFolder: true,
      icon: normalResource,
      selectedIcon: selectedResource,
      editIcon: editResource,
      primaryTitle: 'Directory 1',
      secondaryTitle: '6'
    };

    // Build the tree structure.
    this.treeControllerV2
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: 'Item 1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: 'Directory 2'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 23,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: 'Project 4'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 31,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 5',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 32,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 6',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 32,
        currentNodeId: 35,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 6-1',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 33,
        isFolder: true,
        icon: normalResource,
        selectedIcon: selectedResource,
        editIcon: editResource,
        primaryTitle: 'Directory 7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: 'Item 8'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: 'Item 9'
      })
      .buildDone();

    this.treeControllerV2.refreshNode(-1, 'Parent node', 'Child node');
  }

  build(): void {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        // Tree view component.
        TreeViewV2({ treeControllerV2: this.treeControllerV2 })
        Row() {
          Divider().vertical(true).strokeWidth(2).color(0x000000).lineCap(LineCapStyle.Round)
          Column({ space: 30 }) {
            Text('ClickNodeId=' + this.clickNodeId).fontSize('16fp')
            Button('Add', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.addNode();
              })
            Button('Modify', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.modifyNode();
              })
            Button('Remove', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(120)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.removeNode();
              })
          }.height('100%').width('70%').alignItems(HorizontalAlign.Start).margin(10)
        }
      }
      .focusable(true)
      .showControlButton(false)
      .showSideBar(true)
    }
  }
}
```

<!--Del--> <!--DelEnd-->

### Example 2: Setting a Symbol Icon

Since API version 26.0.0, the following example demonstrates how to customize symbol icons in the tree view by setting the attribute APIs such as **symbolIconStyle**, **symbolEditIconStyle**, and **symbolSelectedIconStyle** of [NodeParamV2](#nodeparamv2).

```ts
import {
  TreeControllerV2,
  TreeListenerV2,
  TreeListenerManagerV2,
  NodeParamV2,
  TreeViewV2,
  CallbackParamV2,
  SymbolGlyphModifier
} from '@kit.ArkUI';

@Entry
@ComponentV2
struct TreeViewV2Demo {
  // Create a tree view controller.
  private treeControllerV2: TreeControllerV2 = new TreeControllerV2();
  // Create a tree view listener.
  private treeListenerV2: TreeListenerV2 = TreeListenerManagerV2.getInstance().getTreeListener();
  // Record the ID of the currently clicked node.
  @Local clickNodeId: number = 0;

  // Cancel all listeners when the component is destroyed.
  aboutToDisappear(): void {
    this.treeListenerV2.offNodeClick();
    this.treeListenerV2.offNodeAdd();
    this.treeListenerV2.offNodeDelete();
    this.treeListenerV2.offNodeModify();
    this.treeListenerV2.offNodeMove();
  }

  // Register the listener and build the tree structure during component initialization.
  aboutToAppear(): void {
    // Register the node click listener.
    this.treeListenerV2.onNodeClick((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    });
    // Register the node add listener.
    this.treeListenerV2.onNodeAdd((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node delete listener.
    this.treeListenerV2.onNodeDelete((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
    })
    // Register the node move listener (destroyed automatically after listening once).
    this.treeListenerV2.onceNodeMove((callbackParam: CallbackParamV2) => {
      this.clickNodeId = callbackParam.currentNodeId;
      console.info(`Node moved to parent: ${callbackParam.parentNodeId}, index: ${callbackParam.childIndex}`);
    })

    let normalResource: Resource = $r('sys.symbol.house');
    let selectedResource: Resource = $r('sys.symbol.car');
    let editResource: Resource = $r('sys.symbol.calendar');

    let normalSymbolResource: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.bell'))
      .fontColor([Color.Red]);
    let selectedSymbolResource: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.heart'))
      .fontColor([Color.Blue]);
    let editSymbolResource: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.cake'))
      .fontColor([Color.Pink]);

    let nodeParam: NodeParamV2 = {
      parentNodeId: -1,
      currentNodeId: 1,
      isFolder: true,
      icon: normalResource,
      selectedIcon: selectedResource,
      editIcon: editResource,
      primaryTitle: 'Directory 1',
      secondaryTitle: '6'
    };

    // Build the tree structure.
    this.treeControllerV2
      .addNode(nodeParam)
      .addNode({
        parentNodeId: 1,
        currentNodeId: 2,
        isFolder: false,
        primaryTitle: 'Item 1_1'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 7,
        isFolder: true,
        primaryTitle: 'Directory 2'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 23,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 3'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 24,
        isFolder: false,
        primaryTitle: 'Project 4'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 31,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 5',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 32,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 6',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 32,
        currentNodeId: 35,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 6-1',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 33,
        isFolder: true,
        icon: normalResource,
        symbolIconStyle: normalSymbolResource,
        selectedIcon: selectedResource,
        symbolSelectedIconStyle: selectedSymbolResource,
        editIcon: editResource,
        symbolEditIconStyle: editSymbolResource,
        primaryTitle: 'Directory 7',
        secondaryTitle: '0'
      })
      .addNode({
        parentNodeId: 33,
        currentNodeId: 34,
        isFolder: false,
        primaryTitle: 'Project 8'
      })
      .addNode({
        parentNodeId: -1,
        currentNodeId: 36,
        isFolder: false,
        primaryTitle: 'Project 9'
      })
      .buildDone();

    this.treeControllerV2.refreshNode(-1, 'Parent node', 'Child node');
  }

  build(): void {
    Column() {
      SideBarContainer(SideBarContainerType.Embed) {
        // Tree view component
        TreeViewV2({ treeControllerV2: this.treeControllerV2 })
        Row() {
          Divider().vertical(true).strokeWidth(2).color(0x000000).lineCap(LineCapStyle.Round)
          Column({ space: 30 }) {
            Text('ClickNodeId=' + this.clickNodeId).fontSize('16fp')
            Button('Add', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.addNode();
              })
            Button('Modify', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(90)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.modifyNode();
              })
            Button('Remove', { type: ButtonType.Normal, stateEffect: true })
              .borderRadius(8).backgroundColor(0x317aff).width(120)
              .onClick((event: ClickEvent) => {
                this.treeControllerV2.removeNode();
              })
          }.height('100%').width('80%').alignItems(HorizontalAlign.Start).margin(10)
        }
      }
      .focusable(true)
      .showControlButton(false)
      .showSideBar(true)
    }
  }
}
```

<!--Del--> <!--DelEnd-->