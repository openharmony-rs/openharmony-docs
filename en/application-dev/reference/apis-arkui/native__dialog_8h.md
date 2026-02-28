# native_dialog.h


## Overview

Declares a set of custom dialog box APIs of ArkUI on the native side.

**Library**: libace_ndk.z.so

**File to include**: <arkui/native_dialog.h>

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](_ark_u_i___native_module.md)


## Summary


### Structs

| Name| Description|
| -------- | -------- |
| struct&nbsp;&nbsp;[ArkUI_NativeDialogAPI_1](_ark_u_i___native_dialog_a_p_i__1.md) | Collection of native-side custom dialog box APIs provided by ArkUI. The range is **ArkUI_NativeDialogAPI_1**. |
| struct&nbsp;&nbsp;[ArkUI_NativeDialogAPI_2](_ark_u_i___native_dialog_a_p_i__2.md) | Collection of native-side custom dialog box APIs provided by ArkUI. The range is **ArkUI_NativeDialogAPI_2**. |
| struct&nbsp;&nbsp;[ArkUI_NativeDialogAPI_3](_ark_u_i___native_dialog_a_p_i__3.md) | Collection of native-side custom dialog box APIs provided by ArkUI. The range is **ArkUI_NativeDialogAPI_3**. |


### Types

| Name| Description|
| -------- | -------- |
| typedef bool(\* [ArkUI_OnWillDismissEvent](_ark_u_i___native_module.md#arkui_onwilldismissevent)) (int32_t reason) | Invoked when the dialog box is closed. |
| typedef struct [ArkUI_DialogDismissEvent](_ark_u_i___native_module.md#arkui_dialogdismissevent) [ArkUI_DialogDismissEvent](_ark_u_i___native_module.md#arkui_dialogdismissevent) | Defines a struct for a dialog box dismiss event. |
| typedef struct [ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) [ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) | Defines a struct for custom dialog box options.|


### Enums

| Name| Description|
| -------- | -------- |
| [ArkUI_DismissReason](_ark_u_i___native_module.md#arkui_dismissreason) { DIALOG_DISMISS_BACK_PRESS = 0, DIALOG_DISMISS_TOUCH_OUTSIDE, DIALOG_DISMISS_CLOSE_BUTTON, DIALOG_DISMISS_SLIDE_DOWN } | Enumerates the actions for triggering closure of the dialog box. |
| [ArkUI_LevelMode](_ark_u_i___native_module.md#arkui_levelmode) { ARKUI_LEVEL_MODE_OVERLAY = 0, ARKUI_LEVEL_MODE_EMBEDDED } | Enumerates the display level modes of the dialog box. |
| [ArkUI_ImmersiveMode](_ark_u_i___native_module.md#arkui_immersivemode) { ARKUI_IMMERSIVE_MODE_DEFAULT = 0, ARKUI_IMMERSIVE_MODE_EXTEND } | Enumerates the display areas of the embedded dialog box overlay. |
| [ArkUI_DialogState](_ark_u_i___native_module.md#arkui_dialogstate) { DIALOG_UNINITIALIZED = 0, DIALOG_INITIALIZED, DIALOG_APPEARING, DIALOG_APPEARED, DIALOG_DISAPPEARING, DIALOG_DISAPPEARED } | Enumerates the dialog box status. |


### Functions

| Name| Description|
| -------- | -------- |
| void [OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss](_ark_u_i___native_module.md#oh_arkui_dialogdismissevent_setshouldblockdismiss) ([ArkUI_DialogDismissEvent](_ark_u_i___native_module.md#arkui_dialogdismissevent) \*event, bool shouldBlockDismiss) | Sets whether to block the system behavior of dismissing a dialog box. |
| void \* [OH_ArkUI_DialogDismissEvent_GetUserData](_ark_u_i___native_module.md#oh_arkui_dialogdismissevent_getuserdata) ([ArkUI_DialogDismissEvent](_ark_u_i___native_module.md#arkui_dialogdismissevent) \*event) | Obtains the pointer to user data in a dialog box dismiss event object. |
| int32_t [OH_ArkUI_DialogDismissEvent_GetDismissReason](_ark_u_i___native_module.md#oh_arkui_dialogdismissevent_getdismissreason) ([ArkUI_DialogDismissEvent](_ark_u_i___native_module.md#arkui_dialogdismissevent) \*event) | Obtains the dismissal reason from a dialog box dismiss event object. |
| int32_t [OH_ArkUI_CustomDialog_OpenDialog](_ark_u_i___native_module.md#oh_arkui_customdialog_opendialog) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, void (\*callback)(int32_t dialogId)) | Displays a custom dialog box. |
| int32_t [OH_ArkUI_CustomDialog_UpdateDialog](_ark_u_i___native_module.md#oh_arkui_customdialog_updatedialog) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, void (\*callback)(int32_t dialogId)) | Updates a custom dialog box. |
| int32_t [OH_ArkUI_CustomDialog_CloseDialog](_ark_u_i___native_module.md#oh_arkui_customdialog_closedialog) (int32_t dialogId) | Closes a custom dialog box. |
| ArkUI_CustomDialogOptions\* [OH_ArkUI_CustomDialog_CreateOptions](_ark_u_i___native_module.md#oh_arkui_customdialog_createoptions) ([ArkUI_NodeHandle](_ark_u_i___native_module.md#arkui_nodehandle) content) | Creates options for a custom dialog box. |
| void [OH_ArkUI_CustomDialog_DisposeOptions](_ark_u_i___native_module.md#oh_arkui_customdialog_disposeoptions) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options) | Disposes options for a custom dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetLevelMode](_ark_u_i___native_module.md#oh_arkui_customdialog_setlevelmode) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, [ArkUI_LevelMode](_ark_u_i___native_module.md#arkui_levelmode) levelMode) | Sets the display level mode for a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetLevelUniqueId](_ark_u_i___native_module.md#oh_arkui_customdialog_setleveluniqueid) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, int32_t uniqueId) | Sets the ID of the node under a dialog box's display level. |
| int32_t [OH_ArkUI_CustomDialog_SetImmersiveMode](_ark_u_i___native_module.md#oh_arkui_customdialog_setimmersivemode) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, [ArkUI_ImmersiveMode](_ark_u_i___native_module.md#arkui_immersivemode) immersiveMode) | Sets the display area of the embedded dialog box overlay. |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundColor](_ark_u_i___native_module.md#oh_arkui_customdialog_setbackgroundcolor) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, uint32_t backgroundColor) | Sets the background color of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetCornerRadius](_ark_u_i___native_module.md#oh_arkui_customdialog_setcornerradius) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, float topLeft, float topRight, float bottomLeft, float bottomRight) | Sets the corner radius for a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetBorderWidth](_ark_u_i___native_module.md#oh_arkui_customdialog_setborderwidth) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, float top, float right, float bottom, float left, [ArkUI_LengthMetricUnit](_ark_u_i___native_module.md#arkui_lengthmetricunit) unit) | Sets the border width of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetBorderColor](_ark_u_i___native_module.md#oh_arkui_customdialog_setbordercolor) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left) | Sets the border color of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetBorderStyle](_ark_u_i___native_module.md#oh_arkui_customdialog_setborderstyle) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, int32_t top, int32_t right, int32_t bottom, int32_t left) | Sets the border style of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetWidth](_ark_u_i___native_module.md#oh_arkui_customdialog_setwidth) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, float width, [ArkUI_LengthMetricUnit](_ark_u_i___native_module.md#arkui_lengthmetricunit) unit) | Sets the backdrop width of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetHeight](_ark_u_i___native_module.md#oh_arkui_customdialog_setheight) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, float height, [ArkUI_LengthMetricUnit](_ark_u_i___native_module.md#arkui_lengthmetricunit) unit) | Sets the backdrop height of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetShadow](_ark_u_i___native_module.md#oh_arkui_customdialog_setshadow) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, [ArkUI_ShadowStyle](_ark_u_i___native_module.md#arkui_shadowstyle) shadow) | Sets the backdrop shadow of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetCustomShadow](_ark_u_i___native_module.md#oh_arkui_customdialog_setcustomshadow) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, const [ArkUI_AttributeItem](_ark_u_i___attribute_item.md) \*customShadow) | Sets the custom shadow of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundBlurStyle](_ark_u_i___native_module.md#oh_arkui_customdialog_setbackgroundblurstyle) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, [ArkUI_BlurStyle](_ark_u_i___native_module.md#arkui_blurstyle) blurStyle) | Sets the background blur style of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetAlignment](_ark_u_i___native_module.md#oh_arkui_customdialog_setalignment) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, int32_t alignment, float offsetX, float offsetY) | Sets the alignment mode of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetModalMode](_ark_u_i___native_module.md#oh_arkui_customdialog_setmodalmode) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, bool isModal) | Sets the modal mode for a custom dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetAutoCancel](_ark_u_i___native_module.md#oh_arkui_customdialog_setautocancel) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, bool autoCancel) | Sets whether to allow users to touch the mask to dismiss a custom dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetSubwindowMode](_ark_u_i___native_module.md#oh_arkui_customdialog_setsubwindowmode) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, bool showInSubwindow) | Sets whether to display the dialog box in a subwindow. |
| int32_t [OH_ArkUI_CustomDialog_SetMask](_ark_u_i___native_module.md#oh_arkui_customdialog_setmask) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, uint32_t maskColor, const [ArkUI_Rect](_ark_u_i___rect.md) \*maskRect) | Sets the mask for a custom dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetKeyboardAvoidMode](_ark_u_i___native_module.md#oh_arkui_customdialog_setkeyboardavoidmode) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, [ArkUI_KeyboardAvoidMode](_ark_u_i___native_module.md#arkui_keyboardavoidmode) keyboardAvoidMode) | Sets the keyboard avoidance mode of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetHoverModeEnabled](_ark_u_i___native_module.md#oh_arkui_customdialog_sethovermodeenabled) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, bool enabled) | Sets whether to enable the hover mode for a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetHoverModeArea](_ark_u_i___native_module.md#oh_arkui_customdialog_sethovermodearea) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, [ArkUI_HoverModeAreaType](_ark_u_i___native_module.md#arkui_hovermodeareatype) hoverModeAreaType) | Sets the default display area of a dialog box in hover mode. |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback](_ark_u_i___native_module.md#oh_arkui_customdialog_registeronwilldismisscallback) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)([ArkUI_DialogDismissEvent](_ark_u_i___native_module.md#arkui_dialogdismissevent) \*event)) | Registers a callback for the dismissal event of a custom dialog box. |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback](_ark_u_i___native_module.md#oh_arkui_customdialog_registeronwillappearcallback) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | Registers a callback to be invoked when the specified custom dialog box is about to appear. |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback](_ark_u_i___native_module.md#oh_arkui_customdialog_registerondidappearcallback) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | Registers a callback to be invoked when the specified custom dialog box appears. |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback](_ark_u_i___native_module.md#oh_arkui_customdialog_registeronwilldisappearcallback) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | Registers a callback to be invoked when the specified custom dialog box is about to disappear. |
| int32_t [OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback](_ark_u_i___native_module.md#oh_arkui_customdialog_registerondiddisappearcallback) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, void\* userData, void (\*callback)(void\* userData)) | Registers a callback to be invoked when the specified custom dialog box disappears. |
| int32_t [OH_ArkUI_CustomDialog_GetState](_ark_u_i___native_module.md#oh_arkui_customdialog_getstate) ([ArkUI_NativeDialogHandle](_ark_u_i___native_module.md#arkui_nativedialoghandle) \handle, [ArkUI_DialogState](_ark_u_i___native_module.md#arkui_dialogstate) \*state) | Obtains the state of a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions](_ark_u_i___native_module.md#oh_arkui_customdialog_setbackgroundblurstyleoptions) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, const [ArkUI_AttributeItem](_ark_u_i___attribute_item.md) \*backgroundBlurStyleOptions) | Sets the background blur effect for a dialog box. |
| int32_t [OH_ArkUI_CustomDialog_SetBackgroundEffect](_ark_u_i___native_module.md#oh_arkui_customdialog_setbackgroundeffect) ([ArkUI_CustomDialogOptions](_ark_u_i___native_module.md#arkui_customdialogoptions) \*options, const [ArkUI_AttributeItem](_ark_u_i___attribute_item.md) \*backgroundEffect) | Sets the background effect parameters for a dialog box.|
