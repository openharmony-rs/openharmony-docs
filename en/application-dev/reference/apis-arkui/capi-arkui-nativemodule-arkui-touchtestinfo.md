# ArkUI_TouchTestInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-23T07:08:58.694Z pushedAt=2026-11-25T01:17:59.239Z nl=1 -->

```c++
typedef struct ArkUI_TouchTestInfo ArkUI_TouchTestInfo
```

## Overview

Defines touch test information, which is used to obtain the touch test policy, the IDs of child components participating in the hit test, and the list of touch test information items during the hit test. It is applicable to scenarios where detailed hit test information needs to be obtained from child component touch events to customize the hit test logic and optimize touch event distribution and response.

This event can be received only after the [NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype) event is registered through [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent). The touch test information includes the touch test policy, the IDs of child components that need to participate in the hit test, and the list of touch test information items.

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)

