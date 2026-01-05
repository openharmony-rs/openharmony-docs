# styled_string.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines text styles and layout managers for the ArkUI text component on the native side.

**File to include**: <arkui/styled_string.h>

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[StyledStringSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StyledStringSample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md) | ArkUI_StyledString | Defines a styled string object supported by the text component.|
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md) | ArkUI_TextLayoutManager | Defines a text layout manager.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)](#oh_arkui_styledstring_create) | Creates an **ArkUI_StyledString** object and returns its pointer.|
| [void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)](#oh_arkui_styledstring_destroy) | Destroys an **ArkUI_StyledString** object and reclaims the memory occupied by the object.|
| [void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)](#oh_arkui_styledstring_pushtextstyle) | Pushes a text style to the top of the style stack of a styled string.|
| [void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)](#oh_arkui_styledstring_addtext) | Adds text for a styled string.|
| [void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)](#oh_arkui_styledstring_poptextstyle) | Pops the style at the top of the style stack of a styled string.|
| [OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)](#oh_arkui_styledstring_createtypography) | Creates an **OH_Drawing_Typography** object based on an **ArkUI_StyledString** object.|
| [void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)](#oh_arkui_styledstring_addplaceholder) | Adds a placeholder.|
| [ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)](#oh_arkui_styledstring_descriptor_create) | Creates an **ArkUI_StyledString_Descriptor** object.|
| [void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_styledstring_descriptor_destroy) | Destroys an **ArkUI_StyledString_Descriptor** object and reclaims the memory occupied by the object.|
| [int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_unmarshallstyledstringdescriptor) | Unmarshals a byte array containing styled string information into a styled string.|
| [int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)](#oh_arkui_marshallstyledstringdescriptor) | Marshals the styled string information into a byte array.|
| [const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)](#oh_arkui_converttohtml) | Converts styled string information into HTML.|
| [void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)](#oh_arkui_textlayoutmanager_dispose) | Releases the memory occupied by the text layout manager.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)](#oh_arkui_textlayoutmanager_getlinecount) | Obtains the number of lines.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)](#oh_arkui_textlayoutmanager_getrectsforrange) | Obtains the drawing area information of characters or placeholders within a specified text range under the given rectangle width and height.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)](#oh_arkui_textlayoutmanager_getglyphpositionatcoordinate) | Obtains the position of the glyph closest to the given coordinates.|
| [ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)](#oh_arkui_textlayoutmanager_getlinemetrics) | Obtains the information about the specified line, including line metrics, text style information, and font properties.|

## Function Description

### OH_ArkUI_StyledString_Create()

```c
ArkUI_StyledString* OH_ArkUI_StyledString_Create(OH_Drawing_TypographyStyle* style, OH_Drawing_FontCollection* collection)
```

**Description**

Creates an **ArkUI_StyledString** object and returns its pointer.

**Since**: 12

**Parameters**

| Name| Description                                                                                                                                                              |
| -- |------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [OH_Drawing_TypographyStyle](../apis-arkgraphics2d/capi-drawing-oh-drawing-typographystyle.md)* style | Pointer to an **OH_Drawing_TypographyStyle** object, obtained using [OH_Drawing_CreateTypographyStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_createtypographystyle).|
| [OH_Drawing_FontCollection](../apis-arkgraphics2d/capi-drawing-oh-drawing-fontcollection.md)* collection | Pointer to an **OH_Drawing_FontCollection** object, obtained using [OH_Drawing_CreateFontCollection](../apis-arkgraphics2d/capi-drawing-font-collection-h.md).                                                                                   |

**Return value**

| Type                     | Description|
|-------------------------| -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* | Pointer to the newly created **ArkUI_StyledString** object. If a null pointer is returned, the creation fails. Possible causes include a full application address space or parameter errors, such as a null pointer being passed for the **style** or **collection** parameter.|

### OH_ArkUI_StyledString_Destroy()

```c
void OH_ArkUI_StyledString_Destroy(ArkUI_StyledString* handle)
```

**Description**

Destroys an **ArkUI_StyledString** object and reclaims the memory occupied by the object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|

### OH_ArkUI_StyledString_PushTextStyle()

```c
void OH_ArkUI_StyledString_PushTextStyle(ArkUI_StyledString* handle, OH_Drawing_TextStyle* style)
```

**Description**

Pushes a text style to the top of the style stack of a styled string.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|
| [OH_Drawing_TextStyle](../apis-arkgraphics2d/capi-drawing-oh-drawing-textstyle.md)* style | Pointer to an **OH_Drawing_TextStyle** object.|

### OH_ArkUI_StyledString_AddText()

```c
void OH_ArkUI_StyledString_AddText(ArkUI_StyledString* handle, const char* content)
```

**Description**

Adds text for a styled string.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|
| const char* content | Pointer to the text content.|

### OH_ArkUI_StyledString_PopTextStyle()

```c
void OH_ArkUI_StyledString_PopTextStyle(ArkUI_StyledString* handle)
```

**Description**

Pops the style at the top of the style stack of a styled string.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|

### OH_ArkUI_StyledString_CreateTypography()

```c
OH_Drawing_Typography* OH_ArkUI_StyledString_CreateTypography(ArkUI_StyledString* handle)
```

**Description**

Creates an **OH_Drawing_Typography** object based on an **ArkUI_StyledString** object.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|

**Return value**

| Type                        | Description|
|----------------------------| -- |
| [OH_Drawing_Typography](../apis-arkgraphics2d/capi-drawing-oh-drawing-typography.md)* | Pointer to the **OH_Drawing_Typography** object. If a null pointer is returned, the creation fails. A possible cause is that a parameter error, for example, a null pointer for the **handle** parameter, occurs.|

### OH_ArkUI_StyledString_AddPlaceholder()

```c
void OH_ArkUI_StyledString_AddPlaceholder(ArkUI_StyledString* handle, OH_Drawing_PlaceholderSpan* placeholder)
```

**Description**

Adds a placeholder.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString](capi-arkui-nativemodule-arkui-styledstring.md)* handle | Pointer to an **ArkUI_StyledString** object.|
| [OH_Drawing_PlaceholderSpan](../apis-arkgraphics2d/capi-drawing-oh-drawing-placeholderspan.md)* placeholder | Pointer to an **OH_Drawing_PlaceholderSpan** object.|

### OH_ArkUI_StyledString_Descriptor_Create()

```c
ArkUI_StyledString_Descriptor* OH_ArkUI_StyledString_Descriptor_Create(void)
```

**Description**

Creates an **ArkUI_StyledString_Descriptor** object.

**Since**: 14

**Return value**

| Type                                | Description|
|------------------------------------| -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* | Pointer to an **ArkUI_StyledString_Descriptor** object.|

### OH_ArkUI_StyledString_Descriptor_Destroy()

```c
void OH_ArkUI_StyledString_Descriptor_Destroy(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Destroys an **ArkUI_StyledString_Descriptor** object and reclaims the memory occupied by the object.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|

### OH_ArkUI_UnmarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_UnmarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Unmarshals a byte array containing styled string information into a styled string.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| uint8_t* buffer | Byte array to be deserialized.|
| size_t bufferSize | Length of the byte array.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_MarshallStyledStringDescriptor()

```c
int32_t OH_ArkUI_MarshallStyledStringDescriptor(uint8_t* buffer, size_t bufferSize, ArkUI_StyledString_Descriptor* descriptor, size_t* resultSize)
```

**Description**

Marshals the styled string information into a byte array.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| uint8_t* buffer | Byte array where the serialized data will be stored.|
| size_t bufferSize | Length of the byte array.|
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|
| size_t* resultSize | Actual length of the resulting byte array after deserialization.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>        Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>        Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>        Returns [ARKUI_ERROR_CODE_INVALID_STYLED_STRING](capi-native-type-h.md#arkui_errorcode) if the styled string is invalid.|

### OH_ArkUI_ConvertToHtml()

```c
const char* OH_ArkUI_ConvertToHtml(ArkUI_StyledString_Descriptor* descriptor)
```

**Description**

Converts styled string information into HTML.

**Since**: 14

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_StyledString_Descriptor](capi-arkui-nativemodule-arkui-styledstring-descriptor.md)* descriptor | Pointer to an **ArkUI_StyledString_Descriptor** object.|

**Return value**

| Type| Description|
| -- | -- |
| const char* | HTML object. The pointer is managed internally and should be destroyed by calling **OH_ArkUI_StyledString_Descriptor_Destroy()** when no longer needed to free the memory.|

### OH_ArkUI_TextLayoutManager_Dispose()

```c
void OH_ArkUI_TextLayoutManager_Dispose(ArkUI_TextLayoutManager* layoutManager)
```

**Description**

Releases the memory occupied by the text layout manager.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|

### OH_ArkUI_TextLayoutManager_GetLineCount()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineCount(ArkUI_TextLayoutManager* layoutManager, int32_t* outLineCount)
```

