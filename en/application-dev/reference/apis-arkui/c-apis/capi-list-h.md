# list.h

## Overview

Provides shared list-related type and function definitions for <b>NativeNode</b> APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | Defines the **ChildrenMainSize** information of the **List** component. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment) | ArkUI_ListItemAlignment | Enumerates the alignment modes of items along the cross axis. The default value is **<br>ARKUI_LIST_ITEM_ALIGNMENT_START**. |
| [ArkUI_StickyStyle](#arkui_stickystyle) | ArkUI_StickyStyle | Enumerates the modes for pinning the header to the top or the footer to the bottom. |
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea) | ArkUI_ListItemGroupArea | Enumerates the areas in the {@link ListItemGroup} component. The default value is **<br>ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE**. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | Creates a **ListChildrenMainSize** instance. |
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | Disposes of a **ListChildrenMainSize** instance. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | Sets the default size of the list item in the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width. |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | Obtains the default size of the list item in the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width. |
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | Adjusts the capacity of the children item size array in the {@link List} component along the main axis. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | Adjusts the children item size array in the {@link List} component along the main axis. |
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | Updates the size at the specified index in the children item size array of the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width. |
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | Obtains the size at the specified index in the children item size array of the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width. |

## Enum type description

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**Description**

Enumerates the alignment modes of items along the cross axis. The default value is **<br>ARKUI_LIST_ITEM_ALIGNMENT_START**.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | The {@link list items} are packed toward the start edge of the **List** component along the cross axis. |
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER | The list items are centered in the **List** component along the cross axis. |
| ARKUI_LIST_ITEM_ALIGNMENT_END | The list items are packed toward the end edge of the **List** component along the cross axis. |

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**Description**

Enumerates the modes for pinning the header to the top or the footer to the bottom.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | {@link header} and {@link footer} of {@link ListItemGroup} are not pinned to the top and bottom, respectively. |
| ARKUI_STICKY_STYLE_HEADER = 1 | {@link header} of {@link ListItemGroup} is pinned to the top, and {@link footer} is not pinned to the bottom. |
| ARKUI_STICKY_STYLE_FOOTER = 2 | {@link header} of {@link ListItemGroup} is not pinned to the top, and {@link footer} is pinned to the bottom. |
| ARKUI_STICKY_STYLE_BOTH = 3 | {@link header} of {@link ListItemGroup} is pinned to the top, and {@link footer} is pinned to the bottom. |

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**Description**

Enumerates the areas in the {@link ListItemGroup} component. The default value is **<br>ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE**.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | Outside the area of the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE | Area without the {@link header}, {@link footer}, and {@link ListItem} in the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM | List item area of the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER | Header area of the **ListItemGroup** component. |
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER | Footer area of the **ListItemGroup** component. |


## Function description

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**Description**

Creates a **ListChildrenMainSize** instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize*](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | Pointer to the created ListChildrenMainSize instance. |

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**Description**

Disposes of a **ListChildrenMainSize** instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Sets the default size of the list item in the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |
| float defaultMainSize | Default size of the list item along the main axis, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <ul>      <li><br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.</li>      </ul> |

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**Description**

Obtains the default size of the list item in the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Default size of the list item along the main axis. The default value is 0. The unit is {@link vp}. If       option is a null pointer, -1 is returned. |

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**Description**

Adjusts the capacity of the children item size array in the {@link List} component along the main axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |
| int32_t totalSize | Capacity of the target array. |

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**Description**

Adjusts the children item size array in the {@link List} component along the main axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |
| int32_t index | Start index. |
| int32_t deleteCount | Number of elements to be deleted from the start position. |
| int32_t addCount | Number of elements to be added from the start position. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <ul>      <li><br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.</li>      </ul> |

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**Description**

Updates the size at the specified index in the children item size array of the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |
| int32_t index | Array index of the target element. |
| float mainSize | Size of the main axis, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <ul>      <li><br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.</li>      </ul> |

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**Description**

Obtains the size at the specified index in the children item size array of the {@link List} component along the main axis. The vertical axis indicates the height, and the horizontal axis indicates the width.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance. |
| int32_t index | Array index of the target element. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Value at the specified index. If a parameter error occurs, -1 is returned. |


