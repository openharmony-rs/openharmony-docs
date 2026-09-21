# ArkUI_NativeDialogAPI_3

```c
typedef struct ArkUI_NativeDialogAPI_3 {...} ArkUI_NativeDialogAPI_3
```

## Overview

Provides the custom dialog box APIs for the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ArkUI_NativeDialogAPI_1](capi-arkui-nativemodule-arkui-nativedialogapi-1.md) nativeDialogAPI1 | Provides the custom dialog box APIs for the native side. The API scope is {@link ArkUI_NativeDialogAPI_1}<br>**Since**: 19 |
| [ArkUI_NativeDialogAPI_2](capi-arkui-nativemodule-arkui-nativedialogapi-2.md) nativeDialogAPI2 | Provides the custom dialog box APIs for the native side. The API scope is {@link ArkUI_NativeDialogAPI_2}<br>**Since**: 19 |


### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*setLevelOrder)(ArkUI_NativeDialogHandle handle, double levelOrder)](#setlevelorder) | Sets the display order for a custom dialog box. |
| [int32_t (\*registerOnWillAppear)(ArkUI_NativeDialogHandle handle, void* userData, void (\*callback)(void* userData))](#registeronwillappear) | Registers a listener callback before the dialog openAnimation starts. |
| [int32_t (\*registerOnDidAppear)(ArkUI_NativeDialogHandle handle, void* userData, void (\*callback)(void* userData))](#registerondidappear) | Registers a listener callback when the dialog appears. |
| [int32_t (\*registerOnWillDisappear)(ArkUI_NativeDialogHandle handle, void* userData, void (\*callback)(void* userData))](#registeronwilldisappear) | Registers a listener callback before the dialog closeAnimation starts. |
| [int32_t (\*registerOnDidDisappear)(ArkUI_NativeDialogHandle handle, void* userData, void (\*callback)(void* userData))](#registerondiddisappear) | Registers a listener callback when the dialog disappears. |
| [int32_t (\*setBorderWidth)(ArkUI_NativeDialogHandle handle, float top, float right, float bottom, float left, ArkUI_LengthMetricUnit unit)](#setborderwidth) | Sets the border width of the dialog box. |
| [int32_t (\*setBorderColor)(ArkUI_NativeDialogHandle handle, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left)](#setbordercolor) | Sets the border color of the dialog box. |
| [int32_t (\*setBorderStyle)(ArkUI_NativeDialogHandle handle, int32_t top, int32_t right, int32_t bottom, int32_t left)](#setborderstyle) | Sets the border style of the dialog box. |
| [int32_t (\*setWidth)(ArkUI_NativeDialogHandle handle, float width, ArkUI_LengthMetricUnit unit)](#setwidth) | Sets the width of the dialog box background. |
| [int32_t (\*setHeight)(ArkUI_NativeDialogHandle handle, float height, ArkUI_LengthMetricUnit unit)](#setheight) | Sets the height of the dialog box background. |
| [int32_t (\*setShadow)(ArkUI_NativeDialogHandle handle, ArkUI_ShadowStyle shadow)](#setshadow) | Sets the shadow of the dialog box background. |
| [int32_t (\*setCustomShadow)(ArkUI_NativeDialogHandle handle, const ArkUI_AttributeItem* customShadow)](#setcustomshadow) | Sets the custom shadow of the dialog box background. |
| [int32_t (\*setBackgroundBlurStyle)(ArkUI_NativeDialogHandle handle, ArkUI_BlurStyle blurStyle)](#setbackgroundblurstyle) | Sets the background blur style of the dialog box. |
| [int32_t (\*setKeyboardAvoidMode)(ArkUI_NativeDialogHandle handle, ArkUI_KeyboardAvoidMode keyboardAvoidMode)](#setkeyboardavoidmode) | Sets the keyboard avoidance mode of the dialog box. |
| [int32_t (\*enableHoverMode)(ArkUI_NativeDialogHandle handle, bool enableHoverMode)](#enablehovermode) | Sets whether to enable the hover mode for the dialog box. |
| [int32_t (\*setHoverModeArea)(ArkUI_NativeDialogHandle handle, ArkUI_HoverModeAreaType hoverModeAreaType)](#sethovermodearea) | Set the default display area of the dialog box in hover mode. |
| [int32_t (\*setFocusable)(ArkUI_NativeDialogHandle handle, bool focusable)](#setfocusable) | Sets whether to get focus when the custom dialog is displayed. |
| [int32_t (\*setBackgroundBlurStyleOptions)(ArkUI_NativeDialogHandle handle, const ArkUI_AttributeItem* backgroundBlurStyleOptions)](#setbackgroundblurstyleoptions) | Sets the background blur effect for a custom dialog box. |
| [int32_t (\*setBackgroundEffect)(ArkUI_NativeDialogHandle handle, const ArkUI_AttributeItem* backgroundEffect)](#setbackgroundeffect) | Sets the background effect parameters for a custom dialog box. |

## Member function description

### setLevelOrder()

```c
int32_t (*setLevelOrder)(ArkUI_NativeDialogHandle handle, double levelOrder)
```

**Description**

Sets the display order for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  double levelOrder | Indicates the display order. The valid range is [-100000.0, 100000.0]. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### registerOnWillAppear()

```c
int32_t (*registerOnWillAppear)(ArkUI_NativeDialogHandle handle, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a listener callback before the dialog openAnimation starts.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| handle | Indicates the pointer to the custom dialog box controller. |
| void* userData | Indicates the pointer to the custom data. |
| callback | Indicates the callback before the dialog openAnimation starts. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### registerOnDidAppear()

```c
int32_t (*registerOnDidAppear)(ArkUI_NativeDialogHandle handle, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a listener callback when the dialog appears.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| handle | Indicates the pointer to the custom dialog box controller. |
| void* userData | Indicates the pointer to the custom data. |
| callback | Indicates the callback when the dialog appears. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### registerOnWillDisappear()

```c
int32_t (*registerOnWillDisappear)(ArkUI_NativeDialogHandle handle, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a listener callback before the dialog closeAnimation starts.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| handle | Indicates the pointer to the custom dialog box controller. |
| void* userData | Indicates the pointer to the custom data. |
| callback | Indicates the callback before the dialog closeAnimation starts. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### registerOnDidDisappear()

```c
int32_t (*registerOnDidDisappear)(ArkUI_NativeDialogHandle handle, void* userData, void (*callback)(void* userData))
```

**Description**

Registers a listener callback when the dialog disappears.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| handle | Indicates the pointer to the custom dialog box controller. |
| void* userData | Indicates the pointer to the custom data. |
| callback | Indicates the callback when the dialog disappears. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setBorderWidth()

```c
int32_t (*setBorderWidth)(ArkUI_NativeDialogHandle handle, float top, float right, float bottom, float left, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the border width of the dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  float top | Width of the top border. |
|  float right | Width of the right border. |
|  float bottom | Width of the bottom border. |
|  float left | Width of the left border. |
|  ArkUI_LengthMetricUnit unit | Unit of the width. The default value is vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setBorderColor()

```c
int32_t (*setBorderColor)(ArkUI_NativeDialogHandle handle, uint32_t top, uint32_t right, uint32_t bottom, uint32_t left)
```

**Description**

Sets the border color of the dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  uint32_t top | Color of the top border. |
|  uint32_t right | Color of the right border. |
|  uint32_t bottom | Color of the bottom border. |
|  uint32_t left | Color of the left border. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setBorderStyle()

```c
int32_t (*setBorderStyle)(ArkUI_NativeDialogHandle handle, int32_t top, int32_t right, int32_t bottom, int32_t left)
```

**Description**

Sets the border style of the dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  int32_t top | Style of the top border. |
|  int32_t right | Style of the right border. |
|  int32_t bottom | Style of the bottom border. |
|  int32_t left | Style of the left border. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setWidth()

```c
int32_t (*setWidth)(ArkUI_NativeDialogHandle handle, float width, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the width of the dialog box background.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  float width | Width of the background. |
|  ArkUI_LengthMetricUnit unit | Unit of the width. The default value is vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setHeight()

```c
int32_t (*setHeight)(ArkUI_NativeDialogHandle handle, float height, ArkUI_LengthMetricUnit unit)
```

**Description**

Sets the height of the dialog box background.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  float height | Height of the background. |
|  ArkUI_LengthMetricUnit unit | Unit of the height. The default value is vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setShadow()

```c
int32_t (*setShadow)(ArkUI_NativeDialogHandle handle, ArkUI_ShadowStyle shadow)
```

**Description**

Sets the shadow of the dialog box background.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  ArkUI_ShadowStyle shadow | Shadow style of the background, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setCustomShadow()

```c
int32_t (*setCustomShadow)(ArkUI_NativeDialogHandle handle, const ArkUI_AttributeItem* customShadow)
```

**Description**

Sets the custom shadow of the dialog box background.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  const ArkUI_AttributeItem* customShadow | Custom shadow parameter. The format is the same as that of the <b>NODE_SHADOW</b> property. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setBackgroundBlurStyle()

```c
int32_t (*setBackgroundBlurStyle)(ArkUI_NativeDialogHandle handle, ArkUI_BlurStyle blurStyle)
```

**Description**

Sets the background blur style of the dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  ArkUI_BlurStyle blurStyle | Background blur style, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setKeyboardAvoidMode()

```c
int32_t (*setKeyboardAvoidMode)(ArkUI_NativeDialogHandle handle, ArkUI_KeyboardAvoidMode keyboardAvoidMode)
```

**Description**

Sets the keyboard avoidance mode of the dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  ArkUI_KeyboardAvoidMode keyboardAvoidMode | Keyboard avoidance mode, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### enableHoverMode()

```c
int32_t (*enableHoverMode)(ArkUI_NativeDialogHandle handle, bool enableHoverMode)
```

**Description**

Sets whether to enable the hover mode for the dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  bool enableHoverMode | Whether to enable the hover mode. The default value is <b>false</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur.. |

### setHoverModeArea()

```c
int32_t (*setHoverModeArea)(ArkUI_NativeDialogHandle handle, ArkUI_HoverModeAreaType hoverModeAreaType)
```

**Description**

Set the default display area of the dialog box in hover mode.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Pointer to the dialog box controller. |
|  ArkUI_HoverModeAreaType hoverModeAreaType | Display area in hover mode, specified by an enumerated value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occur. |

### setFocusable()

```c
int32_t (*setFocusable)(ArkUI_NativeDialogHandle handle, bool focusable)
```

**Description**

Sets whether to get focus when the custom dialog is displayed.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  bool focusable | Specifies whether to get focus when the custom dialog is displayed. The default value is true. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setBackgroundBlurStyleOptions()

```c
int32_t (*setBackgroundBlurStyleOptions)(ArkUI_NativeDialogHandle handle, const ArkUI_AttributeItem* backgroundBlurStyleOptions)
```

**Description**

Sets the background blur effect for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  const ArkUI_AttributeItem* backgroundBlurStyleOptions | Background blur effect options. Format of the {@link ArkUI_AttributeItem} parameter: <br>       .value[0].i32: color mode. The value is an enum of {@link ArkUI_ColorMode}. <br>       .value[1]?.i32: adaptive color mode. The value is an enum of {@link ArkUI_AdaptiveColor}. <br>       .value[2]?.f32: blur degree. The value range is [0.0, 1.0]. <br>       .value[3]?.u32: brightness of black in the grayscale blur. The value range is [0, 127]. <br>       .value[4]?.u32: degree of darkening the white color in the grayscale blur. The value range is [0, 127]. <br>       .value[5]?.i32: blur activation policy. The value is an enum of {@link ArkUI_BlurStyleActivePolicy}.  .value[6]?.u32: background color, in 0xARGB format, of the components within the window after the window loses focus (in which case, the blur effect on the components within the window is removed). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setBackgroundEffect()

```c
int32_t (*setBackgroundEffect)(ArkUI_NativeDialogHandle handle, const ArkUI_AttributeItem* backgroundEffect)
```

**Description**

Sets the background effect parameters for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  const ArkUI_AttributeItem* backgroundEffect | Background effect. Format of the {@link ArkUI_AttributeItem} parameter: <br>       .value[0].f32: blur radius, in vp. <br>       .value[1]?.f32: saturation. <br>       .value[2]?.f32: brightness. <br>       .value[3]?.u32: color, in 0xARGB format. <br>       .value[4]?.i32: adaptive color mode. The value is an enum of {@link ArkUI_AdaptiveColor}. <br>       .value[5]?.u32: brightness of black in the grayscale blur. The value range is [0, 127]. <br>       .value[6]?.u32: degree of darkening the white color in the grayscale blur. The value range is [0, 127]. <br>       .value[7]?.i32: blur activation policy. The value is an enum of {@link ArkUI_BlurStyleActivePolicy}.  .value[8]?.u32: background color, in 0xARGB format, of the components within the window after the window loses focus (in which case, the blur effect on the components within the window is removed). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |


