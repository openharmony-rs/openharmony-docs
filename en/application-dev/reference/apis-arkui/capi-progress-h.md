# progress.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines enumerations and APIs related to **Progress**.

**File to include:** <arkui/node_attributes/progress.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) | ArkUI_ProgressLinearStyleOption | Defines a linear progress indicator style.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ProgressType](#arkui_progresstype) | ArkUI_ProgressType | Enumerates progress indicator types.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)](#oh_arkui_progresslinearstyleoption_create) | Creates a **ProgressLinearStyleOption** instance.|
| [void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_destroy) | Destroys a **ProgressLinearStyleOption** instance.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setsmootheffectenabled) | Sets whether to enable the smooth effect.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setscaneffectenabled) | Sets whether to enable the scan effect.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)](#oh_arkui_progresslinearstyleoption_setstrokewidth) | Sets the stroke width for a progress indicator.|
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)](#oh_arkui_progresslinearstyleoption_setstrokeradius) | Sets the corner radius for a progress indicator.|
| [bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getsmootheffectenabled) | Obtains the enabled status of the smooth effect.|
| [bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getscaneffectenabled) | Obtains the enabled status of the scan effect.|
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokewidth) | Obtains the stroke width of the progress indicator.|
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokeradius) | Obtains the corner radius of the progress indicator.|

## Enum Description

### ArkUI_ProgressType

```c
enum ArkUI_ProgressType
```

**Description**

Enumerates progress indicator types.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_PROGRESS_TYPE_LINEAR = 0 | Linear type.|
| ARKUI_PROGRESS_TYPE_RING = 1 | Ring type without scale marks.|
| ARKUI_PROGRESS_TYPE_ECLIPSE = 2 | Eclipse type.|
| ARKUI_PROGRESS_TYPE_SCALE_RING = 3 | Ring type with scale marks.|
| ARKUI_PROGRESS_TYPE_CAPSULE = 4 | Capsule type.|


## Function Description

### OH_ArkUI_ProgressLinearStyleOption_Create()

```c
ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)
```

**Description**

Creates a **ProgressLinearStyleOption** instance.

**Since:** 15

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption*](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) | Pointer to the **ProgressLinearStyleOption** instance.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_ProgressLinearStyleOption_Destroy()

```c
void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Destroys a **ProgressLinearStyleOption** instance.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|

### OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**Description**

Sets whether to enable the smooth effect.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|
| bool enabled | Whether to enable the smooth effect. When this effect is enabled, the progress changes smoothly from the current value to the target value. When this effect is disabled, the progress changes abruptly to the target value.<br>**true**: Enable the smooth effect.<br>**false**: Disable the smooth effect.<br>The default value is **true**.|

### OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**Description**

Sets whether to enable the scan effect.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|
| bool enabled | Whether to enable the scan effect.<br>**true**: Enable the scan effect.<br>**false**: Disable the scan effect.<br>The default value is **false**.|

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)
```

**Description**

Sets the stroke width for a progress indicator.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|
| float strokeWidth | Stroke width of the progress indicator, in vp. Percentage values are not supported. The default value is **4.0vp**.|

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)
```

**Description**

Sets the corner radius for a progress indicator.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|
| float strokeRadius | Corner radius of the progress indicator, in vp. The value range is [0, strokeWidth/2]. The default value is **strokeWidth/2**.|

### OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Obtains the enabled status of the smooth effect.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the smooth effect is enabled. **true**: The smooth effect is enabled. **false**: The smooth effect is disabled. The default value is **true**.|

### OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Obtains the enabled status of the scan effect.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the scan effect is enabled. **true**: The scan effect is enabled. **false**: The scan effect is disabled. The default value is **false**.|

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Obtains the stroke width of the progress indicator.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| float | Stroke width of the progress indicator, in vp.|

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Obtains the corner radius of the progress indicator.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Pointer to the **ProgressLinearStyleOption** instance.|

**Returns**

| Type| Description|
| -- | -- |
| float | Corner radius of the progress indicator, in vp.|
