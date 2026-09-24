# native_dialog.h

## Overview

Defines a set of custom dialog box APIs of ArkUI on the native side.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_NativeDialogAPI_1](capi-arkui-nativemodule-arkui-nativedialogapi-1.md) | ArkUI_NativeDialogAPI_1 | Provides the custom dialog box APIs for the native side. |
| [ArkUI_NativeDialogAPI_2](capi-arkui-nativemodule-arkui-nativedialogapi-2.md) | ArkUI_NativeDialogAPI_2 | Provides the custom dialog box APIs for the native side. |
| [ArkUI_NativeDialogAPI_3](capi-arkui-nativemodule-arkui-nativedialogapi-3.md) | ArkUI_NativeDialogAPI_3 | Provides the custom dialog box APIs for the native side. |
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md) | ArkUI_DialogDismissEvent | Defines a struct for a dialog box dismiss event. |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md) | ArkUI_CustomDialogOptions | Defines a struct for the content object of a custom dialog box. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_DismissReason](#arkui_dismissreason) | ArkUI_DismissReason | Enumerates the actions for triggering closure of the dialog box. |
| [ArkUI_DialogState](#arkui_dialogstate) | ArkUI_DialogState | Enumerates the state of dialog. |
| [ArkUI_LevelMode](#arkui_levelmode) | ArkUI_LevelMode | Enumerates the level mode. |
| [ArkUI_ImmersiveMode](#arkui_immersivemode) | ArkUI_ImmersiveMode | Enumerates the immersive mode. |
| [OH_ArkUI_DialogDisplayModeInSubWindow](#oh_arkui_dialogdisplaymodeinsubwindow) | OH_ArkUI_DialogDisplayModeInSubWindow | Enumerates the dialog display mode in subwindow. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef bool (\*ArkUI_OnWillDismissEvent)(int32_t reason)](#arkui_onwilldismissevent) | ArkUI_OnWillDismissEvent | Invoked when the dialog box is closed. |
| [void OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss(ArkUI_DialogDismissEvent* event, bool shouldBlockDismiss)](#oh_arkui_dialogdismissevent_setshouldblockdismiss) | - | Sets whether to block the system behavior of dismissing a dialog box. |
| [void* OH_ArkUI_DialogDismissEvent_GetUserData(ArkUI_DialogDismissEvent* event)](#oh_arkui_dialogdismissevent_getuserdata) | - | Obtains the pointer to user data in a dialog box dismiss event object. |
| [int32_t OH_ArkUI_DialogDismissEvent_GetDismissReason(ArkUI_DialogDismissEvent* event)](#oh_arkui_dialogdismissevent_getdismissreason) | - | Obtains the dismiss reason from a dialog box dismiss event object. |
| [int32_t OH_ArkUI_CustomDialog_OpenDialog(ArkUI_CustomDialogOptions* options, void (\*callback)(int32_t dialogId))](#oh_arkui_customdialog_opendialog) | - | Displays a custom dialog box. |
| [typedef void (\*ArkUI_OpenDialogCallback)(int32_t errorCode, int32_t dialogId, void* userData)](#arkui_opendialogcallback) | ArkUI_OpenDialogCallback | Callback function when the dialog is displayed. |
| [void OH_ArkUI_CustomDialog_OpenDialogWithCallback(ArkUI_CustomDialogOptions* options, void* userData, ArkUI_OpenDialogCallback callback)](#oh_arkui_customdialog_opendialogwithcallback) | - | Displays a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_UpdateDialog(ArkUI_CustomDialogOptions* options, void (\*callback)(int32_t dialogId))](#oh_arkui_customdialog_updatedialog) | - | Updates a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_CloseDialog(int32_t dialogId)](#oh_arkui_customdialog_closedialog) | - | Closes a custom dialog box. |
| [ArkUI_CustomDialogOptions* OH_ArkUI_CustomDialog_CreateOptions(ArkUI_NodeHandle content)](#oh_arkui_customdialog_createoptions) | - | Creates custom dialog box options. |
| [void OH_ArkUI_CustomDialog_DisposeOptions(ArkUI_CustomDialogOptions* options)](#oh_arkui_customdialog_disposeoptions) | - | Destroys the custom dialog box options. |
| [int32_t OH_ArkUI_CustomDialog_SetLevelMode(ArkUI_CustomDialogOptions* options, ArkUI_LevelMode levelMode)](#oh_arkui_customdialog_setlevelmode) | - | Sets the level mode for a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetLevelUniqueId(ArkUI_CustomDialogOptions* options, int32_t uniqueId)](#oh_arkui_customdialog_setleveluniqueid) | - | Sets the level uniqueId for a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetImmersiveMode(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMode immersiveMode)](#oh_arkui_customdialog_setimmersivemode) | - | Sets the immersive mode for a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundColor(ArkUI_CustomDialogOptions* options, uint32_t backgroundColor)](#oh_arkui_customdialog_setbackgroundcolor) | - | Sets the background color of the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetCornerRadius(ArkUI_CustomDialogOptions* options, float topLeft, float topRight, float bottomLeft, float bottomRight)](#oh_arkui_customdialog_setcornerradius) | - | Sets the corner radius for a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetBorderWidth(ArkUI_CustomDialogOptions* options, float top, float right, float bottom, float left, ArkUI_LengthMetricUnit unit)](#oh_arkui_customdialog_setborderwidth) | - | Sets the border width of the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetBorderColor(ArkUI_CustomDialogOptions* options, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left)](#oh_arkui_customdialog_setbordercolor) | - | Sets the border color of the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetBorderStyle(ArkUI_CustomDialogOptions* options, int32_t top, int32_t right, int32_t bottom, int32_t left)](#oh_arkui_customdialog_setborderstyle) | - | Sets the border style of the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetWidth(ArkUI_CustomDialogOptions* options, float width, ArkUI_LengthMetricUnit unit)](#oh_arkui_customdialog_setwidth) | - | Sets the width of the dialog box background. |
| [int32_t OH_ArkUI_CustomDialog_SetHeight(ArkUI_CustomDialogOptions* options, float height, ArkUI_LengthMetricUnit unit)](#oh_arkui_customdialog_setheight) | - | Sets the height of the dialog box background. |
| [int32_t OH_ArkUI_CustomDialog_SetShadow(ArkUI_CustomDialogOptions* options, ArkUI_ShadowStyle shadow)](#oh_arkui_customdialog_setshadow) | - | Sets the shadow of the dialog box background. |
| [int32_t OH_ArkUI_CustomDialog_SetCustomShadow(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* customShadow)](#oh_arkui_customdialog_setcustomshadow) | - | Sets the custom shadow of the dialog box background. |
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyle(ArkUI_CustomDialogOptions* options, ArkUI_BlurStyle blurStyle)](#oh_arkui_customdialog_setbackgroundblurstyle) | - | Sets the background blur style of the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetAlignment(ArkUI_CustomDialogOptions* options, int32_t alignment, float offsetX, float offsetY)](#oh_arkui_customdialog_setalignment) | - | Sets the alignment mode of the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetModalMode(ArkUI_CustomDialogOptions* options, bool isModal)](#oh_arkui_customdialog_setmodalmode) | - | Sets the modal mode for a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetAutoCancel(ArkUI_CustomDialogOptions* options, bool autoCancel)](#oh_arkui_customdialog_setautocancel) | - | Specifies whether to allow users to touch the mask to dismiss the custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetSubwindowMode(ArkUI_CustomDialogOptions* options, bool showInSubwindow)](#oh_arkui_customdialog_setsubwindowmode) | - | Sets whether to display the dialog box in a subwindow. |
| [int32_t OH_ArkUI_CustomDialog_SetDisplayModeInSubWindow(ArkUI_CustomDialogOptions* options, OH_ArkUI_DialogDisplayModeInSubWindow displayModeInSubWindow)](#oh_arkui_customdialog_setdisplaymodeinsubwindow) | - | Sets the display mode of the custom dialog box in a subwindow. |
| [int32_t OH_ArkUI_CustomDialog_SetMask(ArkUI_CustomDialogOptions* options, uint32_t maskColor, const ArkUI_Rect* maskRect)](#oh_arkui_customdialog_setmask) | - | Sets the mask for a custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetKeyboardAvoidMode(ArkUI_CustomDialogOptions* options, ArkUI_KeyboardAvoidMode keyboardAvoidMode)](#oh_arkui_customdialog_setkeyboardavoidmode) | - | Sets the keyboard avoidance mode of the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetHoverModeEnabled(ArkUI_CustomDialogOptions* options, bool enabled)](#oh_arkui_customdialog_sethovermodeenabled) | - | Sets whether to enable the hover mode for the dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetHoverModeArea(ArkUI_CustomDialogOptions* options, ArkUI_HoverModeAreaType hoverModeAreaType)](#oh_arkui_customdialog_sethovermodearea) | - | Set the default display area of the dialog box in hover mode. |
| [int32_t OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(ArkUI_DialogDismissEvent* event))](#oh_arkui_customdialog_registeronwilldismisscallback) | - | Registers a callback for the dismissal event of the custom dialog box. |
| [int32_t OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registeronwillappearcallback) | - | Registers a callback to be invoked when the custom dialog box is about to appear. |
| [int32_t OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registerondidappearcallback) | - | Registers a callback to be invoked when the custom dialog box appears. |
| [int32_t OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registeronwilldisappearcallback) | - | Registers a callback to be invoked when the custom dialog box is about to disappear. |
| [int32_t OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (\*callback)(void* userData))](#oh_arkui_customdialog_registerondiddisappearcallback) | - | Registers a callback to be invoked when the custom dialog box disappears. |
| [int32_t OH_ArkUI_CustomDialog_GetState(ArkUI_NativeDialogHandle handle, ArkUI_DialogState* state)](#oh_arkui_customdialog_getstate) | - | Get state of dialog. |
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundBlurStyleOptions)](#oh_arkui_customdialog_setbackgroundblurstyleoptions) | - | Sets the background blur effect for a dialog box. |
| [int32_t OH_ArkUI_CustomDialog_SetBackgroundEffect(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundEffect)](#oh_arkui_customdialog_setbackgroundeffect) | - | Sets the background effect parameters for a dialog box. |
| [int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterialInOptions(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMaterialHandle material)](#oh_arkui_nativemodule_customdialog_setsystemmaterialinoptions) | - | Sets the system material of the dialog box. |
| [int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterial(ArkUI_NativeDialogHandle handle, ArkUI_ImmersiveMaterialHandle material)](#oh_arkui_nativemodule_customdialog_setsystemmaterial) | - | Sets the system material of the dialog box. |

### Variable

| Name | Description |
| -- | -- |
| bool (*ArkUI_OnWillDismissEvent)(int32_t reason) | Invoked when the dialog box is closed.<br>**Since**: 12 |
| void (*ArkUI_OpenDialogCallback)(int32_t errorCode, int32_t dialogId, void* userData) | Callback function when the dialog is displayed.<br>**Since**: 26.0.1 |

## Enum type description

### ArkUI_DismissReason

```c
enum ArkUI_DismissReason
```

**Description**

Enumerates the actions for triggering closure of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| DIALOG_DISMISS_BACK_PRESS = 0 | Touching the system-defined Back button or pressing the Esc key. |
| DIALOG_DISMISS_TOUCH_OUTSIDE | Touching the mask. |
| DIALOG_DISMISS_CLOSE_BUTTON | Touching the Close button. |
| DIALOG_DISMISS_SLIDE_DOWN | Sliding down. |

### ArkUI_DialogState

```c
enum ArkUI_DialogState
```

**Description**

Enumerates the state of dialog.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

| Enum item | Description |
| -- | -- |
| DIALOG_UNINITIALIZED = 0 | Uninitialized.<br>**Since**: 20<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| DIALOG_INITIALIZED | Initialized.<br>**Since**: 20<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| DIALOG_APPEARING | Appearing.<br>**Since**: 20<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| DIALOG_APPEARED | Appeared.<br>**Since**: 20<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| DIALOG_DISAPPEARING | Disappearing.<br>**Since**: 20<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |
| DIALOG_DISAPPEARED | Disappeared.<br>**Since**: 20<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

### ArkUI_LevelMode

```c
enum ArkUI_LevelMode
```

**Description**

Enumerates the level mode.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_LEVEL_MODE_OVERLAY = 0 | overlay mode. |
| ARKUI_LEVEL_MODE_EMBEDDED | embedded mode. |

### ArkUI_ImmersiveMode

```c
enum ArkUI_ImmersiveMode
```

**Description**

Enumerates the immersive mode.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_IMMERSIVE_MODE_DEFAULT = 0 | Mask covering the parent node area. |
| ARKUI_IMMERSIVE_MODE_EXTEND | Mask extend safe area includes status bar and navigation bar. |

### OH_ArkUI_DialogDisplayModeInSubWindow

```c
enum OH_ArkUI_DialogDisplayModeInSubWindow
```

**Description**

Enumerates the dialog display mode in subwindow.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARKUI_DIALOG_DISPLAY_MODE_SCREEN_BASED = 0 |  |
| OH_ARKUI_DIALOG_DISPLAY_MODE_WINDOW_BASED |  |


## Function description

### ArkUI_OnWillDismissEvent()

```c
typedef bool (*ArkUI_OnWillDismissEvent)(int32_t reason)
```

**Description**

Invoked when the dialog box is closed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

### OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss()

```c
void OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss(ArkUI_DialogDismissEvent* event, bool shouldBlockDismiss)
```

**Description**

Sets whether to block the system behavior of dismissing a dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md)* event | Indicates the pointer to a dialog box dismiss event object. |
| bool shouldBlockDismiss | Indicates whether to block the system behavior of dismissing the dialog box. The value <b>true</b> means to block the system behavior, and <b>false</b> means the opposite. |

### OH_ArkUI_DialogDismissEvent_GetUserData()

```c
void* OH_ArkUI_DialogDismissEvent_GetUserData(ArkUI_DialogDismissEvent* event)
```

**Description**

Obtains the pointer to user data in a dialog box dismiss event object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md)* event | Indicates the pointer to a dialog box dismiss event object. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Returns the pointer to user data. |

### OH_ArkUI_DialogDismissEvent_GetDismissReason()

```c
int32_t OH_ArkUI_DialogDismissEvent_GetDismissReason(ArkUI_DialogDismissEvent* event)
```

**Description**

Obtains the dismiss reason from a dialog box dismiss event object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_DialogDismissEvent](capi-arkui-nativemodule-arkui-dialogdismissevent.md)* event | Indicates the pointer to a dialog box dismiss event object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the dismissal reason. Returns <b>-1</b> if an exception occurs.          [DIALOG_DISMISS_BACK_PRESS](capi-native-dialog-h.md#arkui_dismissreason): touching the Back button, swiping left or right on the screen, or                                             pressing the Esc key.          [DIALOG_DISMISS_TOUCH_OUTSIDE](capi-native-dialog-h.md#arkui_dismissreason): touching the mask.          [DIALOG_DISMISS_CLOSE_BUTTON](capi-native-dialog-h.md#arkui_dismissreason): touching the Close button.          [DIALOG_DISMISS_SLIDE_DOWN](capi-native-dialog-h.md#arkui_dismissreason): sliding down. |

### OH_ArkUI_CustomDialog_OpenDialog()

```c
int32_t OH_ArkUI_CustomDialog_OpenDialog(ArkUI_CustomDialogOptions* options, void (*callback)(int32_t dialogId))
```

**Description**

Displays a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_CustomDialogOptions\* options | Dialog box parameters. |
| void (\*callback)(int32_t dialogId) | Callback to be invoked when the custom dialog box displays. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### ArkUI_OpenDialogCallback()

```c
typedef void (*ArkUI_OpenDialogCallback)(int32_t errorCode, int32_t dialogId, void* userData)
```

**Description**

Callback function when the dialog is displayed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t errorCode | the error code. [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) The operation is successful. [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) A parameter error occurs. [ARKUI_ERROR_CODE_DIALOG_NODE_MOUNT_FAILURE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) The dialog cannot be opened due to node mount failure. [ARKUI_ERROR_CODE_DIALOG_SUBWINDOW_CREATE_FAILURE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) The dialog cannot be opened due to subwindow create failure. |
| int32_t dialogId | Dialog id. Returns -1 when the dialog cannot be displayed. |
| void\* userData | Indicates the pointer to the custom data. |

### OH_ArkUI_CustomDialog_OpenDialogWithCallback()

```c
void OH_ArkUI_CustomDialog_OpenDialogWithCallback(ArkUI_CustomDialogOptions* options, void* userData, ArkUI_OpenDialogCallback callback)
```

**Description**

Displays a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| void* userData | Indicates the pointer to the custom data. |
| [ArkUI_OpenDialogCallback](capi-native-dialog-h.md#arkui_opendialogcallback) callback | Callback function when the dialog is displayed. |

### OH_ArkUI_CustomDialog_UpdateDialog()

```c
int32_t OH_ArkUI_CustomDialog_UpdateDialog(ArkUI_CustomDialogOptions* options, void (*callback)(int32_t dialogId))
```

**Description**

Updates a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_CustomDialogOptions\* options | Dialog box parameters. |
| void (\*callback)(int32_t dialogId) | Callback to be invoked when the custom dialog box updates. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_CloseDialog()

```c
int32_t OH_ArkUI_CustomDialog_CloseDialog(int32_t dialogId)
```

**Description**

Closes a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t dialogId | Dialog id. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_CreateOptions()

```c
ArkUI_CustomDialogOptions* OH_ArkUI_CustomDialog_CreateOptions(ArkUI_NodeHandle content)
```

**Description**

Creates custom dialog box options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NodeHandle content | Content of the custom dialog box. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions*](capi-arkui-nativemodule-arkui-customdialogoptions.md) | Returns the pointer to the custom dialog box options. |

### OH_ArkUI_CustomDialog_DisposeOptions()

```c
void OH_ArkUI_CustomDialog_DisposeOptions(ArkUI_CustomDialogOptions* options)
```

**Description**

Destroys the custom dialog box options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | The pointer to the custom dialog box options. |

### OH_ArkUI_CustomDialog_SetLevelMode()

```c
int32_t OH_ArkUI_CustomDialog_SetLevelMode(ArkUI_CustomDialogOptions* options, ArkUI_LevelMode levelMode)
```

**Description**

Sets the level mode for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>OH_ArkUI_CustomDialog_OpenDialog</b> method.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Indicates the pointer to the custom dialog options. |
| [ArkUI_LevelMode](capi-native-dialog-h.md#arkui_levelmode) levelMode | Indicates the level mode. The parameter type is [ArkUI_LevelMode](capi-native-dialog-h.md#arkui_levelmode). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetLevelUniqueId()

```c
int32_t OH_ArkUI_CustomDialog_SetLevelUniqueId(ArkUI_CustomDialogOptions* options, int32_t uniqueId)
```

**Description**

Sets the level uniqueId for a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Indicates the pointer to the custom dialog options. |
| int32_t uniqueId | Indicates the unique id of any nodes in router or navigation pages. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetImmersiveMode()

```c
int32_t OH_ArkUI_CustomDialog_SetImmersiveMode(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMode immersiveMode)
```

**Description**

Sets the immersive mode for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>OH_ArkUI_CustomDialog_OpenDialog</b> method.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Indicates the pointer to the custom dialog options. |
| [ArkUI_ImmersiveMode](capi-native-dialog-h.md#arkui_immersivemode) immersiveMode | Indicates the immersive mode. The parameter type is [ArkUI_ImmersiveMode](capi-native-dialog-h.md#arkui_immersivemode). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetBackgroundColor()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundColor(ArkUI_CustomDialogOptions* options, uint32_t backgroundColor)
```

**Description**

Sets the background color of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| uint32_t backgroundColor | Background color of the dialog box. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetCornerRadius()

```c
int32_t OH_ArkUI_CustomDialog_SetCornerRadius(ArkUI_CustomDialogOptions* options, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**Description**

Sets the corner radius for a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| float topLeft | Corner radius of the upper left corner. |
| float topRight | Corner radius of the upper right corner. |
| float bottomLeft | Corner radius of the lower left corner. |
| float bottomRight | Corner radius of the lower right corner. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetBorderWidth()

```c
int32_t OH_ArkUI_CustomDialog_SetBorderWidth(ArkUI_CustomDialogOptions* options, float top, float right, float bottom, float left, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the border width of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| float top | Width of the top border. |
| float right | Width of the right border. |
| float bottom | Width of the bottom border. |
| float left | Width of the left border. |
| ArkUI_LengthMetricUnit unit | Unit of the width. The default value is vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetBorderColor()

```c
int32_t OH_ArkUI_CustomDialog_SetBorderColor(ArkUI_CustomDialogOptions* options, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left)
```

**Description**

Sets the border color of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| uint32_t top | Color of the top border. |
| uint32_t right | Color of the right border. |
| uint32_t bottom | Color of the bottom border. |
| uint32_t left | Color of the left border. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetBorderStyle()

```c
int32_t OH_ArkUI_CustomDialog_SetBorderStyle(ArkUI_CustomDialogOptions* options, int32_t top, int32_t right, int32_t bottom, int32_t left)
```

**Description**

Sets the border style of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| int32_t top | Style of the top border. |
| int32_t right | Style of the right border. |
| int32_t bottom | Style of the bottom border. |
| int32_t left | Style of the left border. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetWidth()

```c
int32_t OH_ArkUI_CustomDialog_SetWidth(ArkUI_CustomDialogOptions* options, float width, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the width of the dialog box background.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| float width | Width of the background. |
| ArkUI_LengthMetricUnit unit | Unit of the width. The default value is vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetHeight()

```c
int32_t OH_ArkUI_CustomDialog_SetHeight(ArkUI_CustomDialogOptions* options, float height, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the height of the dialog box background.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| float height | Height of the background. |
| ArkUI_LengthMetricUnit unit | Unit of the height. The default value is vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetShadow()

```c
int32_t OH_ArkUI_CustomDialog_SetShadow(ArkUI_CustomDialogOptions* options, ArkUI_ShadowStyle shadow)
```

**Description**

Sets the shadow of the dialog box background.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| ArkUI_ShadowStyle shadow | Shadow style of the background, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetCustomShadow()

```c
int32_t OH_ArkUI_CustomDialog_SetCustomShadow(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* customShadow)
```

**Description**

Sets the custom shadow of the dialog box background.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| const ArkUI_AttributeItem* customShadow | Custom shadow parameter. The format is the same as that of the <b>NODE_CUSTOM_SHADOW</b> property. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetBackgroundBlurStyle()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyle(ArkUI_CustomDialogOptions* options, ArkUI_BlurStyle blurStyle)
```

**Description**

Sets the background blur style of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| ArkUI_BlurStyle blurStyle | Background blur style, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetAlignment()

```c
int32_t OH_ArkUI_CustomDialog_SetAlignment(ArkUI_CustomDialogOptions* options, int32_t alignment, float offsetX, float offsetY)
```

**Description**

Sets the alignment mode of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| int32_t alignment | Alignment mode of the dialog box. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment). |
| float offsetX | Indicates the horizontal offset of the custom dialog box. The value is a floating point number. |
| float offsetY | Indicates the vertical offset of the custom dialog box. The value is a floating point number. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetModalMode()

```c
int32_t OH_ArkUI_CustomDialog_SetModalMode(ArkUI_CustomDialogOptions* options, bool isModal)
```

**Description**

Sets the modal mode for a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| bool isModal | Whether the dialog box is a modal. A modal dialog box has a mask applied, while a non-modal dialog box does not. The value <b>true</b> means that the dialog box is a modal. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetAutoCancel()

```c
int32_t OH_ArkUI_CustomDialog_SetAutoCancel(ArkUI_CustomDialogOptions* options, bool autoCancel)
```

**Description**

Specifies whether to allow users to touch the mask to dismiss the custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| bool autoCancel | Specifies whether to allow users to touch the mask to dismiss the dialog box. The value <b>true</b> means to allow users to do so, and <b>false</b> means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetSubwindowMode()

```c
int32_t OH_ArkUI_CustomDialog_SetSubwindowMode(ArkUI_CustomDialogOptions* options, bool showInSubwindow)
```

**Description**

Sets whether to display the dialog box in a subwindow.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| bool showInSubwindow | Whether to display the dialog box in a subwindow when it is not in the main window. The default value is <b>false</b>, meaning the dialog box is displayed within the application, not in a separate subwindow. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetDisplayModeInSubWindow()

```c
int32_t OH_ArkUI_CustomDialog_SetDisplayModeInSubWindow(ArkUI_CustomDialogOptions* options, OH_ArkUI_DialogDisplayModeInSubWindow displayModeInSubWindow)
```

**Description**

Sets the display mode of the custom dialog box in a subwindow.

> **Note**:
>
> This method takes effect only when the dialog box is displayed in a subwindow.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| [OH_ArkUI_DialogDisplayModeInSubWindow](capi-native-dialog-h.md#oh_arkui_dialogdisplaymodeinsubwindow) displayModeInSubWindow | Display mode of the dialog box in the subwindow. The parameter type is [OH_ArkUI_DialogDisplayModeInSubWindow](capi-native-dialog-h.md#oh_arkui_dialogdisplaymodeinsubwindow). The default value is <b>OH_ARKUI_DIALOG_DISPLAY_MODE_SCREEN_BASED</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetMask()

```c
int32_t OH_ArkUI_CustomDialog_SetMask(ArkUI_CustomDialogOptions* options, uint32_t maskColor, const ArkUI_Rect* maskRect)
```

**Description**

Sets the mask for a custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| uint32_t maskColor | Mask color, in 0xargb format. |
| const ArkUI_Rect* maskRect | Pointer to the mask area. Events outside the mask area are transparently transmitted, and events within the mask area are not. The parameter type is [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetKeyboardAvoidMode()

```c
int32_t OH_ArkUI_CustomDialog_SetKeyboardAvoidMode(ArkUI_CustomDialogOptions* options, ArkUI_KeyboardAvoidMode keyboardAvoidMode)
```

**Description**

Sets the keyboard avoidance mode of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| ArkUI_KeyboardAvoidMode keyboardAvoidMode | Keyboard avoidance mode, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetHoverModeEnabled()

```c
int32_t OH_ArkUI_CustomDialog_SetHoverModeEnabled(ArkUI_CustomDialogOptions* options, bool enabled)
```

**Description**

Sets whether to enable the hover mode for the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| bool enabled | Whether to enable the hover mode. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetHoverModeArea()

```c
int32_t OH_ArkUI_CustomDialog_SetHoverModeArea(ArkUI_CustomDialogOptions* options, ArkUI_HoverModeAreaType hoverModeAreaType)
```

**Description**

Set the default display area of the dialog box in hover mode.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| ArkUI_HoverModeAreaType hoverModeAreaType | Display area in hover mode, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnWillDismissCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(ArkUI_DialogDismissEvent* event))
```

**Description**

Registers a callback for the dismissal event of the custom dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_CustomDialogOptions\* options | Dialog box parameters. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(ArkUI_DialogDismissEvent\* event) | Callback for the dismissal event of the custom dialog box. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnWillAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the custom dialog box is about to appear.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_CustomDialogOptions\* options | Dialog box parameters. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(void\* userData) | Callback to be invoked when the dialog box is about to appear. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnDidAppearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the custom dialog box appears.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_CustomDialogOptions\* options | Dialog box parameters. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(void\* userData) | Callback to be invoked when the custom dialog box appears. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnWillDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the custom dialog box is about to disappear.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_CustomDialogOptions\* options | Dialog box parameters. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(void\* userData) | Callback to be invoked when the dialog box is about to disappear. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback()

```c
int32_t OH_ArkUI_CustomDialog_RegisterOnDidDisappearCallback(ArkUI_CustomDialogOptions* options, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a callback to be invoked when the custom dialog box disappears.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_CustomDialogOptions\* options | Dialog box parameters. |
| void\* userData | Pointer to the user-defined data. |
| void (\*callback)(void\* userData) | Callback to be invoked when the custom dialog box disappears. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_GetState()

```c
int32_t OH_ArkUI_CustomDialog_GetState(ArkUI_NativeDialogHandle handle, ArkUI_DialogState* state)
```

**Description**

Get state of dialog.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
| [ArkUI_DialogState](capi-native-dialog-h.md#arkui_dialogstate)* state | Dialog state object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundBlurStyleOptions(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundBlurStyleOptions)
```

**Description**

Sets the background blur effect for a dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| const ArkUI_AttributeItem* backgroundBlurStyleOptions | Background blur effect options of the dialog box. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter:  .value[0].i32: color mode. The value is an enum of [ArkUI_ColorMode](capi-native-type-h.md#arkui_colormode).  .value[1]?.i32: adaptive color mode. The value is an enum of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).  .value[2]?.f32: blur degree. The value range is [0.0, 1.0].  .value[3]?.u32: brightness of black in the grayscale blur. The value range is [0, 127].  .value[4]?.u32: degree of darkening the white color in the grayscale blur. The value range is [0, 127].  .value[5]?.i32: blur activation policy. The value is an enum of [ArkUI_BlurStyleActivePolicy](capi-native-type-visual-h.md#arkui_blurstyleactivepolicy).  .value[6]?.u32: background color, in 0xARGB format, of the components within the window after the window loses focus (in which case, the blur effect on the components within the window is removed). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_CustomDialog_SetBackgroundEffect()

```c
int32_t OH_ArkUI_CustomDialog_SetBackgroundEffect(ArkUI_CustomDialogOptions* options, const ArkUI_AttributeItem* backgroundEffect)
```

**Description**

Sets the background effect parameters for a dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| const ArkUI_AttributeItem* backgroundEffect | Background effect of the dialog box. Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter:  .value[0].f32: blur radius, in vp.  .value[1]?.f32: saturation.  .value[2]?.f32: brightness.  .value[3]?.u32: color, in 0xARGB format.  .value[4]?.i32: adaptive color mode. The value is an enum of [ArkUI_AdaptiveColor](capi-native-type-h.md#arkui_adaptivecolor).  .value[5]?.u32: brightness of black in the grayscale blur. The value range is [0, 127].  .value[6]?.u32: degree of darkening the white color in the grayscale blur. The value range is [0, 127].  .value[7]?.i32: blur activation policy. The value is an enum of [ArkUI_BlurStyleActivePolicy](capi-native-type-visual-h.md#arkui_blurstyleactivepolicy).  .value[8]?.u32: background color, in 0xARGB format, of the components within the window after the window loses focus (in which case, the blur effect on the components within the window is removed). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.          Returns [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

### OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterialInOptions()

```c
int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterialInOptions(ArkUI_CustomDialogOptions* options, ArkUI_ImmersiveMaterialHandle material)
```

**Description**

Sets the system material of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomDialogOptions](capi-arkui-nativemodule-arkui-customdialogoptions.md)* options | Dialog box parameters. |
| ArkUI_ImmersiveMaterialHandle material | Pointer to material object. The type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterial()

```c
int32_t OH_ArkUI_NativeModule_CustomDialog_SetSystemMaterial(ArkUI_NativeDialogHandle handle, ArkUI_ImmersiveMaterialHandle material)
```

**Description**

Sets the system material of the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
| ArkUI_ImmersiveMaterialHandle material | Pointer to material object. The type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>           <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>           </ul> |


