# custom_span.h

## Overview

Defines enumerations and APIs related to **CustomSpan**, which is used to implement precise size measurement, layout typesetting, and drawing effects for custom spans. It supports you in implementing text and image layout, emoji embedding, custom markers, and other features in scenarios such as rich text editors, chat applications, and document applications, providing flexible custom span capabilities to help improve development efficiency and achieve richer text layout effects.

**Library**: libace_ndk.z.so

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | ArkUI_CustomSpanMeasureInfo | Defines the measurement information of a custom span. This struct is used to provide measurement data in the measurement callback of a custom span, helping you implement precise size measurement and layout of custom text. |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md) | ArkUI_CustomSpanMetrics | Describes the metrics of a custom span, which is used to set layout information such as the width and height of a component. It applies to mixed text and image layout in scenarios such as rich text editors and chat applications. |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | ArkUI_CustomSpanDrawInfo | Defines the drawing information of a custom span, which is passed to you in the drawing callback of the span. You can obtain and use the information in the custom drawing process to achieve custom drawing effects for the span. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)](#oh_arkui_customspanmeasureinfo_create) | Creates measurement information for a custom span. |
| [void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_dispose) | Disposes of measurement information of a custom span. |
| [float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_getfontsize) | Obtains the font size of the parent text node of a custom span. In the measurement callback of a custom span, the layout size of the custom component can be calculated based on the font size of the parent text node. This API is used to implement precise typesetting in scenarios such as layout of text and images and emoji embedding. |
| [ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)](#oh_arkui_customspanmetrics_create) | Creates measurement metrics for a custom span. |
| [void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_customspanmetrics_dispose) | Disposes of measurement metrics of a custom span. |
| [int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)](#oh_arkui_customspanmetrics_setwidth) | Sets the width for a custom span. In text and image layout scenarios, you need to set an appropriate width for embedded images or emojis to match the text line height. In document applications, you may need to set a fixed width for custom marker elements. |
| [int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)](#oh_arkui_customspanmetrics_setheight) | Sets the height for a custom span. In emoji embedding scenarios, you need to set an appropriate height based on the emoji size to maintain alignment with the text. In text and image layout scenarios, you need to set a height for embedded elements that matches the text line height. |
| [ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)](#oh_arkui_customspandrawinfo_create) | Creates drawing information for a custom span. |
| [void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_dispose) | Disposes of drawing information for a custom span. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getxoffset) | Obtains the x-axis offset of the custom span relative to the mounted component. In the custom drawing callback, you need to determine the drawing start position based on the offset value. This API is used to implement precise drawing in scenarios such as emoji embedding and layout of text and images. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinetop) | Obtains the top margin of the custom span relative to the mounted component. In custom drawing, you need to determine the vertical start position of the drawing area based on the top margin. This API is used for precise typesetting in scenarios such as rich text editors and document applications. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinebottom) | Obtains the bottom margin of the custom span relative to the mounted component. In custom drawing, you need to calculate the height range of the drawing area by combining the top margin and bottom margin. This API is used for precise layout in scenarios such as layout of text and images and emoji embedding. |
| [float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getbaseline) | Obtains the baseline offset of the custom span relative to the mounted component. In the drawing callback of a custom span, use this API to obtain the baseline offset for text alignment and typesetting, achieving precise drawing effects in scenarios such as rich text editors and layout of text and images. |

## Function description

### OH_ArkUI_CustomSpanMeasureInfo_Create()

```c
ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)
```

**Description**

Creates measurement information for a custom span.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo*](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | Pointer to the **ArkUI_CustomSpanMeasureInfo** instance. It is used to provide measurement data of the component in the measurement callback of the custom span. <br>If a null pointer is returned, the memory may be insufficient. |

### OH_ArkUI_CustomSpanMeasureInfo_Dispose()

```c
void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Disposes of measurement information of a custom span.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info | Pointer to the measurement information of a custom span. It is used to pass the measurement information object to dispose of. The parameter cannot be null; otherwise, it will cause parameter verification failure. The object must be the one created by **OH_ArkUI_CustomSpanMeasureInfo_Create()**. |

### OH_ArkUI_CustomSpanMeasureInfo_GetFontSize()

```c
float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Obtains the font size of the parent text node of a custom span. In the measurement callback of a custom span, the layout size of the custom component can be calculated based on the font size of the parent text node. This API is used to implement precise typesetting in scenarios such as layout of text and images and emoji embedding.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info | Pointer to the measurement information of a custom span. This parameter cannot be null; otherwise, it will cause parameter verification failure. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Font size of the parent node text, in fp. If parameter verification fails, **0.0f** is returned. <br>A possible cause is that the parameter is null. |

### OH_ArkUI_CustomSpanMetrics_Create()

```c
ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)
```

**Description**

Creates measurement metrics for a custom span.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics*](capi-arkui-nativemodule-arkui-customspanmetrics.md) | Pointer to the **ArkUI_CustomSpanMetrics** instance. It is used to describe layout information such as the width and height of a custom span. <br>If a null pointer is returned, the memory may be insufficient. |

### OH_ArkUI_CustomSpanMetrics_Dispose()

