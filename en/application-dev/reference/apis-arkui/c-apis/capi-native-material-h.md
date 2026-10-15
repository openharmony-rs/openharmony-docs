# native_material.h

## Overview

Provides immersive material types and API declarations for ArkUI on the native side, to implement immersive UI effects such as the blurred background in semi-transparent mode and light sensing interaction feedback.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ImmersiveMaterial](capi-arkui-nativemodule-arkui-immersivematerial.md) | ArkUI_ImmersiveMaterial | Defines an immersive material object on the native side, which provides adaptive visual effects based on the device computing power level. |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) | ArkUI_ImmersiveMaterialHandle | Defines the pointer to an immersive material object, which is used to implement immersive visual effects. |
| [ArkUI_LightEffectOptions](capi-arkui-nativemodule-arkui-lighteffectoptions.md) | ArkUI_LightEffectOptions | Defines a light sensing interaction effect configuration object for immersive materials, which is used to configure the light sensing response effect generated when users interact with immersive materials. For details about the design logic, see [native_material.h](capi-native-material-h.md). An immersive material is a visual material style with a sense of depth and layering, and the light sensing interaction effect refers to the light and shadow visual feedback generated when users interact with components. After creation, the configuration object must be set to the immersive material object through [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setlighteffect) to take effect. |
| [ArkUI_LightEffectOptions*](capi-arkui-nativemodule-arkui-lighteffectoptions8h.md) | ArkUI_LightEffectOptionsHandle | Defines the pointer to the light effect options. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ImmersiveStyle](#arkui_immersivestyle) | ArkUI_ImmersiveStyle | Enumerates the immersive material styles. Different styles correspond to different material parameters, which affect the thickness of the material. |
| [ArkUI_MaterialLevel](#arkui_materiallevel) | ArkUI_MaterialLevel | Enumerates the material levels, which indicate the computing power level of the device. Use [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device. |

### Macro

| Name | Description |
| -- | -- |
| ARKUI_NATIVE_MATERIAL_H | Provides immersive material types and API declarations for ArkUI on the native side, to implement immersive UI effects such as the blurred background in semi-transparent mode and light sensing interaction feedback.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

### Function

| Name | Description |
| -- | -- |
| [bool OH_ArkUI_NativeModule_GetSystemMaterialSupported()](#oh_arkui_nativemodule_getsystemmaterialsupported) | Checks whether the current device supports system materials (that is, the built-in material rendering capability of the device system). |
| [ArkUI_MaterialLevel OH_ArkUI_NativeModule_GetGlobalMaterialLevel()](#oh_arkui_nativemodule_getglobalmateriallevel) | Obtains the global material level, which is related to the device computing power. This configuration item is defined by the device and cannot be modified. |
| [ArkUI_ImmersiveMaterialHandle OH_ArkUI_NativeModule_ImmersiveMaterial_Create(ArkUI_ImmersiveStyle style)](#oh_arkui_nativemodule_immersivematerial_create) | Creates an immersive material object with a specified style. The material level of the created object follows the global material level, which can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel). |
| [void OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy(ArkUI_ImmersiveMaterialHandle material)](#oh_arkui_nativemodule_immersivematerial_destroy) | Destroys the immersive material object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle style)](#oh_arkui_nativemodule_immersivematerial_setstyle) | Sets a style for an immersive material object. This attribute is valid only for display effects of devices with high- and mid-level computing power. It does not take effect for devices with low-level computing power, but no error is reported. You can call [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device to determine whether this attribute takes effect. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle* style)](#oh_arkui_nativemodule_immersivematerial_getstyle) | Obtains the style of an immersive material object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t color)](#oh_arkui_nativemodule_immersivematerial_setmaterialcolor) | Sets a material color for an immersive material object. This attribute is valid for the display effects on devices with all computing power levels. You can call [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device to determine whether this attribute takes effect. If this parameter is not set, the default value **0** is used, indicating the transparent color. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)](#oh_arkui_nativemodule_immersivematerial_getmaterialcolor) | Obtains the material color of an immersive material object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool applyShadow)](#oh_arkui_nativemodule_immersivematerial_setapplyshadow) | Sets whether to apply a shadow to an immersive material object. This parameter takes effect for materials of all levels. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool* applyShadow)](#oh_arkui_nativemodule_immersivematerial_getapplyshadow) | Obtains whether a shadow is applied to an immersive material object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive(ArkUI_ImmersiveMaterialHandle material, bool interactive)](#oh_arkui_nativemodule_immersivematerial_setinteractive) | Sets whether an immersive material object can be interactively deformed. That is, whether the material generates a visual deformation response during user interaction (such as touch and press). This parameter takes effect for materials of all levels. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive(ArkUI_ImmersiveMaterialHandle material, bool* interactive)](#oh_arkui_nativemodule_immersivematerial_getinteractive) | Obtains whether an immersive material object can be interactively deformed. You are advised to call [OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setinteractive) to set this attribute before calling this API. If this attribute has never been set, ARKUI_ERROR_CODE_PARAM_ERROR will be returned. |
| [ArkUI_LightEffectOptionsHandle OH_ArkUI_NativeModule_LightEffectOptions_Create()](#oh_arkui_nativemodule_lighteffectoptions_create) | Creates a light sensing interaction effect configuration object, which is used to configure the effect of highlighted feedback upon touch for an immersive material. The default color is white (0xffffffff). After the creation is complete, you need to call [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setlighteffect) to set the configuration object to the immersive material object for the configuration to take effect. |
| [void OH_ArkUI_NativeModule_LightEffectOptions_Destroy(ArkUI_LightEffectOptionsHandle options)](#oh_arkui_nativemodule_lighteffectoptions_destroy) | Destroys the light sensing interaction effect configuration object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LightEffectOptions_SetColor(ArkUI_LightEffectOptionsHandle options, uint32_t color)](#oh_arkui_nativemodule_lighteffectoptions_setcolor) | Sets a color for the light sensing interaction effect. If this parameter is not set, the default color is white (0xffffffff). |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect(ArkUI_ImmersiveMaterialHandle material, const ArkUI_LightEffectOptionsHandle options)](#oh_arkui_nativemodule_immersivematerial_setlighteffect) | Sets the light sensing interaction effect for an immersive material object, that is, the light reflection on the material surface that dynamically changes with user interaction. This parameter takes effect for materials of all levels. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)](#oh_arkui_nativemodule_immersivematerial_getlighteffectcolor) | Obtains the color of the light sensing interaction effect for an immersive material object. |

### Variable

| Name | Description |
| -- | -- |
| ArkUI_LightEffectOptions* ArkUI_LightEffectOptionsHandle | Defines the pointer to the light effect options.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.ArkUI.ArkUI.Full |

## Enum type description

### ArkUI_ImmersiveStyle

```c
enum ArkUI_ImmersiveStyle
```

**Description**

Enumerates the immersive material styles. Different styles correspond to different material parameters, which affect the thickness of the material.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Checks whether the current device supports system materials (that is, the built-in material rendering capability of the device system).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the current device supports system materials. The value **true** indicates that the current device supports system materials, and **false** indicates the opposite. |

### OH_ArkUI_NativeModule_GetGlobalMaterialLevel()

```c
ArkUI_MaterialLevel OH_ArkUI_NativeModule_GetGlobalMaterialLevel()
```

**Description**

Obtains the global material level, which is related to the device computing power. This configuration item is defined by the device and cannot be modified.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_MaterialLevel](capi-native-material-h.md#arkui_materiallevel) | Material level of the device. <ul> <li>[ARKUI_MATERIAL_LEVEL_EXQUISITE](capi-native-material-h.md#arkui_materiallevel) (0): material level for devices with high-level computing power.</li> <li>[ARKUI_MATERIAL_LEVEL_GENTLE](capi-native-material-h.md#arkui_materiallevel) (1): material level for devices with medium-level computing power.</li> <li>[ARKUI_MATERIAL_LEVEL_SMOOTH](capi-native-material-h.md#arkui_materiallevel) (2): material level for devices with low-level computing power.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_Create()

```c
ArkUI_ImmersiveMaterialHandle OH_ArkUI_NativeModule_ImmersiveMaterial_Create(ArkUI_ImmersiveStyle style)
```

**Description**

Creates an immersive material object with a specified style. The material level of the created object follows the global material level, which can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Resource release**: native_material/OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy {return}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle) style | Material style. Passing an invalid style will cause the setting failure, and the error code ARKUI_ERROR_CODE_PARAM_INVALID will be returned. This style is effective only for the display effect on devices with high- and mid-level computing power, and has no effect on devices with low-level computing power but no error will be reported. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) | Pointer to the created immersive material object. If the creation fails or the material style is invalid, null is returned. The returned object must be released by calling [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_destroy) after being used. |

### OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy()

```c
void OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy(ArkUI_ImmersiveMaterialHandle material)
```

**Description**

Destroys the immersive material object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle style)
```

**Description**

Sets a style for an immersive material object. This attribute is valid only for display effects of devices with high- and mid-level computing power. It does not take effect for devices with low-level computing power, but no error is reported. You can call [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device to determine whether this attribute takes effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. If **material** is **NULL**, the API returns the error code ARKUI_ERROR_CODE_PARAM_INVALID. |
| [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle) style | Material style. Passing an invalid style will cause the setting failure, and the error code ARKUI_ERROR_CODE_PARAM_INVALID will be returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle* style)
```

**Description**

Obtains the style of an immersive material object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |
| [ArkUI_ImmersiveStyle](capi-native-material-h.md#arkui_immersivestyle)* style | Pointer to the variable used to receive the material style. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t color)
```

**Description**

Sets a material color for an immersive material object. This attribute is valid for the display effects on devices with all computing power levels. You can call [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](capi-native-material-h.md#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device to determine whether this attribute takes effect. If this parameter is not set, the default value **0** is used, indicating the transparent color.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. If **material** is **NULL**, the API returns the error code ARKUI_ERROR_CODE_PARAM_INVALID. |
| uint32_t color | Material color, in 0xAARRGGBB format, which takes effect on the display effects of devices with all computing power levels. The value **0** indicates transparent (default value). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)
```

**Description**

Obtains the material color of an immersive material object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |
| uint32_t* color | Pointer to the variable used to receive the material color in 0xAARRGGBB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> <li>ARKUI_ERROR_CODE_PARAM_ERROR if the value is never set.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool applyShadow)
```

**Description**

Sets whether to apply a shadow to an immersive material object. This parameter takes effect for materials of all levels.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |
| bool applyShadow | Whether to apply a shadow to the material. The value **true** indicates that the material shadow takes effect and takes precedence over the common shadow attribute. The value **false** indicates that the material shadow is not added and the common shadow attribute takes effect. The default value is **true**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool* applyShadow)
```

**Description**

Obtains whether a shadow is applied to an immersive material object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |
| bool* applyShadow | Pointer to the variable used to receive whether the shadow is applied. If never explicitly set, this pointer receives the default value **true**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive(ArkUI_ImmersiveMaterialHandle material, bool interactive)
```

**Description**

Sets whether an immersive material object can be interactively deformed. That is, whether the material generates a visual deformation response during user interaction (such as touch and press). This parameter takes effect for materials of all levels.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |
| bool interactive | Whether interactive deformation can be performed for a material. The value **true** indicates that interactive deformation can be performed for a material, and **false** indicates the opposite. If this parameter is not set, the component behavior is followed. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive(ArkUI_ImmersiveMaterialHandle material, bool* interactive)
```

**Description**

Obtains whether an immersive material object can be interactively deformed. You are advised to call [OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setinteractive) to set this attribute before calling this API. If this attribute has never been set, ARKUI_ERROR_CODE_PARAM_ERROR will be returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. If **material** is **NULL**, the API returns the error code ARKUI_ERROR_CODE_PARAM_INVALID. |
| bool* interactive | Pointer to the variable used to receive whether the material supports interactive deformation. If **interactive** is **NULL**, the API returns the error code ARKUI_ERROR_CODE_PARAM_INVALID. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> <li>ARKUI_ERROR_CODE_PARAM_ERROR if the value is never set.</li> </ul> |

### OH_ArkUI_NativeModule_LightEffectOptions_Create()

```c
ArkUI_LightEffectOptionsHandle OH_ArkUI_NativeModule_LightEffectOptions_Create()
```

**Description**

Creates a light sensing interaction effect configuration object, which is used to configure the effect of highlighted feedback upon touch for an immersive material. The default color is white (0xffffffff). After the creation is complete, you need to call [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](capi-native-material-h.md#oh_arkui_nativemodule_immersivematerial_setlighteffect) to set the configuration object to the immersive material object for the configuration to take effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Resource release**: native_material/OH_ArkUI_NativeModule_LightEffectOptions_Destroy {return}

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_LightEffectOptionsHandle | Pointer to the created light sensing interaction effect configuration object. The returned object must be released by calling [OH_ArkUI_NativeModule_LightEffectOptions_Destroy](capi-native-material-h.md#oh_arkui_nativemodule_lighteffectoptions_destroy) after being used. |

### OH_ArkUI_NativeModule_LightEffectOptions_Destroy()

```c
void OH_ArkUI_NativeModule_LightEffectOptions_Destroy(ArkUI_LightEffectOptionsHandle options)
```

**Description**

Destroys the light sensing interaction effect configuration object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_LightEffectOptionsHandle options | Pointer to the light sensing interaction effect configuration object. |

### OH_ArkUI_NativeModule_LightEffectOptions_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LightEffectOptions_SetColor(ArkUI_LightEffectOptionsHandle options, uint32_t color)
```

**Description**

Sets a color for the light sensing interaction effect. If this parameter is not set, the default color is white (0xffffffff).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| ArkUI_LightEffectOptionsHandle options | Pointer to the light sensing interaction effect configuration object. |
| uint32_t color | Color of the light sensing interaction effect, in 0xAARRGGBB format. If this parameter is not set, the default color is white (0xffffffff). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect(ArkUI_ImmersiveMaterialHandle material, const ArkUI_LightEffectOptionsHandle options)
```

**Description**

Sets the light sensing interaction effect for an immersive material object, that is, the light reflection on the material surface that dynamically changes with user interaction. This parameter takes effect for materials of all levels.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |
| const ArkUI_LightEffectOptionsHandle options | Pointer to the light sensing interaction effect configuration object. A null pointer disables the light sensing interaction effect, and a non-null enables it. A non-null pointer must be created through [OH_ArkUI_NativeModule_LightEffectOptions_Create](capi-native-material-h.md#oh_arkui_nativemodule_lighteffectoptions_create). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> </ul> |

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)
```

**Description**

Obtains the color of the light sensing interaction effect for an immersive material object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object. |
| uint32_t* color | Pointer to the variable used to receive the light sensing interaction effect color in 0xAARRGGBB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> <li>ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.</li> <li>ARKUI_ERROR_CODE_PARAM_INVALID if a parameter exception occurs.</li> <li>ARKUI_ERROR_CODE_PARAM_ERROR if lightEffect is never set or disabled.</li> </ul> |


