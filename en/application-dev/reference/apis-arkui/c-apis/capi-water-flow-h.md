# water_flow.h

## Overview

Provides WaterFlow-related type and function definitions for <b>NativeNode</b> APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | ArkUI_Margin | Describes the margins of a component. |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | ArkUI_WaterFlowSectionOption | Defines the water flow section configuration. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_WaterFlowLayoutMode](#arkui_waterflowlayoutmode) | ArkUI_WaterFlowLayoutMode | Enumerates the layout modes of the {@link WaterFlow} component. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()](#oh_arkui_waterflowsectionoption_create) | Creates the {@link FlowItem} section configuration. |
| [void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_dispose) | Disposes of the pointer to the {@link FlowItem} section configuration. |
| [void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)](#oh_arkui_waterflowsectionoption_setsize) | Sets the array length for a water flow section configuration. |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_getsize) | Obtains the length of the {@link FlowItem} section configuration array. |
| [void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)](#oh_arkui_waterflowsectionoption_setitemcount) | Sets the number of {@link water flow items} in the section. |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getitemcount) | Obtains the number of {@link water flow items} at the corresponding index based on the {@link FlowItem} section configuration. |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option, int32_t index, float (\*callback)(int32_t itemIndex))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) | Obtains the main axis size of a specified water flow item based on **itemIndex** in the {@link FlowItem} section configuration. To use custom data in the callback, call [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData](capi-water-flow-h.md#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata). |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata) | Obtains the main axis size of a specified water flow item based on **itemIndex** in the {@link FlowItem} section configuration. The difference between this API and [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex](capi-water-flow-h.md#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) is that this API allows you to pass custom data (**userData**) and receive the data in the callback function. |
| [void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)](#oh_arkui_waterflowsectionoption_setcrosscount) | Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow. |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcrosscount) | Obtains the number of layout grids at the corresponding index based on the {@link FlowItem} section configuration. |
| [void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)](#oh_arkui_waterflowsectionoption_setcolumngap) | Sets the gap between columns in the specified water flow section. |
| [float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcolumngap) | Obtains the gap between columns in the water flow section that matches the specified index. |
| [void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)](#oh_arkui_waterflowsectionoption_setrowgap) | Sets the gap between rows in the **FlowItem** section. |
| [float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getrowgap) | Obtains the gap between rows in the section at the corresponding index based on the {@link FlowItem} section configuration. |
| [void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft)](#oh_arkui_waterflowsectionoption_setmargin) | Sets the margins for the specified water flow section. |
| [ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getmargin) | Obtains the top margin of the section at the corresponding index based on the {@link FlowItem} section configuration. |

## Enum type description

### ArkUI_WaterFlowLayoutMode

```c
enum ArkUI_WaterFlowLayoutMode
```

**Description**

Enumerates the layout modes of the {@link WaterFlow} component.

**Since**: 18

| Enum item | Description |
| -- | -- |
| ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN = 0 | Layout from top to bottom. In scenarios where column switching occurs, the layout starts from the first {@link water flow item} to the currently displayed {@link water flow item}. |
| ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW | Sliding window layout. In scenarios where column switching occurs, only the range of {@link water flow items}<br>currently on display is re-laid out. As the user scrolls down with their finger, {@link water flow items} that enter the display range from above are subsequently laid out. |


## Function description

### OH_ArkUI_WaterFlowSectionOption_Create()

```c
ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()
```

**Description**

Creates the {@link FlowItem} section configuration.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption*](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | Pointer to the {@link FlowItem} section configuration. |

### OH_ArkUI_WaterFlowSectionOption_Dispose()

```c
void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)
```

**Description**

Disposes of the pointer to the {@link FlowItem} section configuration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the {@link FlowItem} section configuration. |

### OH_ArkUI_WaterFlowSectionOption_SetSize()

```c
void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)
```

**Description**

Sets the array length for a water flow section configuration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration. |
| int32_t size | Size of the array. |

### OH_ArkUI_WaterFlowSectionOption_GetSize()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)
```

**Description**

Obtains the length of the {@link FlowItem} section configuration array.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Size of the array. If -1 is returned, an error code indicating failure is returned. The possible cause      is that the option parameter is abnormal, for example, a null pointer. |

### OH_ArkUI_WaterFlowSectionOption_SetItemCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)
```

**Description**

Sets the number of {@link water flow items} in the section.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the {@link FlowItem} section configuration. |
| int32_t index | Index of the target water flow section. |
| int32_t itemCount | Number of {@link water flow items} in the section. |

### OH_ArkUI_WaterFlowSectionOption_GetItemCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**

Obtains the number of {@link water flow items} at the corresponding index based on the {@link FlowItem} section configuration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the {@link FlowItem} section configuration. |
| int32_t index | Index of the target water flow section. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Number of items in the water flow section. |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option, int32_t index, float (*callback)(int32_t itemIndex))
```

**Description**

Obtains the main axis size of a specified water flow item based on **itemIndex** in the {@link FlowItem} section configuration. To use custom data in the callback, call [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData](capi-water-flow-h.md#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_WaterFlowSectionOption\* option | Pointer to the {@link FlowItem} section configuration. |
| int32_t index | Index of the target water flow section. |
| float (\*callback)(int32_t itemIndex) | Callback used to return the result. **itemIndex** indicates the index of {@link FlowItem}. |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (*callback)(int32_t itemIndex, void* userData))
```

