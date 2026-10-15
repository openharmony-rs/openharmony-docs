# ArkUI_TouchTestInfoItem

```c
typedef struct ArkUI_TouchTestInfoItem ArkUI_TouchTestInfoItem
```

## Overview

Defines a touch test information item. A touch test is a hit test process that determines the target component based on touch event coordinates. The touch test information item can be obtained in the event callback only when you register the [NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype) event through [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent). This information item contains the information about child components in the touch test, and is applicable to scenarios where child component information needs to be obtained and identified. You can use the OH_ArkUI_TouchTestInfoItem_GetXXX series APIs to obtain the information and process the touch test result.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)

