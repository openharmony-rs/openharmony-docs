# text_area.h

## Overview

Defines a set of TextArea enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_TextAreaType](#arkui_textareatype) | ArkUI_TextAreaType | Enumerates the text box types. |

## Enum type description

### ArkUI_TextAreaType

```c
enum ArkUI_TextAreaType
```

**Description**

Enumerates the text box types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTAREA_TYPE_NORMAL = 0 | Normal input mode. |
| ARKUI_TEXTAREA_TYPE_NUMBER = 2 | Number input mode. |
| ARKUI_TEXTAREA_TYPE_PHONE_NUMBER = 3 | Phone number input mode. |
| ARKUI_TEXTAREA_TYPE_EMAIL = 5 | Email address input mode. |
| ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE = 14 |  |


