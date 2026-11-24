# drawing_text_font_descriptor.h

## Overview

Defines APIs related to font information, such as obtaining font information, finding and matching specified fonts, reading font descriptor properties, and obtaining Unicode codes and font counts.

**File to Include**: <native_drawing/drawing_text_font_descriptor.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Related module**: [Drawing](capi-arkgraphics2d-drawing.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_FontVariationInstanceCoordinate](capi-drawing-oh-drawing-fontvariationinstancecoordinate.md) | OH_Drawing_FontVariationInstanceCoordinate | Variable font attribute key-value pair. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_SystemFontType](#oh_drawing_systemfonttype) | OH_Drawing_SystemFontType | Defines an enum for the system font types. |
| [OH_Drawing_FontFullDescriptorAttributeId](#oh_drawing_fontfulldescriptorattributeid) | OH_Drawing_FontFullDescriptorAttributeId | Enumerates font descriptor attributes. You can use the corresponding APIs to obtain the attributes of different font descriptor types. For example, if **FULL_DESCRIPTOR_ATTR_I_WEIGHT** is of the int type, use the [OH_Drawing_GetFontFullDescriptorAttributeInt](capi-drawing-text-font-descriptor-h.md#oh_drawing_getfontfulldescriptorattributeint) API to obtain its attribute value. |
| [OH_Drawing_FontVariationAxisAttributeId](#oh_drawing_fontvariationaxisattributeid) | OH_Drawing_FontVariationAxisAttributeId | Enumerates font variable axis attributes. |
| [OH_Drawing_FontVariationInstanceAttributeId](#oh_drawing_fontvariationinstanceattributeid) | OH_Drawing_FontVariationInstanceAttributeId | Enumerates font variable instance attributes. |

### Functions

| Name | Description |
| -- | -- |
| [OH_Drawing_FontDescriptor* OH_Drawing_MatchFontDescriptors(OH_Drawing_FontDescriptor* desc, size_t* num)](#oh_drawing_matchfontdescriptors) | Obtains all system font descriptors that match a font descriptor. In the [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) struct, the **path** field is not used for matching, and other fields are valid only when they are not set to their default values. <br>If all fields in **desc** are set to their default values, all system font descriptors are returned. <br>If no matching is found, NULL is returned. Call [OH_Drawing_DestroyFontDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontdescriptors) to release this pointer when the object is no longer needed. |
| [void OH_Drawing_DestroyFontDescriptors(OH_Drawing_FontDescriptor* descriptors, size_t num)](#oh_drawing_destroyfontdescriptors) | Releases an array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects. |
| [OH_Drawing_FontDescriptor* OH_Drawing_GetFontDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)](#oh_drawing_getfontdescriptorbyfullname) | Obtains the specified font descriptor based on the font name and font type. This API supports system fonts, style fonts, and user-installed fonts. If the acquisition fails, NULL is returned. <br>A font descriptor is a data structure that describes font characteristics. It contains detailed information that defines the appearance and properties of a font. |
| [OH_Drawing_Array* OH_Drawing_GetSystemFontFullNamesByType(OH_Drawing_SystemFontType fontType)](#oh_drawing_getsystemfontfullnamesbytype) | Obtains an array of font names by font type. |
| [const OH_Drawing_String* OH_Drawing_GetSystemFontFullNameByIndex(OH_Drawing_Array* fullNameArray, size_t index)](#oh_drawing_getsystemfontfullnamebyindex) | Obtains the font name at the corresponding position in the font name array by index. If the index is out of range or the array is invalid, NULL is returned. |
| [void OH_Drawing_DestroySystemFontFullNames(OH_Drawing_Array* fullNameArray)](#oh_drawing_destroysystemfontfullnames) | Releases the memory occupied by the font name array obtained by font type. |
| [OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromStream(const void* data, size_t size)](#oh_drawing_getfontfulldescriptorsfromstream) | Obtains the font descriptor array based on the original binary data. |
| [OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromPath(const char* path)](#oh_drawing_getfontfulldescriptorsfrompath) | Obtains an array of font descriptors based on the font file path. |
| [const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByIndex(OH_Drawing_Array* descriptorArray, size_t index)](#oh_drawing_getfontfulldescriptorbyindex) | Obtains the font descriptor from the font descriptor array based on the index. |
| [void OH_Drawing_DestroyFontFullDescriptors(OH_Drawing_Array* descriptorArray)](#oh_drawing_destroyfontfulldescriptors) | Releases the memory occupied by the font descriptor array. |
| [void OH_Drawing_DestroyFontFullDescriptor(const OH_Drawing_FontFullDescriptor* descriptor)](#oh_drawing_destroyfontfulldescriptor) | Releases the memory occupied by the font descriptor pointer. This function can be used to release the font descriptor pointer obtained by the [OH_Drawing_GetFontFullDescriptorByFullName](capi-drawing-text-font-descriptor-h.md#oh_drawing_getfontfulldescriptorbyfullname) API. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromFile(const char* fontSrc, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)](#oh_drawing_getfontunicodearrayfromfile) | Obtains the Unicode code array from a font file. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromBuffer(uint8_t* fontBuffer, size_t length, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)](#oh_drawing_getfontunicodearrayfrombuffer) | Obtains the Unicode code array from a font byte stream buffer. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeInt(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, int* value)](#oh_drawing_getfontfulldescriptorattributeint) | Obtains the attributes of a font descriptor of the int type. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeBool(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, bool* value)](#oh_drawing_getfontfulldescriptorattributebool) | Obtains the font descriptor attribute of the bool type. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeString(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, OH_Drawing_String* str)](#oh_drawing_getfontfulldescriptorattributestring) | Obtains the attributes of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) font descriptor. |
| [OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorAttributeArray(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id)](#oh_drawing_getfontfulldescriptorattributearray) | Obtains the object array attributes of the font descriptor. |
| [OH_Drawing_FontVariationAxis* OH_Drawing_GetFontVariationAxisByIndex(OH_Drawing_Array* array, size_t index)](#oh_drawing_getfontvariationaxisbyindex) | Obtains the corresponding font variable axis from the font variable axis array by index. |
| [void OH_Drawing_DestroyFontVariationAxis(OH_Drawing_Array* fontVariaAxisArray)](#oh_drawing_destroyfontvariationaxis) | Releases the memory occupied by the font variable axis array. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeDouble(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, double *value)](#oh_drawing_getfontvariationaxisattributedouble) | Obtains the font variable axis attributes of the double type. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeInt(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, int *value)](#oh_drawing_getfontvariationaxisattributeint) | Obtains the font variable axis attributes of the int type. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeStr(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, OH_Drawing_String *str)](#oh_drawing_getfontvariationaxisattributestr) | Obtains the font variable axis attributes of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type. |
| [OH_Drawing_FontVariationInstance* OH_Drawing_GetFontVariationInstanceByIndex(OH_Drawing_Array* array, size_t index)](#oh_drawing_getfontvariationinstancebyindex) | Obtains the corresponding font variable instance from the font variable instance array by index. |
| [void OH_Drawing_DestroyFontVariationInstance(OH_Drawing_Array* fontVariaAxisInstance)](#oh_drawing_destroyfontvariationinstance) | Releases the memory occupied by the font variable instance array. |
| [OH_Drawing_ErrorCode OH_Drawing_GetFontVariationInstanceAttributeStr(OH_Drawing_FontVariationInstance* variationInstance, OH_Drawing_FontVariationInstanceAttributeId id, OH_Drawing_String* str)](#oh_drawing_getfontvariationinstanceattributestr) | Obtains the font variable instance attributes of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type. |
| [OH_Drawing_FontVariationInstanceCoordinate* OH_Drawing_GetFontVariationInstanceCoordinate(OH_Drawing_FontVariationInstance* variationInstance, size_t* arrayLength)](#oh_drawing_getfontvariationinstancecoordinate) | Obtains the variable font attribute object of the font variable instance. |
| [const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)](#oh_drawing_getfontfulldescriptorbyfullname) | Obtains the complete font descriptor object based on the font name and type. |
| [uint32_t OH_Drawing_GetFontCountFromFile(const char* fontSrc)](#oh_drawing_getfontcountfromfile) | Obtains the number of fonts contained in a font file. |
| [uint32_t OH_Drawing_GetFontCountFromBuffer(uint8_t* fontBuffer, size_t length)](#oh_drawing_getfontcountfrombuffer) | Obtains the number of fonts contained in a font buffer. |
| [OH_Drawing_String* OH_Drawing_GetFontPathsByType(OH_Drawing_SystemFontType fontType, size_t* pathCount)](#oh_drawing_getfontpathsbytype) | Obtains all font file paths of the specified font type. |
| [OH_Drawing_ErrorCode OH_Drawing_CopyFontFamilyMappings(const OH_Drawing_FontFamilyMapping ***outCopiedMappings, uint32_t *outBorrowedCount)](#oh_drawing_copyfontfamilymappings) | Copies the content of the font family mapping table. |
| [void OH_Drawing_FreeFontFamilyMappings(const OH_Drawing_FontFamilyMapping **mappings)](#oh_drawing_freefontfamilymappings) | Releases a font family mapping table. |
| [OH_Drawing_ErrorCode OH_Drawing_GetSourceFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, const char **outBorrowedSourceFamily)](#oh_drawing_getsourcefamilyfrommapping) | Obtains the source font family name from a specified font family mapping object. |
| [OH_Drawing_ErrorCode OH_Drawing_GetTargetCountFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t *outBorrowedTargetCount)](#oh_drawing_gettargetcountfrommapping) | Obtains the number of target font families contained in a specified font family mapping object. |
| [OH_Drawing_ErrorCode OH_Drawing_GetTargetFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t index, const char **outBorrowedTargetFamily)](#oh_drawing_gettargetfamilyfrommapping) | Obtains the target font family name from a specified font family mapping object based on the index. |

## Enum type description

### OH_Drawing_SystemFontType

```c
enum OH_Drawing_SystemFontType
```

**Description**

Defines an enum for the system font types.

<!--Device-enum OH_Drawing_SystemFontType--><!--Device-enum OH_Drawing_SystemFontType-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

| Enum item | Description |
| -- | -- |
| ALL = 1 << 0 | All font types.<br><!--Device-ALL = 1 << 0--><!--Device-ALL = 1 << 0-End--> |
| GENERIC = 1 << 1 | System font type.<br><!--Device-GENERIC = 1 << 1--><!--Device-GENERIC = 1 << 1-End--> |
| STYLISH = 1 << 2 | Style font type.<br><!--Device-STYLISH = 1 << 2--><!--Device-STYLISH = 1 << 2-End--> |
| INSTALLED = 1 << 3 | User-installed font type.<br><!--Device-INSTALLED = 1 << 3--><!--Device-INSTALLED = 1 << 3-End--> |
| CUSTOMIZED = 1 << 4 | Custom font type.<br>**Since**: 18<br><!--Device-CUSTOMIZED = 1 << 4--><!--Device-CUSTOMIZED = 1 << 4-End--> |

### OH_Drawing_FontFullDescriptorAttributeId

```c
enum OH_Drawing_FontFullDescriptorAttributeId
```

**Description**

Enumerates font descriptor attributes. You can use the corresponding APIs to obtain the attributes of different font descriptor types. For example, if **FULL_DESCRIPTOR_ATTR_I_WEIGHT** is of the int type, use the [OH_Drawing_GetFontFullDescriptorAttributeInt](capi-drawing-text-font-descriptor-h.md#oh_drawing_getfontfulldescriptorattributeint) API to obtain its attribute value.

<!--Device-enum OH_Drawing_FontFullDescriptorAttributeId--><!--Device-enum OH_Drawing_FontFullDescriptorAttributeId-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

| Enum item | Description |
| -- | -- |
| FULL_DESCRIPTOR_ATTR_S_PATH = 0 | Font file path, of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type.<br><!--Device-FULL_DESCRIPTOR_ATTR_S_PATH = 0--><!--Device-FULL_DESCRIPTOR_ATTR_S_PATH = 0-End--> |
| FULL_DESCRIPTOR_ATTR_S_POSTSCRIPT_NAME = 1 | Postscript font name, of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type.<br><!--Device-FULL_DESCRIPTOR_ATTR_S_POSTSCRIPT_NAME = 1--><!--Device-FULL_DESCRIPTOR_ATTR_S_POSTSCRIPT_NAME = 1-End--> |
| FULL_DESCRIPTOR_ATTR_S_FULL_NAME = 2 | Font name, of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type.<br><!--Device-FULL_DESCRIPTOR_ATTR_S_FULL_NAME = 2--><!--Device-FULL_DESCRIPTOR_ATTR_S_FULL_NAME = 2-End--> |
| FULL_DESCRIPTOR_ATTR_S_FAMILY_NAME = 3 | Font family name, of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type.<br><!--Device-FULL_DESCRIPTOR_ATTR_S_FAMILY_NAME = 3--><!--Device-FULL_DESCRIPTOR_ATTR_S_FAMILY_NAME = 3-End--> |
| FULL_DESCRIPTOR_ATTR_S_SUB_FAMILY_NAME = 4 | Font subfamily name, of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type.<br><!--Device-FULL_DESCRIPTOR_ATTR_S_SUB_FAMILY_NAME = 4--><!--Device-FULL_DESCRIPTOR_ATTR_S_SUB_FAMILY_NAME = 4-End--> |
| FULL_DESCRIPTOR_ATTR_I_WEIGHT = 5 | Font weight, of the int type.<br><!--Device-FULL_DESCRIPTOR_ATTR_I_WEIGHT = 5--><!--Device-FULL_DESCRIPTOR_ATTR_I_WEIGHT = 5-End--> |
| FULL_DESCRIPTOR_ATTR_I_WIDTH = 6 | Font width style, of the int type.<br><!--Device-FULL_DESCRIPTOR_ATTR_I_WIDTH = 6--><!--Device-FULL_DESCRIPTOR_ATTR_I_WIDTH = 6-End--> |
| FULL_DESCRIPTOR_ATTR_I_ITALIC = 7 | Whether the font is italic, of the int type. **1** means that the font is italic; **0** otherwise.<br><!--Device-FULL_DESCRIPTOR_ATTR_I_ITALIC = 7--><!--Device-FULL_DESCRIPTOR_ATTR_I_ITALIC = 7-End--> |
| FULL_DESCRIPTOR_ATTR_B_MONO = 8 | Whether the font is monospaced. The value is of the bool type. The value true means the font is monospaced, and false means the opposite.<br><!--Device-FULL_DESCRIPTOR_ATTR_B_MONO = 8--><!--Device-FULL_DESCRIPTOR_ATTR_B_MONO = 8-End--> |
| FULL_DESCRIPTOR_ATTR_B_SYMBOLIC = 9 | Whether the font supports the symbol font, of the bool type. **true** means yes; **false** otherwise.<br><!--Device-FULL_DESCRIPTOR_ATTR_B_SYMBOLIC = 9--><!--Device-FULL_DESCRIPTOR_ATTR_B_SYMBOLIC = 9-End--> |
| FULL_DESCRIPTOR_ATTR_S_LOCAL_POSTSCRIPT_NAME = 10 | Extracts the postscript name of the font based on the system language configuration.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_POSTSCRIPT_NAME = 10--><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_POSTSCRIPT_NAME = 10-End--> |
| FULL_DESCRIPTOR_ATTR_S_LOCAL_FULL_NAME = 11 | Extracts the full name of the font based on the system language configuration.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_FULL_NAME = 11--><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_FULL_NAME = 11-End--> |
| FULL_DESCRIPTOR_ATTR_S_LOCAL_FAMILY_NAME = 12 | Extracts the font family name based on the system language configuration.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_FAMILY_NAME = 12--><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_FAMILY_NAME = 12-End--> |
| FULL_DESCRIPTOR_ATTR_S_LOCAL_SUB_FAMILY_NAME = 13 | Extracts the font subfamily name based on the system language configuration.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_SUB_FAMILY_NAME = 13--><!--Device-FULL_DESCRIPTOR_ATTR_S_LOCAL_SUB_FAMILY_NAME = 13-End--> |
| FULL_DESCRIPTOR_ATTR_S_VERSION = 14 | Font version.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_VERSION = 14--><!--Device-FULL_DESCRIPTOR_ATTR_S_VERSION = 14-End--> |
| FULL_DESCRIPTOR_ATTR_S_MANUFACTURE = 15 | Font manufacturer information.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_MANUFACTURE = 15--><!--Device-FULL_DESCRIPTOR_ATTR_S_MANUFACTURE = 15-End--> |
| FULL_DESCRIPTOR_ATTR_S_COPYRIGHT = 16 | The copyright of the font<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_COPYRIGHT = 16--><!--Device-FULL_DESCRIPTOR_ATTR_S_COPYRIGHT = 16-End--> |
| FULL_DESCRIPTOR_ATTR_S_TRADEMARK = 17 | Font trademark information.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_TRADEMARK = 17--><!--Device-FULL_DESCRIPTOR_ATTR_S_TRADEMARK = 17-End--> |
| FULL_DESCRIPTOR_ATTR_S_LICENSE = 18 | Font license information.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_S_LICENSE = 18--><!--Device-FULL_DESCRIPTOR_ATTR_S_LICENSE = 18-End--> |
| FULL_DESCRIPTOR_ATTR_O_VARIATION_AXIS = 19 | Font variable axis array.<br>**Since**: 24<br><!--Device-FULL_DESCRIPTOR_ATTR_O_VARIATION_AXIS = 19--><!--Device-FULL_DESCRIPTOR_ATTR_O_VARIATION_AXIS = 19-End--> |
| FULL_DESCRIPTOR_ATTR_O_VARIATION_INSTANCE = 20 | Font variable instance array.<br>**Since**: 24<br><!--Device-FULL_DESCRIPTOR_ATTR_O_VARIATION_INSTANCE = 20--><!--Device-FULL_DESCRIPTOR_ATTR_O_VARIATION_INSTANCE = 20-End--> |
| FULL_DESCRIPTOR_ATTR_I_INDEX = 21 | Font index.<br>**Since**: 23<br><!--Device-FULL_DESCRIPTOR_ATTR_I_INDEX = 21--><!--Device-FULL_DESCRIPTOR_ATTR_I_INDEX = 21-End--> |

### OH_Drawing_FontVariationAxisAttributeId

```c
enum OH_Drawing_FontVariationAxisAttributeId
```

**Description**

Enumerates font variable axis attributes.

<!--Device-enum OH_Drawing_FontVariationAxisAttributeId--><!--Device-enum OH_Drawing_FontVariationAxisAttributeId-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

| Enum item | Description |
| -- | -- |
| FONT_VARIATION_AXIS_ATTR_S_KEY = 0 | Keyword identifier of the font variable axis.<br><!--Device-FONT_VARIATION_AXIS_ATTR_S_KEY = 0--><!--Device-FONT_VARIATION_AXIS_ATTR_S_KEY = 0-End--> |
| FONT_VARIATION_AXIS_ATTR_D_MIN_VALUE = 1 | Minimum value of the font variable axis.<br><!--Device-FONT_VARIATION_AXIS_ATTR_D_MIN_VALUE = 1--><!--Device-FONT_VARIATION_AXIS_ATTR_D_MIN_VALUE = 1-End--> |
| FONT_VARIATION_AXIS_ATTR_D_MAX_VALUE = 2 | Maximum value of the font variable axis.<br><!--Device-FONT_VARIATION_AXIS_ATTR_D_MAX_VALUE = 2--><!--Device-FONT_VARIATION_AXIS_ATTR_D_MAX_VALUE = 2-End--> |
| FONT_VARIATION_AXIS_ATTR_D_DEFAULT_VALUE = 3 | Default value of the font variable axis.<br><!--Device-FONT_VARIATION_AXIS_ATTR_D_DEFAULT_VALUE = 3--><!--Device-FONT_VARIATION_AXIS_ATTR_D_DEFAULT_VALUE = 3-End--> |
| FONT_VARIATION_AXIS_ATTR_I_FLAGS = 4 | Flag of the font variable axis. The value **0** indicates that the axis is visible to users, and the value **1** indicates that the axis should be hidden.<br><!--Device-FONT_VARIATION_AXIS_ATTR_I_FLAGS = 4--><!--Device-FONT_VARIATION_AXIS_ATTR_I_FLAGS = 4-End--> |
| FONT_VARIATION_AXIS_ATTR_S_NAME = 5 | English name of the font variable axis.<br><!--Device-FONT_VARIATION_AXIS_ATTR_S_NAME = 5--><!--Device-FONT_VARIATION_AXIS_ATTR_S_NAME = 5-End--> |
| FONT_VARIATION_AXIS_ATTR_S_LOCAL_NAME = 6 | Localized name of the font variable axis.<br><!--Device-FONT_VARIATION_AXIS_ATTR_S_LOCAL_NAME = 6--><!--Device-FONT_VARIATION_AXIS_ATTR_S_LOCAL_NAME = 6-End--> |

### OH_Drawing_FontVariationInstanceAttributeId

```c
enum OH_Drawing_FontVariationInstanceAttributeId
```

**Description**

Enumerates font variable instance attributes.

<!--Device-enum OH_Drawing_FontVariationInstanceAttributeId--><!--Device-enum OH_Drawing_FontVariationInstanceAttributeId-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

| Enum item | Description |
| -- | -- |
| FONT_VARIATION_INSTANCE_ATTR_S_NAME = 0 | English name of the font variable instance.<br><!--Device-FONT_VARIATION_INSTANCE_ATTR_S_NAME = 0--><!--Device-FONT_VARIATION_INSTANCE_ATTR_S_NAME = 0-End--> |
| FONT_VARIATION_INSTANCE_ATTR_S_LOCAL_NAME = 1 | Localized name of the font variable instance.<br><!--Device-FONT_VARIATION_INSTANCE_ATTR_S_LOCAL_NAME = 1--><!--Device-FONT_VARIATION_INSTANCE_ATTR_S_LOCAL_NAME = 1-End--> |


## Function description

### OH_Drawing_MatchFontDescriptors()

```c
OH_Drawing_FontDescriptor* OH_Drawing_MatchFontDescriptors(OH_Drawing_FontDescriptor* desc, size_t* num)
```

**Description**

Obtains all system font descriptors that match a font descriptor. In the [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) struct, the **path** field is not used for matching, and other fields are valid only when they are not set to their default values. <br>If all fields in **desc** are set to their default values, all system font descriptors are returned. <br>If no matching is found, NULL is returned. Call [OH_Drawing_DestroyFontDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontdescriptors) to release this pointer when the object is no longer needed.

<!--Device-OH_Drawing_FontDescriptor* OH_Drawing_MatchFontDescriptors(OH_Drawing_FontDescriptor* desc, size_t* num)--><!--Device-OH_Drawing_FontDescriptor* OH_Drawing_MatchFontDescriptors(OH_Drawing_FontDescriptor* desc, size_t* num)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md)* desc | Pointer to the [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) object. <br>It is recommended to use [OH_Drawing_CreateFontDescriptor](capi-drawing-text-typography-h.md#oh_drawing_createfontdescriptor) to obtain a valid [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) instance. <br>If you create a [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) instance yourself, ensure that the fields not used for matching are set to default values. |
| size_t* num | Output parameter. Used to receive the number of members in the returned array. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_FontDescriptor*](capi-drawing-oh-drawing-fontdescriptor.md) | An array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects. Use [OH_Drawing_DestroyFontDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontdescriptors) to release the array. |

### OH_Drawing_DestroyFontDescriptors()

```c
void OH_Drawing_DestroyFontDescriptors(OH_Drawing_FontDescriptor* descriptors, size_t num)
```

**Description**

Releases an array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects.

<!--Device-void OH_Drawing_DestroyFontDescriptors(OH_Drawing_FontDescriptor* descriptors, size_t num)--><!--Device-void OH_Drawing_DestroyFontDescriptors(OH_Drawing_FontDescriptor* descriptors, size_t num)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md)* descriptors | Pointer to the array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects to be released. |
| size_t num | Number of members in an array of [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) objects. |

### OH_Drawing_GetFontDescriptorByFullName()

```c
OH_Drawing_FontDescriptor* OH_Drawing_GetFontDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)
```

**Description**

Obtains the specified font descriptor based on the font name and font type. This API supports system fonts, style fonts, and user-installed fonts. If the acquisition fails, NULL is returned. <br>A font descriptor is a data structure that describes font characteristics. It contains detailed information that defines the appearance and properties of a font.

<!--Device-OH_Drawing_FontDescriptor* OH_Drawing_GetFontDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)--><!--Device-OH_Drawing_FontDescriptor* OH_Drawing_GetFontDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_String* fullName | Pointer to the font name, which is [OH_Drawing_String](capi-drawing-oh-drawing-string.md). |
| [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype) fontType | Enum for the system font types, which is [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_FontDescriptor*](capi-drawing-oh-drawing-fontdescriptor.md) | Pointer to an [OH_Drawing_FontDescriptor](capi-drawing-oh-drawing-fontdescriptor.md) object. Call [OH_Drawing_DestroyFontDescriptor](capi-drawing-text-typography-h.md#oh_drawing_destroyfontdescriptor) to release this pointer when the object is no longer needed. |

### OH_Drawing_GetSystemFontFullNamesByType()

```c
OH_Drawing_Array* OH_Drawing_GetSystemFontFullNamesByType(OH_Drawing_SystemFontType fontType)
```

**Description**

Obtains an array of font names by font type.

<!--Device-OH_Drawing_Array* OH_Drawing_GetSystemFontFullNamesByType(OH_Drawing_SystemFontType fontType)--><!--Device-OH_Drawing_Array* OH_Drawing_GetSystemFontFullNamesByType(OH_Drawing_SystemFontType fontType)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype) fontType | Enum for the system font types, which is [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Array* | Returns the pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object of the corresponding font type. Call [OH_Drawing_DestroySystemFontFullNames](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroysystemfontfullnames) to release this pointer when the object is no longer needed. |

### OH_Drawing_GetSystemFontFullNameByIndex()

```c
const OH_Drawing_String* OH_Drawing_GetSystemFontFullNameByIndex(OH_Drawing_Array* fullNameArray, size_t index)
```

**Description**

Obtains the font name at the corresponding position in the font name array by index. If the index is out of range or the array is invalid, NULL is returned.

<!--Device-const OH_Drawing_String* OH_Drawing_GetSystemFontFullNameByIndex(OH_Drawing_Array* fullNameArray, size_t index)--><!--Device-const OH_Drawing_String* OH_Drawing_GetSystemFontFullNameByIndex(OH_Drawing_Array* fullNameArray, size_t index)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* fullNameArray | Pointer to an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object. |
| size_t index | Index of the font in the array. |

**Returns**:

| Type | Description |
| -- | -- |
| const OH_Drawing_String* | Returns the pointer to the font name, which is an [OH_Drawing_String](capi-drawing-oh-drawing-string.md) object. |

### OH_Drawing_DestroySystemFontFullNames()

```c
void OH_Drawing_DestroySystemFontFullNames(OH_Drawing_Array* fullNameArray)
```

**Description**

Releases the memory occupied by the font name array obtained by font type.

<!--Device-void OH_Drawing_DestroySystemFontFullNames(OH_Drawing_Array* fullNameArray)--><!--Device-void OH_Drawing_DestroySystemFontFullNames(OH_Drawing_Array* fullNameArray)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* fullNameArray | Pointer to an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object. |

### OH_Drawing_GetFontFullDescriptorsFromStream()

```c
OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromStream(const void* data, size_t size)
```

**Description**

Obtains the font descriptor array based on the original binary data.

<!--Device-OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromStream(const void* data, size_t size)--><!--Device-OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromStream(const void* data, size_t size)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void* data | Pointer to the raw binary font data buffer. |
| size_t size | Size of the font data buffer, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Array* | Returns the pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) array of the font descriptor corresponding to the font file. Call [OH_Drawing_DestroyFontFullDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontfulldescriptors) to release the pointer when the **OH_Drawing_Array** object is no longer needed. <br>Returns NULL if the operation fails due to an invalid data format or parsing error. |

### OH_Drawing_GetFontFullDescriptorsFromPath()

```c
OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromPath(const char* path)
```

**Description**

Obtains an array of font descriptors based on the font file path.

<!--Device-OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromPath(const char* path)--><!--Device-OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorsFromPath(const char* path)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* path | Path of the font file to be queried. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Array* | Returns the pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) array of the font descriptor corresponding to the font file. Call [OH_Drawing_DestroyFontFullDescriptors](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontfulldescriptors) to release the pointer when the **OH_Drawing_Array** object is no longer needed. <br>Returns NULL if the font file is not found, the font file path is invalid, the font file does not have the required permission, or the file is not in the font format. |

### OH_Drawing_GetFontFullDescriptorByIndex()

```c
const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByIndex(OH_Drawing_Array* descriptorArray, size_t index)
```

**Description**

Obtains the font descriptor from the font descriptor array based on the index.

<!--Device-const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByIndex(OH_Drawing_Array* descriptorArray, size_t index)--><!--Device-const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByIndex(OH_Drawing_Array* descriptorArray, size_t index)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* descriptorArray | Pointer to the font descriptor array [OH_Drawing_Array](capi-drawing-oh-drawing-array.md). |
| size_t index | Index of the array, starting from 0. |

**Returns**:

| Type | Description |
| -- | -- |
| [const OH_Drawing_FontFullDescriptor*](capi-drawing-oh-drawing-fontfulldescriptor.md) | Returns the pointer to the font descriptor object [OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md) at the specified index. <br>Returns NULL if the index is out of range or the array is invalid. |

### OH_Drawing_DestroyFontFullDescriptors()

```c
void OH_Drawing_DestroyFontFullDescriptors(OH_Drawing_Array* descriptorArray)
```

**Description**

Releases the memory occupied by the font descriptor array.

<!--Device-void OH_Drawing_DestroyFontFullDescriptors(OH_Drawing_Array* descriptorArray)--><!--Device-void OH_Drawing_DestroyFontFullDescriptors(OH_Drawing_Array* descriptorArray)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* descriptorArray | Pointer to the font descriptor array [OH_Drawing_Array](capi-drawing-oh-drawing-array.md). |

### OH_Drawing_DestroyFontFullDescriptor()

```c
void OH_Drawing_DestroyFontFullDescriptor(const OH_Drawing_FontFullDescriptor* descriptor)
```

**Description**

Releases the memory occupied by the font descriptor pointer. This function can be used to release the font descriptor pointer obtained by the [OH_Drawing_GetFontFullDescriptorByFullName](capi-drawing-text-font-descriptor-h.md#oh_drawing_getfontfulldescriptorbyfullname) API.

<!--Device-void OH_Drawing_DestroyFontFullDescriptor(const OH_Drawing_FontFullDescriptor* descriptor)--><!--Device-void OH_Drawing_DestroyFontFullDescriptor(const OH_Drawing_FontFullDescriptor* descriptor)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md)* descriptor | Pointer to the font descriptor object [OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md). |

### OH_Drawing_GetFontUnicodeArrayFromFile()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromFile(const char* fontSrc, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)
```

**Description**

Obtains the Unicode code array from a font file.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromFile(const char* fontSrc, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromFile(const char* fontSrc, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* fontSrc | Font file path. |
| uint32_t index | Index of the font in the ttc/otc file. The value ranges from 0 to Font Count minus 1. Set this parameter to 0 for non-ttc/otc files. |
| int32_t** unicodeArray | Output parameter, which is used to receive the Unicode array. Use **free()** to release the Unicode array when the array is no longer needed. |
| int32_t* arrayLength | Output parameter, which is used to receive the length of the Unicode array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Result code. <br>Returns OH_DRAWING_SUCCESS if the operation is successful. <br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if the font path is invalid, a non-font file is passed in, or the unicodeArray or arrayLength parameter is NULL. |

### OH_Drawing_GetFontUnicodeArrayFromBuffer()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromBuffer(uint8_t* fontBuffer, size_t length, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)
```

**Description**

Obtains the Unicode code array from a font byte stream buffer.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromBuffer(uint8_t* fontBuffer, size_t length, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontUnicodeArrayFromBuffer(uint8_t* fontBuffer, size_t length, uint32_t index, int32_t** unicodeArray, int32_t* arrayLength)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t* fontBuffer | Font file data. |
| size_t length | Length of the font file data. |
| uint32_t index | Index of the font in the ttc/otc file. The value ranges from 0 to Font Count - 1. For non-ttc/otc files, set this parameter to 0. |
| int32_t** unicodeArray | Output parameter, which is used to receive the Unicode array. Use **free()** to release the Unicode array when the array is no longer needed. |
| int32_t* arrayLength | Output parameter, which is used to receive the length of the Unicode array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Result code. <br>Returns OH_DRAWING_SUCCESS if the operation is successful. <br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if the cached data is invalid, the cached data is not font file data, or the parameters unicodeArray and arrayLength are NULL. |

### OH_Drawing_GetFontFullDescriptorAttributeInt()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeInt(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, int* value)
```

**Description**

Obtains the attributes of a font descriptor of the int type.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeInt(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, int* value)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeInt(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, int* value)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md)* descriptor | Pointer to the font descriptor object [OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md). |
| [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid) id | Font descriptor attribute ID. You can obtain the font descriptor attribute from [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid). |
| int* value | Pointer to the attribute of the **int** type. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the execution result. <br>**OH_DRAWING_SUCCESS** if the operation is successful. <br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the descriptor or value parameter is null. <br>**OH_DRAWING_ERROR_ATTRIBUTE_ID_MISMATCH** if the input attribute ID does not match the called function. |

### OH_Drawing_GetFontFullDescriptorAttributeBool()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeBool(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, bool* value)
```

**Description**

Obtains the font descriptor attribute of the bool type.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeBool(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, bool* value)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeBool(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, bool* value)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md)* descriptor | Pointer to the font descriptor object [OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md). |
| [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid) id | Font descriptor attribute ID. You can obtain the font descriptor attribute from [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid). |
| bool* value | Pointer to the bool attribute It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the execution result. <br>**OH_DRAWING_SUCCESS** if the operation is successful. <br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the descriptor or value parameter is null. <br>**OH_DRAWING_ERROR_ATTRIBUTE_ID_MISMATCH** if the input attribute ID does not match the called function. |

### OH_Drawing_GetFontFullDescriptorAttributeString()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeString(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, OH_Drawing_String* str)
```

**Description**

Obtains the attributes of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) font descriptor.

> **Note**:
>
> The caller is responsible for manually releasing the internal <b>strData</b> member of the <b>OH_Drawing_String</b> structure when it is no longer needed.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeString(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, OH_Drawing_String* str)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontFullDescriptorAttributeString(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id, OH_Drawing_String* str)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md)* descriptor | Pointer to the font descriptor object [OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md). |
| [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid) id | Font descriptor attribute ID. You can obtain the font descriptor attribute from [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid). |
| OH_Drawing_String* str | Pointer to the **OH_Drawing_String** attribute. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the execution result. <br>**OH_DRAWING_SUCCESS** if the operation is successful. <br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **descriptor** or **str** is a null pointer. <br>**OH_DRAWING_ERROR_ATTRIBUTE_ID_MISMATCH** if the input attribute ID does not match the called function. |

### OH_Drawing_GetFontFullDescriptorAttributeArray()

```c
OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorAttributeArray(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id)
```

**Description**

Obtains the object array attributes of the font descriptor.

<!--Device-OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorAttributeArray(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id)--><!--Device-OH_Drawing_Array* OH_Drawing_GetFontFullDescriptorAttributeArray(const OH_Drawing_FontFullDescriptor* descriptor, OH_Drawing_FontFullDescriptorAttributeId id)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md)* descriptor | Pointer to the font descriptor object [OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md). |
| [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid) id | Font descriptor attribute ID. You can obtain the font descriptor attribute from [OH_Drawing_FontFullDescriptorAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontfulldescriptorattributeid). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Array* | Array of objects returned, or NULL if the retrieval fails. When id is FULL_DESCRIPTOR_ATTR_O_VARIATION_AXIS, use the [OH_Drawing_DestroyFontVariationAxis](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontvariationaxis) API to release it when it is no longer needed. When id is FULL_DESCRIPTOR_ATTR_O_VARIATION_INSTANCE, use the [OH_Drawing_DestroyFontVariationInstance](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontvariationinstance) API to release it when it is no longer needed. |

### OH_Drawing_GetFontVariationAxisByIndex()

```c
OH_Drawing_FontVariationAxis* OH_Drawing_GetFontVariationAxisByIndex(OH_Drawing_Array* array, size_t index)
```

**Description**

Obtains the corresponding font variable axis from the font variable axis array by index.

<!--Device-OH_Drawing_FontVariationAxis* OH_Drawing_GetFontVariationAxisByIndex(OH_Drawing_Array* array, size_t index)--><!--Device-OH_Drawing_FontVariationAxis* OH_Drawing_GetFontVariationAxisByIndex(OH_Drawing_Array* array, size_t index)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* array | Pointer to the font variation axis array [OH_Drawing_Array](capi-drawing-oh-drawing-array.md), obtained through [OH_Drawing_GetFontFullDescriptorAttributeArray](capi-drawing-text-font-descriptor-h.md#oh_drawing_getfontfulldescriptorattributearray). |
| size_t index | Index of the array, starting from 0. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_FontVariationAxis*](capi-drawing-oh-drawing-fontvariationaxis.md) | Returns the pointer to the font variable axis object [OH_Drawing_FontVariationAxis](capi-drawing-oh-drawing-fontvariationaxis.md) at the specified index. <br>Returns NULL if the index is out of range or the array is invalid. |

### OH_Drawing_DestroyFontVariationAxis()

```c
void OH_Drawing_DestroyFontVariationAxis(OH_Drawing_Array* fontVariaAxisArray)
```

**Description**

Releases the memory occupied by the font variable axis array.

<!--Device-void OH_Drawing_DestroyFontVariationAxis(OH_Drawing_Array* fontVariaAxisArray)--><!--Device-void OH_Drawing_DestroyFontVariationAxis(OH_Drawing_Array* fontVariaAxisArray)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* fontVariaAxisArray | Pointer to the font variable axis array object [OH_Drawing_Array](capi-drawing-oh-drawing-array.md). |

### OH_Drawing_GetFontVariationAxisAttributeDouble()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeDouble(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, double *value)
```

**Description**

Obtains the font variable axis attributes of the double type.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeDouble(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, double *value)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeDouble(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, double *value)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FontVariationAxis](capi-drawing-oh-drawing-fontvariationaxis.md)* variationAxis | Pointer to the font variable axis object [OH_Drawing_FontVariationAxis](capi-drawing-oh-drawing-fontvariationaxis.md). |
| [OH_Drawing_FontVariationAxisAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationaxisattributeid) id | Font variable axis attribute ID. You can obtain the font variable axis attribute from [OH_Drawing_FontVariationAxisAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationaxisattributeid). |
| double *value | Pointer to the attributes of the double type. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the execution result. <br>**OH_DRAWING_SUCCESS** if the operation is successful. <br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the parameter **variationAxis** or **value** is a null pointer. <br>**OH_DRAWING_ERROR_ATTRIBUTE_ID_MISMATCH** if the input attribute ID does not match the called function. |

### OH_Drawing_GetFontVariationAxisAttributeInt()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeInt(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, int *value)
```

**Description**

Obtains the font variable axis attributes of the int type.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeInt(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, int *value)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeInt(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, int *value)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FontVariationAxis](capi-drawing-oh-drawing-fontvariationaxis.md)* variationAxis | Pointer to the font variable axis object [OH_Drawing_FontVariationAxis](capi-drawing-oh-drawing-fontvariationaxis.md). |
| [OH_Drawing_FontVariationAxisAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationaxisattributeid) id | Font variable axis attribute ID. You can obtain the font variable axis attribute from [OH_Drawing_FontVariationAxisAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationaxisattributeid). |
| int *value | Pointer to the attribute of the **int** type. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the execution result. <br>**OH_DRAWING_SUCCESS** if the operation is successful. <br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the parameter **variationAxis** or **value** is a null pointer. <br>**OH_DRAWING_ERROR_ATTRIBUTE_ID_MISMATCH** if the input attribute ID does not match the called function. |

### OH_Drawing_GetFontVariationAxisAttributeStr()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeStr(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, OH_Drawing_String *str)
```

**Description**

Obtains the font variable axis attributes of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type.

> **Note**:
>
> The caller is responsible for manually releasing the internal <b>strData</b> member of the <b>OH_Drawing_String</b> structure when it is no longer needed.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeStr(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, OH_Drawing_String *str)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationAxisAttributeStr(OH_Drawing_FontVariationAxis* variationAxis, OH_Drawing_FontVariationAxisAttributeId id, OH_Drawing_String *str)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FontVariationAxis](capi-drawing-oh-drawing-fontvariationaxis.md)* variationAxis | Pointer to the font variable axis object [OH_Drawing_FontVariationAxis](capi-drawing-oh-drawing-fontvariationaxis.md). |
| [OH_Drawing_FontVariationAxisAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationaxisattributeid) id | Font variable axis attribute ID. You can obtain the font variable axis attribute from [OH_Drawing_FontVariationAxisAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationaxisattributeid). |
| OH_Drawing_String *str | Pointer to the **OH_Drawing_String** attribute. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the execution result. <br>**OH_DRAWING_SUCCESS** if the operation is successful. <br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the parameter **variationAxis** or **str** is a null pointer. <br>**OH_DRAWING_ERROR_ATTRIBUTE_ID_MISMATCH** if the input attribute ID does not match the called function. |

### OH_Drawing_GetFontVariationInstanceByIndex()

```c
OH_Drawing_FontVariationInstance* OH_Drawing_GetFontVariationInstanceByIndex(OH_Drawing_Array* array, size_t index)
```

**Description**

Obtains the corresponding font variable instance from the font variable instance array by index.

<!--Device-OH_Drawing_FontVariationInstance* OH_Drawing_GetFontVariationInstanceByIndex(OH_Drawing_Array* array, size_t index)--><!--Device-OH_Drawing_FontVariationInstance* OH_Drawing_GetFontVariationInstanceByIndex(OH_Drawing_Array* array, size_t index)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* array | Pointer to the font variation instance array [OH_Drawing_Array](capi-drawing-oh-drawing-array.md). Obtained through [OH_Drawing_GetFontFullDescriptorAttributeArray](capi-drawing-text-font-descriptor-h.md#oh_drawing_getfontfulldescriptorattributearray). |
| size_t index | Index of the array, starting from 0. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_FontVariationInstance*](capi-drawing-oh-drawing-fontvariationinstance.md) | Returns the pointer to the font variable instance object [OH_Drawing_FontVariationInstance](capi-drawing-oh-drawing-fontvariationinstance.md) at the specified index. <br>Returns NULL if the index is out of range or the array is invalid. |

### OH_Drawing_DestroyFontVariationInstance()

```c
void OH_Drawing_DestroyFontVariationInstance(OH_Drawing_Array* fontVariaAxisInstance)
```

**Description**

Releases the memory occupied by the font variable instance array.

<!--Device-void OH_Drawing_DestroyFontVariationInstance(OH_Drawing_Array* fontVariaAxisInstance)--><!--Device-void OH_Drawing_DestroyFontVariationInstance(OH_Drawing_Array* fontVariaAxisInstance)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* fontVariaAxisInstance | Pointer to the font variable instance array object [OH_Drawing_Array](capi-drawing-oh-drawing-array.md). |

### OH_Drawing_GetFontVariationInstanceAttributeStr()

```c
OH_Drawing_ErrorCode OH_Drawing_GetFontVariationInstanceAttributeStr(OH_Drawing_FontVariationInstance* variationInstance, OH_Drawing_FontVariationInstanceAttributeId id, OH_Drawing_String* str)
```

**Description**

Obtains the font variable instance attributes of the [OH_Drawing_String](capi-drawing-oh-drawing-string.md) type.

> **Note**:
>
> The caller is responsible for manually releasing the internal <b>strData</b> member of the <b>OH_Drawing_String</b> structure when it is no longer needed.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationInstanceAttributeStr(OH_Drawing_FontVariationInstance* variationInstance, OH_Drawing_FontVariationInstanceAttributeId id, OH_Drawing_String* str)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetFontVariationInstanceAttributeStr(OH_Drawing_FontVariationInstance* variationInstance, OH_Drawing_FontVariationInstanceAttributeId id, OH_Drawing_String* str)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FontVariationInstance](capi-drawing-oh-drawing-fontvariationinstance.md)* variationInstance | Pointer to the font variable instance object [OH_Drawing_FontVariationInstance](capi-drawing-oh-drawing-fontvariationinstance.md). |
| [OH_Drawing_FontVariationInstanceAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationinstanceattributeid) id | Font variable instance attribute ID. You can obtain the font variable instance attribute from [OH_Drawing_FontVariationInstanceAttributeId](capi-drawing-text-font-descriptor-h.md#oh_drawing_fontvariationinstanceattributeid). |
| OH_Drawing_String* str | Pointer to the **OH_Drawing_String** attribute. It is used as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the execution result. <br>**OH_DRAWING_SUCCESS** if the operation is successful. <br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the parameter **variationInstance** or **str** is a null pointer. <br>**OH_DRAWING_ERROR_ATTRIBUTE_ID_MISMATCH** if the input attribute ID does not match the called function. |

### OH_Drawing_GetFontVariationInstanceCoordinate()

```c
OH_Drawing_FontVariationInstanceCoordinate* OH_Drawing_GetFontVariationInstanceCoordinate(OH_Drawing_FontVariationInstance* variationInstance, size_t* arrayLength)
```

**Description**

Obtains the variable font attribute object of the font variable instance.

<!--Device-OH_Drawing_FontVariationInstanceCoordinate* OH_Drawing_GetFontVariationInstanceCoordinate(OH_Drawing_FontVariationInstance* variationInstance, size_t* arrayLength)--><!--Device-OH_Drawing_FontVariationInstanceCoordinate* OH_Drawing_GetFontVariationInstanceCoordinate(OH_Drawing_FontVariationInstance* variationInstance, size_t* arrayLength)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_FontVariationInstance](capi-drawing-oh-drawing-fontvariationinstance.md)* variationInstance | Pointer to the font variable instance. |
| size_t* arrayLength | Pointer to the list length of OH_Drawing_FontVariationInstanceCoordinate. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Drawing_FontVariationInstanceCoordinate*](capi-drawing-oh-drawing-fontvariationinstancecoordinate.md) | Pointer to the font variation instance coordinate list. NULL if variationInstance is invalid. |

### OH_Drawing_GetFontFullDescriptorByFullName()

```c
const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)
```

**Description**

Obtains the complete font descriptor object based on the font name and type.

<!--Device-const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)--><!--Device-const OH_Drawing_FontFullDescriptor* OH_Drawing_GetFontFullDescriptorByFullName(const OH_Drawing_String* fullName, OH_Drawing_SystemFontType fontType)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_String* fullName | Pointer to the font name object [OH_Drawing_String](capi-drawing-oh-drawing-string.md). |
| [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype) fontType | Enum for the system font type object, which is [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype). |

**Returns**:

| Type | Description |
| -- | -- |
| [const OH_Drawing_FontFullDescriptor*](capi-drawing-oh-drawing-fontfulldescriptor.md) | Returns the pointer to the complete font descriptor object [OH_Drawing_FontFullDescriptor](capi-drawing-oh-drawing-fontfulldescriptor.md). If OH_Drawing_FontFullDescriptor is not required, use the [OH_Drawing_DestroyFontFullDescriptor](capi-drawing-text-font-descriptor-h.md#oh_drawing_destroyfontfulldescriptor) API to release the pointer of the object. |

### OH_Drawing_GetFontCountFromFile()

```c
uint32_t OH_Drawing_GetFontCountFromFile(const char* fontSrc)
```

**Description**

Obtains the number of fonts contained in a font file.

<!--Device-uint32_t OH_Drawing_GetFontCountFromFile(const char* fontSrc)--><!--Device-uint32_t OH_Drawing_GetFontCountFromFile(const char* fontSrc)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* fontSrc | Font file path. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Number of fonts. |

### OH_Drawing_GetFontCountFromBuffer()

```c
uint32_t OH_Drawing_GetFontCountFromBuffer(uint8_t* fontBuffer, size_t length)
```

**Description**

Obtains the number of fonts contained in a font buffer.

<!--Device-uint32_t OH_Drawing_GetFontCountFromBuffer(uint8_t* fontBuffer, size_t length)--><!--Device-uint32_t OH_Drawing_GetFontCountFromBuffer(uint8_t* fontBuffer, size_t length)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t* fontBuffer | Font buffer data. |
| size_t length | Length of the font data. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Number of fonts. |

### OH_Drawing_GetFontPathsByType()

```c
OH_Drawing_String* OH_Drawing_GetFontPathsByType(OH_Drawing_SystemFontType fontType, size_t* pathCount)
```

**Description**

Obtains all font file paths of the specified font type.

<!--Device-OH_Drawing_String* OH_Drawing_GetFontPathsByType(OH_Drawing_SystemFontType fontType, size_t* pathCount)--><!--Device-OH_Drawing_String* OH_Drawing_GetFontPathsByType(OH_Drawing_SystemFontType fontType, size_t* pathCount)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype) fontType | Enum for the system font types, which is [OH_Drawing_SystemFontType](capi-drawing-text-font-descriptor-h.md#oh_drawing_systemfonttype). |
| size_t* pathCount | Output parameter, used to receive the number of font paths returned. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_String* | List of font paths returned. When no longer needed, use free to release the pointer to this object and the pointer held internally by each OH_Drawing_String object. |

### OH_Drawing_CopyFontFamilyMappings()

```c
OH_Drawing_ErrorCode OH_Drawing_CopyFontFamilyMappings(const OH_Drawing_FontFamilyMapping ***outCopiedMappings, uint32_t *outBorrowedCount)
```

**Description**

Copies the content of the font family mapping table.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_CopyFontFamilyMappings(const OH_Drawing_FontFamilyMapping ***outCopiedMappings, uint32_t *outBorrowedCount)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_CopyFontFamilyMappings(const OH_Drawing_FontFamilyMapping ***outCopiedMappings, uint32_t *outBorrowedCount)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 26.1.0

**Resource release**: [OH_Drawing_FreeFontFamilyMappings](#oh_drawing_freefontfamilymappings)

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFamilyMapping](capi-drawing-oh-drawing-fontfamilymapping.md) ***outCopiedMappings | [out] Content of the font family mapping table, populated on success. Call [OH_Drawing_FreeFontFamilyMappings](capi-drawing-text-font-descriptor-h.md#oh_drawing_freefontfamilymappings) to free the memory after use. |
| uint32_t *outBorrowedCount | [out] Number of entries in the font family mapping table, populated on success. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the operation is successful. </li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the **outCopiedMappings** or **outBorrowedCount** parameter is a null pointer. </li> </ul> |

### OH_Drawing_FreeFontFamilyMappings()

```c
void OH_Drawing_FreeFontFamilyMappings(const OH_Drawing_FontFamilyMapping **mappings)
```

**Description**

Releases a font family mapping table.

<!--Device-void OH_Drawing_FreeFontFamilyMappings(const OH_Drawing_FontFamilyMapping **mappings)--><!--Device-void OH_Drawing_FreeFontFamilyMappings(const OH_Drawing_FontFamilyMapping **mappings)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFamilyMapping](capi-drawing-oh-drawing-fontfamilymapping.md) **mappings | [in] Pointer to the font family mapping table. |

### OH_Drawing_GetSourceFamilyFromMapping()

```c
OH_Drawing_ErrorCode OH_Drawing_GetSourceFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, const char **outBorrowedSourceFamily)
```

**Description**

Obtains the source font family name from a specified font family mapping object.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetSourceFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, const char **outBorrowedSourceFamily)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetSourceFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, const char **outBorrowedSourceFamily)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFamilyMapping](capi-drawing-oh-drawing-fontfamilymapping.md) *mapping | [in] Pointer to a single font family mapping object. The pointer cannot be null and must remain valid during the call. The callee does not retain this reference, so the caller does not need to release it after the call. |
| const char **outBorrowedSourceFamily | [out] Source font family name encoded in UTF-8, populated on success. The value of this parameter remains unchanged if the call fails. This parameter cannot be left empty and does not need to be initialized before the call. The string is owned by the **mapping** object and must not be released by the caller. It becomes invalid after the **mapping** object is modified or destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the operation is successful. </li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the **mapping** or **outBorrowedSourceFamily** parameter is a null pointer. </li> </ul> |

### OH_Drawing_GetTargetCountFromMapping()

```c
OH_Drawing_ErrorCode OH_Drawing_GetTargetCountFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t *outBorrowedTargetCount)
```

**Description**

Obtains the number of target font families contained in a specified font family mapping object.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetTargetCountFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t *outBorrowedTargetCount)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetTargetCountFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t *outBorrowedTargetCount)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFamilyMapping](capi-drawing-oh-drawing-fontfamilymapping.md) *mapping | [in] Pointer to a single font family mapping object. The pointer cannot be null and must remain valid during the call. The callee does not retain this reference, so the caller does not need to release it after the call. |
| uint32_t *outBorrowedTargetCount | [out] Number of target font family names, populated on success. The value of this parameter remains unchanged if the call fails. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the operation is successful. </li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the **mapping** or **outBorrowedTargetCount** parameter is a null pointer. </li> </ul> |

### OH_Drawing_GetTargetFamilyFromMapping()

```c
OH_Drawing_ErrorCode OH_Drawing_GetTargetFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t index, const char **outBorrowedTargetFamily)
```

**Description**

Obtains the target font family name from a specified font family mapping object based on the index.

<!--Device-OH_Drawing_ErrorCode OH_Drawing_GetTargetFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t index, const char **outBorrowedTargetFamily)--><!--Device-OH_Drawing_ErrorCode OH_Drawing_GetTargetFamilyFromMapping(const OH_Drawing_FontFamilyMapping *mapping, uint32_t index, const char **outBorrowedTargetFamily)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Drawing_FontFamilyMapping](capi-drawing-oh-drawing-fontfamilymapping.md) *mapping | [in] Pointer to a single font family mapping object. The pointer cannot be null and must remain valid during the call. The callee does not retain this reference, so the caller does not need to release it after the call. |
| uint32_t index | [in] Index of the target font family name. The value range is [0, **targetCount** – 1]. You can obtain **targetCount** by calling [OH_Drawing_GetTargetCountFromMapping](capi-drawing-text-font-descriptor-h.md#oh_drawing_gettargetcountfrommapping). |
| const char **outBorrowedTargetFamily | [out] Target font family name encoded in UTF-8, populated on success. The value of this parameter remains unchanged if the call fails. This parameter cannot be left empty and does not need to be initialized before the call. The string is owned by the **mapping** object and must not be released by the caller. It becomes invalid after the **mapping** object is modified or destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | <ul> <li>[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the operation is successful. </li> <li>[OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the **mapping** or **outBorrowedTargetFamily** parameter is a null pointer. </li> <li>[OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE](capi-drawing-error-code-h.md#oh_drawing_errorcode) is returned if the value of **index** is out of range. </li> </ul> |


