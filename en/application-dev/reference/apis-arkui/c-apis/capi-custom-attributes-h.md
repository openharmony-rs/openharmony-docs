# custom_attributes.h

## Overview

Provides custom node event definitions for <b>NativeNode</b> APIs.

**File to Include**: <arkui/custom_attributes.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NodeCustomEventType](#arkui_nodecustomeventtype) | ArkUI_NodeCustomEventType | Enumerates custom component event types. |

## Enum type description

### ArkUI_NodeCustomEventType

```c
enum ArkUI_NodeCustomEventType
```

**Description**

Enumerates custom component event types.

<!--Device-enum ArkUI_NodeCustomEventType--><!--Device-enum ArkUI_NodeCustomEventType-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0 | Custom measurement.<br>**Since**: 12<br><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0--><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_MEASURE = 1 << 0-End--> |
| ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1 | Custom layout.<br>**Since**: 12<br><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1--><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_LAYOUT = 1 << 1-End--> |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2 | Custom content layer drawing.<br>**Since**: 12<br><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2--><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_DRAW = 1 << 2-End--> |
| ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3 | Custom foreground drawing.<br>**Since**: 12<br><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3--><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_FOREGROUND_DRAW = 1 << 3-End--> |
| ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4 | Custom overlay layer drawing.<br>**Since**: 12<br><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4--><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_OVERLAY_DRAW = 1 << 4-End--> |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5 | Custom content layer foreground drawing.<br>**Since**: 20<br><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5--><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_FRONT = 1 << 5-End--> |
| ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6 | Custom content layer background drawing.<br>**Since**: 20<br><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6--><!--Device-ARKUI_NODE_CUSTOM_EVENT_ON_DRAW_BEHIND = 1 << 6-End--> |


