# list.h

## Overview

Defines enumerations and APIs related to **List**.

**Library**: libace_ndk.z.so

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | Defines the size of the main axis of a child component of the **List** component. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment) | ArkUI_ListItemAlignment | Enumerates the alignment modes of items along the cross axis. The default value is **<br>ARKUI_LIST_ITEM_ALIGNMENT_START**. |
| [ArkUI_StickyStyle](#arkui_stickystyle) | ArkUI_StickyStyle | Enumerates the modes for pinning the header to the top or the footer to the bottom. |
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea) | ArkUI_ListItemGroupArea | Enumerates the areas in the ListItemGroup component. The default value is **<br>ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE**. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | Creates a **ListChildrenMainSize** instance. After use, call [OH_ArkUI_ListChildrenMainSizeOption_Dispose](capi-list-h.md#oh_arkui_listchildrenmainsizeoption_dispose) to release resources. |
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | Disposes of a **ListChildrenMainSize** instance created by [OH_ArkUI_ListChildrenMainSizeOption_Create](capi-list-h.md#oh_arkui_listchildrenmainsizeoption_create). The instance cannot be accessed after disposal. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | Sets the default size of the list item in the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width. |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | Obtains the default size of the list item in the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width. |
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | Adjusts the length of the main axis size array of child items in the List component. When the array is expanded, the initial value of new elements is **-1**. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | Deletes **deleteCount** elements from the main axis size array of child items in the List component starting from the specified index position, and inserts **addCount** elements with an initial value of **-1** at that position. If the value of **deleteCount** exceeds the number of remaining elements, deletion proceeds to the end of the array. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | Updates the size at the specified index in the child item size array of the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width. |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | Obtains the size at the specified index in the child item size array of the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width. |

## Enum type description

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**Description**

Enumerates the alignment modes of items along the cross axis. The default value is **<br>ARKUI_LIST_ITEM_ALIGNMENT_START**.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | The list items are packed toward the start edge of the **List** component along the cross axis. |
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER | The list items are centered in the **List** component along the cross axis. |
| ARKUI_LIST_ITEM_ALIGNMENT_END | The list items are packed toward the end edge of the **List** component along the cross axis. |

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**Description**

Enumerates the modes for pinning the header to the top or the footer to the bottom.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | [header](../../apis-function-flow-runtime-kit/c-apis/capi-type-def-h.md#ffrt_storage_size_t) and footer of ListItemGroup are not pinned to the top and bottom, respectively. |
| ARKUI_STICKY_STYLE_HEADER = 1 | [header](../../apis-function-flow-runtime-kit/c-apis/capi-type-def-h.md#ffrt_storage_size_t) of ListItemGroup is pinned to the top, and footer is not pinned to the bottom. |
| ARKUI_STICKY_STYLE_FOOTER = 2 | [header](../../apis-function-flow-runtime-kit/c-apis/capi-type-def-h.md#ffrt_storage_size_t) of ListItemGroup is not pinned to the top, and footer is pinned to the bottom. |
| ARKUI_STICKY_STYLE_BOTH = 3 | [header](../../apis-function-flow-runtime-kit/c-apis/capi-type-def-h.md#ffrt_storage_size_t) of ListItemGroup is pinned to the top, and footer is pinned to the bottom. |

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**Description**

Enumerates the areas in the ListItemGroup component. The default value is **<br>ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE**.

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | Outside the area of the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE | Area without the [header](../../apis-function-flow-runtime-kit/c-apis/capi-type-def-h.md#ffrt_storage_size_t), footer, and ListItem in the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM | List item area of the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER | Header area of the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER | Footer area of the **ListItemGroup** component. |


## Function description

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**Description**

Creates a **ListChildrenMainSize** instance. After use, call [OH_ArkUI_ListChildrenMainSizeOption_Dispose](capi-list-h.md#oh_arkui_listchildrenmainsizeoption_dispose) to release resources.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize*](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | Pointer to the **ListChildrenMainSize** instance. |

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**Description**

Disposes of a **ListChildrenMainSize** instance created by [OH_ArkUI_ListChildrenMainSizeOption_Create](capi-list-h.md#oh_arkui_listchildrenmainsizeoption_create). The instance cannot be accessed after disposal.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance to dispose of. |

### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)
```

**Description**

Sets the default size of the list item in the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. **ARKUI_ERROR_CODE_PARAM_INVALID** is returned when the parameter is a null pointer. |
| float defaultMainSize | Default size of the list item along the main axis, in vp. The value must be greater than or equal to 0. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**Description**

Obtains the default size of the list item in the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Default size of the list item along the main axis. The default value is **0**. The unit is vp. If ** option** is a null pointer, **-1** is returned. |

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**Description**

Adjusts the length of the main axis size array of child items in the List component. When the array is expanded, the initial value of new elements is **-1**.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. No operation is performed when the parameter is a null pointer. |
| int32_t totalSize | Target array length. The value range is greater than 0. No operation is performed when a value less than or equal to 0 is passed in. |

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**Description**

Deletes **deleteCount** elements from the main axis size array of child items in the List component starting from the specified index position, and inserts **addCount** elements with an initial value of **-1** at that position. If the value of **deleteCount** exceeds the number of remaining elements, deletion proceeds to the end of the array.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. **ARKUI_ERROR_CODE_PARAM_INVALID** is returned when the parameter is a null pointer. |
| int32_t index | Start index of the operation. The value ranges from 0 to the current array length minus 1. |
| int32_t deleteCount | Number of elements to delete starting from the start position. The value is greater than or equal to 0. If the number exceeds the remaining elements, deletion proceeds to the end of the array. |
| int32_t addCount | Number of elements to add starting from the start position. The value is greater than or equal to 0. The initial value of new elements is **-1**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**Description**

Updates the size at the specified index in the child item size array of the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. **ARKUI_ERROR_CODE_PARAM_INVALID** is returned when the parameter is a null pointer. |
| int32_t index | Array index of the target element. The value ranges from 0 to the current array length minus 1. |
| float mainSize | Main axis size value to set, in vp. The value must be greater than or equal to 0. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**Description**

Obtains the size at the specified index in the child item size array of the List component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |
| int32_t index | Array index of the target element. The value ranges from 0 to the current array length minus 1. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Main axis size value at the specified index in the array, in vp. **-1** is returned if **option** is a null pointer or **index** is out of the array range. |


