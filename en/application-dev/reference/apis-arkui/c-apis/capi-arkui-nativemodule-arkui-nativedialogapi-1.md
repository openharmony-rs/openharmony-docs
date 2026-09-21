# ArkUI_NativeDialogAPI_1

```c
typedef struct ArkUI_NativeDialogAPI_1 {...} ArkUI_NativeDialogAPI_1
```

## Overview

Provides the custom dialog box APIs for the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [ArkUI_NativeDialogHandle (\*create)()](#create) | Creates a custom dialog box and returns the pointer to the created dialog box. |
| [void (\*dispose)(ArkUI_NativeDialogHandle handle)](#dispose) | Destroys a custom dialog box. |
| [int32_t (\*setContent)(ArkUI_NativeDialogHandle handle, ArkUI_NodeHandle content)](#setcontent) | Attaches the content of a custom dialog box. |
| [int32_t (\*removeContent)(ArkUI_NativeDialogHandle handle)](#removecontent) | Detaches the content of a custom dialog box. |
| [int32_t (\*setContentAlignment)(ArkUI_NativeDialogHandle handle, int32_t alignment, float offsetX, float offsetY)](#setcontentalignment) | Sets the alignment mode for a custom dialog box. |
| [int32_t (\*resetContentAlignment)(ArkUI_NativeDialogHandle handle)](#resetcontentalignment) | Resets the alignment mode of a custom dialog box to its default settings. |
| [int32_t (\*setModalMode)(ArkUI_NativeDialogHandle handle, bool isModal)](#setmodalmode) | Sets the modal mode for a custom dialog box. |
| [int32_t (\*setAutoCancel)(ArkUI_NativeDialogHandle handle, bool autoCancel)](#setautocancel) | Specifies whether to allow users to touch the mask to dismiss the custom dialog box. |
| [int32_t (\*setMask)(ArkUI_NativeDialogHandle handle, uint32_t maskColor, const ArkUI_Rect* maskRect)](#setmask) | Sets the mask for a custom dialog box. |
| [int32_t (\*setBackgroundColor)(ArkUI_NativeDialogHandle handle, uint32_t backgroundColor)](#setbackgroundcolor) | Sets the background color for a custom dialog box. |
| [int32_t (\*setCornerRadius)(ArkUI_NativeDialogHandle handle, float topLeft, float topRight,float bottomLeft, float bottomRight)](#setcornerradius) | Sets the background corner radius for a custom dialog box. |
| [int32_t (\*setGridColumnCount)(ArkUI_NativeDialogHandle handle, int32_t gridCount)](#setgridcolumncount) | Sets the number of grid columns occupied by a custom dialog box. |
| [int32_t (\*enableCustomStyle)(ArkUI_NativeDialogHandle handle, bool enableCustomStyle)](#enablecustomstyle) | Specifies whether to use a custom style for the custom dialog box. |
| [int32_t (\*enableCustomAnimation)(ArkUI_NativeDialogHandle handle, bool enableCustomAnimation)](#enablecustomanimation) | Specifies whether to use a custom animation for a custom dialog box. |
| [int32_t (\*registerOnWillDismiss)(ArkUI_NativeDialogHandle handle, ArkUI_OnWillDismissEvent eventHandler)](#registeronwilldismiss) | Registers a callback for a custom dialog box so that the user can decide whether to close the dialog box after they touch the Back button or press the Esc key. |
| [int32_t (\*show)(ArkUI_NativeDialogHandle handle, bool showInSubWindow)](#show) | Shows a custom dialog box. |
| [int32_t (\*close)(ArkUI_NativeDialogHandle handle)](#close) | Closes a custom dialog box. If the dialog box has been closed, this API does not take effect. |
| [int32_t (\*registerOnWillDismissWithUserData)(ArkUI_NativeDialogHandle handle, void* userData, void (\*callback)(ArkUI_DialogDismissEvent* event))](#registeronwilldismisswithuserdata) | Registers a listener for the dismiss event of the custom dialog box. |

## Member function description

### create()

```c
ArkUI_NativeDialogHandle (*create)()
```

**Description**

Creates a custom dialog box and returns the pointer to the created dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_NativeDialogHandle | Returns the pointer to the created custom dialog box; returns a null pointer if the creation fails. |

### dispose()

```c
void (*dispose)(ArkUI_NativeDialogHandle handle)
```

**Description**

Destroys a custom dialog box.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |

### setContent()

```c
int32_t (*setContent)(ArkUI_NativeDialogHandle handle, ArkUI_NodeHandle content)
```

**Description**

Attaches the content of a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  ArkUI_NodeHandle content | Indicates the pointer to the root node of the custom dialog box content. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### removeContent()

```c
int32_t (*removeContent)(ArkUI_NativeDialogHandle handle)
```

**Description**

Detaches the content of a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setContentAlignment()

```c
int32_t (*setContentAlignment)(ArkUI_NativeDialogHandle handle, int32_t alignment, float offsetX, float offsetY)
```

**Description**

Sets the alignment mode for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  int32_t alignment | Indicates the alignment mode. The parameter type is {@link ArkUI_Alignment}. |
|  float offsetX | Indicates the horizontal offset of the custom dialog box. The value is a floating point number. |
|  float offsetY | Indicates the vertical offset of the custom dialog box. The value is a floating point number. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### resetContentAlignment()

```c
int32_t (*resetContentAlignment)(ArkUI_NativeDialogHandle handle)
```

**Description**

Resets the alignment mode of a custom dialog box to its default settings.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setModalMode()

```c
int32_t (*setModalMode)(ArkUI_NativeDialogHandle handle, bool isModal)
```

**Description**

Sets the modal mode for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  bool isModal | Specifies whether the custom dialog box is a modal, which has a mask applied. The value <b>true</b> means that the custom dialog box is a modal, and <b>false</b> means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setAutoCancel()

```c
int32_t (*setAutoCancel)(ArkUI_NativeDialogHandle handle, bool autoCancel)
```

**Description**

Specifies whether to allow users to touch the mask to dismiss the custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  bool autoCancel | Specifies whether to allow users to touch the mask to dismiss the dialog box. The value <b>true</b> means to allow users to do so, and <b>false</b> means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setMask()

```c
int32_t (*setMask)(ArkUI_NativeDialogHandle handle, uint32_t maskColor, const ArkUI_Rect* maskRect)
```

**Description**

Sets the mask for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  uint32_t maskColor | Indicates the mask color, in 0xARGB format. |
|  const ArkUI_Rect* maskRect | Indicates the pointer to the mask area. Events outside the mask area are transparently transmitted, and events within the mask area are not. The parameter type is {@link ArkUI_Rect}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setBackgroundColor()

```c
int32_t (*setBackgroundColor)(ArkUI_NativeDialogHandle handle, uint32_t backgroundColor)
```

**Description**

Sets the background color for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  uint32_t backgroundColor | Indicates the background color of the custom dialog box, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setCornerRadius()

```c
int32_t (*setCornerRadius)(ArkUI_NativeDialogHandle handle, float topLeft, float topRight,float bottomLeft, float bottomRight)
```

**Description**

Sets the background corner radius for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  float topLeft | Indicates the radius of the upper left corner of the custom dialog box background. |
|  float topRight | Indicates the radius of the upper right corner of the custom dialog box background. |
| float bottomLeft | Indicates the radius of the lower left corner of the custom dialog box background. |
|  float bottomRight | Indicates the radius of the lower right corner of the custom dialog box background. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setGridColumnCount()

```c
int32_t (*setGridColumnCount)(ArkUI_NativeDialogHandle handle, int32_t gridCount)
```

**Description**

Sets the number of grid columns occupied by a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  int32_t gridCount | Indicates the number of grid columns occupied by the dialog box. The default value is subject to the window size, and the maximum value is the maximum number of columns supported by the system. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### enableCustomStyle()

```c
int32_t (*enableCustomStyle)(ArkUI_NativeDialogHandle handle, bool enableCustomStyle)
```

**Description**

Specifies whether to use a custom style for the custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  bool enableCustomStyle | Specifies whether to use a custom style for the dialog box. <b>true</b>: The dialog box automatically adapts its width to the child components; the rounded corner is 0; the background color is transparent. <b>false</b>: The dialog box automatically adapts its width to the grid system and its height to the child components; the rounded corner is 24 vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### enableCustomAnimation()

```c
int32_t (*enableCustomAnimation)(ArkUI_NativeDialogHandle handle, bool enableCustomAnimation)
```

**Description**

Specifies whether to use a custom animation for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  bool enableCustomAnimation | Specifies whether to use a custom animation. The value <b>true</b> means to use a custom animation, and <b>false</b> means to use the default animation. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### registerOnWillDismiss()

```c
int32_t (*registerOnWillDismiss)(ArkUI_NativeDialogHandle handle, ArkUI_OnWillDismissEvent eventHandler)
```

**Description**

Registers a callback for a custom dialog box so that the user can decide whether to close the dialog box after they touch the Back button or press the Esc key.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  [ArkUI_OnWillDismissEvent](capi-native-dialog-h.md#arkui_onwilldismissevent) eventHandler | Indicates the callback to register. The parameter type is {@link ArkUI_OnWillDismissEvent}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### show()

```c
int32_t (*show)(ArkUI_NativeDialogHandle handle, bool showInSubWindow)
```

**Description**

Shows a custom dialog box.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  bool showInSubWindow | Specifies whether to show the dialog box in a sub-window. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### close()

```c
int32_t (*close)(ArkUI_NativeDialogHandle handle)
```

**Description**

Closes a custom dialog box. If the dialog box has been closed, this API does not take effect.

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### registerOnWillDismissWithUserData()

```c
int32_t (*registerOnWillDismissWithUserData)(ArkUI_NativeDialogHandle handle, void* userData, void (*callback)(ArkUI_DialogDismissEvent* event))
```

**Description**

Registers a listener for the dismiss event of the custom dialog box.

**Parameters**:

| Parameter | Description |
| -- | -- |
| handle | Indicates the pointer to the custom dialog box controller. |
| userData | Indicates the pointer to the custom data. |
| callback | Indicates the callback for the dismiss event of the custom dialog box. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |


