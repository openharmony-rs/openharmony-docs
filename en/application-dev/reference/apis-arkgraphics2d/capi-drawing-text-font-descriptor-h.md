# drawing_text_font_descriptor.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Overview

This file declares the capabilities of font information, such as obtaining font information and searching for a font.

**File to include**: <native_drawing/drawing_text_font_descriptor.h>

**Library**: libnative_drawing.so

**Since**: 14

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_SystemFontType](#oh_drawing_systemfonttype) | OH_Drawing_SystemFontType | Defines an enum for the system font types.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_FontDescriptor* OH_Drawing_MatchFontDescriptors(OH_Drawing_FontDescriptor* desc, size_t* num)](#oh_drawing_matchfontdescriptors) | Obtains all system font descriptors that match a font descriptor. In the [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) struct, the **path** field is not used for matching, and other fields are valid only when they are not set to their default values.<br>If all fields in **desc** are set to their default values, all system font descriptors are returned.<br>If no matching is found, NULL is returned. Call [OH_Drawing_DestroyFontDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontdescriptors) to release this pointer when the object is no longer needed.|
| [void OH_Drawing_DestroyFontDescriptors(OH_Drawing_FontDescriptor* descriptors, size_t num)](#oh_drawing_destroyfontdescriptors) | Releases an array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects.|
| [OH_Drawing_FontDescriptor* OH_Drawing_GetFontDescriptorByFullName(const OH_Drawing_String* fullName,OH_Drawing_SystemFontType fontType)](#oh_drawing_getfontdescriptorbyfullname) | Obtains a font descriptor based on the font name and type. System fonts, style fonts, and user-installed fonts are supported.<br>A font descriptor is a data structure that describes font features. It contains details of the font appearance and properties.|
| [OH_Drawing_Array* OH_Drawing_GetSystemFontFullNamesByType(OH_Drawing_SystemFontType fontType)](#oh_drawing_getsystemfontfullnamesbytype) | Obtains an array of font names by font type.|
| [const OH_Drawing_String* OH_Drawing_GetSystemFontFullNameByIndex(OH_Drawing_Array* fullNameArray, size_t index)](#oh_drawing_getsystemfontfullnamebyindex) | Obtains the font name with the specified index in the font name array.|
| [void OH_Drawing_DestroySystemFontFullNames(OH_Drawing_Array* fullNameArray)](#oh_drawing_destroysystemfontfullnames) | Releases the memory occupied by the font name array obtained by font type.|

## Enum Description

### OH_Drawing_SystemFontType

```
enum OH_Drawing_SystemFontType
```

**Description**

Defines an enum for the system font types.

**Since**: 14

| Value| Description|
| -- | -- |
| ALL = 1 << 0 | All font types.|
| GENERIC = 1 << 1 | System font type.|
| STYLISH = 1 << 2 | Style font type.|
| INSTALLED = 1 << 3 | User-installed font type.|
| CUSTOMIZED = 1 << 4 | Custom font type.<br> **Since**: 18|

## Function Description

### OH_Drawing_MatchFontDescriptors()

```
OH_Drawing_FontDescriptor* OH_Drawing_MatchFontDescriptors(OH_Drawing_FontDescriptor* desc, size_t* num)
```

**Description**

Obtains all system font descriptors that match a font descriptor. In the [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) struct, the **path** field is not used for matching, and other fields are valid only when they are not set to their default values.<br>If all fields in **desc** are set to their default values, all system font descriptors are returned.<br>If no matching is found, NULL is returned. Call [OH_Drawing_DestroyFontDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontdescriptors) to release this pointer when the object is no longer needed.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md)* desc | Pointer.<br>You are advised to use [OH_Drawing_CreateFontDescriptor](capi-drawing-text-typography-h.md#oh_drawing_createfontdescriptor) to obtain a valid [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) instance.<br>For an [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) instance created by yourself, ensure that the fields that are not used for matching are set to default values.|
| size_t* num | Pointer to the number of elements in the array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md)* | An array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects. Use [OH_Drawing_DestroyFontDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontdescriptors) to release the array.|

### OH_Drawing_DestroyFontDescriptors()

```
void OH_Drawing_DestroyFontDescriptors(OH_Drawing_FontDescriptor* descriptors, size_t num)
```

**Description**

Releases an array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md)* descriptors | Array.|
| size_t num | Number of members in an array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects.|

### OH_Drawing_GetFontDescriptorByFullName()

```
OH_Drawing_FontDescriptor* OH_Drawing_GetFontDescriptorByFullName(const OH_Drawing_String* fullName,OH_Drawing_SystemFontType fontType)
```

**Description**

Obtains a font descriptor based on the font name and type. System fonts, style fonts, and user-installed fonts are supported.<br>A font descriptor is a data structure that describes font features. It contains details of the font appearance and properties.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_String](capi-drawing-oh-drawing-string.md)* fullName | Pointer to the font name, which is [OH_Drawing_String](capi-drawing-oh-drawing-string.md).|
| [OH_Drawing_SystemFontType](#oh_drawing_systemfonttype) fontType | Enum for the system font types, which is [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md)* | Pointer to an [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) object. Call [OH_Drawing_DestroyFontDescriptor](capi-drawing-text-typography-h.md#oh_drawing_destroyfontdescriptor) to release this pointer when the object is no longer needed.|

### OH_Drawing_GetSystemFontFullNamesByType()

```
OH_Drawing_Array* OH_Drawing_GetSystemFontFullNamesByType(OH_Drawing_SystemFontType fontType)
```

**Description**

Obtains an array of font names by font type.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_SystemFontType](#oh_drawing_systemfonttype) fontType | Enum for the system font types, which is [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* | Returns the pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object of the corresponding font type. Call [OH_Drawing_DestroySystemFontFullNames](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroysystemfontfullnames) to release this pointer when the object is no longer needed.|

### OH_Drawing_GetSystemFontFullNameByIndex()

```
const OH_Drawing_String* OH_Drawing_GetSystemFontFullNameByIndex(OH_Drawing_Array* fullNameArray, size_t index)
```

**Description**

Obtains the font name with the specified index in the font name array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* fullNameArray | Pointer to an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|
| size_t index | Index of the font in the array.|

**Returns**

| Type| Description|
| -- | -- |
| const [OH_Drawing_String](capi-drawing-oh-drawing-string.md)* | Returns the pointer to the font name, which is an [OH_Drawing_String](capi-drawing-oh-drawing-string.md) object.|

### OH_Drawing_DestroySystemFontFullNames()

```
void OH_Drawing_DestroySystemFontFullNames(OH_Drawing_Array* fullNameArray)
```

**Description**

Releases the memory occupied by the font name array obtained by font type.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* fullNameArray | Pointer to an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|


