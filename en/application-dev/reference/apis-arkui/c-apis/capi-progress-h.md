# progress.h

## Overview

Defines a set of Progress enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) | ArkUI_ProgressLinearStyleOption | Set the linear progress indicator style. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ProgressType](#arkui_progresstype) | ArkUI_ProgressType | Enumerates the styles of the progress indicator. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)](#oh_arkui_progresslinearstyleoption_create) | Create linear progress indicator style information. |
| [void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_destroy) | Destroy linear progress indicator style information. |
| [void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setscaneffectenabled) | Set whether the scan effect is enabled. |
| [void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)](#oh_arkui_progresslinearstyleoption_setsmootheffectenabled) | Set whether smoothing effect is enabled. |
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)](#oh_arkui_progresslinearstyleoption_setstrokewidth) | Set linear progress indicator stroke width. |
| [void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)](#oh_arkui_progresslinearstyleoption_setstrokeradius) | Set linear progress indicator stroke radius. |
| [bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getscaneffectenabled) | Get whether scan effect is enable. |
| [bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getsmootheffectenabled) | Get whether smoothing effect is enabled. |
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokewidth) | Get linear progress indicator stroke width. |
| [float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)](#oh_arkui_progresslinearstyleoption_getstrokeradius) | Get linear progress indicator stroke radius. |

## Enum type description

### ArkUI_ProgressType

```c
enum ArkUI_ProgressType
```

**Description**

Enumerates the styles of the progress indicator.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_PROGRESS_TYPE_LINEAR = 0 | Linear style. |
| ARKUI_PROGRESS_TYPE_RING | Indeterminate ring style. |
| ARKUI_PROGRESS_TYPE_ECLIPSE | Eclipse style. |
| ARKUI_PROGRESS_TYPE_SCALE_RING | Determinate ring style. |
| ARKUI_PROGRESS_TYPE_CAPSULE | Capsule style. |


## Function description

### OH_ArkUI_ProgressLinearStyleOption_Create()

```c
ArkUI_ProgressLinearStyleOption* OH_ArkUI_ProgressLinearStyleOption_Create(void)
```

**Description**

Create linear progress indicator style information.

**Since**: 15

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption*](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) | Returns a <b>ProgressLinearStyleOption</b> instance.  <br> If the result returns nullptr, there may be out of memory. |

### OH_ArkUI_ProgressLinearStyleOption_Destroy()

```c
void OH_ArkUI_ProgressLinearStyleOption_Destroy(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Destroy linear progress indicator style information.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |

### OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**Description**

Set whether the scan effect is enabled.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |
| bool enabled | Whether to enable the scan effect. Default value: false. |

### OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option, bool enabled)
```

**Description**

Set whether smoothing effect is enabled.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |
| bool enabled | Whether to enable the smooth effect. When this effect is enabled, the progress change to the set value takes place gradually. Otherwise, it takes place immediately. Default value: true. |

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeWidth(ArkUI_ProgressLinearStyleOption* option, float strokeWidth)
```

**Description**

Set linear progress indicator stroke width.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |
| float strokeWidth | Stroke width of the progress indicator. It cannot be set in percentage. Default value: 4.0vp. |

### OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius()

```c
void OH_ArkUI_ProgressLinearStyleOption_SetStrokeRadius(ArkUI_ProgressLinearStyleOption* option, float strokeRadius)
```

**Description**

Set linear progress indicator stroke radius.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |
| float strokeRadius | Rounded corner radius of the progress indicator. Value range: [0, strokeWidth/2]. Default value: strokeWidth/2. |

### OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetScanEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Get whether scan effect is enable.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether to enable the scan effect. |

### OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled()

```c
bool OH_ArkUI_ProgressLinearStyleOption_GetSmoothEffectEnabled(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Get whether smoothing effect is enabled.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether to enable the smooth effect. |

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeWidth(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Get linear progress indicator stroke width.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Stroke width of the progress indicator. |

### OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius()

```c
float OH_ArkUI_ProgressLinearStyleOption_GetStrokeRadius(ArkUI_ProgressLinearStyleOption* option)
```

**Description**

Get linear progress indicator stroke radius.

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md)* option | Linear progress indicator style information. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Rounded corner radius of the progress indicator. |


