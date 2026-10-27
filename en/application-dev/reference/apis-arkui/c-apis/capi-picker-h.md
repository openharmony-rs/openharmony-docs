# picker.h

## Overview

Defines **Picker** node types for **NativeNode** APIs, which support various picker components including the date picker and text picker. It is applicable to scenarios requiring scroll‑selection implementation at the native layer. It provides rich style configuration and data‑linkage capabilities for you to flexibly construct diverse selection interactions.

**Include**: <arkui/node_attributes/picker.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) | ARKUI_TextPickerRangeContent | Defines the image resource supported by a single-column text picker. This struct is used to display both images and text in the **TextPicker** component, and is suitable for scenarios where icons and text combinations need to be displayed in a single-column text picker. It supports custom icon paths and text content. Each item can be set with an independent icon and text, or only one of them, helping you implement flexible image-text picker configurations. |
| [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md) | ARKUI_TextPickerCascadeRangeContent | Defines a multi-column text cascade picker, which describes the hierarchical data structure of the multi- column text cascade picker. This struct forms a tree structure through children members to support multi-level cascade selection. It is suitable for scenarios that require displaying hierarchical data such as province/city/ district and year/month/day, and can simplify the development of the multi-level text cascade picker. |
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) | ArkUI_PickerIndicatorBackground | Defines the style parameter of the background-style indicator of the selected item. The background-style indicator highlights the selected item with a background color and rounded corners, including the background color and corner radius of the selected item.<br>Usage scenarios: |
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md) | ArkUI_PickerIndicatorDivider | Defines the style parameter of the divider-style indicator. This struct supports customizing the stroke width of the divider, color of the divider, and distance between the divider and the container edges. It applies to scenarios where the appearance of the **Picker** control's divider needs to be beautified. You can configure this struct to achieve personalized divider effects, improving the aesthetics of the UI and the user experience. |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | ArkUI_PickerIndicatorStyle | Defines the style of the selected item indicator. It contains attribute configurations such as the indicator color and size, used to enhance the visual effect of the selected item in the **Picker** component and improve the user interaction experience. |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | ArkUI_TextPickerRangeContentArray | Defines the option content array of a text picker. This struct is used to configure the option list of a text picker, setting the icon and text content of each option by index. It applies to scenarios such as date selection, time selection, and list selection that require displaying multiple options for users to select by scrolling. |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | ArkUI_TextCascadePickerRangeContentArray | Defines an option array of a multi-column text cascade picker. This struct is used to configure the hierarchical data of a multi-column text cascade picker, that is, configure the text and child-level data of each column's options through indexes. It is applicable to scenarios that require multi-column data cascade, such as province-city-district cascade and product category selection. |

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
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | Creates an **ArkUI_TextPickerRangeContentArray** array object, which is used to construct the data list of a single-column sliding data picker, commonly seen in scenarios such as date selection, time selection, and list selection. After creation, you must call **OH_ArkUI_TextPickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | Sets the icon data at the specified position of the **ArkUI_TextPickerRangeContentArray** array, which is used to set options with icons in a single-column text picker, commonly seen in scenarios such as mixed text-and- image lists and option lists with icon hints. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | Sets the text data at the specified position of the **ArkUI_TextPickerRangeContentArray** array, which is used to set the text content in a data picker. This is an essential step for constructing picker options. This API is commonly used in scenarios such as setting date text in a date picker, setting city names in a city picker, and setting category names in a product category picker. |
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | Destroys the **ArkUI_TextPickerRangeContentArray** array object. This API must be used in pair with **<br>OH_ArkUI_TextPickerRangeContentArray_Create** to release the created array object resources. |
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | Creates an **ArkUI_TextCascadePickerRangeContentArray** array object, which is used to construct a multi-column cascade data picker, commonly seen in scenarios such as year-month-day linkage selection and province-city-district three-level linkage selection. After creation, you must call **OH_ArkUI_TextCascadePickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | Sets the text data at the specified position of the **ArkUI_TextCascadePickerRangeContentArray** array, which is used to set the text content of a multi-column cascade picker. This API is commonly used in scenarios such as setting province names in a province-city-district three-level cascade picker, setting years in a year-month-day cascade picker, and setting brand names in a brand-vehicle model cascade picker. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | Sets the child data at the specified position of the **ArkUI_TextCascadePickerRangeContentArray** array, which is used to set the child-level data of a multi-column cascade picker to implement the linkage effect. This API is commonly used in scenarios such as setting the city-level data corresponding to a province in a province-city- district three-level cascade picker, setting the date data corresponding to a month in a year-month-day cascade picker, and setting the model list corresponding to a brand in a brand-vehicle model cascade picker. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | Destroys the **ArkUI_TextCascadePickerRangeContentArray** array object. This API must be used in pair with **<br>OH_ArkUI_TextCascadePickerRangeContentArray_Create** to release the created array object resources. |
| [ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | Creates a style instance of the selected item indicator, which is used to highlight the option currently selected by the user and improve the user interaction experience. After creation, you must call **<br>OH_ArkUI_PickerIndicatorStyle_Dispose** to release resources after use; otherwise, a memory leak occurs. |
| [void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | Disposes of the style instance of the selected item indicator. This API must be used in pair with **<br>OH_ArkUI_PickerIndicatorStyle_Create** to release the created style instance resources. |

## Enum type description

### ArkUI_DatePickerMode

```c
enum ArkUI_DatePickerMode
```

**Description**

Enumerates the column display modes of the date picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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

Creates an **ArkUI_TextPickerRangeContentArray** array object, which is used to construct the data list of a single-column sliding data picker, commonly seen in scenarios such as date selection, time selection, and list selection. After creation, you must call **OH_ArkUI_TextPickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Resource release**: OH_ArkUI_TextPickerRangeContentArray_Destroy {return}

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t length | Length of the **ArkUI_TextPickerRangeContentArray** array. The value must be greater than 0. A null pointer is returned if a non-positive integer is passed in or creation fails. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray*](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | Pointer to the **ArkUI_TextPickerRangeContentArray** array object (the array length is specified by the ** length** parameter). If a null pointer is returned, the creation fails. |

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**Description**

Sets the icon data at the specified position of the **ArkUI_TextPickerRangeContentArray** array, which is used to set options with icons in a single-column text picker, commonly seen in scenarios such as mixed text-and- image lists and option lists with icon hints.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **ArkUI_TextPickerRangeContentArray** array, which must first be created through **<br>OH_ArkUI_TextPickerRangeContentArray_Create**. |
| char* icon | Pointer to the icon path, which supports a relative path or an absolute path. A relative path is relative to the application resource directory. The path must point to a valid icon resource file. |
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. If an icon was already set at <b>index</b>, the previous buffer is released before assigning the new value. |

### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

Sets the text data at the specified position of the **ArkUI_TextPickerRangeContentArray** array, which is used to set the text content in a data picker. This is an essential step for constructing picker options. This API is commonly used in scenarios such as setting date text in a date picker, setting city names in a city picker, and setting category names in a product category picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **ArkUI_TextPickerRangeContentArray** array, which must first be created through **<br>OH_ArkUI_TextPickerRangeContentArray_Create**. |
| char* text | Pointer to the text content. |
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. If text was already set at <b>index</b>, the previous buffer is released before assigning the new value. |

### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)
```

**Description**

Destroys the **ArkUI_TextPickerRangeContentArray** array object. This API must be used in pair with **<br>OH_ArkUI_TextPickerRangeContentArray_Create** to release the created array object resources.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **ArkUI_TextPickerRangeContentArray** array. After this call, <b>handle</b> must not be used. Do not pass pointers that were not returned by [OH_ArkUI_TextPickerRangeContentArray_Create](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_create). |

### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```c
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)
```

**Description**

Creates an **ArkUI_TextCascadePickerRangeContentArray** array object, which is used to construct a multi-column cascade data picker, commonly seen in scenarios such as year-month-day linkage selection and province-city-district three-level linkage selection. After creation, you must call **OH_ArkUI_TextCascadePickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Resource release**: OH_ArkUI_TextCascadePickerRangeContentArray_Destroy {return}

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t length | Length of the **ArkUI_TextCascadePickerRangeContentArray** array. The value must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray*](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | Pointer to the **ArkUI_TextCascadePickerRangeContentArray** array object (the array length is specified by the **length** parameter). If a null pointer is returned, the creation fails. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

Sets the text data at the specified position of the **ArkUI_TextCascadePickerRangeContentArray** array, which is used to set the text content of a multi-column cascade picker. This API is commonly used in scenarios such as setting province names in a province-city-district three-level cascade picker, setting years in a year-month-day cascade picker, and setting brand names in a brand-vehicle model cascade picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the  **ArkUI_TextCascadePickerRangeContentArray** array, which must first be created through **OH_ArkUI_TextCascadePickerRangeContentArray_Create**. |
| char* text | Pointer to the text content. |
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. If text was already set at <b>index</b>, the previous buffer is released before assigning the new value. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)
```

**Description**

Sets the child data at the specified position of the **ArkUI_TextCascadePickerRangeContentArray** array, which is used to set the child-level data of a multi-column cascade picker to implement the linkage effect. This API is commonly used in scenarios such as setting the city-level data corresponding to a province in a province-city- district three-level cascade picker, setting the date data corresponding to a month in a year-month-day cascade picker, and setting the model list corresponding to a brand in a brand-vehicle model cascade picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the  **ArkUI_TextCascadePickerRangeContentArray** array, which must first be created through **OH_ArkUI_TextCascadePickerRangeContentArray_Create**. |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* child | Pointer to the child data list at the specified position of the cascade picker, which must first be created through **OH_ArkUI_TextCascadePickerRangeContentArray_Create**. |
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. |

### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)
```

**Description**

Destroys the **ArkUI_TextCascadePickerRangeContentArray** array object. This API must be used in pair with **<br>OH_ArkUI_TextCascadePickerRangeContentArray_Create** to release the created array object resources.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the  **ArkUI_TextCascadePickerRangeContentArray** array. After this call, <b>handle</b> must not be used. Do not pass pointers that were not returned by [OH_ArkUI_TextCascadePickerRangeContentArray_Create](capi-picker-h.md#oh_arkui_textcascadepickerrangecontentarray_create). Do not call [OH_ArkUI_TextCascadePickerRangeContentArray_Destroy](capi-picker-h.md#oh_arkui_textcascadepickerrangecontentarray_destroy) on a <b>child</b> while it is still stored in a parent's {@code children}. |

### OH_ArkUI_PickerIndicatorStyle_Create()

```c
ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)
```

**Description**

Creates a style instance of the selected item indicator, which is used to highlight the option currently selected by the user and improve the user interaction experience. After creation, you must call **<br>OH_ArkUI_PickerIndicatorStyle_Dispose** to release resources after use; otherwise, a memory leak occurs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PickerIndicatorType](capi-picker-h.md#arkui_pickerindicatortype) type | Type of the selected item indicator in the picker. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_PickerIndicatorStyle*](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | Pointer to the **ArkUI_PickerIndicatorStyle** instance. If a null pointer is returned, the creation fails. The failure may be caused by a full address space or an unsupported type. |

### OH_ArkUI_PickerIndicatorStyle_Dispose()

```c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**Description**

Disposes of the style instance of the selected item indicator. This API must be used in pair with **<br>OH_ArkUI_PickerIndicatorStyle_Create** to release the created style instance resources.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | Pointer to the [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance to be disposed of. |


