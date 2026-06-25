# picker.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines **Picker** node types for **NativeNode** APIs.

**File to include:** <arkui/picker.h>

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
| [ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)](#oh_arkui_textpickerrangecontentarray_create) | Creates a **TextPickerRangeContent** array object.|
| [void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)](#oh_arkui_textpickerrangecontentarray_seticonatindex) | Configures the icon data at a specified position in the **TextPickerRangeContent** array.|
| [void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textpickerrangecontentarray_settextatindex) | Configures the text data at a specified position in the **TextPickerRangeContent** array.|
| [void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)](#oh_arkui_textpickerrangecontentarray_destroy) | Destroys a **TextPickerRangeContent** array object.|
| [ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)](#oh_arkui_textcascadepickerrangecontentarray_create) | Creates a **TextCascadePickerRangeContent** array object.|
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_settextatindex) | Configures the text data at a specified position in the **TextCascadePickerRangeContent** array.|
| [void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex (ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)](#oh_arkui_textcascadepickerrangecontentarray_setchildatindex) | Configures the child data at a specified position in the **TextCascadePickerRangeContent** array.|
| [void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy (ArkUI_TextCascadePickerRangeContentArray* handle)](#oh_arkui_textcascadepickerrangecontentarray_destroy) | Destroys a **TextCascadePickerRangeContent** array object.|
| [ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)](#oh_arkui_pickerindicatorstyle_create) | Creates a style instance of the selected item indicator.|
| [void  OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)](#oh_arkui_pickerindicatorstyle_dispose) | Disposes of the style instance of the selected item indicator.|

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
| ARKUI_DATEPICKER_MODE_DATE = 0 | Default value. The date displays three columns: year, month, and day.|
| ARKUI_DATEPICKER_YEAR_AND_MONTH = 1 | The date displays two columns: year and month.|
| ARKUI_DATEPICKER_MONTH_AND_DAY = 2 | The date displays two columns: month and day.|

### ArkUI_TextPickerRangeType

```c
enum ArkUI_TextPickerRangeType
```

**Description**

Enumerates the types of the text picker.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXTPICKER_RANGETYPE_SINGLE = 0 | Single-column text picker.|
| ARKUI_TEXTPICKER_RANGETYPE_MULTI = 1 | Multi-column text picker.|
| ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT = 2 | Single-column text picker with image resources.|
| ARKUI_TEXTPICKER_RANGETYPE_CASCADE_RANGE_CONTENT = 3 | Cascading multi-column text picker.|

### ArkUI_CalendarAlignment

```c
enum ArkUI_CalendarAlignment
```

**Description**

Enumerates the alignment modes between the calendar picker and the entry component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_CALENDAR_ALIGNMENT_START = 0 | Left aligned.|
| ARKUI_CALENDAR_ALIGNMENT_CENTER = 1 | Center aligned.|
| ARKUI_CALENDAR_ALIGNMENT_END = 2 | Right aligned.|

### ArkUI_PickerIndicatorType

``` c
enum ArkUI_PickerIndicatorType
```

**Description**

Enumerates the indicator types of the selected item.

**Since:** 23

| Value| Description|
| -- | -- |
| ARKUI_PICKER_INDICATOR_BACKGROUND  = 0 | Background.|
| ARKUI_PICKER_INDICATOR_DIVIDER  = 1 | Divider.|

## Functions

### OH_ArkUI_TextPickerRangeContentArray_Create()

```c
ArkUI_TextPickerRangeContentArray* OH_ArkUI_TextPickerRangeContentArray_Create(int32_t length)
```

**Description**

Creates an object of the [TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md) array.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| int32_t length | Length of the **TextPickerRangeContent** array.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* | Pointer to an empty **TextPickerRangeContent** array.|

### OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* icon, int32_t index)
```

**Description**

Configures the icon data at a specified position in the **TextPickerRangeContent** array.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array.|
| char* icon | Pointer to the icon path.|
| int32_t index | Array index, starting from 0.|

### OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex(ArkUI_TextPickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

Configures the text data at a specified position in the **TextPickerRangeContent** array.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array.|
| char* text | Pointer to the text content.|
| int32_t index | Position in the array, starting from 0.|

### OH_ArkUI_TextPickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextPickerRangeContentArray_Destroy(ArkUI_TextPickerRangeContentArray* handle)
```

**Description**

Destroys a **TextPickerRangeContent** array object.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextPickerRangeContentArray](capi-arkui-nativemodule-arkui-textpickerrangecontentarray.md)* handle | Pointer to the **TextPickerRangeContent** array.|

### OH_ArkUI_TextCascadePickerRangeContentArray_Create()

```c
ArkUI_TextCascadePickerRangeContentArray* OH_ArkUI_TextCascadePickerRangeContentArray_Create(int32_t length)
```

**Description**

Creates an object of the [TextCascadePickerRangeContent](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md) array.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| int32_t length | Length of the **TextPickerRangeContent** array.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* | Pointer to an empty **TextCascadePickerRangeContent** array.|

### OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetTextAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, char* text, int32_t index)
```

**Description**

Configures the text data at a specified position in the **TextCascadePickerRangeContent** array.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance.|
| char* text | Pointer to the text content.|
| int32_t index | Position in the array, starting from 0.|

### OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_SetChildAtIndex(ArkUI_TextCascadePickerRangeContentArray* handle, ArkUI_TextCascadePickerRangeContentArray* child, int32_t index)
```

**Description**

Configures the child data at a specified position in the **TextCascadePickerRangeContent** array.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance.|
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* child | Pointer to the child node array.|
| int32_t index | Position in the array, starting from 0.|

### OH_ArkUI_TextCascadePickerRangeContentArray_Destroy()

```c
void OH_ArkUI_TextCascadePickerRangeContentArray_Destroy(ArkUI_TextCascadePickerRangeContentArray* handle)
```

**Description**

Destroys a **TextCascadePickerRangeContent** array object.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextCascadePickerRangeContentArray](capi-arkui-nativemodule-arkui-textcascadepickerrangecontentarray.md)* handle | Pointer to the **TextCascadePickerRangeContentHandle** instance.|

### OH_ArkUI_PickerIndicatorStyle_Create()

``` c
ArkUI_PickerIndicatorStyle* OH_ArkUI_PickerIndicatorStyle_Create(ArkUI_PickerIndicatorType type)
```

**Description**

Creates a style instance of the selected item indicator.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorType](capi-picker-h.md#arkui_pickerindicatortype) type | Type of the selected item indicator.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* | Pointer to the [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance. If a null pointer is returned, the creation fails. The possible cause is that the address space is full or the type is not supported.|

### OH_ArkUI_PickerIndicatorStyle_Dispose()

``` c
void OH_ArkUI_PickerIndicatorStyle_Dispose(ArkUI_PickerIndicatorStyle* style)
```

**Description**

Disposes of the style instance of the selected item indicator.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md)* style | Pointer to the [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md) instance to be disposed of.|
