# grid.h

## Overview

Provides Grid-related type and function definitions for <b>NativeNode</b> APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_GridItemSize](capi-arkui-nativemodule-arkui-griditemsize.md) | ArkUI_GridItemSize | Defines the return value for the **onGetIrregularSizeByIndex** callback in **Grid** layout options. |
| [ArkUI_GridItemRect](capi-arkui-nativemodule-arkui-griditemrect.md) | ArkUI_GridItemRect | Defines the return value for the **onGetRectByIndex** callback in **Grid** layout options. |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) | ArkUI_GridLayoutOptions | Defines the **Grid** layout options. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_GridItemAlignment](#arkui_griditemalignment) | ArkUI_GridItemAlignment | Enumerates the alignment modes of the {@link GridItem} component. |
| [ArkUI_GridItemStyle](#arkui_griditemstyle) | ArkUI_GridItemStyle | Enumerates styles of grid items. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()](#oh_arkui_gridlayoutoptions_create) | Creates **Grid** layout options. |
| [void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)](#oh_arkui_gridlayoutoptions_dispose) | Disposes of the **Grid** layout option. |
| [int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)](#oh_arkui_gridlayoutoptions_setirregularindexes) | Sets the irregular grid item index array for the grid layout. |
| [int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)](#oh_arkui_gridlayoutoptions_getirregularindexes) | Obtains the irregular grid item index array for the grid layout. When **<br>OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback** is not set, the grid item specified in this parameter occupies an entire row of the grid that scrolls vertically or an entire column of the grid that scrolls horizontally. |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetirregularsizebyindexcallback) | Registers a callback to obtain the row and column span for the grid item at the specified index. |
| [void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (\*callback)(int32_t itemIndex, void* userData))](#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback) | Registers a callback to obtain the starting row, starting column, row span, and column span for the grid item at the specified index. |

## Enum type description

### ArkUI_GridItemAlignment

```c
enum ArkUI_GridItemAlignment
```

**Description**

Enumerates the alignment modes of the {@link GridItem} component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

| Enum item | Description |
| -- | -- |
| GRID_ITEM_ALIGNMENT_DEFAULT = 0 | Use the default alignment mode of the grid. |
| GRID_ITEM_ALIGNMENT_STRETCH = 1 | Use the height of the tallest grid item in a row as the height for all other grid items in that row. |

### ArkUI_GridItemStyle

```c
enum ArkUI_GridItemStyle
```

**Description**

Enumerates styles of grid items.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

| Enum item | Description |
| -- | -- |
| GRID_ITEM_STYLE_NONE = 0 | No style. |
| GRID_ITEM_STYLE_PLAIN = 1 | Hover or press style. |


## Function description

### OH_ArkUI_GridLayoutOptions_Create()

```c
ArkUI_GridLayoutOptions* OH_ArkUI_GridLayoutOptions_Create()
```

**Description**

Creates **Grid** layout options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_GridLayoutOptions*](capi-arkui-nativemodule-arkui-gridlayoutoptions.md) | Pointer to the Grid layout option. |

### OH_ArkUI_GridLayoutOptions_Dispose()

```c
void OH_ArkUI_GridLayoutOptions_Dispose(ArkUI_GridLayoutOptions* option)
```

**Description**

Disposes of the **Grid** layout option.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Pointer to the **Grid** layout option. |

### OH_ArkUI_GridLayoutOptions_SetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_SetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t size)
```

**Description**

Sets the irregular grid item index array for the grid layout.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Pointer to the **Grid** layout option. |
| uint32_t* irregularIndexes | Pointer to the **GridItem** index array. |
| int32_t size | Size of the **GridItem** index array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <ul>      <li><br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.</li>      <li><br>A possible cause is that mandatory parameters are left unspecified.</li>      </ul> |

### OH_ArkUI_GridLayoutOptions_GetIrregularIndexes()

```c
int32_t OH_ArkUI_GridLayoutOptions_GetIrregularIndexes(ArkUI_GridLayoutOptions* option, uint32_t* irregularIndexes, int32_t* size)
```

**Description**

Obtains the irregular grid item index array for the grid layout. When **<br>OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback** is not set, the grid item specified in this parameter occupies an entire row of the grid that scrolls vertically or an entire column of the grid that scrolls horizontally.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_GridLayoutOptions](capi-arkui-nativemodule-arkui-gridlayoutoptions.md)* option | Pointer to the **Grid** layout option. |
| uint32_t* irregularIndexes | Pointer to the **GridItem** index array. |
| int32_t* size | Size of the **GridItem** index array. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code.      <ul>      <li><br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs.</li><br>    <li><br>Returns {@link ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR} if the buffer size is insufficient.</li>      <li><br>A possible cause is that mandatory parameters are left unspecified.</li>      </ul> |

### OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemSize (*callback)(int32_t itemIndex, void* userData))
```

**Description**

Registers a callback to obtain the row and column span for the grid item at the specified index.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_GridLayoutOptions\* option | Pointer to the **Grid** layout option. |
| void\* userData | Pointer to the user-defined data. |
| ArkUI_GridItemSize (\*callback)(int32_t itemIndex | Callback that returns the row and column span for the grid item at the specified index. itemIndex: grid item index, which must be within the range set by [OH_ArkUI_GridLayoutOptions_SetIrregularIndexes](capi-grid-h.md#oh_arkui_gridlayoutoptions_setirregularindexes). |

### OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback()

```c
void OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback(ArkUI_GridLayoutOptions* option, void* userData, ArkUI_GridItemRect (*callback)(int32_t itemIndex, void* userData))
```

**Description**

Registers a callback to obtain the starting row, starting column, row span, and column span for the grid item at the specified index.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| rkUI_GridLayoutOptions\* option | Pointer to the **Grid** layout option. |
| void\* userData | Pointer to the user-defined data. |
| ArkUI_GridItemRect (\*callback)(int32_t itemIndex | Callback that returns the starting row, starting column, row span, and column span for the grid item at the specified index. itemIndex: grid item index. |


