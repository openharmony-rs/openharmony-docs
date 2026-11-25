# ArkUI_DialogDismissEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e9a97a68d126c7235376425c6dd78a98d1147512 translatedAt=2026-11-23T06:58:14.231Z pushedAt=2026-11-24T09:22:22.786Z nl=1 -->

```c
typedef struct ArkUI_DialogDismissEvent ArkUI_DialogDismissEvent
```

## Overview

Defines a dialog box dismissal event object, which is used to notify you when a dialog box is dismissed and is suitable for scenarios where the dialog box dismissal event needs to be listened for. This event object uses a callback mechanism. When a dialog box triggers a dismissal operation, the system creates and passes this event object to the callback function you register. Through this object, you can obtain the dismissal reason, set whether to intercept the dismissal, or pass custom data. This event object does not expose its internal members. You need to use the corresponding APIs (such as [OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss](./capi-native-dialog-h.md#oh_arkui_dialogdismissevent_setshouldblockdismiss), [OH_ArkUI_DialogDismissEvent_GetUserData](./capi-native-dialog-h.md#oh_arkui_dialogdismissevent_getuserdata), and [OH_ArkUI_DialogDismissEvent_GetDismissReason](./capi-native-dialog-h.md#oh_arkui_dialogdismissevent_getdismissreason)) to obtain or set the related information.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

