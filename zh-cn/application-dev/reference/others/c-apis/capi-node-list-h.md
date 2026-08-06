# node_list.h

## 概述

定义List组件相关的枚举和接口。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | 定义List组件子组件的主轴尺寸信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment) | ArkUI_ListItemAlignment | 交叉轴方向的布局方式，默认值为ARKUI_LIST_ITEM_ALIGNMENT_START。 |
| [ArkUI_StickyStyle](#arkui_stickystyle) | ArkUI_StickyStyle | 定义列表是否吸顶和吸底枚举值。 |
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea) | ArkUI_ListItemGroupArea | 定义{@link ListItemGroup}组件区域，默认值为ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | 创建ListChildrenMainSize接口设置的配置项。使用结束后需调用[OH_ArkUI_ListChildrenMainSizeOption_Dispose](capi-node-list-h.md#oh_arkui_listchildrenmainsizeoption_dispose)释放资源。 |
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | 销毁由[OH_ArkUI_ListChildrenMainSizeOption_Create](capi-node-list-h.md#oh_arkui_listchildrenmainsizeoption_create)创建的ListChildrenMainSize实例。销毁后不得继续访问该实例。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | 设置{@link List}组件列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | 获取{@link List}组件的列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | 调整{@link List}组件子项主轴尺寸数组的长度。扩大数组时，新增元素的初始值为-1。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | 从指定索引位置开始删除deleteCount个{@link List}组件子项主轴尺寸数组元素，并在该位置插入addCount个初始值为-1的元素。deleteCount超出剩余元素个数时，删除至数组末尾。 |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | 更新{@link List}组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | 获取{@link List}组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。 |

## 枚举类型说明

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**描述**

交叉轴方向的布局方式，默认值为ARKUI_LIST_ITEM_ALIGNMENT_START。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | The {@link list items} are packed toward the start edge of the **List** component along the cross axis. |
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER | ListItem在List中，交叉轴方向居中对齐。 |
| ARKUI_LIST_ITEM_ALIGNMENT_END | ListItem在List中，交叉轴方向尾部对齐。 |

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**描述**

定义列表是否吸顶和吸底枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | {@link header} and {@link footer} of {@link ListItemGroup} are not pinned to the top and bottom, respectively. |
| ARKUI_STICKY_STYLE_HEADER = 1 | {@link header} of {@link ListItemGroup} is pinned to the top, and {@link footer} is not pinned to the bottom. |
| ARKUI_STICKY_STYLE_FOOTER = 2 | {@link header} of {@link ListItemGroup} is not pinned to the top, and {@link footer} is pinned to the bottom. |
| ARKUI_STICKY_STYLE_BOTH = 3 | {@link header} of {@link ListItemGroup} is pinned to the top, and {@link footer} is pinned to the bottom. |

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**描述**

定义{@link ListItemGroup}组件区域，默认值为ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | ListItemGroup区域外。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE | Area without the {@link header}, {@link footer}, and {@link ListItem} in the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM | ListItemGroup的ListItem区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER | ListItemGroup的header区域。 |
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER | ListItemGroup的footer区域。 |


## 函数说明

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**描述**

创建ListChildrenMainSize接口设置的配置项。使用结束后需调用[OH_ArkUI_ListChildrenMainSizeOption_Dispose](capi-node-list-h.md#oh_arkui_listchildrenmainsizeoption_dispose)释放资源。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ListChildrenMainSize*](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ListChildrenMainSize配置项实例。 |

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**描述**

销毁由[OH_ArkUI_ListChildrenMainSizeOption_Create](capi-node-list-h.md#oh_arkui_listchildrenmainsizeoption_create)创建的ListChildrenMainSize实例。销毁后不得继续访问该实例。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | 要销毁的ListChildrenMainSize实例。 |

### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)
```

**描述**

设置{@link List}组件列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。为空指针时返回ARKUI_ERROR_CODE_PARAM_INVALID。 |
| float defaultMainSize | 列表项在主轴方向的默认尺寸值，单位为vp，取值范围为大于等于0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>{@link ARKUI_ERROR_CODE_NO_ERROR} 成功。<br>     <br>{@link ARKUI_ERROR_CODE_PARAM_INVALID} 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**描述**

获取{@link List}组件的列表项在主轴方向的默认尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 列表项在主轴方向的默认尺寸值，默认为0，单位为{@link vp}，option为空指针时返回-1。 |

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**描述**

调整{@link List}组件子项主轴尺寸数组的长度。扩大数组时，新增元素的初始值为-1。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。为空指针时不执行操作。 |
| int32_t totalSize | 目标数组长度，取值范围为大于0。传入小于等于0的值时不执行操作。 |

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**描述**

从指定索引位置开始删除deleteCount个{@link List}组件子项主轴尺寸数组元素，并在该位置插入addCount个初始值为-1的元素。deleteCount超出剩余元素个数时，删除至数组末尾。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。为空指针时返回ARKUI_ERROR_CODE_PARAM_INVALID。 |
| int32_t index | 操作起始索引位置，取值范围为0至数组当前长度减1。 |
| int32_t deleteCount | 从起始位置开始删除的元素数量，取值范围为大于等于0。数量超出剩余元素个数时删除至数组末尾。 |
| int32_t addCount | 从起始位置开始新增的元素数量，取值范围为大于等于0。新增元素的初始值为-1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>{@link ARKUI_ERROR_CODE_NO_ERROR} 成功。<br>     <br>{@link ARKUI_ERROR_CODE_PARAM_INVALID} 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**描述**

更新{@link List}组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。为空指针时返回ARKUI_ERROR_CODE_PARAM_INVALID。 |
| int32_t index | 目标元素的数组索引位置，取值范围为0至数组当前长度减1。 |
| float mainSize | 要设置的主轴尺寸值，单位为vp，取值范围为大于等于0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>     <br>{@link ARKUI_ERROR_CODE_NO_ERROR} 成功。<br>     <br>{@link ARKUI_ERROR_CODE_PARAM_INVALID} 函数参数异常。 |

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**描述**

获取{@link List}组件子项主轴尺寸数组中指定索引位置的尺寸。主轴方向为纵向时表示高度，为横向时表示宽度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | ListChildrenMainSize实例。 |
| int32_t index | 目标元素的数组索引位置，取值范围为0至数组当前长度减1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 数组指定位置的主轴尺寸值，单位为vp。option为空指针或index超出数组范围时返回-1。 |


