# Drag Event

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_ON_PRE_DRAG

```c
NODE_ON_PRE_DRAG = 14
```

**Description**

Notifies the listener of the interaction state prior to a drop and drop operation.<br> This event is triggered when a drag operation is about to start on a draggable item. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter: <ul> <li>ArkUI_NodeComponentEvent.data[0].i32</b>: corresponds to [ArkUI_PreDragStatus](capi-drag-and-drop-h.md#arkui_predragstatus).</li> </ul>

**Since**: 12

### NODE_ON_DRAG_START

```c
NODE_ON_DRAG_START = 15
```

**Description**

Called when the user starts to drag an ite<br> A drag operation is recognized only when the dragged item is moved far enough. When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 12

### NODE_ON_DRAG_ENTER

```c
NODE_ON_DRAG_ENTER = 16
```

**Description**

Called when a dragged item enters the boundaries of the current component.<br> The current component refers to the component that listens for this event. When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 12

### NODE_ON_DRAG_MOVE

```c
NODE_ON_DRAG_MOVE = 17
```

**Description**

Called when a dragged item moves in the current component.<br> The current component refers to the component that listens for this event. When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 12

### NODE_ON_DRAG_LEAVE

```c
NODE_ON_DRAG_LEAVE = 18
```

**Description**

Called when a dragged item leaves the boundaries of the current component.<br> The current component refers to the component that listens for this event. When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 12

### NODE_ON_DROP

```c
NODE_ON_DROP = 19
```

**Description**

Called when a dragged item is dropped on the current component. The component can obtain the drag data for processing through the callback.<br> The current component refers to the component that listens for this event. When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 12

### NODE_ON_DRAG_END

```c
NODE_ON_DRAG_END = 20
```

**Description**

Called when a drag operation ends. The drag source can obtain the drag result by registering this callback.<br> A drag operation ends when the dragged item is released. When the event callback occurs, the [ArkUI_DragEvent](capi-arkui-nativemodule-arkui-dragevent.md) object can be obtained from the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object.

**Since**: 12


