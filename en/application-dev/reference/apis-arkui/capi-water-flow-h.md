# water_flow.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @guozejun-->
<!--Designer: @guozejun-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines enumerations and APIs related to **WaterFlow**.

**File to include:** <arkui/water_flow.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[NDKWaterFlowSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKWaterFlowSample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | ArkUI_Margin | Describes the margins of a component.|
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | ArkUI_WaterFlowSectionOption | Defines the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_WaterFlowLayoutMode](#arkui_waterflowlayoutmode) | ArkUI_WaterFlowLayoutMode | Enumerates the layout modes of the [WaterFlow](../apis-arkui/arkui-ts/ts-container-waterflow.md) component.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()](#oh_arkui_waterflowsectionoption_create) | - | Creates a water flow section configuration.|
| [void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_dispose) | - | Disposes of the pointer to a water flow section configuration.|
| [void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)](#oh_arkui_waterflowsectionoption_setsize) | - | Sets the array length for a water flow section configuration.|
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_getsize) | - | Obtains the array length of a water flow section configuration.|
| [void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)](#oh_arkui_waterflowsectionoption_setitemcount) | - | Sets the number of items in a water flow section.|
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getitemcount) | - | Obtains the number of items in the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)](#oh_arkui_waterflowsectionoption_setcrosscount) | - | Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow section.|
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcrosscount) | - | Obtains the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow section.|
| [void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)](#oh_arkui_waterflowsectionoption_setcolumngap) | - | Sets the gap between columns in the specified water flow section.|
| [float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcolumngap) | - | Obtains the gap between columns in the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)](#oh_arkui_waterflowsectionoption_setrowgap) | - | Sets the gap between rows in the specified water flow section.|
| [float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getrowgap) | - | Obtains the gap between rows in the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index,float marginTop, float marginRight, float marginBottom, float marginLeft)](#oh_arkui_waterflowsectionoption_setmargin) | - | Sets the margins for the specified water flow section.|
| [ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getmargin) | - | Obtains the margins of the water flow section that matches the specified index.|
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex (ArkUI_WaterFlowSectionOption* option, int32_t index, float(\*callback)(int32_t itemIndex))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) | - | Obtains the main axis size of a specified water flow item based on **itemIndex** in the water flow section configuration. To use custom data in the callback, call [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata).|
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData (ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata) | - | Obtains the main axis size of a specified item based on **itemIndex** in the water flow section configuration. The difference between this API and [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) is that this API allows you to pass custom data (**userData**) and receive the data in the callback function.|

## Enum Description

### ArkUI_WaterFlowLayoutMode

```c
enum ArkUI_WaterFlowLayoutMode
```

**Description**


Enumerates the layout modes of the [WaterFlow](../apis-arkui/arkui-ts/ts-container-waterflow.md) component.

**Since:** 18

| Value| Description|
| -- | -- |
| ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN = 0 | Layout from top to bottom. In scenarios where column switching occurs, the layout starts from the first [water flow item](../apis-arkui/arkui-ts/ts-container-flowitem.md) to the currently displayed [water flow item](../apis-arkui/arkui-ts/ts-container-flowitem.md).|
| ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW = 1 | Sliding window layout. In scenarios where column switching occurs, only the range of [water flow items](../apis-arkui/arkui-ts/ts-container-flowitem.md) currently on display is re-laid out. As the user scrolls down with their finger, [water flow items](../apis-arkui/arkui-ts/ts-container-flowitem.md) that enter the display range from above are subsequently laid out.|

## Function Description

### OH_ArkUI_WaterFlowSectionOption_Create()

```c
ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()
```

**Description**


Creates the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.

**Since:** 12

**Returns**

| Type                               | Description|
|-----------------------------------| -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|

### OH_ArkUI_WaterFlowSectionOption_Dispose()

```c
void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)
```

**Description**


Disposes of the pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|

### OH_ArkUI_WaterFlowSectionOption_SetSize()

```c
void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option,int32_t size)
```

**Description**


Sets the array length for a water flow section configuration.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t size | Size of the array.|

