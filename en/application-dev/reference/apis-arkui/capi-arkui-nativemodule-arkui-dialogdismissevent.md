# ArkUI_DialogDismissEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=86ce2b7ed3ca03b420a1e39316aea5781e8c605d translatedAt=2026-11-09T11:41:11.380Z pushedAt=2026-11-10T02:03:25.002Z nl=1 -->

```c
typedef struct ArkUI_DialogDismissEvent ArkUI_DialogDismissEvent
```

## Overview

Defines a dialog box dismissal event object, which is used to notify you when a dialog box is dismissed and is suitable for scenarios where the dialog box dismissal event needs to be listened for. This event object uses a callback mechanism. When a dialog box triggers a dismissal operation, the system creates and passes this event object to the callback function you register. Through this object, you can obtain the dismissal reason, set whether to intercept the dismissal, or pass custom data. This event object does not expose its internal members. You need to use the corresponding APIs (such as [OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss](./capi-native-dialog-h.md#oh_arkui_dialogdismissevent_setshouldblockdismiss), [OH_ArkUI_DialogDismissEvent_GetUserData](./capi-native-dialog-h.md#oh_arkui_dialogdismissevent_getuserdata), and [OH_ArkUI_DialogDismissEvent_GetDismissReason](./capi-native-dialog-h.md#oh_arkui_dialogdismissevent_getdismissreason)) to obtain or set the related information.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

