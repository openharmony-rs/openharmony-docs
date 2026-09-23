# ArkUI_TouchTestInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=177cf08b41b42ef2a0a1e73e96f1ea583ec5a150 translatedAt=2026-09-22T09:16:41.959Z pushedAt=2026-09-22T11:36:36.136Z -->

```c++
typedef struct ArkUI_TouchTestInfo ArkUI_TouchTestInfo
```

## Overview

Defines touch test information, which is used to obtain the touch test policy, the IDs of child components participating in the hit test, and the list of touch test information items during the hit test. It is applicable to scenarios where detailed hit test information needs to be obtained from child component touch events to customize the hit test logic and optimize touch event distribution and response.

This event can be received only after the [NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype) event is registered through [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent). The touch test information includes the touch test policy, the IDs of child components that need to participate in the hit test, and the list of touch test information items.

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)

