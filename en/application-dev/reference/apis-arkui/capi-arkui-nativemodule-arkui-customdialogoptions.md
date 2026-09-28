# ArkUI_CustomDialogOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=34139b640e7f5cff7ecd77a979f553b6821e37f2 translatedAt=2026-09-18T11:31:13.969Z pushedAt=2026-09-20T08:26:33.266Z -->

```c
typedef struct ArkUI_CustomDialogOptions ArkUI_CustomDialogOptions
```

## Overview

Defines custom dialog box options. This object does not expose any member fields. You set dialog box attributes (such as the background, rounded corners, shadow, blur, position, and modal) through the APIs prefixed with `OH_ArkUI_CustomDialog_Set` in [ArkUI_NativeModule](capi-arkui-nativemodule.md), and then call `OH_ArkUI_CustomDialog_OpenDialog` to open the dialog box.

**Since**: 19

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

