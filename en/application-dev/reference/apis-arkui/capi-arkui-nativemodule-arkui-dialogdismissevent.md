# ArkUI_DialogDismissEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d0611b26974cd3320fc5c6f33fb63f1a56638307 translatedAt=2026-09-18T11:33:16.323Z pushedAt=2026-09-20T08:33:34.141Z -->

```c
typedef struct ArkUI_DialogDismissEvent ArkUI_DialogDismissEvent
```

## Overview

Defines a dialog box dismiss event object, which is used to notify you when a dialog box is dismissed and is applicable to scenarios that require listening for dialog box dismiss events. This event object adopts a callback mechanism: when a dialog box triggers a dismiss operation, the system creates and passes this event object to the callback function you registered. Through this object, you can obtain the dismiss reason, set whether to block the dismissal, or pass custom data. This event object does not expose internal members, and relevant information needs to be obtained or set through the corresponding APIs (such as **OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss**, **OH_ArkUI_DialogDismissEvent_GetUserData**, and **OH_ArkUI_DialogDismissEvent_GetDismissReason**).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