### OH_ArkUI_WaterFlowSectionOption_GetSize()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)
```

**Description**


Obtains the length of the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration array.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Size of the array. If **-1** is returned, an error code indicating failure is returned. The possible cause is that the **option** parameter is abnormal, for example, a null pointer.|

### OH_ArkUI_WaterFlowSectionOption_SetItemCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option,int32_t index, int32_t itemCount)
```

**Description**


Sets the number of [water flow items](../apis-arkui/arkui-ts/ts-container-flowitem.md) in the section.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|
| int32_t index | Index of the target water flow section.|
| int32_t itemCount | Number of [water flow items](../apis-arkui/arkui-ts/ts-container-flowitem.md) in the section.|

### OH_ArkUI_WaterFlowSectionOption_GetItemCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the number of [water flow items](../apis-arkui/arkui-ts/ts-container-flowitem.md) at the corresponding index based on the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of items in the water flow section.|

### OH_ArkUI_WaterFlowSectionOption_SetCrossCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option,int32_t index, int32_t crossCount)
```

**Description**


Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow section.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| int32_t crossCount | Number of columns or rows, depending on the layout direction.|

### OH_ArkUI_WaterFlowSectionOption_GetCrossCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the number of layout grids at the corresponding index based on the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of columns or rows, depending on the layout direction.|

### OH_ArkUI_WaterFlowSectionOption_SetColumnGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option,int32_t index, float columnGap)
```

**Description**


Sets the gap between columns in the specified water flow section.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| float columnGap | Gap between columns. The unit is vp.|

### OH_ArkUI_WaterFlowSectionOption_GetColumnGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the gap between columns in the water flow section that matches the specified index.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| float | Gap between columns. The unit is vp.|

### OH_ArkUI_WaterFlowSectionOption_SetRowGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option,int32_t index, float rowGap)
```

**Description**


Sets the gap between rows in the **FlowItem** section.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration.|
| int32_t index | Index of the target water flow section.|
| float rowGap | Gap between rows. The unit is vp.|

### OH_ArkUI_WaterFlowSectionOption_GetRowGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the gap between rows in the section at the corresponding index based on the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| float | Gap between rows. The unit is vp.|

### OH_ArkUI_WaterFlowSectionOption_SetMargin()

```c
void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index,float marginTop, float marginRight, float marginBottom, float marginLeft)
```

**Description**


Sets the margins for the specified water flow section.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|
| int32_t index | Index of the target water flow section.|
| float marginTop | Top margin of [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md).|
| float marginRight | Right margin of [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md).|
| float marginBottom | Bottom margin of [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md).|
| float marginLeft | Left margin of [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md).|

### OH_ArkUI_WaterFlowSectionOption_GetMargin()

```c
ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**


Obtains the margins of the section at the corresponding index based on the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|
| int32_t index | Index of the target water flow section.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | Margin. The unit is vp.|

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option,int32_t index, float(*callback)(int32_t itemIndex))
```

**Description**


Obtains the main axis size of a specified water flow item based on **itemIndex** in the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration. To use custom data in the callback, call [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata).

**Since:** 12


**Parameters**

| Name                                           | Description|
|------------------------------------------------| -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|
| int32_t index                                  | Index of the target water flow section.|
| callback                                       | Callback used to return the result. **itemIndex** indicates the index of [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md).|

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData,float (*callback)(int32_t itemIndex, void* userData))
```

**Description**


Obtains the main axis size of a specified item based on **itemIndex** in the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration. The difference between this API and [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) is that this API allows you to pass custom data (**userData**) and receive the data in the callback function.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the [FlowItem](../apis-arkui/arkui-ts/ts-container-flowitem.md) section configuration.|
| int32_t index | Index of the target water flow section.|
|  void* userData |Pointer to user-defined data, which will be passed back to the user in the callback.|
| callback | Callback used to return the result. **itemIndex**: index of the [water flow item](../apis-arkui/arkui-ts/ts-container-flowitem.md); **userData**: user-defined data.|
