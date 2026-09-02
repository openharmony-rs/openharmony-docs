# picker.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=730cf983570c1d7d7d25392911a45e3269fd9c72 translatedAt=2026-08-27T08:54:52.888Z pushedAt=2026-08-28T06:31:12.616Z -->

## Overview

> Defines **Picker** node types for **NativeNode** APIs, which support various picker components including the date picker and text picker. It is applicable to scenarios requiring scroll‑selection implementation at the native layer. It provides rich style configuration and data‑linkage capabilities for you to flexibly construct diverse selection interactions.

**File to include:** <arkui/node_attributes/picker.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) | ARKUI_TextPickerRangeContent | Defines the image resource for a single-column text picker.|
| [ARKUI_TextPickerCascadeRangeContent](capi-arkui-nativemodule-arkui-textpickercascaderangecontent.md) | ARKUI_TextPickerCascadeRangeContent | Defines a multi-column cascading text picker.|
| [ArkUI_PickerIndicatorBackground](capi-arkui-nativemodule-arkui-pickerindicatorbackground.md) | ArkUI_PickerIndicatorBackground | Defines the style parameter of the background-style indicator.|
| [ArkUI_PickerIndicatorDivider](capi-arkui-nativemodule-arkui-pickerindicatordivider.md) | ArkUI_PickerIndicatorDivider | Defines the style parameter of the divider-style indicator.|
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) | ArkUI_PickerIndicatorStyle | Defines the style of the selected item indicator.|
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) | ArkUI_TextPickerRangeContentArray | Defines the data list for the text picker.|
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) | ArkUI_TextCascadePickerRangeContentArray | Defines the list for a multi-column cascading picker.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_DatePickerMode](#arkui_datepickermode) | ArkUI_DatePickerMode | Enumerates the column display modes of the date picker.|
| [ArkUI_TextPickerRangeType](#arkui_textpickerrangetype) | ArkUI_TextPickerRangeType | Enumerates the types of the text picker.|
| [ArkUI_CalendarAlignment](#arkui_calendaralignment) | ArkUI_CalendarAlignment | Enumerates the alignment modes between the calendar picker and the entry component.|
| [ArkUI_PickerIndicatorType](#arkui_pickerindicatortype) | ArkUI_PickerIndicatorType | Enumerates the indicator types of the selected item.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | Creates a **TextPickerRangeContent** array object, which is used to construct the data list of a single-column sliding data picker, commonly seen in scenarios such as date selection, time selection, and list selection. After creation, you must call **OH_ArkUI_TextPickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | Sets the icon data at the specified position of the **TextPickerRangeContent** array, which is used to set options with icons in a single-column text picker, commonly seen in scenarios such as mixed text-and-image lists and option lists with icon hints. |
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | Sets the text data at the specified position of the **TextPickerRangeContent** array, which is used to set the text content in a data picker. This is an essential step for constructing picker options. |
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | Destroys a **TextPickerRangeContent** array object. This API must be used in pair with **OH_ArkUI_TextPickerRangeContentArray_Create** to release the created array object resources. |
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | Creates a **TextCascadePickerRangeContent** array object, which is used to construct a multi-column cascade data picker, commonly seen in scenarios such as year-month-day linkage selection and province-city-district three-level linkage selection. After creation, you must call **OH_ArkUI_TextCascadePickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | Sets the text data at the specified position of the **TextCascadePickerRangeContent** array, which is used to set the text content of a multi-column cascade picker. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | Sets the child data at the specified position of the **TextCascadePickerRangeContent** array, which is used to set the child-level data of a multi-column cascade picker to implement the linkage effect. |
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy (ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | Destroys a **TextCascadePickerRangeContent** array object. This API must be used in pair with **OH_ArkUI_TextCascadePickerRangeContentArray_Create** to release the created array object resources. |
| [ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | Creates a style instance of the selected item indicator, which is used to highlight the option currently selected by the user and improve the user interaction experience. After creation, you must call **OH_ArkUI_PickerIndicatorStyle_Dispose** to release resources after use; otherwise, a memory leak occurs. |
| [void  OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | Disposes of a style instance of the selected item indicator. This API must be used in pair with **OH_ArkUI_PickerIndicatorStyle_Create** to release the created style instance resources. |

## Enumeration Description

### ArkUI_DatePickerMode

```c
enum ArkUI_DatePickerMode
```

**Description**

Enumerates the column display modes of the date picker.

**Since:** 18

| Value| Description|
| -- | -- |
| ARKUI_DATEPICKER_MODE_DATE = 0 | Default value. The date displays three columns for year, month, and day. It is applicable to scenarios that require complete date information, such as birth date selection and appointment date selection. |
| ARKUI_DATEPICKER_YEAR_AND_MONTH = 1 | The date displays two columns for year and month. It is applicable to scenarios that require only year and month information, such as credit card expiration date selection and contract term selection. |
| ARKUI_DATEPICKER_MONTH_AND_DAY = 2 | The date displays two columns for month and day. It is applicable to scenarios that require only month and day information, such as birth date selection (without regard to the year) and anniversary selection. |

### ArkUI_TextPickerRangeType

```c
enum ArkUI_TextPickerRangeType
```

**Description**

Enumerates the types of the text picker.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0 | Single-column data picker, applicable to single-column data selection scenarios such as gender selection and education level selection. |
| ARKUI_TEXTPICKER_RANGETYPE_MULTI = 1 | Multi-column data picker, applicable to multi-column independent data selection scenarios such as time selection (hour, minute, second) and date selection (year, month, day). |
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT = 2 | Single-column data picker that supports image resources, applicable to single-column data selection scenarios with icons, such as city selection (with national flag icons) and product category selection. |
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT = 3 | Multi-column data picker that supports linkage, applicable to multi-column linkage data selection scenarios such as province-city-district three-level linkage selection and year-month-day linkage selection. |

### ArkUI_CalendarAlignment

```c
enum ArkUI_CalendarAlignment
```

**Description**

Enumerates the alignment modes between the calendar picker and the entry component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_CALENDAR_ALIGNMENT_START = 0 | Sets the alignment mode of the picker and entry component to left-aligned. |
| ARKUI_CALENDAR_ALIGNMENT_CENTER = 1 | Sets the alignment mode of the picker and entry component to center-aligned. |
| ARKUI_CALENDAR_ALIGNMENT_END = 2 | Sets the alignment mode of the picker and entry component to right-aligned. |

### ArkUI_PickerIndicatorType

``` c
enum ArkUI_PickerIndicatorType
```

**Description**

Enumerates the indicator types of the selected item.

**Since:** 23

| Value| Description|
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND  = 0 | Background style, applicable to scenarios such as dark-themed pickers and form selection that needs to highlight the selected item. |
| ARKUI_PICKER_INDICATOR_DIVIDER  = 1 | Divider style, applicable to scenarios such as lightweight pickers and divider-style UI design. |

## Functions

### OH_ArkUI_TextPickerRangeContentArray_Create()

```c
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```

**Description**

> Creates an [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) array object, which is used to construct the data list of a single-column sliding data picker, commonly seen in scenarios such as date selection, time selection, and list selection. After creation, you must call **OH_ArkUI_TextPickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| int32_t length | Length of the **ArkUI_TextPickerRangeContentArray** array. The value must be greater than 0. A null pointer is returned if a non-positive integer is passed in or creation fails. |

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* | Pointer to the **ArkUI_TextPickerRangeContentArray** array object (the array length is specified by the **length** parameter). If a null pointer is returned, the creation fails. |

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**Description**

Sets the icon data at the specified position of the **ArkUI_TextPickerRangeContentArray** array, which is used to set options with icons in a single-column text picker, commonly seen in scenarios such as mixed text-and-image lists and option lists with icon hints.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **ArkUI_TextPickerRangeContentArray** array, which must first be created through **OH_ArkUI_TextPickerRangeContentArray_Create**. |
| char* icon | Pointer to the icon path, which supports a relative path or an absolute path. A relative path is relative to the application resource directory. The path must point to a valid icon resource file. |
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. |

### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

Sets the text data at the specified position of the **ArkUI_TextPickerRangeContentArray** array, which is used to set the text content in a data picker. This is an essential step for constructing picker options. This API is commonly used in scenarios such as setting date text in a date picker, setting city names in a city picker, and setting category names in a product category picker.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **ArkUI_TextPickerRangeContentArray** array, which must first be created through **OH_ArkUI_TextPickerRangeContentArray_Create**. |
| char* text | Pointer to the text content.|
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. |

### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)
```

**Description**

Destroys the **ArkUI_TextPickerRangeContentArray** array object. This API must be used in pair with **OH_ArkUI_TextPickerRangeContentArray_Create** to release the created array object resources.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **ArkUI_TextPickerRangeContentArray** array. |

### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```c
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)
```

**Description**

> Creates an [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) array object, which is used to construct a multi-column cascade data picker, commonly seen in scenarios such as year-month-day linkage selection and province-city-district three-level linkage selection. After creation, you must call **OH_ArkUI_TextCascadePickerRangeContentArray_Destroy** to release resources after use; otherwise, a memory leak occurs.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| int32_t length | Length of the **ArkUI_TextCascadePickerRangeContentArray** array. The value must be greater than 0. |

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* | Pointer to the **ArkUI_TextCascadePickerRangeContentArray** array object (the array length is specified by the **length** parameter). If a null pointer is returned, the creation fails. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

> Sets the text data at the specified position of the **ArkUI_TextCascadePickerRangeContentArray** array, which is used to set the text content of a multi-column cascade picker. This API is commonly used in scenarios such as setting province names in a province-city-district three-level cascade picker, setting years in a year-month-day cascade picker, and setting brand names in a brand-vehicle model cascade picker.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the  **ArkUI_TextCascadePickerRangeContentArray** array, which must first be created through **OH_ArkUI_TextCascadePickerRangeContentArray_Create**. |
| char* text | Pointer to the text content.|
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. |

### OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)
```

**Description**

Sets the child data at the specified position of the **ArkUI_TextCascadePickerRangeContentArray** array, which is used to set the child-level data of a multi-column cascade picker to implement the linkage effect. This API is commonly used in scenarios such as setting the city-level data corresponding to a province in a province-city-district three-level cascade picker, setting the date data corresponding to a month in a year-month-day cascade picker, and setting the model list corresponding to a brand in a brand-vehicle model cascade picker.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the  **ArkUI_TextCascadePickerRangeContentArray** array, which must first be created through **OH_ArkUI_TextCascadePickerRangeContentArray_Create**. |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* child | Pointer to the child data list at the specified position of the cascade picker, which must first be created through **OH_ArkUI_TextCascadePickerRangeContentArray_Create**. |
| int32_t index | Array index, with a value range of [0, Array length - 1], starting from 0. The value is not effective when out of range. |

### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)
```

**Description**

Destroys the **ArkUI_TextCascadePickerRangeContentArray** array object. This API must be used in pair with **OH_ArkUI_TextCascadePickerRangeContentArray_Create** to release the created array object resources.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the  **ArkUI_TextCascadePickerRangeContentArray** array. |

### OH_ArkUI_PickerIndicatorStyle_Create()

``` c
ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)
```

**Description**

Creates a style instance of the selected item indicator, which is used to highlight the option currently selected by the user and improve the user interaction experience. After creation, you must call **OH_ArkUI_PickerIndicatorStyle_Dispose** to release resources after use; otherwise, a memory leak occurs.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorType](#arkui_pickerindicatortype) type | Type of the selected item indicator in the picker. |

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* | Pointer to the **ArkUI_PickerIndicatorStyle** instance. If a null pointer is returned, the creation fails. The failure may be caused by a full address space or an unsupported type. |

### OH_ArkUI_PickerIndicatorStyle_Dispose()

``` c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**Description**

Disposes of the style instance of the selected item indicator. This API must be used in pair with **OH_ArkUI_PickerIndicatorStyle_Create** to release the created style instance resources.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | Pointer to the [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance to be disposed of.|
