# ArkUI_CoastingAxisEvent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-17T02:51:53.012Z pushedAt=2026-07-17T05:59:39.239Z -->

```c
typedef struct ArkUI_CoastingAxisEvent ArkUI_CoastingAxisEvent
```

## Overview

Defines a coasting axis event.

When the user performs a two-finger swipe on the touchpad, the system constructs swipe events based on the finger lift speed, following a specific attenuation curve. You can listen for this type of event to handle the coasting effect immediately after a regular axis event.

This event can only be received when the user performs a two-finger swipe on the touchpad and a component registered for the [NODE_ON_COASTING_AXIS_EVENT](capi-native-node-h.md#arkui_nodeeventtype) event via [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) exists at the pointer position. When this event is no longer needed, unregister the event listener through [unregisterNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeevent) to prevent the callback from being triggered continuously.

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)