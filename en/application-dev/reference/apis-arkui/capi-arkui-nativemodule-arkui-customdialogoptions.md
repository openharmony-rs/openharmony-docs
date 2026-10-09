# ArkUI_CustomDialogOptions

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-17T02:51:51.217Z pushedAt=2026-07-17T06:07:11.653Z -->

```c
typedef struct ArkUI_CustomDialogOptions ArkUI_CustomDialogOptions
```

## Overview

Defines custom dialog box options. This object does not expose any member fields. You set dialog box attributes (such as the background, rounded corners, shadow, blur, position, and modal) through the APIs prefixed with `OH_ArkUI_CustomDialog_Set` in [ArkUI_NativeModule](capi-arkui-nativemodule.md), and then call `OH_ArkUI_CustomDialog_OpenDialog` to open the dialog box.

**Since**: 19

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)