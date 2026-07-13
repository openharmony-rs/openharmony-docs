# node_water_flow.h

## 概述

Provides WaterFlow-related type and function definitions for<b>NativeNode</b> APIs.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | ArkUI_Margin | Describes the margins of a component. |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | ArkUI_WaterFlowSectionOption | 定义FlowItem分组配置信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_WaterFlowLayoutMode](#arkui_waterflowlayoutmode) | ArkUI_WaterFlowLayoutMode | 定义WaterFlow组件布局模式枚举值。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()](#oh_arkui_waterflowsectionoption_create) | 创建FlowItem分组配置信息。 |
| [void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_dispose) | 销毁FlowItem分组配置信息指针。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)](#oh_arkui_waterflowsectionoption_setsize) | 设置FlowItem分组配置信息数组长度。 |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)](#oh_arkui_waterflowsectionoption_getsize) | 获取FlowItem分组配置信息数组长度。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)](#oh_arkui_waterflowsectionoption_setitemcount) | 设置分组中FlowItem数量。 |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getitemcount) | 通过FlowItem分组配置信息获取对应索引下的FlowItem数量。 |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option, int32_t index, float (\*callback)(int32_t itemIndex))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindex) | 通过FlowItem分组配置信息根据flowItemIndex获取指定FlowItem的主轴大小。 |
| [void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_waterflowsectionoption_registergetitemmainsizecallbackbyindexwithuserdata) | 通过FlowItem分组配置信息根据flowItemIndex获取指定Item的主轴大小。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)](#oh_arkui_waterflowsectionoption_setcrosscount) | 设置布局栅格，纵向布局时为列数，横向布局时为行数。 |
| [int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcrosscount) | 通过FlowItem分组配置信息获取对应索引下的布局栅格数。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)](#oh_arkui_waterflowsectionoption_setcolumngap) | 设置分组的列间距。 |
| [float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getcolumngap) | 通过FlowItem分组配置信息获取对应索引下的分组的列间距。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)](#oh_arkui_waterflowsectionoption_setrowgap) | 设置FlowItem分组的行间距。 |
| [float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getrowgap) | 通过FlowItem分组配置信息获取对应索引下的分组的行间距。 |
| [void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft)](#oh_arkui_waterflowsectionoption_setmargin) | 设置分组的外边距。 |
| [ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)](#oh_arkui_waterflowsectionoption_getmargin) | 通过FlowItem分组配置信息获取对应索引下的分组的外边距。 |

## 枚举类型说明

### ArkUI_WaterFlowLayoutMode

```c
enum ArkUI_WaterFlowLayoutMode
```

**描述**

定义WaterFlow组件布局模式枚举值。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_WATER_FLOW_LAYOUT_MODE_ALWAYS_TOP_DOWN = 0 | Layout from top to bottom. In scenarios where column switching occurs, the layout starts from the first{@link water flow item} to the currently displayed {@link water flow item}. |
| ARKUI_WATER_FLOW_LAYOUT_MODE_SLIDING_WINDOW | Sliding window layout. In scenarios where column switching occurs, only the range of {@link water flow items}currently on display is re-laid out. As the user scrolls down with their finger, {@link water flow items} thatenter the display range from above are subsequently laid out. |


## 函数说明

### OH_ArkUI_WaterFlowSectionOption_Create()

```c
ArkUI_WaterFlowSectionOption* OH_ArkUI_WaterFlowSectionOption_Create()
```

**描述**

创建FlowItem分组配置信息。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption*](capi-arkui-nativemodule-arkui-waterflowsectionoption.md) | FlowItem分组配置信息。 |

### OH_ArkUI_WaterFlowSectionOption_Dispose()

```c
void OH_ArkUI_WaterFlowSectionOption_Dispose(ArkUI_WaterFlowSectionOption* option)
```

**描述**

销毁FlowItem分组配置信息指针。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |

### OH_ArkUI_WaterFlowSectionOption_SetSize()

```c
void OH_ArkUI_WaterFlowSectionOption_SetSize(ArkUI_WaterFlowSectionOption* option, int32_t size)
```

**描述**

设置FlowItem分组配置信息数组长度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t size | 数组长度。 |

