# ArkUI_TouchTestInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-09T11:48:53.739Z pushedAt=2026-11-10T03:55:32.132Z nl=1 -->

```c++
typedef struct ArkUI_TouchTestInfo ArkUI_TouchTestInfo
```

## Overview

Defines touch test information, which is used to set the hit test policy and the child components that take effect during the hit test, and to obtain the touch test result of each child component.

You can obtain this touch test information struct in the event callback only after registering the [NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype) event through [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent).

This struct supports setting the touch test policy (for the value selection principle, see [ArkUI_TouchTestStrategy](capi-ui-input-event-h.md#arkui_touchteststrategy)) and the ID of the child component to which the hit test applies, and obtaining the touch test information item array that contains the detailed test result of each child component.

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)

