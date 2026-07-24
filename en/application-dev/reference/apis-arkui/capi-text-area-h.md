# text_area.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines enumerations and APIs related to **TextArea**.

**File to include:** <arkui/node_attributes/text_area.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_TextAreaType](#arkui_textareatype) | ArkUI_TextAreaType | Enumerates the input method types of multi-line text.|

## Enum Description

### ArkUI_TextAreaType

```c
enum ArkUI_TextAreaType
```

**Description**

Enumerates the input method types of multi-line text.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTAREA_TYPE_NORMAL = 0 | Normal input mode.|
| ARKUI_TEXTAREA_TYPE_NUMBER = 2 | Number input mode.|
| ARKUI_TEXTAREA_TYPE_PHONE_NUMBER = 3 | Phone number input mode.|
| ARKUI_TEXTAREA_TYPE_EMAIL = 5 | Email address input mode.|
| ARKUI_TEXTAREA_TYPE_ONE_TIME_CODE = 14 | Verification code input mode.<br>**Since:** 20|
