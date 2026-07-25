# drawing_register_font.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @gmiao522-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=26f1a11070a0259938fa2e9b40098b1fb904b6e8 translatedAt=2026-07-25T02:01:43.073Z pushedAt=2026-07-25T07:43:40.550Z -->

## Overview

Defines functions related to the font manager in the drawing module, providing capabilities for registering and unregistering custom fonts as well as detecting font formats, and supporting multiple font file formats such as ttf, otf, ttc, and otc.

**File to include**: <native_drawing/drawing_register_font.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [uint32_t OH_Drawing_RegisterFont(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, const char* familySrc)](#oh_drawing_registerfont) | Registers a custom font in the Font Manager. The supported font file formats include ttf and otf. |
| [uint32_t OH_Drawing_RegisterFontBuffer(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, uint8_t* fontBuffer, size_t length)](#oh_drawing_registerfontbuffer) | Registers a font buffer in the Font Manager. Supports data read from ttf and otf files. |
| [uint32_t OH_Drawing_UnregisterFont(OH_Drawing_FontCollection* fontCollection, const char* fontFamily)](#oh_drawing_unregisterfont) | Unregisters a custom font by font name.<br> Unregistering a font currently in use may cause text rendering anomalies, including garbled text or missing glyphs.<br> All typesetting objects that use the unregistered font name should be destroyed and recreated. |
| [uint32_t OH_Drawing_RegisterFontByIndex(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, const char* familySrc, uint32_t index)](#oh_drawing_registerfontbyindex) | Registers a custom font using a ttc/otc file, and specifies the index of the font to register via the index parameter. |
| [uint32_t OH_Drawing_RegisterFontBufferByIndex(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, uint8_t* fontBuffer, size_t length, uint32_t index)](#oh_drawing_registerfontbufferbyindex) | Registers a font using the font buffer of a TTC/OTC file.|
| [bool OH_Drawing_IsFontSupportedFromPath(const char* path)](#oh_drawing_isfontsupportedfrompath) | Checks whether the system supports the font format of the specified path.|
| [bool OH_Drawing_IsFontSupportedFromBuffer(uint8_t* data, size_t dataLength)](#oh_drawing_isfontsupportedfrombuffer) | Checks whether the system supports the font format specified in the buffer.|

## Function Description

### OH_Drawing_RegisterFont()

```c
uint32_t OH_Drawing_RegisterFont(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, const char* familySrc)
```

**Description**

Registers a custom font with the font manager. The supported font file formats are .ttf and .otf.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object. |
| const char* fontFamily | Name of the font to register. |
| const char* familySrc | Path to the font file to register. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Result code.<br>Returns 0 if the operation is successful.<br>Returns 1 if the file does not exist.<br>Returns 2 if opening the file fails.<br>Returns 3 if reading the file fails.<br>Returns 4 if seeking the file fails.<br>Returns 5 if obtaining the file size fails.<br>Returns 8 if fontCollection is NULL.<br>Returns 9 if the file is corrupted. |

### OH_Drawing_RegisterFontBuffer()

```c
uint32_t OH_Drawing_RegisterFontBuffer(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, uint8_t* fontBuffer, size_t length)
```

**Description**

Registers a font buffer in the font manager, supporting data read from ttf and otf files.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object. |
| const char* fontFamily | Font name of the font to register. |
| uint8_t* fontBuffer | Buffer of the font file to register. |
| size_t length | Length of the font file to register. Must match the actual length of fontBuffer. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Result code. Returns 0 if the function is executed successfully; returns 6 if fontBuffer is NULL; returns 7 if the buffer size is zero; returns 8 if fontCollection is NULL. |

### OH_Drawing_UnregisterFont()

```c
uint32_t OH_Drawing_UnregisterFont(OH_Drawing_FontCollection* fontCollection, const char* fontFamily)
```

**Description**

Unregisters a custom font by font name.

Unregistering a font that is currently in use may lead to text rendering exceptions (such as garbled characters or missing glyphs).

All typesetting objects that use the unregistered font name should be destroyed and recreated.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| const char* fontFamily | Font name to unregister. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Result code. Returns 0 if the function is executed successfully, 8 if the input parameter is invalid, and 1 if the unregistration fails. |

### OH_Drawing_RegisterFontByIndex()

```c
uint32_t OH_Drawing_RegisterFontByIndex(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, const char* familySrc, uint32_t index)
```

**Description**

Registers a custom font using a ttc/otc file, with the index parameter specifying the font index to register.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| const char* fontFamily | Family name of the font to register.|
| const char* familySrc | Path of the font file to register.|
| uint32_t index | Index of the font in the ttc/otc file. The value ranges from 0 to the total number of fonts minus 1. For non-ttc/otc files, set this parameter to 0. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Result code. 0 indicates function execution is successful, 1 indicates file does not exist, 2 indicates file opening failure, 3 indicates file reading failure, 4 indicates file seeking failure, 5 indicates size obtaining failure, 8 indicates fontCollection is NULL, and 9 indicates file corruption. |

### OH_Drawing_RegisterFontBufferByIndex()

```c
uint32_t OH_Drawing_RegisterFontBufferByIndex(OH_Drawing_FontCollection* fontCollection, const char* fontFamily, uint8_t* fontBuffer, size_t length, uint32_t index)
```

**Description**

Registers a font using the font buffer of a TTC/OTC file.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md)* fontCollection | Pointer to an [OH_Drawing_FontCollection](capi-drawing-oh-drawing-fontcollection.md) object.|
| const char* fontFamily | Family name of the font to register.|
| uint8_t* fontBuffer | Font buffer of the font file to register.|
| size_t length | Length of the byte stream data, which must match the actual length of fontBuffer. |
| uint32_t index | Index of the font in the ttc/otc file. The value ranges from 0 to the number of fonts minus 1. For files in non-ttc/otc formats, set this parameter to 0. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Result code. Returns 0 if the function is executed successfully. Returns 6 if fontBuffer is NULL. Returns 7 if the buffer size is 0. Returns 8 if fontCollection is NULL. Returns 9 if the file is corrupted. |

### OH_Drawing_IsFontSupportedFromPath()

```c
bool OH_Drawing_IsFontSupportedFromPath(const char* path)
```

**Description**

Checks whether the system supports the font format of the specified path.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const char* path | Absolute path of the font file.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the font is supported; returns **false** otherwise.|

### OH_Drawing_IsFontSupportedFromBuffer()

```c
bool OH_Drawing_IsFontSupportedFromBuffer(uint8_t* data, size_t dataLength)
```

**Description**

Checks whether the system supports the font format specified in the buffer.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| uint8_t* data | Pointer to the buffer that contains the font data.|
| size_t dataLength | Size of the font data, in bytes. Must match the actual length of data. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the font is supported; returns **false** otherwise.|