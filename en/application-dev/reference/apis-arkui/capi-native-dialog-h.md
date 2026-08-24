# native_dialog.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f9ee958314ea662124f5aa4c8b3902f47eb53485 translatedAt=2026-08-21T12:11:06.379Z pushedAt=2026-08-24T09:08:35.543Z -->

## Overview

Declares a set of custom dialog box APIs of ArkUI on the native side. These APIs support creating, displaying, updating, and closing custom dialog boxes, setting dialog box styles, backgrounds, borders, shadows, and other attributes, and registering listeners for dialog box lifecycle events. They are suitable for scenarios where flexible dialog box interactions need to be implemented on the native side.

**File to include**: <arkui/native_dialog.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[NativeDialogSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeDialogSample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_NativeDialogAPI_1](capi-arkui-nativemodule-arkui-nativedialogapi-1.md) | ArkUI_NativeDialogAPI_1 | Provides a collection of native-side custom dialog box APIs provided by ArkUI.|
| [ArkUI_NativeDialogAPI_2](capi-arkui-nativemodule-arkui-nativedialogapi-2.md) | ArkUI_NativeDialogAPI_2 | Provides a collection of native-side custom dialog box APIs provided by ArkUI.|
| [ArkUI_NativeDialogAPI_3](capi-arkui-nativemodule-arkui-nativedialogapi-3.md) | ArkUI_NativeDialogAPI_3 | Provides a collection of native-side custom dialog box APIs provided by ArkUI.|
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md) | ArkUI_DialogDismissEvent | Defines a dialog box dismiss event.|
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md) | ArkUI_CustomDialogOptions | Defines custom dialog box options. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_DismissReason](#arkui_dismissreason) | ArkUI_DismissReason | Enumerates the actions for triggering closure of the dialog box.|
| [ArkUI_LevelMode](#arkui_levelmode) | ArkUI_LevelMode | Enumerates the display level modes of the dialog box.|
| [ArkUI_ImmersiveMode](#arkui_immersivemode) | ArkUI_ImmersiveMode | Enumerates the display areas of the embedded dialog box overlay.|
| [OH_ArkUI_DialogDisplayModeInSubWindow](#oh_arkui_dialogdisplaymodeinsubwindow) | OH_ArkUI_DialogDisplayModeInSubWindow | Enumerates the display modes of the dialog box in the subwindow.|
| [ArkUI_DialogState](#arkui_dialogstate) | ArkUI_DialogState | Enumerates dialog box states. |

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef bool (\*ArkUI_OnWillDismissEvent)(int32_t reason)](#arkui_onwilldismissevent) | ArkUI_OnWillDismissEvent | Defines a pointer to the callback invoked when the dialog box is closed.|
| [typedef void (\*ArkUI_OpenDialogCallback)(int32_t errorCode, int32_t dialogId, void* userData)](#arkui_opendialogcallback) | ArkUI_OpenDialogCallback | Defines a pointer to the callback invoked when the dialog box is displayed. |
| [void OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss(ArkUI_DialogDismissEvent* event, bool shouldBlockDismiss)](#oh_arkui_dialogdismissevent_setshouldblockdismiss) | - | Sets whether to block the system behavior of dismissing a dialog box.|
| [void* OH_ArkUI_DialogDismissEvent_GetUserData(ArkUI_DialogDismissEvent* event)](#oh_arkui_dialogdismissevent_getuserdata) | - | Obtains the pointer to user data in a dialog box dismiss event object.|
| [int32_t OH_ArkUI_DialogDismissEvent_GetDismissReason(ArkUI_DialogDismissEvent* event)](#oh_arkui_dialogdismissevent_getdismissreason) | - | Obtains the dismissal reason from a dialog box dismiss event object. |
| [int32_t OH_ArkUI_CustomDialog_OpenDialog(ArkUI_CustomDialogOptions* options, void (\*callback)(int32_t dialogId))](#oh_arkui_customdialog_opendialog) | - | Displays a custom dialog box.|
| [void OH_ArkUI_CustomDialog_OpenDialogWithCallback(ArkUI_CustomDialogOptions* options, void* userData, ArkUI_OpenDialogCallback callback)](#oh_arkui_customdialog_opendialogwithcallback) | - | Displays a custom dialog box and returns the result and dialog box ID through the callback. |
| [int32_t OH_ArkUI_CustomDialog_UpdateDialog(ArkUI_CustomDialogOptions* options, void (*callback)(int32_t dialogId))](#oh_arkui_customdialog_updatedialog) | - | Updates a custom dialog box.|
| [int32_t OH_ArkUI_CustomDialog_CloseDialog(int32_t dialogId)](#oh_arkui_customdialog_closedialog) | - | Closes a custom dialog box.|
| [ArkUI_CustomDialogOptions* OH_ArkUI_CustomDialog_CreateOptions(ArkUI_NodeHandle content)](#oh_arkui_customdialog_createoptions) | - | Creates custom dialog box options.|
| [void OH_ArkUI_CustomDialog_DisposeOptions(ArkUI_CustomDialogOptions* options)](#oh_arkui_customdialog_disposeoptions) | - | Disposes of the custom dialog box options.|
| [int32_t OH_ArkUI_CustomDialog_SetLevelMode(ArkUI_CustomDialogOptions* options, ArkUI_LevelMode levelMode)](#oh_arkui_customdialog_setlevelmode) | - | Sets the display level of the dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetLevelUniqueId(ArkUI_CustomDialogOptions* options, int32_t uniqueId)](#oh_arkui_customdialog_setleveluniqueid) | - | Sets the ID of the node under the dialog box's display level.|
| [int32_t OH_ArkUI_CustomDialog_SetImmersiveMode(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMode immersiveMode)](#oh_arkui_customdialog_setimmersivemode) | - | Sets the display area of the embedded dialog box overlay.|
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundColor(ArkUI_CustomDialogOptions* options, uint32_t backgroundColor)](#oh_arkui_customdialog_setbackgroundcolor) | - | Sets the background color of a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetCornerRadius(ArkUI_CustomDialogOptions* options, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_customdialog_setcornerradius) | - | Sets the corner radius for a custom dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetBorderWidth(ArkUI_CustomDialogOptions* options, float top, float right, float bottom, float left, ArkUI_LengthMetricUnit unit)](#oh_arkui_customdialog_setborderwidth) | - | Sets the border width of a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetBorderColor(ArkUI_CustomDialogOptions* options, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left)](#oh_arkui_customdialog_setbordercolor) | - | Sets the border color of the dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetBorderStyle(ArkUI_CustomDialogOptions* options, int32_t top, int32_t right, int32_t bottom, int32_t left)](#oh_arkui_customdialog_setborderstyle) | - | Sets the border style of a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetWidth(ArkUI_CustomDialogOptions* options, float width, ArkUI_LengthMetricUnit unit)](#oh_arkui_customdialog_setwidth) | - | Sets the width of the dialog box background.|
| [int32_t OH_ArkUI_CustomDialog_SetHeight(ArkUI_CustomDialogOptions* options, float height, ArkUI_LengthMetricUnit unit)](#oh_arkui_customdialog_setheight) | - | Sets the height of the dialog box background.|
| [int32_t OH_ArkUI_CustomDialog_SetShadow(ArkUI_CustomDialogOptions* options, ArkUI_ShadowStyle shadow)](#oh_arkui_customdialog_setshadow) | - | Sets the shadow of the dialog box background.|
| [int32_t OH_ArkUI_CustomDialog_SetCustomShadow(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* customShadow)](#oh_arkui_customdialog_setcustomshadow) | - | Sets the shadow of the dialog box background.|
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyle(ArkUI_CustomDialogOptions* options, ArkUI_BlurStyle blurStyle)](#oh_arkui_customdialog_setbackgroundblurstyle) | - | Sets the background blur style of the dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetAlignment(ArkUI_CustomDialogOptions* options, int32_t alignment, float offsetX, float offsetY)](#oh_arkui_customdialog_setalignment) | - | Sets the alignment mode of a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetModalMode(ArkUI_CustomDialogOptions* options, bool isModal)](#oh_arkui_customdialog_setmodalmode) | - | Sets the modal mode for a custom dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetAutoCancel(ArkUI_CustomDialogOptions* options, bool autoCancel)](#oh_arkui_customdialog_setautocancel) | - | Specifies whether to allow users to touch the mask to dismiss the custom dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetSubwindowMode(ArkUI_CustomDialogOptions* options, bool showInSubwindow)](#oh_arkui_customdialog_setsubwindowmode) | - | Sets whether to display the dialog box in a subwindow.|
| [int32_t OH_ArkUI_CustomDialog_SetDisplayModeInSubWindow(ArkUI_CustomDialogOptions* options, OH_ArkUI_DialogDisplayModeInSubWindow displayModeInSubWindow)](#oh_arkui_customdialog_setdisplaymodeinsubwindow) | - | Sets the display mode of the dialog box in the subwindow.|
| [int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterial(ArkUI_NativeDialogHandle handle, ArkUI_ImmersiveMaterialHandle material)](#oh_arkui_nativemodule_customdialog_setsystemmaterial) | - | Sets the immersive material for a specified dialog box.|
| [int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterialInOptions(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMaterialHandle material)](#oh_arkui_nativemodule_customdialog_setsystemmaterialinoptions) | - | Sets the immersive material attributes for a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetMask(ArkUI_CustomDialogOptions* options, uint32_t maskColor, const ArkUI_Rect* maskRect)](#oh_arkui_customdialog_setmask) | - | Sets the mask for a custom dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetKeyboardAvoidMode(ArkUI_CustomDialogOptions* options, ArkUI_KeyboardAvoidMode keyboardAvoidMode)](#oh_arkui_customdialog_setkeyboardavoidmode) | - | Sets the keyboard avoidance mode of a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetHoverModeEnabled(ArkUI_CustomDialogOptions* options, bool enabled)](#oh_arkui_customdialog_sethovermodeenabled) | - | Sets whether to enable the hover mode for a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetHoverModeArea(ArkUI_CustomDialogOptions* options, ArkUI_HoverModeAreaType hoverModeAreaType)](#oh_arkui_customdialog_sethovermodearea) | - | Sets the default display area of a dialog box in hover mode.|
| [int32_t OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(ArkUI_DialogDismissEvent* event))](#oh_arkui_customdialog_registeronwilldismisscallback) | - | Registers a callback for the dismissal event of a custom dialog box.|
| [int32_t OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registeronwillappearcallback) | - | Registers a callback to be invoked when the specified custom dialog box is about to appear.|
| [int32_t OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registerondidappearcallback) | - | Registers a callback to be invoked when the specified custom dialog box appears.|
| [int32_t OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registeronwilldisappearcallback) | - | Registers a callback to be invoked when the specified custom dialog box is about to disappear.|
| [int32_t OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registerondiddisappearcallback) | - | Registers a callback to be invoked when the specified custom dialog box disappears.|
| [int32_t OH_ArkUI_CustomDialog_GetState(ArkUI_NativeDialogHandle handle, ArkUI_DialogState* state)](#oh_arkui_customdialog_getstate) | - | Obtains the state of a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundBlurStyleOptions)](#oh_arkui_customdialog_setbackgroundblurstyleoptions) | - | Sets the background blur effect for a dialog box.|
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundEffect(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundEffect)](#oh_arkui_customdialog_setbackgroundeffect) | - | Sets the background effect parameters for a dialog box.|

## Enum Description

### ArkUI_DismissReason

```c
enum ArkUI_DismissReason
```

**Description**

Enumerates the actions for triggering closure of the dialog box.

**Since**: 12

| Value| Description|
| -- | -- |
| DIALOG_DISMISS_BACK_PRESS = 0 | Touching the Back button, swiping left or right on the screen, or pressing the Esc key.|
| DIALOG_DISMISS_TOUCH_OUTSIDE = 1 | Touching the mask. |
| DIALOG_DISMISS_CLOSE_BUTTON = 2 | Touching the Close button.|
| DIALOG_DISMISS_SLIDE_DOWN = 3 | Sliding down.|

### ArkUI_LevelMode

```c
enum ArkUI_LevelMode
```

**Description**

Enumerates the display level modes of the dialog box.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_LEVEL_MODE_OVERLAY = 0 | The dialog box is displayed above all other application content.|
| ARKUI_LEVEL_MODE_EMBEDDED = 1 | The dialog box is embedded within the application's page content.|

### ArkUI_ImmersiveMode

```c
enum ArkUI_ImmersiveMode
```

**Description**

Enumerates the display areas of the embedded dialog box overlay.

**Since**: 15

| Value| Description|
| -- | -- |
| ARKUI_IMMERSIVE_MODE_DEFAULT = 0 | The dialog box overlay follows the layout constraints of its parent node.|
| ARKUI_IMMERSIVE_MODE_EXTEND = 1 | The dialog box overlay can extend to cover the status bar and navigation bar for a more immersive look.|

### OH_ArkUI_DialogDisplayModeInSubWindow

```c
enum OH_ArkUI_DialogDisplayModeInSubWindow
```

**Description**

Enumerates the display modes of the dialog box in the subwindow.

**Since**: 26.0.0

| Value| Description|
| -- | -- |
| OH_ARKUI_DIALOG_DISPLAY_MODE_SCREEN_BASED = 0 | The dialog box is displayed in the center of the screen.|
| OH_ARKUI_DIALOG_DISPLAY_MODE_WINDOW_BASED = 1 | The dialog box is displayed in the center of the application window.|

### ArkUI_DialogState

```c
enum ArkUI_DialogState
```

**Description**

Enumerates dialog box states.

**Since**: 20

| Value| Description|
| -- | -- |
| DIALOG_UNINITIALIZED = 0 | State before the controller is bound to the dialog box.|
| DIALOG_INITIALIZED = 1 | State after the controller is bound to the dialog box.|
| DIALOG_APPEARING = 2 | State during the dialog box appearance animation.|
| DIALOG_APPEARED = 3 | State after the dialog display appearance ends.|
| DIALOG_DISAPPEARING = 4 | State during the dialog box disappearance animation.|
| DIALOG_DISAPPEARED = 5 | State after the dialog box disappearance animation ends.|

## Function Description

### ArkUI_OnWillDismissEvent()

```c
typedef bool (*ArkUI_OnWillDismissEvent)(int32_t reason)
```

**Description**

Defines a pointer to the callback invoked when the dialog box is closed.

**Since**: 12

**Parameters**

| Name | Description |
| -------- | -------- |
| int32_t reason | Reason for dialog box dismissal, which is specified by [ArkUI_DismissReason](#arkui_dismissreason). |

**Returns**

| Type| Description|
| -- | -- |
| bool | Any return value indicates that the dialog box will not be closed.|

### OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss()

```c
void OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss(ArkUI_DialogDismissEvent* event, bool shouldBlockDismiss)
```

**Description**

Sets whether to block the system behavior of dismissing a dialog box. The value **true** indicates that the system behavior is blocked and the dialog box is not dismissed, and **false** indicates that it is not blocked. When there are important unfinished operations in the dialog box (such as unsaved form data or payment confirmation), you can set **shouldBlockDismiss** to **true** to prevent users from dismissing the dialog box through system methods such as touching the Back button, swiping left or right on the screen, or pressing the Esc key, forcing them to complete the operation or tap the dismissal button.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md)* event | Pointer to a dialog box dismiss event object.|
| bool shouldBlockDismiss | Whether to block the system behavior of dismissing a dialog box. The value **true** indicates that the system behavior is blocked and the dialog box is not dismissed; **false** indicates that the system behavior is not blocked and the dialog box is allowed to be dismissed. |

### OH_ArkUI_DialogDismissEvent_GetUserData()

```c
void* OH_ArkUI_DialogDismissEvent_GetUserData(ArkUI_DialogDismissEvent* event)
```

**Description**

Obtains the pointer to user data in a dialog box dismiss event object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md)* event | Pointer to a dialog box dismiss event object.|

**Returns**

| Type| Description|
| -- | -- |
| void* | Pointer to the user-defined data passed in when registering the callback. It is commonly used to obtain context information in the callback function. |

### OH_ArkUI_DialogDismissEvent_GetDismissReason()

```c
int32_t OH_ArkUI_DialogDismissEvent_GetDismissReason(ArkUI_DialogDismissEvent* event)
```

**Description**

Obtains the dismissal reason from a dialog box dismiss event object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md)* event | Pointer to a dialog box dismiss event object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Dismissal reason, or **-1** if an exception occurs.<br>         [DIALOG_DISMISS_BACK_PRESS](#arkui_dismissreason): touching the Back button, swiping left or right on the screen, or pressing the Esc key.<br>         [DIALOG_DISMISS_TOUCH_OUTSIDE](#arkui_dismissreason): touching the mask.<br>         [DIALOG_DISMISS_CLOSE_BUTTON](#arkui_dismissreason): touching the close button.<br>         [DIALOG_DISMISS_SLIDE_DOWN](#arkui_dismissreason): swiping down. |

### OH_ArkUI_CustomDialog_OpenDialog()

```c
int32_t OH_ArkUI_CustomDialog_OpenDialog(ArkUI_CustomDialogOptions* options, void (*callback)(int32_t dialogId))
```

**Description**

Displays a custom dialog box.

**Since**: 19

**Parameters**

| Name                                   | Description|
|----------------------------------------| -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| void (*callback)(int32_t dialogId) | Pointer to the callback invoked when the dialog box is displayed, which returns the dialog box ID. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### ArkUI_OpenDialogCallback()

```c
typedef void (*ArkUI_OpenDialogCallback)(int32_t errorCode, int32_t dialogId, void* userData)
```

**Description**

A callback invoked when the dialog box is displayed.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| int32_t errorCode | Result of displaying the dialog box.<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode): The operation is successful.<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode): A parameter error occurs.<br>         [ARKUI_ERROR_CODE_DIALOG_NODE_MOUNT_FAILURE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode): The dialog box cannot be displayed because the node fails to be mounted.<br>         [ARKUI_ERROR_CODE_DIALOG_SUBWINDOW_CREATE_FAILURE](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode): The dialog box cannot be displayed because the subwindow fails to be created.|
| int32_t dialogId | ID of the dialog box. The value **-1** is returned when the dialog box cannot be displayed.|
| void* userData | Pointer to the user-defined data.|

### OH_ArkUI_CustomDialog_OpenDialogWithCallback()

```c
void OH_ArkUI_CustomDialog_OpenDialogWithCallback(ArkUI_CustomDialogOptions* options, void* userData, ArkUI_OpenDialogCallback callback)
```

**Description**

Opens a custom dialog box.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration. |
| void* userData | Pointer to the user-defined data.|
| [ArkUI_OpenDialogCallback](#arkui_opendialogcallback) callback | Callback invoked when the dialog box is displayed. The input parameters are the error code and the dialog box ID.|

### OH_ArkUI_CustomDialog_UpdateDialog()

```c
int32_t OH_ArkUI_CustomDialog_UpdateDialog(ArkUI_CustomDialogOptions* options, void (*callback)(int32_t dialogId))
```

**Description**

Updates a custom dialog box.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| void (*callback)(int32_t dialogId)                               | Pointer to the callback for updating the dialog box, which returns the dialog box ID. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_CloseDialog()

```c
int32_t OH_ArkUI_CustomDialog_CloseDialog(int32_t dialogId)
```

**Description**

Closes a custom dialog box.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| int32_t dialogId | ID of the dialog box to close.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_CreateOptions()

```c
ArkUI_CustomDialogOptions* OH_ArkUI_CustomDialog_CreateOptions(ArkUI_NodeHandle content)
```

**Description**

Creates custom dialog box options.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) content | Pointer to the content node of the custom dialog box. The type is **ArkUI_NodeHandle**. |

**Returns**

| Type                            | Description|
|--------------------------------| -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* | Pointer to the custom dialog box configuration.|

### OH_ArkUI_CustomDialog_DisposeOptions()

```c
void OH_ArkUI_CustomDialog_DisposeOptions(ArkUI_CustomDialogOptions* options)
```

**Description**

Disposes of the custom dialog box options.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the custom dialog box configuration.|

### OH_ArkUI_CustomDialog_SetLevelMode()

```c
int32_t OH_ArkUI_CustomDialog_SetLevelMode(ArkUI_CustomDialogOptions* options, ArkUI_LevelMode levelMode)
```

**Description**

Sets the display level of the dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the custom dialog box configuration.|
| [ArkUI_LevelMode](#arkui_levelmode) levelMode | Display level of the dialog box. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetLevelUniqueId()

```c
int32_t OH_ArkUI_CustomDialog_SetLevelUniqueId(ArkUI_CustomDialogOptions* options, int32_t uniqueId)
```

**Description**

Sets the ID of the node under the dialog box's display level.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the custom dialog box options.|
| int32_t uniqueId | ID of the node under the dialog box's display level. The dialog box will be displayed on the same page as this node.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetImmersiveMode()

```c
int32_t OH_ArkUI_CustomDialog_SetImmersiveMode(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMode immersiveMode)
```

**Description**

Sets the display area of the embedded dialog box overlay.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the custom dialog box configuration.|
| [ArkUI_ImmersiveMode](#arkui_immersivemode) immersiveMode | Area covered by the mask of an embedded dialog box. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetBackgroundColor()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundColor(ArkUI_CustomDialogOptions* options, uint32_t backgroundColor)
```

**Description**

Sets the background color of a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| uint32_t backgroundColor | Background color of the dialog box, in 0xARGB format.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetCornerRadius()

```c
int32_t OH_ArkUI_CustomDialog_SetCornerRadius(ArkUI_CustomDialogOptions* options, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**Description**

Sets the corner radius for a custom dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| float topLeft | Radius of the upper left corner of the dialog box, in vp. Default value: 32vp. |
| float topRight | Radius of the upper right corner of the dialog box, in vp. Default value: 32vp. |
| float bottomLeft | Radius of the lower left corner of the dialog box, in vp. Default value: 32vp. |
| float bottomRight | Radius of the lower right corner of the dialog box, in vp. Default value: 32vp. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetBorderWidth()

```c
int32_t OH_ArkUI_CustomDialog_SetBorderWidth(ArkUI_CustomDialogOptions* options, float top, float right, float bottom, float left, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the border width of a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| float top | Width of the top border of the dialog box, in vp. |
| float right | Width of the right border of the dialog box, in vp. |
| float bottom | Width of the bottom border of the dialog box, in vp. |
| float left | Width of the left border of the dialog box, in vp. |
| [ArkUI_LengthMetricUnit](capi-native-type-h.md#arkui_lengthmetricunit) unit | Unit of the width. The default value is vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetBorderColor()

```c
int32_t OH_ArkUI_CustomDialog_SetBorderColor(ArkUI_CustomDialogOptions* options, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left)
```

**Description**

Sets the border color of the dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| uint32_t top | Color of the top border of the dialog box, in 0xARGB format.|
| uint32_t right | Color of the right border of the dialog box, in 0xARGB format.|
| uint32_t bottom | Color of the bottom border of the dialog box, in 0xARGB format.|
| uint32_t left | Color of the left border of the dialog box, in 0xARGB format.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetBorderStyle()

```c
int32_t OH_ArkUI_CustomDialog_SetBorderStyle(ArkUI_CustomDialogOptions* options, int32_t top, int32_t right, int32_t bottom, int32_t left)
```

**Description**

Sets the border style of a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| int32_t top | Style of the top border of the dialog box. The default value is **ARKUI_BORDER_STYLE_SOLID**. |
| int32_t right | Style of the right border of the dialog box. The default value is **ARKUI_BORDER_STYLE_SOLID**. |
| int32_t bottom | Style of the bottom border of the dialog box. The default value is **ARKUI_BORDER_STYLE_SOLID**. |
| int32_t left | Style of the left border of the dialog box. The default value is **ARKUI_BORDER_STYLE_SOLID**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetWidth()

```c
int32_t OH_ArkUI_CustomDialog_SetWidth(ArkUI_CustomDialogOptions* options, float width, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the width of the dialog box background.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| float width | Width of the dialog box background, in vp. |
| [ArkUI_LengthMetricUnit](capi-native-type-h.md#arkui_lengthmetricunit) unit | Unit of the width. The default value is vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetHeight()

```c
int32_t OH_ArkUI_CustomDialog_SetHeight(ArkUI_CustomDialogOptions* options, float height, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the height of the dialog box background.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| float height | Height of the dialog box background, in vp. |
| [ArkUI_LengthMetricUnit](capi-native-type-h.md#arkui_lengthmetricunit) unit | Unit of the height. The default value is vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetShadow()

```c
int32_t OH_ArkUI_CustomDialog_SetShadow(ArkUI_CustomDialogOptions* options, ArkUI_ShadowStyle shadow)
```

**Description**

Sets the shadow of the dialog box background.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| [ArkUI_ShadowStyle](capi-native-type-visual-h.md#arkui_shadowstyle) shadow | Shadow style of the background, specified by an enumerated value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetCustomShadow()

```c
int32_t OH_ArkUI_CustomDialog_SetCustomShadow(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* customShadow)
```

**Description**

Sets the shadow of the dialog box background.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| [const ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)* customShadow | Custom shadow parameters. The format is consistent with the **NODE_CUSTOM_SHADOW** property in [ArkUI_NodeAttributeType](./capi-native-node-h.md#arkui_nodeattributetype).|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetBackgroundBlurStyle()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyle(ArkUI_CustomDialogOptions* options, ArkUI_BlurStyle blurStyle)
```

**Description**

Sets the background blur style of the dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| [ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle) blurStyle | Background blur style, specified by an enumerated value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetAlignment()

```c
int32_t OH_ArkUI_CustomDialog_SetAlignment(ArkUI_CustomDialogOptions* options, int32_t alignment, float offsetX, float offsetY)
```

**Description**

Sets the alignment mode of a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| int32_t alignment | Alignment mode of the dialog box. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).|
| float offsetX | Horizontal offset of the dialog box. The value is a floating point number, in vp.|
| float offsetY | Vertical offset of the dialog box. The value is a floating point number, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetModalMode()

```c
int32_t OH_ArkUI_CustomDialog_SetModalMode(ArkUI_CustomDialogOptions* options, bool isModal)
```

**Description**

Sets whether to enable the modal mode for a custom dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| bool isModal | Whether to enable the modal window mode. The modal window mode has a mask, and the non-modal window mode has no mask. The value **true** indicates to enable the modal window mode, and **false** indicates the opposite.<br/>Default value: **false**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetAutoCancel()

```c
int32_t OH_ArkUI_CustomDialog_SetAutoCancel(ArkUI_CustomDialogOptions* options, bool autoCancel)
```

**Description**

Sets whether to allow users to touch the mask to dismiss the custom dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| bool autoCancel | Whether to allow users to touch the mask to dismiss the dialog box. The value **true** means to allow users to do so, and false means the opposite.<br/>Default value: **true**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetSubwindowMode()

```c
int32_t OH_ArkUI_CustomDialog_SetSubwindowMode(ArkUI_CustomDialogOptions* options, bool showInSubwindow)
```

**Description**

Sets whether to display the dialog box in a subwindow.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.
>
> When used together with [OH_ArkUI_CustomDialog_SetDisplayModeInSubWindow](#oh_arkui_customdialog_setdisplaymodeinsubwindow), this API can further set the display mode of the dialog box in the subwindow.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| bool showInSubwindow | Whether to display the dialog box in a subwindow. The value **true** means the dialog box can be displayed outside the main window and in an independent subwindow. The value **false** means the dialog box is displayed within the application, not in an independent subwindow.<br/>Default value: **false**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterial()

```c
int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterial(ArkUI_NativeDialogHandle handle, ArkUI_ImmersiveMaterialHandle material)
```

**Description**

Sets the immersive material for a specified dialog box. Immersive materials are classified into different levels based on device computing power. A material level is defined by [ArkUI_MaterialLevel](./capi-native-material-h.md#arkui_materiallevel) and can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](./capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel). For devices with high- and medium-level computing power, the filter, shadow, ([OH_ArkUI_CustomDialog_SetShadow](./capi-native-dialog-h.md#oh_arkui_customdialog_setshadow) or [OH_ArkUI_CustomDialog_SetCustomShadow](./capi-native-dialog-h.md#oh_arkui_customdialog_setcustomshadow)), background blur ([OH_ArkUI_CustomDialog_SetBackgroundBlurStyle](./capi-native-dialog-h.md#oh_arkui_customdialog_setbackgroundblurstyle)), and background effect ([OH_ArkUI_CustomDialog_SetBackgroundEffect](./capi-native-dialog-h.md#oh_arkui_customdialog_setbackgroundeffect)) of the material layer are affected. For devices with low-level computing power, the background color ([OH_ArkUI_CustomDialog_SetBackgroundColor](./capi-native-dialog-h.md#oh_arkui_customdialog_setbackgroundcolor)), background blur ([OH_ArkUI_CustomDialog_SetBackgroundBlurStyle](./capi-native-dialog-h.md#oh_arkui_customdialog_setbackgroundblurstyle)), background effect ([OH_ArkUI_CustomDialog_SetBackgroundEffect](./capi-native-dialog-h.md#oh_arkui_customdialog_setbackgroundeffect)), border color ([OH_ArkUI_CustomDialog_SetBorderColor](./capi-native-dialog-h.md#oh_arkui_customdialog_setbordercolor)), border width ([OH_ArkUI_CustomDialog_SetBorderWidth](./capi-native-dialog-h.md#oh_arkui_customdialog_setborderwidth)), and shadow ([OH_ArkUI_CustomDialog_SetShadow](./capi-native-dialog-h.md#oh_arkui_customdialog_setshadow) or [OH_ArkUI_CustomDialog_SetCustomShadow](./capi-native-dialog-h.md#oh_arkui_customdialog_setcustomshadow)) are affected. The interactive deformation and flowing light effects automatically take effect based on devices' computing power levels. The interactive deformation and flowing light effects take effect on devices with high-level computing power, the interactive deformation effect takes effect on devices with medium-level computing power, and neither of the two effects takes effect on devices with low-level computing power.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterialInOptions()

```c
int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterialInOptions(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMaterialHandle material)
```

**Description**

Sets the immersive material attributes for a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box parameter object.|
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetDisplayModeInSubWindow()

```c
int32_t OH_ArkUI_CustomDialog_SetDisplayModeInSubWindow(ArkUI_CustomDialogOptions* options, OH_ArkUI_DialogDisplayModeInSubWindow displayModeInSubWindow)
```

**Description**

Sets the display mode of the dialog box in the subwindow.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.
>
> This API takes effect only when the dialog box is set to be displayed in a subwindow by calling [OH_ArkUI_CustomDialog_SetSubwindowMode](#oh_arkui_customdialog_setsubwindowmode).

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| [OH_ArkUI_DialogDisplayModeInSubWindow](#oh_arkui_dialogdisplaymodeinsubwindow) displayModeInSubWindow | Display mode of the dialog box in the subwindow. The type is [OH_ArkUI_DialogDisplayModeInSubWindow](#oh_arkui_dialogdisplaymodeinsubwindow).<br/>Default value: **OH_ARKUI_DIALOG_DISPLAY_MODE_SCREEN_BASED**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetMask()

```c
int32_t OH_ArkUI_CustomDialog_SetMask(ArkUI_CustomDialogOptions* options, uint32_t maskColor, const ArkUI_Rect* maskRect)
```

**Description**

Sets the mask for a custom dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| uint32_t maskColor | Mask color of the dialog box, in 0xARGB format. |
| [const ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md)* maskRect | Pointer to the mask area. Events within the mask area are not passed through, while events outside the mask area are passed through. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetKeyboardAvoidMode()

```c
int32_t OH_ArkUI_CustomDialog_SetKeyboardAvoidMode(ArkUI_CustomDialogOptions* options, ArkUI_KeyboardAvoidMode keyboardAvoidMode)
```

**Description**

Sets the keyboard avoidance mode of a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| [ArkUI_KeyboardAvoidMode](capi-native-type-h.md#arkui_keyboardavoidmode) keyboardAvoidMode | Keyboard avoidance mode, specified by an enumerated value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetHoverModeEnabled()

```c
int32_t OH_ArkUI_CustomDialog_SetHoverModeEnabled(ArkUI_CustomDialogOptions* options, bool enabled)
```

**Description**

Sets whether to enable the hover mode for a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| bool enabled | Whether to enable the hover mode for the dialog box. The value **true** indicates to enable the hover mode, and **false** indicates the opposite. Default value: **false**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetHoverModeArea()

```c
int32_t OH_ArkUI_CustomDialog_SetHoverModeArea(ArkUI_CustomDialogOptions* options, ArkUI_HoverModeAreaType hoverModeAreaType)
```

**Description**

Sets the default display area of a dialog box in hover mode.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| [ArkUI_HoverModeAreaType](capi-native-type-h.md#arkui_hovermodeareatype) hoverModeAreaType | Display area in hover mode, specified by an enumerated value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(ArkUI_DialogDismissEvent* event))
```

**Description**

Registers a callback for the dismissal event of a custom dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box option.|
| void* userData | Pointer to user data.|
| void (\*callback)(ArkUI_DialogDismissEvent\* event) | Callback for the dismissal event of the custom dialog box.<br> - **event**: input parameter of the callback, which captures the reason for dismissal.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the specified custom dialog box is about to appear.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| void* userData | Pointer to the user-defined data.|
| void (\*callback)(void\* userData) | Pointer to the callback invoked when the dialog box is about to appear. The input parameter **userData** indicates the user-defined data. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the specified custom dialog box appears.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| void* userData | Pointer to the user-defined data.|
| void (\*callback)(void\* userData) | Pointer to the callback invoked when the dialog box appears. The input parameter **userData** indicates the user-defined data. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the specified custom dialog box is about to disappear.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| void* userData | Pointer to the user-defined data.|
| void (\*callback)(void\* userData) | Pointer to the callback invoked when the dialog box is about to disappear. The input parameter **userData** indicates the user-defined data. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the specified custom dialog box disappears.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| void* userData | Pointer to the user-defined data.|
| void (\*callback)(void\* userData) | Pointer to the callback invoked when the dialog box disappears. The input parameter **userData** indicates the user-defined data. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t  | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_GetState()

```c
int32_t OH_ArkUI_CustomDialog_GetState(ArkUI_NativeDialogHandle handle, ArkUI_DialogState* state)
```

**Description**

Obtains the state of a dialog box.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
| [ArkUI_DialogState](#arkui_dialogstate)* state | Pointer to the state of the custom dialog box, used to receive the returned state value. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundBlurStyleOptions)
```

**Description**

Sets the background blur effect for a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| [const ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)* backgroundBlurStyleOptions | Pointer to the background blur effect for the dialog box. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter is as follows:<br>        .value[0].i32: color mode, specified by an enumerated value of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).<br>        .value[1]?.i32: adaptive color mode, specified by an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).<br>        .value[2]?.f32: blur degree. The value range is [0.0, 1.0]. If the value is out of the valid range, **0.0** is used when it is less than 0.0, and **1.0** is used when it is greater than 1.0.<br>        .value[3]?.u32: brightness of black in the grayscale blur. The value range is [0, 127]. If the value is out of the valid range, **0** is used.<br>        .value[4]?.u32: darkening degree of white in the grayscale blur. The value range is [0, 127]. If the value is out of the valid range, **0** is used.<br>        .value[5]?.i32: blur activation policy, specified by an enumerated value of [ArkUI_BlurStyleActivePolicy](capi-native-type-visual-h.md#arkui_blurstyleactivepolicy).<br>        .value[6]?.u32: background color, in 0xARGB format, of the components within the window after the window loses focus (in which case, the blur effect on the components within the window is removed). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_CustomDialog_SetBackgroundEffect()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundEffect(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundEffect)
```

**Description**

Sets the background effect parameters for a dialog box.

> **NOTE**
>
> This API must be called before the [OH_ArkUI_CustomDialog_OpenDialog](#oh_arkui_customdialog_opendialog) API is invoked.

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Pointer to the dialog box configuration.|
| [const ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)* backgroundEffect | Pointer to the background effect of the dialog box. The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter is as follows:<br>        .value[0].f32: blur radius, in vp.<br>        .value[1]?.f32: saturation.<br>        .value[2]?.f32: brightness.<br>        .value[3]?.u32: color, in 0xARGB format.<br>        .value[4]?.i32: adaptive color mode, specified by an enumerated value of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).<br>        .value[5]?.u32: brightness of black in the grayscale blur. The value range is [0, 127]. If the value is out of the valid range, **0** is used.<br>        .value[6]?.u32: darkening degree of white in the grayscale blur. The value range is [0, 127]. If the value is out of the valid range, **0** is used.<br>        .value[7]?.i32: blur activation policy, specified by an enumerated value of [ArkUI_BlurStyleActivePolicy](capi-native-type-visual-h.md#arkui_blurstyleactivepolicy).<br>        .value[8]?.u32: background color, in 0xARGB format, of the components within the window after the window loses focus (in which case, the blur effect on the components within the window is removed). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|