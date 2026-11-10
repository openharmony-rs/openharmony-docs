# ArkUI_NodeComponentEvent

```c
typedef struct ArkUI_NodeComponentEvent {...} ArkUI_NodeComponentEvent
```

## Overview

Defines the parameter type of a component callback event, which is used to pass event-related data when the component callback is triggered, so that the application can obtain the callback event parameters.

<!--Device-typedef struct ArkUI_NodeComponentEvent {...} ArkUI_NodeComponentEvent--><!--Device-typedef struct ArkUI_NodeComponentEvent {...} ArkUI_NodeComponentEvent-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) data[MAX_COMPONENT_EVENT_ARG_NUM] | Data array object. |


