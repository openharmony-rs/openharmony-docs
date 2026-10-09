# OH_ArkUI_UserDataSpan

 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2c5ecf1461774eee81076a9dfbe0054fd9d94ff3 translatedAt=2026-08-21T04:08:38.289Z pushedAt=2026-08-21T07:00:31.060Z -->

```c
typedef struct OH_ArkUI_UserDataSpan OH_ArkUI_UserDataSpan
```

## Overview

Defines a user data span style, which is used to attach custom user data to a styled string in rich text for data identification and association during text interaction or custom rendering. For example, it can be used in scenarios such as attaching a message ID to a message text span in an instant messaging application, or attaching a custom-style tag to a text fragment in a rich text editor.<br>Call [OH_ArkUI_UserDataSpan_Create](capi-styled-string-h.md#oh_arkui_userdataspan_create) to create a user data span style object.<br>After use, call [OH_ArkUI_UserDataSpan_Destroy](capi-styled-string-h.md#oh_arkui_userdataspan_destroy) to destroy the user data span style object.<br>After successful creation, call [OH_ArkUI_UserDataSpan_SetUserData](capi-styled-string-h.md#oh_arkui_userdataspan_setuserdata) to set the user data.<br>Call [OH_ArkUI_UserDataSpan_GetUserData](capi-styled-string-h.md#oh_arkui_userdataspan_getuserdata) to obtain the user data.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)