### OH_ArkUI_WaterFlowSectionOption_GetSize()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetSize(ArkUI_WaterFlowSectionOption* option)
```

**描述**

获取FlowItem分组配置信息数组长度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 数组长度。如果返回-1，则返回失败。失败的原因可能是option参数异常，如空指针。 |

### OH_ArkUI_WaterFlowSectionOption_SetItemCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t itemCount)
```

**描述**

设置分组中FlowItem数量。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| int32_t itemCount | 分组中FlowItem数量。 |

### OH_ArkUI_WaterFlowSectionOption_GetItemCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetItemCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

通过FlowItem分组配置信息获取对应索引下的FlowItem数量。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 分组中FlowItem数量。 |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndex(ArkUI_WaterFlowSectionOption* option, int32_t index, float (*callback)(int32_t itemIndex))
```

**描述**

通过FlowItem分组配置信息根据flowItemIndex获取指定FlowItem的主轴大小。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)\* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| float (\*callback)(int32_t itemIndex) | 根据index获取指定Item的主轴大小。flowItemIndex：FlowItem索引值。 |

### OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData()

```c
void OH_ArkUI_WaterFlowSectionOption_RegisterGetItemMainSizeCallbackByIndexWithUserData(ArkUI_WaterFlowSectionOption* option, int32_t index, void* userData, float (*callback)(int32_t itemIndex, void* userData))
```

**描述**

通过FlowItem分组配置信息根据flowItemIndex获取指定Item的主轴大小。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)\* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| void\* userData | FlowItem自定义数据。 |
| float (\*callback)(int32_t itemIndex | 根据index获取指定Item的主轴大小。itemIndex：FlowItem索引值。 |

### OH_ArkUI_WaterFlowSectionOption_SetCrossCount()

```c
void OH_ArkUI_WaterFlowSectionOption_SetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index, int32_t crossCount)
```

**描述**

设置布局栅格，纵向布局时为列数，横向布局时为行数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| int32_t crossCount | 布局栅格数量。 |

### OH_ArkUI_WaterFlowSectionOption_GetCrossCount()

```c
int32_t OH_ArkUI_WaterFlowSectionOption_GetCrossCount(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

通过FlowItem分组配置信息获取对应索引下的布局栅格数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 布局栅格数量。 |

### OH_ArkUI_WaterFlowSectionOption_SetColumnGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float columnGap)
```

**描述**

设置分组的列间距。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| float columnGap | 列间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_GetColumnGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetColumnGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

通过FlowItem分组配置信息获取对应索引下的分组的列间距。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 列间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_SetRowGap()

```c
void OH_ArkUI_WaterFlowSectionOption_SetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index, float rowGap)
```

**描述**

设置FlowItem分组的行间距。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | FlowItem分组配置信息数组索引值。 |
| float rowGap | 行间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_GetRowGap()

```c
float OH_ArkUI_WaterFlowSectionOption_GetRowGap(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

通过FlowItem分组配置信息获取对应索引下的分组的行间距。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 行间距。单位：vp。 |

### OH_ArkUI_WaterFlowSectionOption_SetMargin()

```c
void OH_ArkUI_WaterFlowSectionOption_SetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index, float marginTop, float marginRight, float marginBottom, float marginLeft)
```

**描述**

设置分组的外边距。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |
| float marginTop | FlowItem上外边距。 |
| float marginRight | FlowItem右外边距。 |
| float marginBottom | FlowItem下外边距。 |
| float marginLeft | FlowItem左外边距。 |

### OH_ArkUI_WaterFlowSectionOption_GetMargin()

```c
ArkUI_Margin OH_ArkUI_WaterFlowSectionOption_GetMargin(ArkUI_WaterFlowSectionOption* option, int32_t index)
```

**描述**

通过FlowItem分组配置信息获取对应索引下的分组的外边距。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_WaterFlowSectionOption](capi-arkui-nativemodule-arkui-waterflowsectionoption.md)* option | FlowItem分组配置信息。 |
| int32_t index | 分组配置信息数组索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_Margin](capi-arkui-nativemodule-arkui-margin.md) | 外边距。单位：vp。 |


