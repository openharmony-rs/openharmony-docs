# ArkUI_NativeDialogAPI_1

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8e22c68cdd7ecb0668db21c4312cda839c2cdaa0 translatedAt=2026-08-19T08:25:21.834Z pushedAt=2026-08-20T03:18:36.661Z -->

```c
typedef struct {...} ArkUI_NativeDialogAPI_1
```

## Overview

Provides a collection of native-side custom dialog box APIs provided by ArkUI.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle (\*create)()](#create) | Creates a custom dialog box and returns the pointer to the created dialog box.|
| [void (\*dispose)(ArkUI_NativeDialogHandle handle)](#dispose) | Destroys a custom dialog box.|
| [int32_t (\*setContent)(ArkUI_NativeDialogHandle handle, ArkUI_NodeHandle content)](#setcontent) | Sets the content for a custom dialog box.|
| [int32_t (\*removeContent)(ArkUI_NativeDialogHandle handle)](#removecontent) | Removes the content of a custom dialog box.|
| [int32_t (\*setContentAlignment)(ArkUI_NativeDialogHandle handle, int32_t alignment, float offsetX, float offsetY)](#setcontentalignment) | Sets the alignment mode of a custom dialog box.|
| [int32_t (\*resetContentAlignment)(ArkUI_NativeDialogHandle handle)](#resetcontentalignment) | Resets the alignment mode of a custom dialog box to its default settings.|
| [int32_t (\*setModalMode)(ArkUI_NativeDialogHandle handle, bool isModal)](#setmodalmode) | Sets whether to enable the modal mode for a custom dialog box. |
| [int32_t (\*setAutoCancel)(ArkUI_NativeDialogHandle handle, bool autoCancel)](#setautocancel) | Specifies whether to allow users to touch the mask to dismiss a custom dialog box.|
| [int32_t (\*setMask)(ArkUI_NativeDialogHandle handle, uint32_t maskColor, const ArkUI_Rect* maskRect)](#setmask) | Sets the mask for a custom dialog box.|
| [int32_t (\*setBackgroundColor)(ArkUI_NativeDialogHandle handle, uint32_t backgroundColor)](#setbackgroundcolor) | Sets the background color for a custom dialog box.|
| [int32_t (\*setCornerRadius)(ArkUI_NativeDialogHandle handle, float topLeft, float topRight,float bottomLeft, float bottomRight)](#setcornerradius) | Sets the background corner radius for a custom dialog box.|
| [int32_t (\*setGridColumnCount)(ArkUI_NativeDialogHandle handle, int32_t gridCount)](#setgridcolumncount) | Sets the number of grid columns occupied by a custom dialog box.|
| [int32_t (\*enableCustomStyle)(ArkUI_NativeDialogHandle handle, bool enableCustomStyle)](#enablecustomstyle) | Specifies whether to use a custom style for the custom dialog box.|
| [int32_t (\*enableCustomAnimation)(ArkUI_NativeDialogHandle handle, bool enableCustomAnimation)](#enablecustomanimation) | Specifies whether to use a custom animation for a custom dialog box.|
| [int32_t (\*registerOnWillDismiss)(ArkUI_NativeDialogHandle handle, ArkUI_OnWillDismissEvent eventHandler)](#registeronwilldismiss) | Registers a callback for a custom dialog box so that the user can decide whether to close the dialog box after they touch the back button or press the Esc key.|
| [int32_t (\*show)(ArkUI_NativeDialogHandle handle, bool showInSubWindow)](#show) | Shows a custom dialog box.|
| [int32_t (\*close)(ArkUI_NativeDialogHandle handle)](#close) | Closes a custom dialog box. If the dialog box has been closed, this API does not take effect. This API is executed asynchronously in the background. The dialog box node is removed from the tree only after the dismissal animation is complete. If you want to open the dialog box again after closing it, wait for 300 ms and then perform the operation again.|
| [int32_t (\*registerOnWillDismissWithUserData)(ArkUI_NativeDialogHandle handle, void* userData, void (\*callback)(ArkUI_DialogDismissEvent* event))](#registeronwilldismisswithuserdata) | Registers a callback for the dismissal event of a custom dialog box.|

## Member Function Description

### create()

```c
ArkUI_NativeDialogHandle (*create)()
```

**Description**

Creates a custom dialog box and returns the pointer to the created dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Returns**

| Type                          | Description|
|------------------------------| -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) | Pointer to the custom dialog box, or a null pointer if the creation fails.|

### dispose()

```c
void (*dispose)(ArkUI_NativeDialogHandle handle)
```

**Description**

Disposes of a custom dialog box. This API is used in pair with [create](#create) to release the dialog box resources created by **create**. After calling this API, the handle will be released and can no longer be used. To use the dialog box again, call [create](#create) to create a new one.

| Name                                                                               | Description|
|------------------------------------------------------------------------------------| -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|

### setContent()

```c
int32_t (*setContent)(ArkUI_NativeDialogHandle handle, ArkUI_NodeHandle content)
```

**Description**

Sets the content for a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name                                                                               | Description|
|------------------------------------------------------------------------------------| -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) content                                                       | Pointer to the root node of the custom dialog box content.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### removeContent()

```c
int32_t (*removeContent)(ArkUI_NativeDialogHandle handle)
```

**Description**

Removes the content of a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### setContentAlignment()

```c
int32_t (*setContentAlignment)(ArkUI_NativeDialogHandle handle, int32_t alignment, float offsetX, float offsetY)
```

**Description**

Sets the alignment mode of a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  int32_t alignment | Alignment mode. The parameter type is [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).|
|  float offsetX | Horizontal offset of the dialog box. The value is a floating point number, in vp.|
|  float offsetY | Vertical offset of the dialog box. The value is a floating point number, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### resetContentAlignment()

```c
int32_t (*resetContentAlignment)(ArkUI_NativeDialogHandle handle)
```

**Description**

Resets the alignment mode of a custom dialog box to its default settings. The default value is **ARKUI_ALIGNMENT_TOP_START**. For details, see [ArkUI_Alignment](capi-layout-h.md#arkui_alignment).

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### setModalMode()

```c
int32_t (*setModalMode)(ArkUI_NativeDialogHandle handle, bool isModal)
```

**Description**

Sets whether to enable the modal mode for a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  bool isModal | Whether to enable the modal mode. A modal window has a mask, while a non-modal window does not. The value **true** means to enable the modal mode, and **false** means the opposite. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### setAutoCancel()

```c
int32_t (*setAutoCancel)(ArkUI_NativeDialogHandle handle, bool autoCancel)
```

**Description**

Specifies whether to allow users to touch the mask to dismiss a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  bool autoCancel | Whether to allow dismissing the dialog box by tapping the mask. The value **true** means the dialog box can be dismissed by tapping the mask, and **false** means the opposite. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### setMask()

```c
int32_t (*setMask)(ArkUI_NativeDialogHandle handle, uint32_t maskColor, const ArkUI_Rect* maskRect)
```

**Description**

Sets the mask for a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name                                                                               | Description|
|------------------------------------------------------------------------------------| -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
| uint32_t maskColor                                                                 | Mask color, in 0xARGB format. |
| const [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md)* maskRect                                                     | Pointer to the mask area. Events outside the mask area are transparently transmitted, and events within the mask area are not. The parameter type is [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### setBackgroundColor()

```c
int32_t (*setBackgroundColor)(ArkUI_NativeDialogHandle handle, uint32_t backgroundColor)
```

**Description**

Sets the background color for a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  uint32_t backgroundColor | Background color of the dialog box, in 0xARGB format. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### setCornerRadius()

```c
int32_t (*setCornerRadius)(ArkUI_NativeDialogHandle handle, float topLeft, float topRight, float bottomLeft, float bottomRight)
```

**Description**

Sets the background corner radius for a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  float topLeft | Radius of the upper left corner of the background for the custom dialog box, in vp. Default value: 32 vp since API version 12; 24 vp in API version 11 and earlier versions.|
|  float topRight | Radius of the upper right corner of the background for the custom dialog box, in vp. Default value: 32 vp since API version 12; 24 vp in API version 11 and earlier versions.|
| float bottomLeft | Radius of the lower left corner of the background for the custom dialog box, in vp. Default value: 32 vp since API version 12; 24 vp in API version 11 and earlier versions. |
|  float bottomRight | Radius of the lower right corner of the background for the custom dialog box, in vp. Default value: 32 vp since API version 12; 24 vp in API version 11 and earlier versions.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### setGridColumnCount()

```c
int32_t (*setGridColumnCount)(ArkUI_NativeDialogHandle handle, int32_t gridCount)
```

**Description**

Sets the number of grid columns occupied by a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  int32_t gridCount | Number of grids. The default value is subject to the window size, and the maximum value is the [maximum number of columns supported by the system](../../ui/arkts-layout-development-grid-layout.md#columns).<br>The value is an integer greater than or equal to 0.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### enableCustomStyle()

```c
int32_t (*enableCustomStyle)(ArkUI_NativeDialogHandle handle, bool enableCustomStyle)
```

**Description**

Specifies whether to use a custom style for the custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  bool enableCustomStyle | Whether the dialog box container style can be customized.<br>Default value: **false**.<br>**true**: The dialog box container style can be customized. Its width adapts to its child nodes, with zero corner radius and a transparent background.<br>**false**: The dialog box container style cannot be customized. Its height adapts to its child nodes and its width is defined by the grid system. The corner radius is 24 vp. On PCs/2-in-1 devices, the container automatically avoids screen edges and window title bars. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### enableCustomAnimation()

```c
int32_t (*enableCustomAnimation)(ArkUI_NativeDialogHandle handle, bool enableCustomAnimation)
```

**Description**

Specifies whether to use a custom animation for a custom dialog box.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  bool enableCustomAnimation | Whether to use a custom animation for a custom dialog box. The value **true** means to use a custom animation and disable the system default animation, and **false** means to use the system default animation. Default value: **false**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### registerOnWillDismiss()

```c
int32_t (*registerOnWillDismiss)(ArkUI_NativeDialogHandle handle, ArkUI_OnWillDismissEvent eventHandler)
```

**Description**

Registers a callback for a custom dialog box so that the user can decide whether to close the dialog box after they touch the back button or press the Esc key.

> **NOTE**
>
> This API must be called before the [show](#show) API is invoked.

**Parameters**

| Name                                                                                      | Description|
|-------------------------------------------------------------------------------------------| -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle        | Pointer to the custom dialog box controller.|
| [ArkUI_OnWillDismissEvent](capi-native-dialog-h.md#arkui_onwilldismissevent) eventHandler | Callback for dialog box dismissal.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### show()

```c
int32_t (*show)(ArkUI_NativeDialogHandle handle, bool showInSubWindow)
```

**Description**

Shows a custom dialog box.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
|  bool showInSubWindow | Whether to show a dialog box in a sub-window. The value **true** means to show the dialog box in a sub-window, and **false** means to show it in the main window. Default value: **false**. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### close()

```c
int32_t (*close)(ArkUI_NativeDialogHandle handle)
```

**Description**

Closes a custom dialog box. This API is executed asynchronously in the background, and the dialog box node is removed from the tree only after the dismissal animation is complete. If the dialog box is already closed, calling this API will not execute the close operation again. To reopen the dialog box after closing, wait for 300 ms before doing so.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful. This only indicates that the close command is successfully delivered, but does not indicate that the dialog box is completely closed.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### registerOnWillDismissWithUserData()

```c
int32_t (*registerOnWillDismissWithUserData)(ArkUI_NativeDialogHandle handle, void* userData, void (*callback)(ArkUI_DialogDismissEvent* event))
```

**Description**

Registers a callback for the dismissal event of a custom dialog box. Difference from [registerOnWillDismiss](#registeronwilldismiss), this API uses **void* userData** and a callback function pointer (with **ArkUI_DialogDismissEvent** as the callback input parameter, and whether to block the dismissal can be set through **OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss**), suitable for scenarios where a custom data pointer needs to be carried. **registerOnWillDismiss** uses an event handler of the **ArkUI_OnWillDismissEvent** type and determines whether to block the dismissal through the callback return value.

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_NativeDialogHandle](capi-arkui-nativemodule-arkui-nativedialog8h.md) handle | Pointer to the custom dialog box controller.|
| void* userData | Pointer to user data.|
| void (*callback)(ArkUI_DialogDismissEvent* event) | Callback invoked when the custom dialog box is closed.<br> - **event**: input parameter of the callback, used to capture the reason for closure. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>             Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>             Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|