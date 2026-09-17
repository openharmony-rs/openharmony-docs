# picker.h

## Overview

Defines **Picker** node types for **NativeNode** APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) | ARKUI_TextPickerRangeContent | Defines the option content supported by the single-column text picker, including text and image resources. |
| [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md) | ARKUI_TextPickerCascadeRangeContent | Defines a multi-column cascade picker. |
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) | ArkUI_PickerIndicatorBackground | Defines the style parameter of the background-style indicator of the selected item. |
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md) | ArkUI_PickerIndicatorDivider | Defines the style parameter of the divider-style indicator. |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | ArkUI_PickerIndicatorStyle | Defines the style of the selected item indicator. |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | ArkUI_TextPickerRangeContentArray | Defines the data list for the text picker. |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | ArkUI_TextCascadePickerRangeContentArray | Defines an array of multi-column cascade pickers. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_DatePickerMode](#arkui_datepickermode) | ArkUI_DatePickerMode | Enumerates the column display modes of the date picker. |
| [ArkUI_TextPickerRangeType](#arkui_textpickerrangetype) | ArkUI_TextPickerRangeType | Enumerates the types of the text picker. |
| [ArkUI_CalendarAlignment](#arkui_calendaralignment) | ArkUI_CalendarAlignment | Enumerates the alignment modes between the calendar picker and the entry component. |
| [ArkUI_PickerIndicatorType](#arkui_pickerindicatortype) | ArkUI_PickerIndicatorType | Enumerates the indicator types of the selected item. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | Creates an object of the {@link TextPickerRangeContent} array. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | Configures the icon data at a specified position in the **TextPickerRangeContent** array. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | Configures the text data at a specified position in the **TextPickerRangeContent** array. |
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | Destroys a **TextPickerRangeContent** array object. |
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | Creates an object of the {@link TextCascadePickerRangeContent} array. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | Configures the text data at a specified position in the **TextCascadePickerRangeContent** array. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | Configures the child data at a specified position in the **TextCascadePickerRangeContent** array. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | Destroys a **TextCascadePickerRangeContent** array object. |
| [ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | Creates a style instance of the selected item indicator. |
| [void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | Disposes of the style instance of the selected item indicator. |

## Enum type description

### ArkUI_DatePickerMode

```c
enum ArkUI_DatePickerMode
```

**Description**

Enumerates the column display modes of the date picker.

**Since**: 18

| Enum item | Description |
| -- | -- |
| ARKUI_DATEPICKER_MODE_DATE = 0 |  |
| ARKUI_DATEPICKER_YEAR_AND_MONTH = 1 |  |
| ARKUI_DATEPICKER_MONTH_AND_DAY = 2 |  |

### ArkUI_TextPickerRangeType

```c
enum ArkUI_TextPickerRangeType
```

**Description**

Enumerates the types of the text picker.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0 |  |
| ARKUI_TEXTPICKER_RANGETYPE_MULTI = 1 |  |
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT = 2 |  |
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT = 3 |  |

### ArkUI_CalendarAlignment

```c
enum ArkUI_CalendarAlignment
```

**Description**

Enumerates the alignment modes between the calendar picker and the entry component.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_CALENDAR_ALIGNMENT_START = 0 |  |
| ARKUI_CALENDAR_ALIGNMENT_CENTER = 1 |  |
| ARKUI_CALENDAR_ALIGNMENT_END = 2 |  |

### ArkUI_PickerIndicatorType

```c
enum ArkUI_PickerIndicatorType
```

**Description**

Enumerates the indicator types of the selected item.

**Since**: 23

| Enum item | Description |
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND = 0 |  |
| ARKUI_PICKER_INDICATOR_DIVIDER = 1 |  |


## Function description

### OH_ArkUI_TextPickerRangeContentArray_Create()

```c
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```

**Description**

Creates an object of the {@link TextPickerRangeContent} array.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t length | Length of the **TextPickerRangeContent** array. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray*](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | Pointer to an empty TextPickerRangeContent array. |

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**Description**

Configures the icon data at a specified position in the **TextPickerRangeContent** array.

> **Note**:
>
> If an icon was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array. |
| char* icon | Pointer to the icon path. |
| int32_t index | Array index, starting from 0. |

### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

Configures the text data at a specified position in the **TextPickerRangeContent** array.

> **Note**:
>
> If text was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array. |
| char* text | Pointer to the text content. |
| int32_t index | Position in the array, starting from 0. |

### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)
```

**Description**

Destroys a **TextPickerRangeContent** array object.

> **Note**:
>
> After this call, <b>handle</b> must not be used. Do not pass pointers that were not returned by [OH_ArkUI_TextPickerRangeContentArray_Create](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_create).

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array. |

### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```c
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)
```

**Description**

Creates an object of the {@link TextCascadePickerRangeContent} array.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t length | Length of the **TextPickerRangeContent** array. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray*](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | Pointer to an empty TextCascadePickerRangeContent array. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

Configures the text data at a specified position in the **TextCascadePickerRangeContent** array.

> **Note**:
>
> If text was already set at <b>index</b>, the previous buffer is released before assigning the new value.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance. |
| char* text | Pointer to the text content. |
| int32_t index | Position in the array, starting from 0. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)
```

**Description**

Configures the child data at a specified position in the **TextCascadePickerRangeContent** array.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance. |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* child | Pointer to the child node array. |
| int32_t index | Position in the array, starting from 0. |

### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)
```

**Description**

Destroys a **TextCascadePickerRangeContent** array object.

> **Note**:
>
> Do not call [OH_ArkUI_TextCascadePickerRangeContentArray_Destroy](capi-picker-h.md#oh_arkui_textcascadepickerrangecontentarray_destroy) on a <b>child</b> while it is still stored in a parent's {@code children}.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance. |

### OH_ArkUI_PickerIndicatorStyle_Create()

```c
ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)
```

**Description**

Creates a style instance of the selected item indicator.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PickerIndicatorType](capi-picker-h.md#arkui_pickerindicatortype) type | Type of the selected item indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_PickerIndicatorStyle*](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | Pointer to the [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance. If a null pointer is returned, the creation      fails. The possible cause is that the address space is full or the type is not supported. |

### OH_ArkUI_PickerIndicatorStyle_Dispose()

```c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**Description**

Disposes of the style instance of the selected item indicator.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | Pointer to the [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance to be disposed of. |