```c
void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)
```

**Description**

Disposes of measurement metrics of a custom span.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Pointer to the **CustomSpanMetrics** instance. It is used to pass the measurement metric object to dispose of. The parameter cannot be null; otherwise, it will cause parameter verification failure. The object must be the one created by **OH_ArkUI_CustomSpanMetrics_Create()**. |

### OH_ArkUI_CustomSpanMetrics_SetWidth()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)
```

**Description**

Sets the width for a custom span. In text and image layout scenarios, you need to set an appropriate width for embedded images or emojis to match the text line height. In document applications, you may need to set a fixed width for custom marker elements.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Pointer to the **CustomSpanMetrics** instance. It is used to pass the measurement metric object whose width needs to be set. The parameter cannot be null; otherwise, parameter validation fails. |
| float width | Width, in vp. The value range is [0, +∞). The default value is **0.0f**. Negative values have the same effect as the default value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Possible cause: Parameter validation fails because the parameter is null. <br>Handling steps: Ensure that the **metrics** parameter passed in is not a null pointer. |

### OH_ArkUI_CustomSpanMetrics_SetHeight()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)
```

**Description**

Sets the height for a custom span. In emoji embedding scenarios, you need to set an appropriate height based on the emoji size to maintain alignment with the text. In text and image layout scenarios, you need to set a height for embedded elements that matches the text line height.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Pointer to the **CustomSpanMetrics** instance. It is used to pass the measurement metric object whose height needs to be set. The parameter cannot be null; otherwise, it will cause parameter verification failure. The object must be a valid object created by **OH_ArkUI_CustomSpanMetrics_Create()**. |
| float height | Height, in vp. The value range is [0, +∞), and the default value is **0.0f**. Negative values have the same effect as the default value. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. <br>Possible cause: Parameter validation fails because the parameter is null. <br>Handling steps: Ensure that the **metrics** parameter passed in is not a null pointer. |

### OH_ArkUI_CustomSpanDrawInfo_Create()

```c
ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)
```

**Description**

Creates drawing information for a custom span.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo*](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | Pointer to the **ArkUI_CustomSpanDrawInfo** instance, indicating the drawing information of the custom span. <br>If a null pointer is returned, the memory may be insufficient. |

### OH_ArkUI_CustomSpanDrawInfo_Dispose()

```c
void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Disposes of drawing information for a custom span.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Pointer to the drawing information of a custom span. It is used to pass the drawing information object to dispose of. The parameter cannot be null, otherwise it will cause parameter verification failure. The object must be the one created by **OH_ArkUI_CustomSpanDrawInfo_Create()**. |

### OH_ArkUI_CustomSpanDrawInfo_GetXOffset()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the x-axis offset of the custom span relative to the mounted component. In the custom drawing callback, you need to determine the drawing start position based on the offset value. This API is used to implement precise drawing in scenarios such as emoji embedding and layout of text and images.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Pointer to the drawing information of a custom span. It is used to pass the drawing information object for which the x-axis offset value needs to be obtained. The parameter cannot be null; otherwise, parameter verification will fail. |

**Returns**:

| Type | Description |
| -- | -- |
| float | X-axis offset value, in px. If parameter verification fails, **0.0f** is returned. <br>The parameter verification fails because the parameter is null. |

### OH_ArkUI_CustomSpanDrawInfo_GetLineTop()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the top margin of the custom span relative to the mounted component. In custom drawing, you need to determine the vertical start position of the drawing area based on the top margin. This API is used for precise typesetting in scenarios such as rich text editors and document applications.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Pointer to the drawing information of a custom span. It is used to pass the drawing information object for which the top margin needs to be obtained. The parameter cannot be null; otherwise, parameter verification will fail. The value must be a valid object created by **OH_ArkUI_CustomSpanDrawInfo_Create()**. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Top margin, in px. If parameter validation fails, **0.0f** is returned. <br>The parameter validation fails because the parameter is null. |

### OH_ArkUI_CustomSpanDrawInfo_GetLineBottom()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the bottom margin of the custom span relative to the mounted component. In custom drawing, you need to calculate the height range of the drawing area by combining the top margin and bottom margin. This API is used for precise layout in scenarios such as layout of text and images and emoji embedding.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Pointer to the drawing information of a custom span. It is used to pass the drawing information object whose bottom margin needs to be obtained. The parameter cannot be null; otherwise, parameter verification will fail. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Bottom margin, in px. If parameter validation fails, **0.0f** is returned. <br>The parameter validation fails because the parameter is null. |

### OH_ArkUI_CustomSpanDrawInfo_GetBaseline()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the baseline offset of the custom span relative to the mounted component. In the drawing callback of a custom span, use this API to obtain the baseline offset for text alignment and typesetting, achieving precise drawing effects in scenarios such as rich text editors and layout of text and images.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info | Pointer to the drawing information of a custom span. It is used to pass the drawing information object for which the baseline offset needs to be obtained. The parameter cannot be empty; otherwise, parameter verification will fail. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Baseline offset, in px. If parameter verification fails, **0.0f** is returned. <br>The parameter verification fails because the parameter is null. |


