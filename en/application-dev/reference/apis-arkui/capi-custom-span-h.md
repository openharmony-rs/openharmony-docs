# custom_span.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines enumerations and APIs related to **CustomSpan**.

**File to include:** <arkui/node_attributes/custom_span.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | ArkUI_CustomSpanMeasureInfo | Defines the measurement information of a custom span.|
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md) | ArkUI_CustomSpanMetrics | Defines the measurement metrics of a custom span.|
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | ArkUI_CustomSpanDrawInfo | Defines the drawing information of a custom span.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)](#oh_arkui_customspanmeasureinfo_create) | Creates measurement information for a custom span.|
| [void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_dispose) | Disposes of measurement information of a custom span.|
| [float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)](#oh_arkui_customspanmeasureinfo_getfontsize) | Obtains the font size of the parent text node of a custom span.|
| [ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)](#oh_arkui_customspanmetrics_create) | Creates measurement metrics for a custom span.|
| [void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)](#oh_arkui_customspanmetrics_dispose) | Disposes of measurement metrics of a custom span.|
| [int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)](#oh_arkui_customspanmetrics_setwidth) | Sets the width for a custom span.|
| [int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)](#oh_arkui_customspanmetrics_setheight) | Sets the height for a custom span.|
| [ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)](#oh_arkui_customspandrawinfo_create) | Creates drawing information for a custom span.|
| [void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_dispose) | Disposes of drawing information for a custom span.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getxoffset) | Obtains the x-axis offset of the custom span relative to the mounted component.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinetop) | Obtains the top margin of the custom span relative to the mounted component.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getlinebottom) | Obtains the bottom margin of the custom span relative to the mounted component.|
| [float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)](#oh_arkui_customspandrawinfo_getbaseline) | Obtains the baseline offset of the custom span relative to the mounted component.|

## Function Description

### OH_ArkUI_CustomSpanMeasureInfo_Create()

```c
ArkUI_CustomSpanMeasureInfo* OH_ArkUI_CustomSpanMeasureInfo_Create(void)
```

**Description**

Creates measurement information for a custom span.

**Since:** 12

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo*](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md) | Pointer to the **CustomSpanMeasureInfo** instance.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_CustomSpanMeasureInfo_Dispose()

```c
void OH_ArkUI_CustomSpanMeasureInfo_Dispose(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Disposes of measurement information of a custom span.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info |  Pointer to the measurement information of a custom span.|

### OH_ArkUI_CustomSpanMeasureInfo_GetFontSize()

```c
float OH_ArkUI_CustomSpanMeasureInfo_GetFontSize(ArkUI_CustomSpanMeasureInfo* info)
```

**Description**

Obtains the font size of the parent text node of a custom span.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMeasureInfo](capi-arkui-nativemodule-arkui-customspanmeasureinfo.md)* info |  Pointer to the measurement information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Font size of the parent node text, in fp. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanMetrics_Create()

```c
ArkUI_CustomSpanMetrics* OH_ArkUI_CustomSpanMetrics_Create(void)
```

**Description**

Creates measurement metrics for a custom span.

**Since:** 12

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_CustomSpanMetrics*](capi-arkui-nativemodule-arkui-customspanmetrics.md) | Pointer to the **CustomSpanMetrics** instance.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_CustomSpanMetrics_Dispose()

```c
void OH_ArkUI_CustomSpanMetrics_Dispose(ArkUI_CustomSpanMetrics* metrics)
```

**Description**

Disposes of measurement metrics of a custom span.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Pointer to the **CustomSpanMetrics** instance.|

### OH_ArkUI_CustomSpanMetrics_SetWidth()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetWidth(ArkUI_CustomSpanMetrics* metrics, float width)
```

**Description**

Sets the width for a custom span.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Pointer to the **CustomSpanMetrics** instance.|
| float width | Width, in vp. The default value is **0.0f**. The negative value has the same effect as the default value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanMetrics_SetHeight()

```c
int32_t OH_ArkUI_CustomSpanMetrics_SetHeight(ArkUI_CustomSpanMetrics* metrics, float height)
```

**Description**

Sets the height for a custom span.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanMetrics](capi-arkui-nativemodule-arkui-customspanmetrics.md)* metrics | Pointer to the **CustomSpanMetrics** instance.|
| float height | Height, in vp. The default value is **0.0f**. The negative value has the same effect as the default value.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_Create()

```c
ArkUI_CustomSpanDrawInfo* OH_ArkUI_CustomSpanDrawInfo_Create(void)
```

**Description**

Creates drawing information for a custom span.

**Since:** 12

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo*](capi-arkui-nativemodule-arkui-customspandrawinfo.md) | Pointer to the **CustomSpanDrawInfo** instance.<br> If a null pointer is returned, the memory may be insufficient.|

### OH_ArkUI_CustomSpanDrawInfo_Dispose()

```c
void OH_ArkUI_CustomSpanDrawInfo_Dispose(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Disposes of drawing information for a custom span.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

### OH_ArkUI_CustomSpanDrawInfo_GetXOffset()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetXOffset(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the x-axis offset of the custom span relative to the mounted component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | X-axis offset, in px. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_GetLineTop()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineTop(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the top margin of the custom span relative to the mounted component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Top margin, in px. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_GetLineBottom()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetLineBottom(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the bottom margin of the custom span relative to the mounted component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Bottom margin, in px. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_CustomSpanDrawInfo_GetBaseline()

```c
float OH_ArkUI_CustomSpanDrawInfo_GetBaseline(ArkUI_CustomSpanDrawInfo* info)
```

**Description**

Obtains the baseline offset of the custom span relative to the mounted component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_CustomSpanDrawInfo](capi-arkui-nativemodule-arkui-customspandrawinfo.md)* info |  Pointer to the drawing information of a custom span.|

**Returns**

| Type| Description|
| -- | -- |
| float | Baseline offset, in px. If a parameter error occurs, **0.0f** is returned.<br> A possible cause is that mandatory parameters are left unspecified.|
