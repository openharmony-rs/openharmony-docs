# ArkUI_CoastingAxisEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the inertial scroll axis event.

When the user performs a two-finger swipe on the touchpad, the system constructs a swipe event based on the finger lift speed, following a specific attenuation curve. You can listen for this event to handle the flick effect immediately after processing regular axis events.

This event is only dispatched if two conditions are met: 1. The user executes a two-finger swipe on the touchpad. 2. A component registered for the [NODE_ON_COASTING_AXIS_EVENT](capi-native-node-h.md#arkui_nodeeventtype) event (via [registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)) exists at the pointer's position.

**Since**: 22

**Related module**: [ArkUI_EventModule](capi-arkui-eventmodule.md)

**Header file**: [ui_input_event.h](capi-ui-input-event-h.md)
