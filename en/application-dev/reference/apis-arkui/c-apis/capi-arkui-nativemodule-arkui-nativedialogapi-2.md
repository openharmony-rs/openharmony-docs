# ArkUI_NativeDialogAPI_2

```c
typedef struct ArkUI_NativeDialogAPI_2 {...} ArkUI_NativeDialogAPI_2
```

## Overview

Provides the custom dialog box APIs for the native side.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_dialog.h](capi-native-dialog-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ArkUI_NativeDialogAPI_1](capi-arkui-nativemodule-arkui-nativedialogapi-1.md) nativeDialogAPI1 | Provides the custom dialog box APIs for the native side. The API scope is {@link ArkUI_NativeDialogAPI_1}<br>**Since**: 15 |


### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*setKeyboardAvoidDistance)(ArkUI_NativeDialogHandle handle, float distance, ArkUI_LengthMetricUnit unit)](#setkeyboardavoiddistance) | Defines the distance between the customDialog and system keyboard.<br>  |
| [int32_t (\*setLevelMode)(ArkUI_NativeDialogHandle handle, ArkUI_LevelMode levelMode)](#setlevelmode) | Sets the level mode for a custom dialog box. |
| [int32_t (\*setLevelUniqueId)(ArkUI_NativeDialogHandle handle, int32_t uniqueId)](#setleveluniqueid) | Sets the level uniqueId for a custom dialog box. |
| [int32_t (\*setImmersiveMode)(ArkUI_NativeDialogHandle handle, ArkUI_ImmersiveMode immersiveMode)](#setimmersivemode) | Sets the immersive mode for a custom dialog box. |

## Member function description

### setKeyboardAvoidDistance()

```c
int32_t (*setKeyboardAvoidDistance)(ArkUI_NativeDialogHandle handle, float distance, ArkUI_LengthMetricUnit unit)
```

**Description**

Defines the distance between the customDialog and system keyboard.<br> 

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  float distance | distance, in vp. |
|  ArkUI_LengthMetricUnit unit |  Indicates the unit, which is an enumerated value of {@link ArkUI_LengthMetricUnit} |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.              Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_CAPI_INIT_ERROR} if the CAPI init error.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setLevelMode()

```c
int32_t (*setLevelMode)(ArkUI_NativeDialogHandle handle, ArkUI_LevelMode levelMode)
```

**Description**

Sets the level mode for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  [ArkUI_LevelMode](capi-native-dialog-h.md#arkui_levelmode) levelMode | Indicates the level mode. The parameter type is {@link ArkUI_LevelMode}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setLevelUniqueId()

```c
int32_t (*setLevelUniqueId)(ArkUI_NativeDialogHandle handle, int32_t uniqueId)
```

**Description**

Sets the level uniqueId for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>setLevelMode</b> method.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  int32_t uniqueId | Indicates the uniqueId of any nodes in router or navigation pages. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |

### setImmersiveMode()

```c
int32_t (*setImmersiveMode)(ArkUI_NativeDialogHandle handle, ArkUI_ImmersiveMode immersiveMode)
```

**Description**

Sets the immersive mode for a custom dialog box.

> **Note**:
>
> This method must be called before the <b>show</b> method.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_NativeDialogHandle handle | Indicates the pointer to the custom dialog box controller. |
|  [ArkUI_ImmersiveMode](capi-native-dialog-h.md#arkui_immersivemode) immersiveMode | Indicates the immersive mode. The parameter type is {@link ArkUI_ImmersiveMode}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the error code.             Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |


