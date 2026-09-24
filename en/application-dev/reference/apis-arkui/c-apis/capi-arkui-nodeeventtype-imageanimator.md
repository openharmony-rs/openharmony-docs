# ImageAnimator

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_IMAGE_ANIMATOR_EVENT_ON_START

```c
NODE_IMAGE_ANIMATOR_EVENT_ON_START = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE_ANIMATOR
```

**Description**

Defines the event triggered when the animation starts to play.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE

```c
NODE_IMAGE_ANIMATOR_EVENT_ON_PAUSE = 19001
```

**Description**

Defines the event triggered when the animation playback is paused.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT

```c
NODE_IMAGE_ANIMATOR_EVENT_ON_REPEAT = 19002
```

**Description**

Defines the event triggered when the animation playback is repeated.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL

```c
NODE_IMAGE_ANIMATOR_EVENT_ON_CANCEL = 19003
```

**Description**

Defines the event triggered when the animation playback returns to the initial state.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH

```c
NODE_IMAGE_ANIMATOR_EVENT_ON_FINISH = 19004
```

**Description**

Defines the event triggered when the animation playback is complete or stopped.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12