**Description**

Obtains the main axis size of a specified water flow item based on **itemIndex** in the {@link FlowItem} section configuration. The difference between this API and [OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex](capi-water-flow-h.md#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) is that this API allows you to pass custom data (**userData**) and receive the data in the callback function.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_WaterFlowSectionOption\* option | Pointer to the {@link FlowItem} section configuration. |
| int32_t index | Index of the target water flow section. |
| void\* userData | Pointer to user-defined data, which will be passed back to the user in the callback. |
| float (\*callback)(int32_t itemIndex | Callback used to return the result. **itemIndex**: index of the {@link water flow item}; **userData**<br>: user-defined data. |

### OH_ArkUI_WaterFlowSectionOption_SetCrossCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)
```

**Description**

Sets the number of columns (in a vertical layout) or rows (in a horizontal layout) of a water flow.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration. |
| int32_t index | Index of the target water flow section. |
| int32_t crossCount | Number of columns or rows, depending on the layout direction. |

### OH_ArkUI_WaterFlowSectionOption_GetCrossCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**

Obtains the number of layout grids at the corresponding index based on the {@link FlowItem} section configuration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration. |
| int32_t index | Index of the target water flow section. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Number of columns or rows, depending on the layout direction. |

### OH_ArkUI_WaterFlowSectionOption_SetColumnGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)
```

**Description**

Sets the gap between columns in the specified water flow section.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration. |
| int32_t index | Index of the target water flow section. |
| float columnGap | Gap between columns. Unit: vp. |

### OH_ArkUI_WaterFlowSectionOption_GetColumnGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**

Obtains the gap between columns in the water flow section that matches the specified index.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration. |
| int32_t index | Index of the target water flow section. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Gap between columns. Unit: vp. |

### OH_ArkUI_WaterFlowSectionOption_SetRowGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)
```

**Description**

Sets the gap between rows in the **FlowItem** section.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to a water flow section configuration. |
| int32_t index | Index of the **FlowItem** section configuration array. |
| float rowGap | Gap between rows. Unit: vp. |

### OH_ArkUI_WaterFlowSectionOption_GetRowGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**

Obtains the gap between rows in the section at the corresponding index based on the {@link FlowItem} section configuration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the {@link FlowItem} section configuration. |
| int32_t index | Index of the target water flow section. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Gap between rows. Unit: vp. |

### OH_ArkUI_WaterFlowSectionOption_SetMargin()

```c
void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft)
```

**Description**

Sets the margins for the specified water flow section.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the {@link FlowItem} section configuration. |
| int32_t index | Index of the target water flow section. |
| float marginTop | Top margin of {@link FlowItem}. |
| float marginRight | Right margin of {@link FlowItem}. |
| float marginBottom | Bottom margin of {@link FlowItem}. |
| float marginLeft | Left margin of {@link FlowItem}. |

### OH_ArkUI_WaterFlowSectionOption_GetMargin()

```c
ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**Description**

Obtains the top margin of the section at the corresponding index based on the {@link FlowItem} section configuration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | Pointer to the {@link FlowItem} section configuration. |
| int32_t index | Index of the target water flow section. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | Margins. Unit: vp. |


