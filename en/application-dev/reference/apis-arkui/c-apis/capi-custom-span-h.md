# custom_span.h

## Overview

Defines a set of CustomSpan enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | ArkUI_CustomSpanMeasureInfo | Defines a struct for the measurement information of a custom span. |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md) | ArkUI_CustomSpanMetrics | Defines a struct for the measurement metrics of a custom span. |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | ArkUI_CustomSpanDrawInfo | Defines a struct for the drawing information of a custom span. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)](#oh_arkui_customspanmeasureinfo_create) | Creates measurement information for this custom span. |
| [void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_dispose) | Disposes of measurement information of this custom span. |
| [float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_getfontsize) | Obtains the font size of a custom span. |
| [ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)](#oh_arkui_customspanmetrics_create) | Creates measurement metrics for this custom span. |
| [void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_customspanmetrics_dispose) | Disposes of measurement metrics of this custom span. |
| [int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)](#oh_arkui_customspanmetrics_setwidth) | Sets the width for a custom span. |
| [int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)](#oh_arkui_customspanmetrics_setheight) | Sets the height for a custom span. |
| [ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)](#oh_arkui_customspandrawinfo_create) | Creates drawing information for this custom span. |
| [void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_dispose) | Disposes of drawing information for this custom span. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getxoffset) | Obtains the x-axis offset of the custom span relative to the mounted component. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinetop) | Obtains the top margin of the custom span relative to the mounted component. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinebottom) | Obtains the bottom margin of the custom span relative to the mounted component. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getbaseline) | Obtains the baseline offset of the custom span relative to the mounted component. |

## Function description

### OH_ArkUI_CustomSpanMeasureInfo_Create()

```c
ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)
```

**Description**

Creates measurement information for this custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo*](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | Returns a <b>CustomSpanMeasureInfo</b> instance.  <br> If the result returns nullptr, there may be out of memory. |

### OH_ArkUI_CustomSpanMeasureInfo_Dispose()

```c
void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Disposes of measurement information of this custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info | The CustomSpanMeasureInfo instance to be destroyed. |

### OH_ArkUI_CustomSpanMeasureInfo_GetFontSize()

```c
float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Obtains the font size of a custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info | Indicates the pointer to the measurement information of a custom span. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the font size. If a parameter error occurs, <b>0.0f</b> is returned.  <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_CustomSpanMetrics_Create()

```c
ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)
```

**Description**

Creates measurement metrics for this custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics*](capi-arkui-nativemodule-arkui-customspanmetrics.md) | Returns a <b>CustomSpanMetrics</b> instance.  <br> If the result returns nullptr, there may be out of memory. |

### OH_ArkUI_CustomSpanMetrics_Dispose()

```c
void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)
```

**Description**

Disposes of measurement metrics of this custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | The CustomSpanMetrics instance to be destroyed. |

### OH_ArkUI_CustomSpanMetrics_SetWidth()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)
```

**Description**

Sets the width for a custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Indicates the pointer to a <b>CustomSpanMetrics</b> instance. |
| float width | Indicates the width, in vp. The width should be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.          <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_CustomSpanMetrics_SetHeight()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)
```

**Description**

Sets the height for a custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Indicates the pointer to a <b>CustomSpanMetrics</b> instance. |
| float height | Indicates the height, in vp. The height should be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the result code.          Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.          <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_CustomSpanDrawInfo_Create()

```c
ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)
```

**Description**

Creates drawing information for this custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo*](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | Returns a <b>CustomSpanDrawInfo</b> instance.  <br> If the result returns nullptr, there may be out of memory. |

### OH_ArkUI_CustomSpanDrawInfo_Dispose()

```c
void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Disposes of drawing information for this custom span.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | The CustomSpanDrawInfo instance to be destroyed. |

### OH_ArkUI_CustomSpanDrawInfo_GetXOffset()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the x-axis offset of the custom span relative to the mounted component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Indicates the pointer to the drawing information of a custom span. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the x-axis offset. If a parameter error occurs, <b>0.0f</b> is returned.  <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_CustomSpanDrawInfo_GetLineTop()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the top margin of the custom span relative to the mounted component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Indicates the pointer to the drawing information of a custom span. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the top margin. If a parameter error occurs, <b>0.0f</b> is returned.  <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_CustomSpanDrawInfo_GetLineBottom()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the bottom margin of the custom span relative to the mounted component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Indicates the pointer to the drawing information of a custom span. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the bottom margin. If a parameter error occurs, <b>0.0f</b> is returned.  <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |

### OH_ArkUI_CustomSpanDrawInfo_GetBaseline()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the baseline offset of the custom span relative to the mounted component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Indicates the pointer to the drawing information of a custom span. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the baseline offset. If a parameter error occurs, <b>0.0f</b> is returned.  <br> Possible causes: Parameter verification failed, the parameter should not be nullptr. |


