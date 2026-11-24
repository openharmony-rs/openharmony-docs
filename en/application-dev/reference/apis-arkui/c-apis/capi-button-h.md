# button.h

## Overview

Provides Button node type definitions for <b>NativeNode</b> APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ButtonType](#arkui_buttontype) | ArkUI_ButtonType | Enumerates the button types. |

## Enum type description

### ArkUI_ButtonType

```c
enum ArkUI_ButtonType
```

**Description**

Enumerates the button types.

<!--Device-enum ArkUI_ButtonType--><!--Device-enum ArkUI_ButtonType-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_BUTTON_TYPE_NORMAL = 0 | Normal button (without rounded corners by default).<br>**Since**: 12<br><!--Device-ARKUI_BUTTON_TYPE_NORMAL = 0--><!--Device-ARKUI_BUTTON_TYPE_NORMAL = 0-End--> |
| ARKUI_BUTTON_TYPE_CAPSULE | Capsule-type button (the round corner is half of the height by default).<br>**Since**: 12<br><!--Device-ARKUI_BUTTON_TYPE_CAPSULE--><!--Device-ARKUI_BUTTON_TYPE_CAPSULE-End--> |
| ARKUI_BUTTON_TYPE_CIRCLE | Circle button.<br>**Since**: 12<br><!--Device-ARKUI_BUTTON_TYPE_CIRCLE--><!--Device-ARKUI_BUTTON_TYPE_CIRCLE-End--> |
| ARKUI_BUTTON_ROUNDED_RECTANGLE = 8 | Rounded rectangle button.<br>**Since**: 19<br><!--Device-ARKUI_BUTTON_ROUNDED_RECTANGLE = 8--><!--Device-ARKUI_BUTTON_ROUNDED_RECTANGLE = 8-End--> |


