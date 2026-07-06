# list.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong; @rongShao-Z; @wind_-->
<!--Designer: @yylong-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines enumerations and APIs related to **List**.

**File to include:** <arkui/list.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[ScrollableNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ScrollableNDK)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md) | ArkUI_ListChildrenMainSize | Defines the **ChildrenMainSize** information of the **List** component.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_ListItemAlignment](#arkui_listitemalignment) | ArkUI_ListItemAlignment | Enumerates the alignment modes of items along the cross axis.|
| [ArkUI_StickyStyle](#arkui_stickystyle) | ArkUI_StickyStyle | Enumerates the modes for pinning the header to the top or the footer to the bottom.|
| [ArkUI_ListItemGroupArea](#arkui_listitemgrouparea) | ArkUI_ListItemGroupArea | Enumerates areas of the **ListItemGroup** component.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()](#oh_arkui_listchildrenmainsizeoption_create) | Creates a **ListChildrenMainSize** instance.|
| [void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_dispose) | Disposes of a **ListChildrenMainSize** instance.|
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)](#oh_arkui_listchildrenmainsizeoption_setdefaultmainsize) | Sets the default size of the list item in the **List** component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.|
| [float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)](#oh_arkui_listchildrenmainsizeoption_getdefaultmainsize) | Obtains the default size of the list item in the **List** component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.|
| [void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)](#oh_arkui_listchildrenmainsizeoption_resize) | Adjusts the capacity of the child item size array in the **List** component along the main axis.|
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)](#oh_arkui_listchildrenmainsizeoption_splice) | Adjusts the child item size array in the **List** component along the main axis.|
| [int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)](#oh_arkui_listchildrenmainsizeoption_updatesize) | Updates the size at the specified index in the child item size array of the **List** component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.|
| [float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)](#oh_arkui_listchildrenmainsizeoption_getmainsize) | Obtains the size at the specified index in the child item size array of the **List** component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.|

## Enum Description

### ArkUI_ListItemAlignment

```c
enum ArkUI_ListItemAlignment
```

**Description**


Enumerates the alignment modes of items along the cross axis. The default value is **ARKUI_LIST_ITEM_ALIGNMENT_START**.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_LIST_ITEM_ALIGNMENT_START = 0 | The [list items](./arkui-ts/ts-container-listitem.md#listitem10) are packed toward the start edge of the **List** component along the cross axis.|
| ARKUI_LIST_ITEM_ALIGNMENT_CENTER = 1 | The list items are centered in the **List** component along the cross axis.|
| ARKUI_LIST_ITEM_ALIGNMENT_END = 2 | The list items are packed toward the end edge of the **List** component along the cross axis.|

### ArkUI_StickyStyle

```c
enum ArkUI_StickyStyle
```

**Description**


Enumerates the modes for pinning the header to the top or the footer to the bottom.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_STICKY_STYLE_NONE = 0 | [header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) and [footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) of [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md) are not pinned to the top and bottom, respectively.|
| ARKUI_STICKY_STYLE_HEADER = 1 | [header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) of [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md) is pinned to the top, and [footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) is not pinned to the bottom.|
| ARKUI_STICKY_STYLE_FOOTER = 2 | [header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) of [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md) is not pinned to the top, and [footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) is pinned to the bottom.|
| ARKUI_STICKY_STYLE_BOTH = 3 | [header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) of [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md) is pinned to the top, and [footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions) is pinned to the bottom.|

### ArkUI_ListItemGroupArea

```c
enum ArkUI_ListItemGroupArea
```

**Description**


Enumerates the areas in the [ListItemGroup](./arkui-ts/ts-container-listitemgroup.md) component. The default value is **ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE**.

**Since:** 15

| Value| Description|
| -- | -- |
| ARKUI_LIST_ITEM_GROUP_AREA_OUTSIDE = 0 | Outside the area of the **ListItemGroup** component.|
| ARKUI_LIST_ITEM_SWIPE_AREA_NONE = 1 | Area without the [header](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions), [footer](./arkui-ts/ts-container-listitemgroup.md#listitemgroupoptions), and [ListItem](./arkui-ts/ts-container-listitem.md#listitem10) in the **ListItemGroup** component.|
| ARKUI_LIST_ITEM_SWIPE_AREA_ITEM = 2 | List item area of the **ListItemGroup** component.|
| ARKUI_LIST_ITEM_SWIPE_AREA_HEADER = 3 | Header area of the **ListItemGroup** component.|
| ARKUI_LIST_ITEM_SWIPE_AREA_FOOTER = 4 | Footer area of the **ListItemGroup** component.|

## Function Description

### OH_ArkUI_ListChildrenMainSizeOption_Create()

```c
ArkUI_ListChildrenMainSize* OH_ArkUI_ListChildrenMainSizeOption_Create()
```

**Description**


Creates a **ListChildrenMainSize** instance.

**Since:** 12

**Returns**

| Type                             | Description|
|---------------------------------| -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* | Pointer to the **ListChildrenMainSize** instance.|

### OH_ArkUI_ListChildrenMainSizeOption_Dispose()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Dispose(ArkUI_ListChildrenMainSize* option)
```

**Description**


Disposes of a **ListChildrenMainSize** instance.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance to dispose of.|

### OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_SetDefaultMainSize(ArkUI_ListChildrenMainSize* option, float defaultMainSize)
```

**Description**


Sets the default size of the list item in the [List](./arkui-ts/ts-container-list.md) component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance.|
| float defaultMainSize | Default size of the list item along the main axis, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetDefaultMainSize(ArkUI_ListChildrenMainSize* option)
```

**Description**


Obtains the default size of the list item in the [List](./arkui-ts/ts-container-list.md) component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance.|

**Returns**

| Type| Description|
| -- | -- |
| float | Default size of the list item along the main axis. The default value is **0**. The unit is [vp](../apis-arkui/arkui-ts/ts-types.md#vp10). If **option** is a null pointer, **-1** is returned.|

### OH_ArkUI_ListChildrenMainSizeOption_Resize()

```c
void OH_ArkUI_ListChildrenMainSizeOption_Resize(ArkUI_ListChildrenMainSize* option, int32_t totalSize)
```

**Description**


Adjusts the capacity of the child item size array in the [List](./arkui-ts/ts-container-list.md) component along the main axis.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance.|
| int32_t totalSize | Capacity of the target array.|

### OH_ArkUI_ListChildrenMainSizeOption_Splice()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_Splice(ArkUI_ListChildrenMainSize* option, int32_t index, int32_t deleteCount, int32_t addCount)
```

**Description**


Adjusts the child item size array in the [List](./arkui-ts/ts-container-list.md) component along the main axis.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance.|
| int32_t index | Start index.|
| int32_t deleteCount | Number of elements to be deleted from the start position.|
| int32_t addCount | Number of elements to be added from the start position.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ListChildrenMainSizeOption_UpdateSize()

```c
int32_t OH_ArkUI_ListChildrenMainSizeOption_UpdateSize(ArkUI_ListChildrenMainSize* option, int32_t index, float mainSize)
```

**Description**


Updates the size at the specified index in the child item size array of the [List](./arkui-ts/ts-container-list.md) component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance.|
| int32_t index | Array index of the target element.|
| float mainSize | Size along the main axis, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_ListChildrenMainSizeOption_GetMainSize()

```c
float OH_ArkUI_ListChildrenMainSizeOption_GetMainSize(ArkUI_ListChildrenMainSize* option, int32_t index)
```

**Description**


Obtains the size at the specified index in the child item size array of the [List](./arkui-ts/ts-container-list.md) component along the main axis. The vertical direction indicates the height, and the horizontal direction indicates the width.

**Since:** 12


**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_ListChildrenMainSize](capi-arkui-nativemodule-arkui-listchildrenmainsize.md)* option | Pointer to the **ListChildrenMainSize** instance.|
| int32_t index | Array index of the target element.|

**Returns**

| Type| Description|
| -- | -- |
| float | Value at the specified index. If a parameter error occurs, **-1** is returned.|
