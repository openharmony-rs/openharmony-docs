# native_material.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Provides immersive material types and API declarations for ArkUI on the native side.

**File to include**: <arkui/native_material.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Since**: 26.0.0

## Summary

### Enum

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ImmersiveStyle](#arkui_immersivestyle) | ArkUI_ImmersiveStyle | Enumerates immersive material styles. Different styles correspond to different material parameters, which affect material thickness.|
| [ArkUI_MaterialLevel](#arkui_materiallevel) | ArkUI_MaterialLevel | Enumerates material levels, which are related to device computing power levels. You can use [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device.|

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ImmersiveMaterial](./capi-arkui-nativemodule-arkui-immersivematerial.md) | ArkUI_ImmersiveMaterial | Defines an immersive material object on the native side. Immersive materials are classified into different levels based on device computing power. A material level is defined by [ArkUI_MaterialLevel](#arkui_materiallevel) and can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](#oh_arkui_nativemodule_getglobalmateriallevel). On devices with high- and mid-level computing power, the filter and shadow ([NODE_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_shadow) or [NODE_CUSTOM_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_custom_shadow)) of the material layer are affected. On devices with low computing power, the background color ([NODE_BACKGROUND_COLOR](./capi-native-node-h-nodeattributetype-common.md#node_background_color)), border color ([NODE_BORDER_COLOR](./capi-native-node-h-nodeattributetype-layoutattributes.md#node_border_color)), border width ([NODE_BORDER_WIDTH](./capi-native-node-h-nodeattributetype-layoutattributes.md#node_border_width)), and shadow ([NODE_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_shadow) or [NODE_CUSTOM_SHADOW](./capi-native-node-h-nodeattributetype-animator.md#node_custom_shadow)) are affected.|
| [ArkUI_ImmersiveMaterial*](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) | ArkUI_ImmersiveMaterialHandle | Defines the pointer to an immersive material object. [OH_ArkUI_NativeModule_ImmersiveMaterial_Create](#oh_arkui_nativemodule_immersivematerial_create) can be used to create an immersive material object. [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](#oh_arkui_nativemodule_immersivematerial_destroy) can be used to destroy the immersive material object.|
| [ArkUI_LightEffectOptions](./capi-arkui-nativemodule-arkui-lighteffectoptions.md) | ArkUI_LightEffectOptions | Defines a light sensing interaction effect configuration object for immersive materials. By default, the light sensing interaction color is white (0xffffffff) during creation.|
| [ArkUI_LightEffectOptions*](./capi-arkui-nativemodule-arkui-lighteffectoptionshandle.md) | ArkUI_LightEffectOptionsHandle | Defines the pointer to a light sensing interaction effect configuration object. [OH_ArkUI_NativeModule_LightEffectOptions_Create](#oh_arkui_nativemodule_lighteffectoptions_create) can be used to create a light sensing interaction effect configuration object. [OH_ArkUI_NativeModule_LightEffectOptions_Destroy](#oh_arkui_nativemodule_lighteffectoptions_destroy) can be used to destroy the light sensing interaction effect configuration object.|

### Function

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [bool OH_ArkUI_NativeModule_GetSystemMaterialSupported()](#oh_arkui_nativemodule_getsystemmaterialsupported) | - | Checks whether the current device supports system materials. If **true** is returned, the [NODE_SYSTEM_MATERIAL](./capi-native-node-h-nodeattributetype-animator.md#node_system_material) attribute can be used. Otherwise, setting this attribute will not take effect. This configuration item is defined by the device and cannot be modified.|
| [ArkUI_MaterialLevel OH_ArkUI_NativeModule_GetGlobalMaterialLevel()](#oh_arkui_nativemodule_getglobalmateriallevel) | - | Obtains the global material level, which is related to the device computing power. This configuration item is defined by the device and cannot be modified.|
| [ArkUI_ImmersiveMaterialHandle OH_ArkUI_NativeModule_ImmersiveMaterial_Create(ArkUI_ImmersiveStyle style)](#oh_arkui_nativemodule_immersivematerial_create) | - | Creates an immersive material object with a specified style. The material level of the created object follows the global material level, which can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](#oh_arkui_nativemodule_getglobalmateriallevel).|
| [void OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy(ArkUI_ImmersiveMaterialHandle material)](#oh_arkui_nativemodule_immersivematerial_destroy) | - | Destroys the immersive material object.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle style)](#oh_arkui_nativemodule_immersivematerial_setstyle) | - | Sets a style for an immersive material object. This parameter is valid only for display effects of devices with high- and mid-level computing power. It does not take effect for devices with low-level computing power, but no error is reported.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle* style)](#oh_arkui_nativemodule_immersivematerial_getstyle) | - | Obtains the style of an immersive material object.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t color)](#oh_arkui_nativemodule_immersivematerial_setmaterialcolor) | - | Sets a material color for an immersive material object. This parameter is valid only for display effects of devices with high- and mid-computing power. It does not take effect for devices with low-computing power, but no error is reported. If this parameter is not set, the default value **0** is used, indicating the transparent color.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)](#oh_arkui_nativemodule_immersivematerial_getmaterialcolor) | - | Obtains the material color of an immersive material object.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool applyShadow)](#oh_arkui_nativemodule_immersivematerial_setapplyshadow) | - | Sets whether to apply a shadow attribute to an immersive material object. This parameter takes effect for materials of all levels. If this parameter is set to **true**, the shadow effect in the material takes effect and takes precedence over the common shadow attribute. If this parameter is set to **false**, the common shadow attribute takes effect, and the material has no shadow effect. If this parameter is not set, the default value **true** is used.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool* applyShadow)](#oh_arkui_nativemodule_immersivematerial_getapplyshadow) | - | Obtains whether a shadow attribute is applied to an immersive material object.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive(ArkUI_ImmersiveMaterialHandle material, bool interactive)](#oh_arkui_nativemodule_immersivematerial_setinteractive) | - | Sets whether interactive deformation can be performed for an immersive material object. This parameter takes effect for materials of all levels. If this parameter is set to **true**, the material can be interactively deformed. If this parameter is set to **false**, the material cannot be interactively deformed. If this parameter is not set, the component behavior is followed.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive(ArkUI_ImmersiveMaterialHandle material, bool* interactive)](#oh_arkui_nativemodule_immersivematerial_getinteractive) | - | Obtains whether interactive deformation can be performed for an immersive material object. If this attribute has never been set, [ARKUI_ERROR_CODE_PARAM_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) will be returned.|
| [ArkUI_LightEffectOptionsHandle OH_ArkUI_NativeModule_LightEffectOptions_Create()](#oh_arkui_nativemodule_lighteffectoptions_create) | - | Creates a light sensing interaction effect configuration object. The default color is white (0xffffffff).|
| [void OH_ArkUI_NativeModule_LightEffectOptions_Destroy(ArkUI_LightEffectOptionsHandle options)](#oh_arkui_nativemodule_lighteffectoptions_destroy) | - | Destroys the light sensing interaction effect configuration object.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LightEffectOptions_SetColor(ArkUI_LightEffectOptionsHandle options, uint32_t color)](#oh_arkui_nativemodule_lighteffectoptions_setcolor) | - | Sets a color for the light sensing interaction effect. If this parameter is not set, the default color is white (0xffffffff).|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect(ArkUI_ImmersiveMaterialHandle material, const ArkUI_LightEffectOptionsHandle options)](#oh_arkui_nativemodule_immersivematerial_setlighteffect) | - | Sets the light sensing interaction effect for an immersive material object. This parameter takes effect for materials of all levels. If a null pointer is passed, the light sensing interaction effect is disabled. If a non-null pointer is passed, the light sensing interaction effect is enabled using the configuration parameters. If this API is not called, the light sensing interaction effect follows the component's behavior.|
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)](#oh_arkui_nativemodule_immersivematerial_getlighteffectcolor) | - | Obtains the color of the light sensing interaction effect for an immersive material object. This API can successfully obtain the color value only after [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](#oh_arkui_nativemodule_immersivematerial_setlighteffect) is called to set a non-null pointer to the light sensing interaction effect. If the light sensing interaction effect has never been set or has been disabled (by passing a null pointer to the light sensing interaction effect configuration), [ARKUI_ERROR_CODE_PARAM_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) will be returned.|

## Enumeration Type Description

### ArkUI_ImmersiveStyle

```c
enum ArkUI_ImmersiveStyle
```

Enumerates immersive material styles. Different styles correspond to different material parameters, which affect material thickness.

**Since**: 26.0.0

| Enum Item| Description|
| -- | -- |
| ARKUI_IMMERSIVE_STYLE_ULTRA_THIN = 0 | Ultra-thin style, which provides a very strong transparent effect.|
| ARKUI_IMMERSIVE_STYLE_THIN = 1 | Thin style, which provides a strong transparent effect.|
| ARKUI_IMMERSIVE_STYLE_REGULAR = 2 | Regular style, which provides a balanced visual effect.|
| ARKUI_IMMERSIVE_STYLE_THICK = 3 | Thick style, which provides a strong blur effect.|
| ARKUI_IMMERSIVE_STYLE_ULTRA_THICK = 4 | Ultra-thick style.|

### ArkUI_MaterialLevel

```c
enum ArkUI_MaterialLevel
```

Enumerates material levels, which are related to device computing power levels.

You can use [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](#oh_arkui_nativemodule_getglobalmateriallevel) to obtain the material level of the current device.

**Since**: 26.0.0

| Enum Item| Description|
| -- | -- |
| ARKUI_MATERIAL_LEVEL_EXQUISITE = 0 | Material level of devices with high-level computing power.|
| ARKUI_MATERIAL_LEVEL_GENTLE = 1 | Material level of devices with mid-level computing power.|
| ARKUI_MATERIAL_LEVEL_SMOOTH = 2 | Material level of devices with low-level computing power.|

## Function Description

### OH_ArkUI_NativeModule_GetSystemMaterialSupported()

```c
bool OH_ArkUI_NativeModule_GetSystemMaterialSupported()
```

**Description**

Checks whether the current device supports system materials.

If **true** is returned, the [NODE_SYSTEM_MATERIAL](./capi-native-node-h-nodeattributetype-animator.md#node_system_material) attribute can be used. Otherwise, setting this attribute will not take effect. This configuration item is defined by the device and cannot be modified.

**Since**: 26.0.0

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the current device supports system materials. The value **true** indicates that the current device supports system materials, and **false** indicates the opposite.|

### OH_ArkUI_NativeModule_GetGlobalMaterialLevel()

```c
ArkUI_MaterialLevel OH_ArkUI_NativeModule_GetGlobalMaterialLevel()
```

**Description**

Obtains the global material level, which is related to the device computing power. This configuration item is defined by the device and cannot be modified.

**Since**: 26.0.0

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_MaterialLevel](#arkui_materiallevel) | Material level of the device. The return type is [ArkUI_MaterialLevel](#arkui_materiallevel).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_Create()

```c
ArkUI_ImmersiveMaterialHandle OH_ArkUI_NativeModule_ImmersiveMaterial_Create(ArkUI_ImmersiveStyle style)
```

**Description**

Creates an immersive material object with a specified style. The material level of the created object follows the global material level, which can be obtained through [OH_ArkUI_NativeModule_GetGlobalMaterialLevel](#oh_arkui_nativemodule_getglobalmateriallevel).

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveStyle](#arkui_immersivestyle) style | Material style.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) | Pointer to the created immersive material object. If the creation fails or the material style is invalid, null is returned.<br>The returned object must be released by calling [OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy](#oh_arkui_nativemodule_immersivematerial_destroy) after being used.|

### OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy()

```c
void OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy(ArkUI_ImmersiveMaterialHandle material)
```

**Description**

Destroys the immersive material object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle style)
```

**Description**

Sets a style for an immersive material object. This parameter is valid only for display effects of devices with high- and mid-level computing power. It does not take effect for devices with low-level computing power, but no error is reported.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| [ArkUI_ImmersiveStyle](#arkui_immersivestyle) style | Material style.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** is **NULL** or **style** is invalid).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetStyle(ArkUI_ImmersiveMaterialHandle material, ArkUI_ImmersiveStyle* style)
```

**Description**

Obtains the style of an immersive material object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| [ArkUI_ImmersiveStyle](#arkui_immersivestyle) style | Pointer to the variable used to receive the material style.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** or **style** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t color)
```

**Description**

Sets a material color for an immersive material object. This parameter is valid only for display effects of devices with high- and mid-level computing power. It does not take effect for devices with low-level computing power, but no error is reported. If this parameter is not set, the default value **0** is used, indicating the transparent color.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| uint32_t color | Material color, in 0xAARRGGBB format. The value **0** indicates transparent (default value).|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetMaterialColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)
```

**Description**

Obtains the material color of an immersive material object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| uint32_t* color | Pointer to the variable used to receive the material color in 0xAARRGGBB format.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** or **color** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool applyShadow)
```

**Description**

Sets whether to apply a shadow attribute to an immersive material object. This parameter takes effect for materials of all levels.

If this parameter is set to **true**, the shadow effect in the material takes effect and takes precedence over the common shadow attribute. If this parameter is set to **false**, the common shadow attribute takes effect, and the material has no shadow effect. If this parameter is not set, the default value **true** is used.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| bool applyShadow | Whether to apply a shadow to the material. The value **true** indicates to apply a shadow to the material, and **false** indicates the opposite. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetApplyShadow(ArkUI_ImmersiveMaterialHandle material, bool* applyShadow)
```

**Description**

Obtains whether a shadow attribute is applied to an immersive material object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| bool* applyShadow | Pointer to the variable used to receive whether a shadow attribute is applied. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** or **applyShadow** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetInteractive(ArkUI_ImmersiveMaterialHandle material, bool interactive)
```

**Description**

Sets whether interactive deformation can be performed for an immersive material object. This parameter takes effect for materials of all levels.

If this parameter is set to **true**, the material can be interactively deformed. If this parameter is set to **false**, the material cannot be interactively deformed. If this parameter is not set, the component behavior is followed.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| bool interactive | Whether interactive deformation can be performed for a material. The value **true** indicates that interactive deformation can be performed for a material, and **false** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetInteractive(ArkUI_ImmersiveMaterialHandle material, bool* interactive)
```

**Description**

Obtains whether interactive deformation can be performed for an immersive material object.

If this attribute has never been set, [ARKUI_ERROR_CODE_PARAM_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) will be returned.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| bool* interactive | Pointer to the variable used to receive whether the material can be interactively deformed.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** or **interactive** is **NULL**).<br>Returns [ARKUI_ERROR_CODE_PARAM_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the attribute has never been set.|

### OH_ArkUI_NativeModule_LightEffectOptions_Create()

```c
ArkUI_LightEffectOptionsHandle OH_ArkUI_NativeModule_LightEffectOptions_Create()
```

**Description**

Creates a light sensing interaction effect configuration object. The default color is white (0xffffffff).

**Since**: 26.0.0

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_LightEffectOptionsHandle](./capi-arkui-nativemodule-arkui-lighteffectoptionshandle.md) | Pointer to the created light sensing interaction effect configuration object. The returned object must be released by calling [OH_ArkUI_NativeModule_LightEffectOptions_Destroy](#oh_arkui_nativemodule_lighteffectoptions_destroy) after being used.|

### OH_ArkUI_NativeModule_LightEffectOptions_Destroy()

```c
void OH_ArkUI_NativeModule_LightEffectOptions_Destroy(ArkUI_LightEffectOptionsHandle options)
```

**Description**

Destroys the light sensing interaction effect configuration object.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LightEffectOptionsHandle](./capi-arkui-nativemodule-arkui-lighteffectoptionshandle.md) options | Pointer to the light sensing interaction effect configuration object.|

### OH_ArkUI_NativeModule_LightEffectOptions_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LightEffectOptions_SetColor(ArkUI_LightEffectOptionsHandle options, uint32_t color)
```

**Description**

Sets a color for the light sensing interaction effect. If this parameter is not set, the default color is white (0xffffffff).

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_LightEffectOptionsHandle](./capi-arkui-nativemodule-arkui-lighteffectoptionshandle.md) options | Pointer to the light sensing interaction effect configuration object.|
| uint32_t color | Color of the light sensing interaction effect, in 0xAARRGGBB format.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**options** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect(ArkUI_ImmersiveMaterialHandle material, const ArkUI_LightEffectOptionsHandle options)
```

**Description**

Sets the light sensing interaction effect for an immersive material object. This parameter takes effect for materials of all levels.

If a null pointer is passed, the light sensing interaction effect is disabled. If a non-null pointer is passed, the light sensing interaction effect is enabled using the configuration parameters. If this API is not called, the light sensing interaction effect follows the component's behavior.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| const [ArkUI_LightEffectOptionsHandle](./capi-arkui-nativemodule-arkui-lighteffectoptionshandle.md) options | Pointer to the light sensing interaction effect configuration object. If a null pointer is passed, the light sensing interaction effect is disabled. If a non-null pointer is passed, the effect is enabled.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** is **NULL**).|

### OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_ImmersiveMaterial_GetLightEffectColor(ArkUI_ImmersiveMaterialHandle material, uint32_t* color)
```

**Description**

Obtains the color of the light sensing interaction effect for an immersive material object.

This API can successfully obtain the color value only after [OH_ArkUI_NativeModule_ImmersiveMaterial_SetLightEffect](#oh_arkui_nativemodule_immersivematerial_setlighteffect) is called to set a non-null pointer to the light sensing interaction effect. If the light sensing interaction effect has never been set or has been disabled (by passing a null pointer to the light sensing interaction effect configuration), [ARKUI_ERROR_CODE_PARAM_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) will be returned.

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ImmersiveMaterialHandle](./capi-arkui-nativemodule-arkui-immersivematerialhandle.md) material | Pointer to the immersive material object.|
| uint32_t* color | Pointer to the variable used to receive the color of the light sensing interaction effect.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Returns [ARKUI_ERROR_CODE_NO_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>Returns [ARKUI_ERROR_CODE_PARAM_INVALID](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs (**material** or **color** is **NULL**).<br>Returns [ARKUI_ERROR_CODE_PARAM_ERROR](./capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the light sensing interaction effect has never been set or has been disabled.|
