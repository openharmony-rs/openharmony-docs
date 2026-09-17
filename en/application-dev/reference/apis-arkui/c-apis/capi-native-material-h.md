# native_material.h

## Overview

Declares the immersive material types and APIs for ArkUI on the native side.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ImmersiveMaterial](capi-arkui-nativemodule-arkui-immersivematerial.md) | ArkUI_ImmersiveMaterial | Defines the immersive material object on the native side. Immersive materials have different performance levels based on the computing power of the device. The performance level is defined by [ArkUI_MaterialLevel](capi-native-material-h.md#arkui_materiallevel), which can be obtained by [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel). On high-end and mid-range computing power devices, they affect the filter effect of the material layer and shadow effect. On low-end computing power devices, it affects the background color, border color, border width, and shadow effect. |
| [ArkUI_ImmersiveMaterial*](capi-arkui-nativemodule-arkui-immersivematerial8h.md) | ArkUI_ImmersiveMaterialHandle | Defines the pointer to the immersive material object. |
| [ArkUI_LightEffectOptions](capi-arkui-nativemodule-arkui-lighteffectoptions.md) | ArkUI_LightEffectOptions | Defines the light effect options for immersive material. The object is created with a default white color. |
| [ArkUI_LightEffectOptions*](capi-arkui-nativemodule-arkui-lighteffectoptions8h.md) | ArkUI_LightEffectOptionsHandle | Defines the pointer to the light effect options. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ImmersiveStyle](#arkui_immersivestyle) | ArkUI_ImmersiveStyle | Enumerates the immersive material styles. Different styles correspond to different material parameters, which affect the thickness of the material. |
| [ArkUI_MaterialLevel](#arkui_materiallevel) | ArkUI_MaterialLevel | Enumerates the material levels, which indicate the computing power level of the device. Use [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device. |

### Macro

| Name | Description |
| -- | -- |
| ARKUI_NATIVE_MATERIAL_H | Declares the immersive material types and APIs for ArkUI on the native side.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

### Function

| Name | Description |
| -- | -- |
| [bool OH_ArkUI_NativeModule_GetSystemMaterialSupported()](#oh_arkui_nativemodule_getsystemmaterialsupported) | Check whether systemMaterial is supported on the current device. If it is true, the {@link NODE_SYSTEM_MATERIAL} attribute can be used; otherwise, setting the NODE_SYSTEM_MATERIAL attribute will be ineffective. It is defined by the device and cannot be modified. |
| [ArkUI_MaterialLevel OH_ArkUI_NativeModule_GetGlobalMaterialLevel()](#oh_arkui_nativemodule_getglobalmateriallevel) | Obtain the global material level, which is related to the computing power of the device. It is defined by the device and cannot be modified. |
| [ArkUI_ImmersiveMaterialHandle OH_ArkUI_NativeModule_ImmersiveMaterial_Create(ArkUI_ImmersiveStyle style)](#oh_arkui_nativemodule_immersivematerial_create) | Creates an immersive material object with the specified style. The level of the created material follows the global material level and can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel). |
| [void OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy(ArkUI_ImmersiveMaterialHandle material)](#oh_arkui_nativemodule_immersivematerial_destroy) | Destroys an immersive material object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle style)](#oh_arkui_nativemodule_immersivematerial_setstyle) | Sets the style. Only effective for exquisite and gentle materials. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle* style)](#oh_arkui_nativemodule_immersivematerial_getstyle) | Gets the style of an immersive material object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t color)](#oh_arkui_nativemodule_immersivematerial_setmaterialcolor) | Sets the material color of an immersive material object. This parameter is effective for all levels of materials. If not set, the default visual behavior varies by material level: for exquisite and gentle levels, the material color appears transparent; for smooth level, the default background color of that level is used. When set, the specified color takes effect on all levels. Calling [OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_getmaterialcolor) on an unset value will return {@link ARKUI_ERROR_CODE_PARAM_ERROR}. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)](#oh_arkui_nativemodule_immersivematerial_getmaterialcolor) | Gets the material color of an immersive material object. If the value is never set, the function will return {@link ARKUI_ERROR_CODE_PARAM_ERROR}. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool applyShadow)](#oh_arkui_nativemodule_immersivematerial_setapplyshadow) | Sets the apply shadow attribute of an immersive material object. This parameter is effective for all levels of materials. When this parameter is true, the shadow effect in the material takes effect, taking precedence over the shadow general property. When this parameter is false, the shadow general property takes effect, and the material has no shadow effect. If not set, the default value is true. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool* applyShadow)](#oh_arkui_nativemodule_immersivematerial_getapplyshadow) | Gets the apply shadow attribute of an immersive material object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive(ArkUI_ImmersiveMaterialHandle material, bool interactive)](#oh_arkui_nativemodule_immersivematerial_setinteractive) | Sets the interactive attribute of an immersive material object. This parameter is effective for all levels of materials. When this parameter is true, the material is interactive. When this parameter is false, the material is not interactive. If not set, it follows the behavior of the component. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive(ArkUI_ImmersiveMaterialHandle material, bool* interactive)](#oh_arkui_nativemodule_immersivematerial_getinteractive) | Gets the interactive attribute of an immersive material object. If the value is never set, the function will return {@link ARKUI_ERROR_CODE_PARAM_ERROR}. |
| [ArkUI_LightEffectOptionsHandle OH_ArkUI_NativeModule_LightEffectOptions_Create()](#oh_arkui_nativemodule_lighteffectoptions_create) | Creates a light effect options object with default white color. |
| [void OH_ArkUI_NativeModule_LightEffectOptions_Destroy(ArkUI_LightEffectOptionsHandle options)](#oh_arkui_nativemodule_lighteffectoptions_destroy) | Destroys a light effect options object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LightEffectOptions_SetColor(ArkUI_LightEffectOptionsHandle options, uint32_t color)](#oh_arkui_nativemodule_lighteffectoptions_setcolor) | Sets the color of the light effect. If not set, the default white color is white(0xffffffff). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect(ArkUI_ImmersiveMaterialHandle material, const ArkUI_LightEffectOptionsHandle options)](#oh_arkui_nativemodule_immersivematerial_setlighteffect) | Sets the light effect of an immersive material object. Passing NULL disables the light effect. Passing non-NULL enables it with the options. If not set, it follows the behavior of the component. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)](#oh_arkui_nativemodule_immersivematerial_getlighteffectcolor) | Gets the color of the light effect of an immersive material object. Only succeeds if [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setlighteffect) was called with non-NULL options. If never set or disabled (NULL passed), returns {@link ARKUI_ERROR_CODE_PARAM_ERROR}. |

### Variable

| Name | Description |
| -- | -- |
| ArkUI_LightEffectOptions* ArkUI_LightEffectOptionsHandle | Defines the pointer to the light effect options.<br>**Since**: 26.0.0 |

## Enum type description

### ArkUI_ImmersiveStyle

```c
enum ArkUI_ImmersiveStyle
```

**Description**

Enumerates the immersive material styles. Different styles correspond to different material parameters, which affect the thickness of the material.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| ARKUI_IMMERSIVE_STYLE_ULTRA_THIN = 0 |  |
| ARKUI_IMMERSIVE_STYLE_THIN |  |
| ARKUI_IMMERSIVE_STYLE_REGULAR |  |
| ARKUI_IMMERSIVE_STYLE_THICK |  |
| ARKUI_IMMERSIVE_STYLE_ULTRA_THICK |  |

### ArkUI_MaterialLevel

```c
enum ArkUI_MaterialLevel
```

**Description**

Enumerates the material levels, which indicate the computing power level of the device. Use [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| ARKUI_MATERIAL_LEVEL_EXQUISITE = 0 |  |
| ARKUI_MATERIAL_LEVEL_GENTLE |  |
| ARKUI_MATERIAL_LEVEL_SMOOTH |  |


## Function description

### OH_ArkUI_NativeModule_GetSystemMaterialSupported()

```c
bool OH_ArkUI_NativeModule_GetSystemMaterialSupported()
```

**Description**

Check whether systemMaterial is supported on the current device. If it is true, the {@link NODE_SYSTEM_MATERIAL} attribute can be used; otherwise, setting the NODE_SYSTEM_MATERIAL attribute will be ineffective. It is defined by the device and cannot be modified.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns whether systemMaterial is enabled on the device. |

### OH_ArkUI_NativeModule_GetGlobalMaterialLevel()

```c
ArkUI_MaterialLevel OH_ArkUI_NativeModule_GetGlobalMaterialLevel()
```

**Description**

Obtain the global material level, which is related to the computing power of the device. It is defined by the device and cannot be modified.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_MaterialLevel](capi-native-material-h.md#arkui_materiallevel) | Returns the material level of the device. The return type is [ArkUI_MaterialLevel](capi-native-material-h.md#arkui_materiallevel). |

### OH_ArkUI_NativeModule_ImmersiveMaterial_Create()

```c
ArkUI_ImmersiveMaterialHandle OH_ArkUI_NativeModule_ImmersiveMaterial_Create(ArkUI_ImmersiveStyle style)
```

**Description**

Creates an immersive material object with the specified style. The level of the created material follows the global material level and can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle) style | The material style. The parameter type is [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle). |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) | Returns the pointer to the created immersive material object.          If creation fails or the style is invalid, returns NULL. |

### OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy()

```c
void OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy(ArkUI_ImmersiveMaterialHandle material)
```

**Description**

Destroys an immersive material object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | Pointer to material object. The type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle style)
```

**Description**

Sets the style. Only effective for exquisite and gentle materials.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | Pointer to material object. The type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle) style | The material style. The type is [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle* style)
```

**Description**

Gets the style of an immersive material object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | Pointer to material object. The type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle)* style | Pointer to style. The type is [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t color)
```

**Description**

Sets the material color of an immersive material object. This parameter is effective for all levels of materials. If not set, the default visual behavior varies by material level: for exquisite and gentle levels, the material color appears transparent; for smooth level, the default background color of that level is used. When set, the specified color takes effect on all levels. Calling [OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_getmaterialcolor) on an unset value will return {@link ARKUI_ERROR_CODE_PARAM_ERROR}.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | The pointer to the immersive material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| uint32_t color | The material color in 0xAARRGGBB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)
```

**Description**

Gets the material color of an immersive material object. If the value is never set, the function will return {@link ARKUI_ERROR_CODE_PARAM_ERROR}.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | Pointer to material object. The type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| uint32_t* color | Pointer to color in 0xAARRGGBB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_ERROR} if the value is never set.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool applyShadow)
```

**Description**

Sets the apply shadow attribute of an immersive material object. This parameter is effective for all levels of materials. When this parameter is true, the shadow effect in the material takes effect, taking precedence over the shadow general property. When this parameter is false, the shadow general property takes effect, and the material has no shadow effect. If not set, the default value is true.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | Pointer to material object. The type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| bool applyShadow | Whether to add shadows of the material effect. Default value is true. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool* applyShadow)
```

**Description**

Gets the apply shadow attribute of an immersive material object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | The pointer to the immersive material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| bool* applyShadow | Pointer to the variable that receives whether to apply shadow. Default value is true. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive(ArkUI_ImmersiveMaterialHandle material, bool interactive)
```

**Description**

Sets the interactive attribute of an immersive material object. This parameter is effective for all levels of materials. When this parameter is true, the material is interactive. When this parameter is false, the material is not interactive. If not set, it follows the behavior of the component.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | The pointer to the immersive material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| bool interactive | Whether the material is interactive. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive(ArkUI_ImmersiveMaterialHandle material, bool* interactive)
```

**Description**

Gets the interactive attribute of an immersive material object. If the value is never set, the function will return {@link ARKUI_ERROR_CODE_PARAM_ERROR}.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | The pointer to the immersive material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| bool* interactive | Pointer to the variable that receives whether the material is interactive. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_ERROR} if the value is never set.</li>          </ul> |

### OH_ArkUI_NativeModule_LightEffectOptions_Create()

```c
ArkUI_LightEffectOptionsHandle OH_ArkUI_NativeModule_LightEffectOptions_Create()
```

**Description**

Creates a light effect options object with default white color.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_LightEffectOptionsHandle | Returns the pointer to the created object. |

### OH_ArkUI_NativeModule_LightEffectOptions_Destroy()

```c
void OH_ArkUI_NativeModule_LightEffectOptions_Destroy(ArkUI_LightEffectOptionsHandle options)
```

**Description**

Destroys a light effect options object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_LightEffectOptionsHandle options | The pointer to the options object. |

### OH_ArkUI_NativeModule_LightEffectOptions_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LightEffectOptions_SetColor(ArkUI_LightEffectOptionsHandle options, uint32_t color)
```

**Description**

Sets the color of the light effect. If not set, the default white color is white(0xffffffff).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_LightEffectOptionsHandle options | The pointer to the options object. The parameter type is {@link ArkUI_LightEffectOptionsHandle}. |
| uint32_t color | The light effect color in 0xAARRGGBB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect(ArkUI_ImmersiveMaterialHandle material, const ArkUI_LightEffectOptionsHandle options)
```

**Description**

Sets the light effect of an immersive material object. Passing NULL disables the light effect. Passing non-NULL enables it with the options. If not set, it follows the behavior of the component.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | The pointer to the immersive material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| const ArkUI_LightEffectOptionsHandle options | The light effect options. Pass NULL to disable. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)
```

**Description**

Gets the color of the light effect of an immersive material object. Only succeeds if [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setlighteffect) was called with non-NULL options. If never set or disabled (NULL passed), returns {@link ARKUI_ERROR_CODE_PARAM_ERROR}.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md) material | The pointer to the immersive material object. The parameter type is [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerial8h.md). |
| uint32_t* color | Pointer to the variable that receives the light effect color. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>          <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter exception occurs.</li><br>        <li>{@link ARKUI_ERROR_CODE_PARAM_ERROR} if lightEffect is never set or disabled.</li>          </ul> |


