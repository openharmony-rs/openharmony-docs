# text_area.h

## Overview

Defines enumerations related to **TextArea**. The **TextArea** component is used for receiving multi-line text input. The enumerated values specify different input types, which affect the validation rules for input content, such as basic input, pure numbers, phone numbers, email addresses, and verification codes. You can select the appropriate enumerated value based on the form type, and the system will automatically provide corresponding content validation, thereby optimizing the user input experience and ensuring the correctness of the data format.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_TextAreaType](#arkui_textareatype) | ArkUI_TextAreaType | Enumerates the input types of multi-line text. Different enumerated values specify the input types of the **<br>TextArea** component and affect the validation rules for the input content. |

## Enum type description

### ArkUI_TextAreaType

```c
enum ArkUI_TextAreaType
```

**Description**

Enumerates the input types of multi-line text. Different enumerated values specify the input types of the **<br>TextArea** component and affect the validation rules for the input content.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTAREA_TYPE_NORMAL = 0 | Normal input mode. |
| ARKUI_TEXTAREA_TYPE_NUMBER = 2 | Number input mode. |
| ARKUI_TEXTAREA_TYPE_PHONE_NUMBER = 3 | Phone number input mode. |
| ARKUI_TEXTAREA_TYPE_EMAIL = 5 | Email address input mode. |
| ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE = 14 |  |


