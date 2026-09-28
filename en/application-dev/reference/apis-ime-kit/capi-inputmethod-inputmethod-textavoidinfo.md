# InputMethod_TextAvoidInfo

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8e856b06a34a819612cae112a81452d688b21bcf translatedAt=2026-08-19T01:22:24.938Z pushedAt=2026-08-24T07:06:19.339Z -->

```c
typedef struct InputMethod_TextAvoidInfo InputMethod_TextAvoidInfo
```

## Overview

Represents a struct that describes the position and height of an edit box on the physical screen for input box avoidance. The input method framework calculates the avoidance area based on **positionY** and **height** in **TextAvoidInfo**, so that the edit box can automatically move up or adjust its layout when the soft keyboard is shown. This ensures that the input area is not covered by the keyboard and remains visible and operable to the user.

Purpose: Serves as the parameter carrier that conveys the vertical position and height information of the edit box to the input method framework so that the edit box can avoid the keyboard area. Based on **positionY** (the y coordinate of the top of the edit box, which must be greater than or equal to 0) and **height** (the height of the edit box, which must be greater than 0), the input method framework determines the complete vertical range of the edit box on the screen (from **positionY** to **positionY** + **height**), compares it with the screen area occupied by the keyboard, and calculates whether avoidance is needed and the avoidance offset.

Usage scenarios: After the edit box is attached to the input method service via **OH_InputMethodController_Attach**, the edit box client passes **TextAvoidInfo** to the input method framework via **InputMethod_TextConfig**. When the keyboard pops up, the input method framework reads the avoidance information, determines whether the edit box is in the area obscured by the keyboard, and triggers the corresponding avoidance adjustment. This struct can also be read by the input method app to learn the screen position of the edit box and optimize the keyboard layout.

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

**Header file**: [inputmethod_text_avoid_info_capi.h](capi-inputmethod-text-avoid-info-capi-h.md)

Related functions

| Function | Description |
| --- | --- |
| [OH_TextAvoidInfo_Create](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_create) | Creates an **InputMethod_TextAvoidInfo** instance. |
| [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) | Destroys an **InputMethod_TextAvoidInfo** instance. |
| [OH_TextAvoidInfo_SetPositionY](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_setpositiony) | Sets the y coordinate value. |
| [OH_TextAvoidInfo_SetHeight](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_setheight) | Sets the height value. |
| [OH_TextAvoidInfo_GetPositionY](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_getpositiony) | Obtains the y coordinate value. |
| [OH_TextAvoidInfo_GetHeight](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_getheight) | Obtains the height value. |
| [OH_TextConfig_GetTextAvoidInfo](capi-inputmethod-text-config-capi-h.md#oh_textconfig_gettextavoidinfo) | Obtains **TextAvoidInfo** from **TextConfig**. |

Related structs

| Structure | Description |
| --- | --- |
| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) | Configuration struct for the text input box, which includes **TextAvoidInfo** as a sub-property. |