**Description**

Obtains the number of lines.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| int32_t* outLineCount | Number of text lines.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_GetRectsForRange()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetRectsForRange(ArkUI_TextLayoutManager* layoutManager, int32_t start, int32_t end, OH_Drawing_RectWidthStyle widthStyle, OH_Drawing_RectHeightStyle heightStyle, OH_Drawing_TextBox** outTextBoxes)
```

**Description**

Obtains the drawing area information of characters or placeholders within a specified text range under the given rectangle width and height.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| int32_t start | Start index. The value of **start** must be greater than or equal to **0**. Otherwise, a parameter error is returned.|
| int32_t end | End index. The value of **end** must be greater than or equal to that of **start**. Otherwise, aparameter error is returned.|
| [OH_Drawing_RectWidthStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_rectwidthstyle) widthStyle | Width style of the rectangle.|
| [OH_Drawing_RectHeightStyle](../apis-arkgraphics2d/capi-drawing-text-typography-h.md#oh_drawing_rectheightstyle) heightStyle | Height style of the rectangle.|
| [OH_Drawing_TextBox](../apis-arkgraphics2d/capi-drawing-oh-drawing-textbox.md)** outTextBoxes | Level-2 pointer to the **OH_Drawing_TextBox** object.|

**Return value**

| Type| Description|
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|


### OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetGlyphPositionAtCoordinate(ArkUI_TextLayoutManager* layoutManager, double dx, double dy, OH_Drawing_PositionAndAffinity** outPos)
```

**Description**

Obtains the position of the glyph closest to the given coordinates.

**Since**: 22

**Parameters**

| Name| Description|
| ------ | --- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| double dx | X coordinate relative to the control, in px.|
| double dy | Y coordinate relative to the control, in px.|
| [OH_Drawing_PositionAndAffinity](../apis-arkgraphics2d/capi-drawing-oh-drawing-positionandaffinity.md)** outPos | Level-2 pointer to the **OH_Drawing_PositionAndAffinity** object.|

**Return value**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_TextLayoutManager_GetLineMetrics()

```c
ArkUI_ErrorCode OH_ArkUI_TextLayoutManager_GetLineMetrics(ArkUI_TextLayoutManager* layoutManager, int32_t lineNumber, OH_Drawing_LineMetrics* outMetrics)
```

**Description**

Obtains the information about the specified line, including line metrics, text style information, and font properties.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)* layoutManager | Pointer to the **ArkUI_TextLayoutManager** object.|
| int32_t lineNumber | Index of the line number. It starts from **0**. If the value of **lineNumber** is less than **0** or greater than or equal to the number of text lines, a parameter error is returned.|
| [OH_Drawing_LineMetrics](../apis-arkgraphics2d/capi-drawing-oh-drawing-linemetrics.md)* outMetrics | Pointer to the **OH_Drawing_LineMetrics** object.|

**Return value**

| Type| Description|
| ---- | --- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | Return result.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|
