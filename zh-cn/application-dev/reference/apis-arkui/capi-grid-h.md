# grid.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @guozejun-->
<!--Designer: @guozejun-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

定义Grid组件相关的枚举和接口。

**引用文件：** <arkui/grid.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 22

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[NDKGridSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKGridSample)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_GridItemSize](capi-arkui-nativemodule-arkui-griditemsize.md) | ArkUI_GridItemSize | 定义Grid布局选项onGetIrregularSizeByIndex回调返回值结构体。 |
| [ArkUI_GridItemRect](capi-arkui-nativemodule-arkui-griditemrect.md) | ArkUI_GridItemRect | 定义Grid布局选项onGetRectByIndex回调返回值结构体。 |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) | ArkUI_GridLayoutOptions | 定义Grid布局选项。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_GridItemAlignment](#arkui_griditemalignment) | ArkUI_GridItemAlignment | [GridItem](../apis-arkui/arkui-ts/ts-container-griditem.md)对齐方式枚举。 |
| [ArkUI_GridItemStyle](#arkui_griditemstyle) | ArkUI_GridItemStyle | GridItem样式枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()](#oh_arkui_gridlayoutoptions_create) | 创建Grid布局选项。 |
| [void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)](#oh_arkui_gridlayoutoptions_dispose) | 销毁Grid布局选项。 |
| [int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)](#oh_arkui_gridlayoutoptions_setirregularindexes) | 设置Grid中不规则GridItem的索引数组。 |
| [int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)](#oh_arkui_gridlayoutoptions_getirregularindexes) | 获取Grid中不规则GridItem的索引数组。当不设置OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback时，irregularIndexes中GridItem的默认大小为垂直滚动Grid的一整行或水平滚动Grid的一整列。 |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize(\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetirregularsizebyindexcallback) | Grid布局选项通过GridItem索引获取指定Item占用的行列数。 |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback) | Grid布局选项通过GridItem索引获取指定Item的起始行列和占用的行列数。 |

## 枚举类型说明

### ArkUI_GridItemAlignment

```c
enum ArkUI_GridItemAlignment
```
**描述：**

[GridItem](../apis-arkui/arkui-ts/ts-container-griditem.md)对齐方式枚举。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| GRID_ITEM_ALIGNMENT_DEFAULT = 0 | Grid的默认对齐方式。 |
| GRID_ITEM_ALIGNMENT_STRETCH  = 1  | 以一行中的最高的GridItem作为其他GridItem的高度。 |


### ArkUI_GridItemStyle

```c
enum ArkUI_GridItemStyle
```

**描述：**


GridItem样式枚举。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| GRID_ITEM_STYLE_NONE  = 0 | 无样式。 |
| GRID_ITEM_STYLE_PLAIN  = 1  | 显示Hover、Press态样式。 |

## 函数说明

### OH_ArkUI_GridLayoutOptions_Create()

```c
ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()
```

**描述：**

创建Grid布局选项。

**起始版本：** 22

**返回：**

| 类型                                | 说明 |
|-----------------------------------| -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* | Grid布局选项。 |

### OH_ArkUI_GridLayoutOptions_Dispose()

```c
void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)
```

**描述：**

销毁Grid布局选项。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |


### OH_ArkUI_GridLayoutOptions_SetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)
```

**描述：**

设置Grid中不规则GridItem的索引数组。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| uint32_t* irregularIndexes |  GridItem索引数组。 |
| int32_t size | GridItem索引数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)  函数参数异常。<br>         异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_GridLayoutOptions_GetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)
```

**描述：**

获取Grid中不规则GridItem的索引数组。当不设置OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback时，irregularIndexes中GridItem的默认大小为垂直滚动Grid的一整行或水平滚动Grid的一整列。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| uint32_t* irregularIndexes |  GridItem索引数组。 |
| int32_t size | GridItem索引数组大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。<br>         [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) 数组大小不够。<br>         异常原因：传入参数验证失败，参数不能为空。 |

### OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize (*callback)(int32_t itemIndex, void* userData))
```

**描述：**

Grid布局选项通过GridItem索引获取指定Item占用的行列数。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| void* userData | 用户自定义数据。 |
| ArkUI_GridItemSize (\*callback)(int32_t itemIndex, void* userData) | 根据index获取指定Item占用的行列数。<br> itemIndex: GridItem索引值，取值范围来自[OH_ArkUI_GridLayoutOptions_SetIrregularIndexes](#oh_arkui_gridlayoutoptions_setirregularindexes)。 |

### OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (*callback)(int32_t itemIndex, void* userData))
```

**描述：**

Grid布局选项通过GridItem索引获取指定Item的起始行列和占用的行列数。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Grid布局选项。 |
| void* userData | 用户自定义数据。 |
| ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData) | 根据index获取指定Item的起始行列和占用的行列数。<br>   itemIndex: GridItem索引值。 |
