# ArkUI_CoastingAxisEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=177cf08b41b42ef2a0a1e73e96f1ea583ec5a150 translatedAt=2026-09-18T11:25:49.810Z pushedAt=2026-09-20T07:53:21.686Z -->

```c
typedef struct ArkUI_CoastingAxisEvent ArkUI_CoastingAxisEvent
```

## Overview

Defines the coasting axis event.

When the user performs a two-finger swipe on the touchpad, the system constructs a coasting axis event based on the finger lift speed, following a specific decaying curve. You can listen for this type of event to handle the inertial scrolling effect immediately after a regular axis event.

You can receive this event only when the following conditions are met: The user performs a two-finger swipe on the touchpad, and a component registered for the [NODE_ON_COASTING_AXIS_EVENT](capi-native-node-h.md#arkui_nodeeventtype) event via [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) exists at the pointer position. When this event is no longer needed, unregister the event listener through [unregisterNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeevent) to prevent the callback from being triggered continuously.

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)

