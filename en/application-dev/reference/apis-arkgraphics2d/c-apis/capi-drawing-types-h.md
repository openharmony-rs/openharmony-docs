# drawing_types.h

## Overview

This file declares the data types of the canvas, brush, pen, bitmap, and path used to draw 2D graphics.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) | OH_Drawing_Point2D | **OH_Drawing_Point2D** defines a two-dimensional coordinate point.<br>**OH_Drawing_Corner_Radii** defines rounded corner radii, consisting of an x-axis radius and a y-axis radius. |
| [OH_Drawing_Point3D](capi-drawing-oh-drawing-point3d.md) | OH_Drawing_Point3D | This struct describes a three-dimensional coordinate point. |
| [OH_Drawing_RectStyle_Info](capi-drawing-oh-drawing-rectstyle-info.md) | OH_Drawing_RectStyle_Info | This struct describes the style of a rectangle. |
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) | OH_Drawing_Image_Info | This struct describes the image information. |
| [OH_Drawing_String](capi-drawing-oh-drawing-string.md) | OH_Drawing_String | This struct describes a string of characters encoded in UTF-16. |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) | OH_Drawing_Canvas | Defines a struct for a rectangular canvas, on which various shapes, images, and texts can be drawn by using the brush and pen. |
| [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md) | OH_Drawing_Pen | Defines a struct for a pen, which is used to describe the style and color to outline a shape. |
| [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) | OH_Drawing_Region | Defines a struct for a region, which represents a closed area on the canvas for more accurate graphic control. |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) | OH_Drawing_Brush | Defines a struct for a brush, which is used to describe the style and color to fill in a shape. |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) | OH_Drawing_Path | Defines a struct for a path, which is used to customize various shapes. |
| [OH_Drawing_PathIterator](capi-drawing-oh-drawing-pathiterator.md) | OH_Drawing_PathIterator | This struct defines a path operation iterator that enables path operation instructions to be read via iterator traversal. |
| [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md) | OH_Drawing_Lattice | This struct defines a rectangle grid, which is used to divide an image by rectangle grid. |
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md) | OH_Drawing_Bitmap | Defines a struct for a bitmap, which is a memory area that contains the pixel data of a shape. |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) | OH_Drawing_Point | Defines a struct for a coordinate point. |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) | OH_Drawing_PixelMap | Defines a struct for a pixel map, which is used to wrap the real pixel map supported by the image framework. |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md) | OH_Drawing_ColorSpace | Defines a struct for a color space, which is used to describe the color information. |
| [OH_Drawing_PathEffect](capi-drawing-oh-drawing-patheffect.md) | OH_Drawing_PathEffect | Defines a struct for a path effect that affects the stroke. |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) | OH_Drawing_Rect | Defines a struct for a rectangle. |
| [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md) | OH_Drawing_RoundRect | Defines a struct for a rounded rectangle. |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) | OH_Drawing_Matrix | Defines a struct for a matrix, which is used to describe coordinate transformation. |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md) | OH_Drawing_ShaderEffect | Defines a struct for a shader effect, which is used to describe the source color of the drawn content. |
| [OH_Drawing_ShadowLayer](capi-drawing-oh-drawing-shadowlayer.md) | OH_Drawing_ShadowLayer | Defines a struct for a shadow, which is used to describe the shadow layer of the drawn content. |
| [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md) | OH_Drawing_Filter | Defines a struct for a filter, which consists of a color filter, mask filter, and image filter. |
| [OH_Drawing_MaskFilter](capi-drawing-oh-drawing-maskfilter.md) | OH_Drawing_MaskFilter | Defines a struct for a mask filter. |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md) | OH_Drawing_ColorFilter | Defines a struct for a color filter, which is used to convert a color into a new one. |
| [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) | OH_Drawing_Font | Defines a struct for a font. |
| [OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md) | OH_Drawing_FontFeatures | Defines a struct for font features, which are typesetting rules within a font that determine how glyphs look, such as ligatures, alternates, and superscripts/subscripts. |
| [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md) | OH_Drawing_MemoryStream | Defines a struct for a memory stream. |
| [OH_Drawing_FontArguments](capi-drawing-oh-drawing-fontarguments.md) | OH_Drawing_FontArguments | Defines a struct for font arguments. |
| [OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md) | OH_Drawing_Typeface | Defines a struct for a typeface. |
| [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md) | OH_Drawing_TextBlob | Defines a struct for a text blob, an immutable container that holds multiple texts. Each text blob consists of glyphs and position. |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) | OH_Drawing_Image | Defines a struct for an image that describes a two-dimensional pixel array. |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md) | OH_Drawing_ImageFilter | Defines a struct for an image filter, which is used to operate all color bits that make up image pixels. |
| [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) | OH_Drawing_SamplingOptions | Defines a struct for sampling options, which describe the sampling methods for images and bitmaps. |
| [OH_Drawing_TextBlobBuilder](capi-drawing-oh-drawing-textblobbuilder.md) | OH_Drawing_TextBlobBuilder | Defines a struct for a text blob builder, which is used to build a text blob. |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) | OH_Drawing_GpuContext | Defines a struct for the GPU context, which is used to describe the GPU backend context. |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md) | OH_Drawing_Surface | Defines a struct for a surface, which is used to manage the content drawn on the canvas. |
| [OH_Drawing_FontMgr](capi-drawing-oh-drawing-fontmgr.md) | OH_Drawing_FontMgr | Defines a struct for the font manager, which is used for font management. |
| [OH_Drawing_FontStyleSet](capi-drawing-oh-drawing-fontstyleset.md) | OH_Drawing_FontStyleSet | Defines a struct for a font style set, which is used for font style family matching. |
| [OH_Drawing_RecordCmdUtils](capi-drawing-oh-drawing-recordcmdutils.md) | OH_Drawing_RecordCmdUtils | Defines the recording command tool, which is used to generate recording commands. |
| [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md) | OH_Drawing_RecordCmd | Defines the recording command class, which is used to store the set of recording commands. |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) | OH_Drawing_Array | Defines a struct for an array object, which is used to store multiple objects of the same type. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_ColorFormat](#oh_drawing_colorformat) | OH_Drawing_ColorFormat | Defines an enum for the storage formats of bitmap pixels. |
| [OH_Drawing_AlphaFormat](#oh_drawing_alphaformat) | OH_Drawing_AlphaFormat | Defines an enum for the alpha formats of bitmap pixels. |
| [OH_Drawing_BlendMode](#oh_drawing_blendmode) | OH_Drawing_BlendMode | Defines an enum for blend modes. In blend mode, each operation generates a new color from two colors (source color and destination color). These operations are the same for the red, green, and blue color channels (the alpha channel follows a different rule). For simplicity, the following description uses the alpha channel as an example rather than naming each channel individually. For brevity, the following abbreviations are used: **s**: source. **d**: destination. **sa**: source alpha. **da**: destination alpha. The following abbreviations are used in the calculation result: **r**: The calculation methods of the four channels are the same. **ra**: used when only the alpha channel is manipulated. **rc**: used when the other three color channels are manipulated. |
| [OH_Drawing_TextEncoding](#oh_drawing_textencoding) | OH_Drawing_TextEncoding | Defines an enum for the text encoding types. |

### Variable

| Name | Description |
| -- | -- |
| OH_Drawing_Point2D OH_Drawing_Corner_Radii | Defines corner radii, which is on x-axis and y-axis.<br>**Since**: 12 |

## Enum type description

### OH_Drawing_ColorFormat

```c
enum OH_Drawing_ColorFormat
```

**Description**

Defines an enum for the storage formats of bitmap pixels.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

| Enum item | Description |
| -- | -- |
| COLOR_FORMAT_UNKNOWN |  |
| COLOR_FORMAT_ALPHA_8 |  |
| COLOR_FORMAT_RGB_565 |  |
| COLOR_FORMAT_ARGB_4444 |  |
| COLOR_FORMAT_RGBA_8888 |  |
| COLOR_FORMAT_BGRA_8888 |  |

### OH_Drawing_AlphaFormat

```c
enum OH_Drawing_AlphaFormat
```

**Description**

Defines an enum for the alpha formats of bitmap pixels.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

| Enum item | Description |
| -- | -- |
| ALPHA_FORMAT_UNKNOWN |  |
| ALPHA_FORMAT_OPAQUE |  |
| ALPHA_FORMAT_PREMUL |  |
| ALPHA_FORMAT_UNPREMUL |  |

### OH_Drawing_BlendMode

```c
enum OH_Drawing_BlendMode
```

**Description**

Defines an enum for blend modes. In blend mode, each operation generates a new color from two colors (source color and destination color). These operations are the same for the red, green, and blue color channels (the alpha channel follows a different rule). For simplicity, the following description uses the alpha channel as an example rather than naming each channel individually. For brevity, the following abbreviations are used: **s**: source. **d**: destination. **sa**: source alpha. **da**: destination alpha. The following abbreviations are used in the calculation result: **r**: The calculation methods of the four channels are the same. **ra**: used when only the alpha channel is manipulated. **rc**: used when the other three color channels are manipulated.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

| Enum item | Description |
| -- | -- |
| BLEND_MODE_CLEAR |  |
| BLEND_MODE_SRC |  |
| BLEND_MODE_DST |  |
| BLEND_MODE_SRC_OVER |  |
| BLEND_MODE_DST_OVER |  |
| BLEND_MODE_SRC_IN |  |
| BLEND_MODE_DST_IN |  |
| BLEND_MODE_SRC_OUT |  |
| BLEND_MODE_DST_OUT |  |
| BLEND_MODE_SRC_ATOP |  |
| BLEND_MODE_DST_ATOP |  |
| BLEND_MODE_XOR |  |
| BLEND_MODE_PLUS |  |
| BLEND_MODE_MODULATE |  |
| BLEND_MODE_SCREEN |  |
| BLEND_MODE_OVERLAY |  |
| BLEND_MODE_DARKEN |  |
| BLEND_MODE_LIGHTEN |  |
| BLEND_MODE_COLOR_DODGE |  |
| BLEND_MODE_COLOR_BURN |  |
| BLEND_MODE_HARD_LIGHT |  |
| BLEND_MODE_SOFT_LIGHT |  |
| BLEND_MODE_DIFFERENCE |  |
| BLEND_MODE_EXCLUSION |  |
| BLEND_MODE_MULTIPLY |  |
| BLEND_MODE_HUE |  |
| BLEND_MODE_SATURATION |  |
| BLEND_MODE_COLOR |  |
| BLEND_MODE_LUMINOSITY |  |

### OH_Drawing_TextEncoding

```c
enum OH_Drawing_TextEncoding
```

**Description**

Defines an enum for the text encoding types.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

| Enum item | Description |
| -- | -- |
| TEXT_ENCODING_UTF8 |  |
| TEXT_ENCODING_UTF16 |  |
| TEXT_ENCODING_UTF32 |  |
| TEXT_ENCODING_GLYPH_ID |  |


