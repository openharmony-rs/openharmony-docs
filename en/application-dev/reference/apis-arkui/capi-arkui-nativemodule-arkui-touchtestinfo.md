# ArkUI_TouchTestInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=307c96700aa31ceaed2d16437f8e9e4fabcbd960 translatedAt=2026-08-21T01:45:06.429Z pushedAt=2026-08-21T03:06:03.611Z -->

```c++
typedef struct ArkUI_TouchTestInfo ArkUI_TouchTestInfo
```

## Overview

Defines touch test information, which is used to set the hit test policy and the child components to which the result applies, and to obtain the touch test result of each child component.

You can obtain this touch test information struct in the event callback only after registering the [NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype) event through [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent).

This struct supports setting the touch test policy (for the value selection principle, see [ArkUI_TouchTestStrategy](capi-ui-input-event-h.md#arkui_touchteststrategy)) and the ID of the child component to which the hit test applies, and obtaining the touch test information item array that contains the detailed test result of each child component.

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)