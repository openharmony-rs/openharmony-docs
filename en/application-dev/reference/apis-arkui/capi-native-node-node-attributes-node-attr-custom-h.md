# node_attr_custom.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Declares the custom node events for **NativeNode** APIs.

**File to include:** <arkui/node_attributes/node_attr_custom.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[native_node_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/native_node_sample)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) | ArkUI_NodeCustomEventType | Enumerates custom component event types.|

## Enumeration Description

### ArkUI_NodeCustomEventType

```c
enum ArkUI_NodeCustomEventType
```

**Description**


Enumerates custom component event types.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0 | Custom measurement.<br>**Since:** 12|
| ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1 | Custom layout.<br>**Since:** 12|
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2 | Custom content layer drawing.<br>**Since:** 12|
| ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3 | Custom foreground drawing.<br>**Since:** 12|
| ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4 | Custom overlay layer drawing.<br>**Since:** 12|
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5 | Custom content layer foreground drawing.<br>**Since:** 20|
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6 | Custom content layer background drawing.<br>**Since:** 20|
