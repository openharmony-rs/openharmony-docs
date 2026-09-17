# drawing_font_mgr.h

## Overview

Declares functions related to system font management, used to match and obtain fonts preset in the system. OH_Drawing_FontMgr (font manager) manages the font families preset in the system. Each font family corresponds to a font style set {@link OH_Drawing_FontStyleSet}, and each style set contains multiple typeface objects<br>{@link OH_Drawing_Typeface}.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_FontMgr* OH_Drawing_FontMgrCreate(void)](#oh_drawing_fontmgrcreate) | Creates an **OH_Drawing_FontMgr** object, which can be used only to manage system fonts. |
| [void OH_Drawing_FontMgrDestroy(OH_Drawing_FontMgr* drawingFontMgr)](#oh_drawing_fontmgrdestroy) | Destroys an **OH_Drawing_FontMgr** object and reclaims the memory occupied by the object. |
| [int OH_Drawing_FontMgrGetFamilyCount(OH_Drawing_FontMgr* drawingFontMgr)](#oh_drawing_fontmgrgetfamilycount) | Obtains the number of font families. |
| [char* OH_Drawing_FontMgrGetFamilyName(OH_Drawing_FontMgr* drawingFontMgr, int index)](#oh_drawing_fontmgrgetfamilyname) | Obtains the font family name based on an index. When the returned name is no longer needed, use [OH_Drawing_FontMgrDestroyFamilyName](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrdestroyfamilyname) to release the memory occupied by the name. |
| [void OH_Drawing_FontMgrDestroyFamilyName(char* familyName)](#oh_drawing_fontmgrdestroyfamilyname) | Reclaims the memory occupied by a font family name. |
| [OH_Drawing_FontStyleSet* OH_Drawing_FontMgrCreateFontStyleSet(OH_Drawing_FontMgr* drawingFontMgr, int index)](#oh_drawing_fontmgrcreatefontstyleset) | Creates a font style set object from a font manager object. |
| [void OH_Drawing_FontMgrDestroyFontStyleSet(OH_Drawing_FontStyleSet* drawingFontStyleSet)](#oh_drawing_fontmgrdestroyfontstyleset) | Reclaims the memory occupied by a font style set. |
| [OH_Drawing_FontStyleSet* OH_Drawing_FontMgrMatchFamily(OH_Drawing_FontMgr* drawingFontMgr, const char* familyName)](#oh_drawing_fontmgrmatchfamily) | Obtains a font style set object based on a specified font family name. When the object is no longer needed, use [OH_Drawing_FontMgrDestroyFontStyleSet](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrdestroyfontstyleset) to release it. |
| [OH_Drawing_Typeface* OH_Drawing_FontMgrMatchFamilyStyle(OH_Drawing_FontMgr* drawingFontMgr, const char* familyName, OH_Drawing_FontStyleStruct fontStyle)](#oh_drawing_fontmgrmatchfamilystyle) | Obtains a typeface object based on the specified font style information and font family name. When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it. |
| [OH_Drawing_Typeface* OH_Drawing_FontMgrMatchFamilyStyleCharacter(OH_Drawing_FontMgr* drawingFontMgr, const char* familyName, OH_Drawing_FontStyleStruct fontStyle, const char* bcp47[], int bcp47Count, int32_t character)](#oh_drawing_fontmgrmatchfamilystylecharacter) | Obtains a typeface for the specified character. A null pointer is returned only when no typeface corresponding to the input UTF-8 character is found in the font management object. When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it. |
| [OH_Drawing_Typeface* OH_Drawing_FontStyleSetCreateTypeface(OH_Drawing_FontStyleSet* fontStyleSet, int index)](#oh_drawing_fontstylesetcreatetypeface) | Gets a typeface for the specified index. When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it. |
| [OH_Drawing_FontStyleStruct OH_Drawing_FontStyleSetGetStyle(OH_Drawing_FontStyleSet* fontStyleSet, int32_t index, char** styleName)](#oh_drawing_fontstylesetgetstyle) | Obtains the font style. Call [OH_Drawing_FontStyleSetFreeStyleName](capi-drawing-font-mgr-h.md#oh_drawing_fontstylesetfreestylename) to release **styleName** when it is no longer needed, freeing up the allocated memory. |
| [void OH_Drawing_FontStyleSetFreeStyleName(char** styleName)](#oh_drawing_fontstylesetfreestylename) | Frees the memory occupied by a font style. |
| [OH_Drawing_Typeface* OH_Drawing_FontStyleSetMatchStyle(OH_Drawing_FontStyleSet* fontStyleSet, OH_Drawing_FontStyleStruct fontStyleStruct)](#oh_drawing_fontstylesetmatchstyle) | Obtains the typeface closest to the font style (font weight, font width, and slant). When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it. |
| [int OH_Drawing_FontStyleSetCount(OH_Drawing_FontStyleSet* fontStyleSet)](#oh_drawing_fontstylesetcount) | Obtains the number of fonts in the font style set. |

## Function description

### OH_Drawing_FontMgrCreate()

```c
OH_Drawing_FontMgr* OH_Drawing_FontMgrCreate(void)
```

**Description**

Creates an **OH_Drawing_FontMgr** object, which can be used only to manage system fonts.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_FontMgr* | Pointer to the {@link OH_Drawing_FontMgr} object created. |

### OH_Drawing_FontMgrDestroy()

```c
void OH_Drawing_FontMgrDestroy(OH_Drawing_FontMgr* drawingFontMgr)
```

**Description**

Destroys an **OH_Drawing_FontMgr** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontMgr* drawingFontMgr | Pointer to an {@link OH_Drawing_FontMgr} object, which is obtained from [OH_Drawing_FontMgrCreate](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrcreate). |

### OH_Drawing_FontMgrGetFamilyCount()

```c
int OH_Drawing_FontMgrGetFamilyCount(OH_Drawing_FontMgr* drawingFontMgr)
```

**Description**

Obtains the number of font families.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontMgr* drawingFontMgr | Pointer to an {@link OH_Drawing_FontMgr} object, which is obtained from [OH_Drawing_FontMgrCreate](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrcreate). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the number of font families. |

### OH_Drawing_FontMgrGetFamilyName()

```c
char* OH_Drawing_FontMgrGetFamilyName(OH_Drawing_FontMgr* drawingFontMgr, int index)
```

**Description**

Obtains the font family name based on an index. When the returned name is no longer needed, use [OH_Drawing_FontMgrDestroyFamilyName](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrdestroyfamilyname) to release the memory occupied by the name.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontMgr* drawingFontMgr | Pointer to an {@link OH_Drawing_FontMgr} object, which is obtained from [OH_Drawing_FontMgrCreate](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrcreate). |
| int index | Index used to obtain the corresponding font family name. The value range is [0, OH_Drawing_FontMgrGetFamilyCount() - 1]. |

**Returns**:

| Type | Description |
| -- | -- |
| char* | Font family name corresponding to the index. When no longer needed, use      [OH_Drawing_FontMgrDestroyFamilyName](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrdestroyfamilyname) to release the memory occupied by the name. |

### OH_Drawing_FontMgrDestroyFamilyName()

```c
void OH_Drawing_FontMgrDestroyFamilyName(char* familyName)
```

**Description**

Reclaims the memory occupied by a font family name.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* familyName | Pointer to a font family name. |

### OH_Drawing_FontMgrCreateFontStyleSet()

```c
OH_Drawing_FontStyleSet* OH_Drawing_FontMgrCreateFontStyleSet(OH_Drawing_FontMgr* drawingFontMgr, int index)
```

**Description**

Creates a font style set object from a font manager object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontMgr* drawingFontMgr | Pointer to an {@link OH_Drawing_FontMgr} object, which is obtained from [OH_Drawing_FontMgrCreate](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrcreate). |
| int index | Index value used to obtain the font style set object from the font manager object. Value range: [0, OH_Drawing_FontMgrGetFamilyCount() - 1]. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_FontStyleSet* | Returns a pointer to the {@link OH_Drawing_FontStyleSet} object created. |

### OH_Drawing_FontMgrDestroyFontStyleSet()

```c
void OH_Drawing_FontMgrDestroyFontStyleSet(OH_Drawing_FontStyleSet* drawingFontStyleSet)
```

**Description**

Reclaims the memory occupied by a font style set.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontStyleSet* drawingFontStyleSet | Pointer to an {@link OH_Drawing_FontStyleSet} object. |

### OH_Drawing_FontMgrMatchFamily()

```c
OH_Drawing_FontStyleSet* OH_Drawing_FontMgrMatchFamily(OH_Drawing_FontMgr* drawingFontMgr, const char* familyName)
```

**Description**

Obtains a font style set object based on a specified font family name. When the object is no longer needed, use [OH_Drawing_FontMgrDestroyFontStyleSet](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrdestroyfontstyleset) to release it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontMgr* drawingFontMgr | Pointer to an {@link OH_Drawing_FontMgr} object, which is obtained from [OH_Drawing_FontMgrCreate](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrcreate). |
| const char* familyName | Pointer to a font family name. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_FontStyleSet* | Pointer to the corresponding font style set object {@link OH_Drawing_FontStyleSet}. When no longer needed,      use [OH_Drawing_FontMgrDestroyFontStyleSet](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrdestroyfontstyleset) to release the object pointer. <br>NULL is returned if      matching fails. |

### OH_Drawing_FontMgrMatchFamilyStyle()

```c
OH_Drawing_Typeface* OH_Drawing_FontMgrMatchFamilyStyle(OH_Drawing_FontMgr* drawingFontMgr, const char* familyName, OH_Drawing_FontStyleStruct fontStyle)
```

**Description**

Obtains a typeface object based on the specified font style information and font family name. When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontMgr* drawingFontMgr | Pointer to an {@link OH_Drawing_FontMgr} object, which is obtained from [OH_Drawing_FontMgrCreate](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrcreate). |
| const char* familyName | Pointer to a font family name. |
| OH_Drawing_FontStyleStruct fontStyle | Font style, including the font weight, width, and slant. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Pointer to the {@link OH_Drawing_Typeface} object corresponding to the font style. Use<br>    {@link OH_Drawing_TypefaceDestroy} to release the pointer when it is no longer needed. <br>NULL is returned if      the match fails. |

### OH_Drawing_FontMgrMatchFamilyStyleCharacter()

```c
OH_Drawing_Typeface* OH_Drawing_FontMgrMatchFamilyStyleCharacter(OH_Drawing_FontMgr* drawingFontMgr, const char* familyName, OH_Drawing_FontStyleStruct fontStyle, const char* bcp47[], int bcp47Count, int32_t character)
```

**Description**

Obtains a typeface for the specified character. A null pointer is returned only when no typeface corresponding to the input UTF-8 character is found in the font management object. When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontMgr* drawingFontMgr | Pointer to an {@link OH_Drawing_FontMgr} object, which is obtained from [OH_Drawing_FontMgrCreate](capi-drawing-font-mgr-h.md#oh_drawing_fontmgrcreate). |
| const char* familyName | Pointer to a font family name. |
| OH_Drawing_FontStyleStruct fontStyle | Font style, including the font weight, width, and slant. |
| const char* bcp47[] | Array of BCP47 language codes, which is a combination of ISO 639, 15924, and 3166-1 language codes. |
| int bcp47Count | Size of the bcp47 array, which must match the actual number of elements in the bcp47 array. |
| int32_t character | UTF-8 character used for matching. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Pointer to the corresponding {@link OH_Drawing_Typeface} typeface object, or NULL if no typeface is matched. |

### OH_Drawing_FontStyleSetCreateTypeface()

```c
OH_Drawing_Typeface* OH_Drawing_FontStyleSetCreateTypeface(OH_Drawing_FontStyleSet* fontStyleSet, int index)
```

**Description**

Gets a typeface for the specified index. When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontStyleSet* fontStyleSet | Pointer to an {@link OH_Drawing_FontStyleSet} object. |
| int index | Index of the specified typeface object. The value range is [0, OH_Drawing_FontStyleSetCount() - 1]. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Typeface object if successful; NULL otherwise. |

### OH_Drawing_FontStyleSetGetStyle()

```c
OH_Drawing_FontStyleStruct OH_Drawing_FontStyleSetGetStyle(OH_Drawing_FontStyleSet* fontStyleSet, int32_t index, char** styleName)
```

**Description**

Obtains the font style. Call [OH_Drawing_FontStyleSetFreeStyleName](capi-drawing-font-mgr-h.md#oh_drawing_fontstylesetfreestylename) to release **styleName** when it is no longer needed, freeing up the allocated memory.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontStyleSet* fontStyleSet | Pointer to an {@link OH_Drawing_FontStyleSet} object. |
| int32_t index | Index of the specified font style. The value range is [0, OH_Drawing_FontStyleSetCount() - 1]. |
| char** styleName | String specifying the font style name. Call [OH_Drawing_FontStyleSetFreeStyleName](capi-drawing-font-mgr-h.md#oh_drawing_fontstylesetfreestylename) to release it when it is no longer needed, freeing up the allocated memory. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_FontStyleStruct | Returns the font style. |

### OH_Drawing_FontStyleSetFreeStyleName()

```c
void OH_Drawing_FontStyleSetFreeStyleName(char** styleName)
```

**Description**

Frees the memory occupied by a font style.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char** styleName | Double pointer to the string that specifies the font style name. |

### OH_Drawing_FontStyleSetMatchStyle()

```c
OH_Drawing_Typeface* OH_Drawing_FontStyleSetMatchStyle(OH_Drawing_FontStyleSet* fontStyleSet, OH_Drawing_FontStyleStruct fontStyleStruct)
```

**Description**

Obtains the typeface closest to the font style (font weight, font width, and slant). When the object is no longer needed, use {@link OH_Drawing_TypefaceDestroy} to release it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontStyleSet* fontStyleSet | Pointer to an {@link OH_Drawing_FontStyleSet} object. |
| OH_Drawing_FontStyleStruct fontStyleStruct | Font style, including the font weight, width, and slant. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Typeface* | Pointer to the corresponding typeface object {@link OH_Drawing_Typeface}, or NULL if matching fails. |

### OH_Drawing_FontStyleSetCount()

```c
int OH_Drawing_FontStyleSetCount(OH_Drawing_FontStyleSet* fontStyleSet)
```

**Description**

Obtains the number of fonts in the font style set.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_FontStyleSet* fontStyleSet | Pointer to an {@link OH_Drawing_FontStyleSet} object. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the number of fonts. |


