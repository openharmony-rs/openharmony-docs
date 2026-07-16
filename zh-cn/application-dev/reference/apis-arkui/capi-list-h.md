# list.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong; @rongShao-Z; @wind_-->
<!--Designer: @yylong-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

定义List组件相关的枚举和接口。

**引用文件：** <arkui/node_attributes/list.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[ScrollableNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ScrollableNDK)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | 定义List的ChildrenMainSize类信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment) | ArkUI_ListItemAlignment | 交叉轴方向的布局方式。 |
| [ArkUI_StickyStyle](#arkui_stickystyle) | ArkUI_StickyStyle | 定义列表是否吸顶和吸底枚举值。 |
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea) | ArkUI_ListItemGroupArea | 定义ListItemGroup组件区域。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | 创建ListChildrenMainSize接口设置的配置项。 |
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | 销毁ListChildrenMainSize实例。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | 设置List组件列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | 获取List组件的列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | 调整List组件子项主轴尺寸数组的容量大小。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | 对List组件子项主轴尺寸数组进行大小调整。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | 更新List组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | 获取List组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |

## 枚举类型说明

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**描述：**


交叉轴方向的布局方式，默认值为ARKUI_LIST_ITEM_ALIGNMENT_START。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | [ListItem](./arkui-ts/ts-container-listitem.md#listitem10)在List中，交叉轴方向首部对齐。 |
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER = 1 | ListItem在List中，交叉轴方向居中对齐。 |
| ARKUI_LIST_ITEM_ALIGNMENT_END = 2 | ListItem在List中，交叉轴方向尾部对齐。 |

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**描述：**


定义列表是否吸顶和吸底枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸底。 |
| ARKUI_STICKY_STYLE_HEADER = 1 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸底。 |
| ARKUI_STICKY_STYLE_FOOTER = 2 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)不吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸底。 |
| ARKUI_STICKY_STYLE_BOTH = 3 | [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)的[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸顶，[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)吸底。 |

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**描述：**


定义[ListItemGroup](./arkui-ts/ts-container-listitemgroup.md)组件区域，默认值为ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | ListItemGroup区域外。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE = 1 | ListItemGroup没有[header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)、[footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions对象说明)和[ListItem](./arkui-ts/ts-container-listitem.md#listitem10)时的区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM = 2 | ListItemGroup的ListItem区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER = 3 | ListItemGroup的header区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER = 4 | ListItemGroup的footer区域。 |

## 函数说明

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**描述：**


创建ListChildrenMainSize接口设置的配置项。

**起始版本：** 12

**返回：**

| 类型                              | 说明 |
|---------------------------------| -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* | ListChildrenMainSize配置项实例。 |

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**描述：**


销毁ListChildrenMainSize实例。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | 要销毁的ListChildrenMainSize实例。 |

### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)
```

**描述：**


设置[List](./arkui-ts/ts-container-list.md)组件列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| float defaultMainSize | 列表项在主轴方向的默认尺寸值，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**描述：**


获取[List](./arkui-ts/ts-container-list.md)组件的列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 列表项在主轴方向的默认尺寸值，默认为0，单位为[vp](../apis-arkui/arkui-ts/ts-types.md#vp10)，option为空指针时返回-1。 |

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**描述：**


调整[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组的容量大小。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t totalSize | 目标数组容量大小。 |

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**描述：**


对[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组进行大小调整。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t index | 操作起始索引位置。 |
| int32_t deleteCount | 从起始位置开始删除的元素数量。 |
| int32_t addCount | 从起始位置开始新增的元素数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**描述：**


更新[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t index | 目标元素的数组索引位置。 |
| float mainSize | 要设置的主轴尺寸值，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**描述：**


获取[List](./arkui-ts/ts-container-list.md)组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t index | 目标元素的数组索引位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 数组具体位置的值。若函数参数异常，返回-1。 |
