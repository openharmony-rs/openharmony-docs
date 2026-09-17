# Drawing

## Overview

Provides functions such as 2D graphics rendering, text drawing, and image display.

**Since**: 8

## Files

| Name | Description |
| -- | -- |
| [drawing_lattice.h](capi-drawing-lattice-h.md) | This file declares the functions related to the rectangular lattice object. |
| [drawing_point.h](capi-drawing-point-h.md) | This file declares the functions related to the coordinate point in the drawing module. |
| [drawing_round_rect.h](capi-drawing-round-rect-h.md) | This file declares the functions related to the rounded rectangle in the drawing module. |
| [drawing_shadow_layer.h](capi-drawing-shadow-layer-h.md) | This file declares the functions related to the shadow in the drawing module. |
| [drawing_text_line.h](capi-drawing-text-line-h.md) | This file declares the capabilities for obtaining the character position in a text line, obtaining the run information, and truncating text by line. |
| [drawing_color_space.h](capi-drawing-color-space-h.md) | This file declares the functions related to the color space in the drawing module. |
| [drawing_path_iterator.h](capi-drawing-path-iterator-h.md) | This file declares the functions related to the path operation iterator object. |
| [drawing_text_run.h](capi-drawing-text-run-h.md) | This file declares the capabilities of runs, such as obtaining the typographic boundary and drawing. |
| [drawing_text_global.h](capi-drawing-text-global-h.md) | Provides APIs for global text information, such as setting the text rendering high contrast mode and the presentation mode of undefined glyphs. |
| [drawing_pen.h](capi-drawing-pen-h.md) | This file declares functions related to the pen in the drawing module. |
| [drawing_bitmap.h](capi-drawing-bitmap-h.md) | This file declares the functions related to the bitmap in the drawing module. |
| [drawing_matrix.h](capi-drawing-matrix-h.md) | This file declares the functions related to the matrix in the drawing module. |
| [drawing_memory_stream.h](capi-drawing-memory-stream-h.md) | This file declares the functions related to the memory stream in the drawing module. |
| [drawing_canvas.h](capi-drawing-canvas-h.md) | This file declares the functions related to the canvas in the drawing module. By default, the canvas has a black brush with anti-aliasing enabled and without any other style. This brush takes effect only when no brush or pen is proactively set in the canvas. |
| [drawing_error_code.h](capi-drawing-error-code-h.md) | This file declares the functions related to the error code in the drawing module. |
| [drawing_gpu_context.h](capi-drawing-gpu-context-h.md) | This file declares the functions related to the GPU context in the drawing module. |
| [drawing_filter.h](capi-drawing-filter-h.md) | This file declares the functions related to the filter in the drawing module. |
| [drawing_text_blob.h](capi-drawing-text-blob-h.md) | This file declares the functions related to the text blob in the drawing module. |
| [drawing_surface.h](capi-drawing-surface-h.md) | This file declares the functions related to the surface in the drawing module, including creating, destroying, and using the surface. |
| [drawing_brush.h](capi-drawing-brush-h.md) | This file declares the functions related to the brush in the drawing module. |
| [drawing_mask_filter.h](capi-drawing-mask-filter-h.md) | This file declares the functions related to the mask filter in the drawing module. |
| [drawing_text_declaration.h](capi-drawing-text-declaration-h.md) | Provides declarations of data structures related to 2D text drawing. |
| [drawing_text_font_descriptor.h](capi-drawing-text-font-descriptor-h.md) | Defines APIs related to font information, such as obtaining font information, finding and matching specified fonts, reading font descriptor properties, and obtaining Unicode codes and font counts. |
| [drawing_record_cmd.h](capi-drawing-record-cmd-h.md) | This file declares the functions related to a recording command object. |
| [drawing_font_collection.h](capi-drawing-font-collection-h.md) | Defines functions related to font collections in the drawing module, which are used to manage font resources required for text typography. It supports creating independent or shareable font collection objects to meet text typography requirements in different scenarios. Through font collection objects, you can implement custom font loading, system font management, font cache cleanup, and other functions. |
| [drawing_sampling_options.h](capi-drawing-sampling-options-h.md) | This file declares the functions related to sampling in the drawing module. It is used for image or texture sampling. |
| [drawing_text_lineTypography.h](capi-drawing-text-linetypography-h.md) | Provides APIs related to typography lines, such as obtaining the number of characters that can be typeset starting from a specified position. |
| [drawing_pixel_map.h](capi-drawing-pixel-map-h.md) | This file declares the functions related to the pixel map in the drawing module. |
| [drawing_typeface.h](capi-drawing-typeface-h.md) | This file declares the functions related to the typeface in the drawing module. Different platforms have their own default typefaces. You can also parse the .ttf file to obtain the typefaces specified by the third party, such as SimSun and SimHei. |
| [drawing_color.h](capi-drawing-color-h.md) | This file declares the functions related to the color in the drawing module. |
| [drawing_shader_effect.h](capi-drawing-shader-effect-h.md) | This file declares the functions related to the shader effect in the drawing module. |
| [drawing_font.h](capi-drawing-font-h.md) | This file declares the functions related to the font in the drawing module. |
| [drawing_rect.h](capi-drawing-rect-h.md) | This file declares the functions related to the rectangle in the drawing module. |
| [drawing_types.h](capi-drawing-types-h.md) | This file declares the data types of the canvas, brush, pen, bitmap, and path used to draw 2D graphics. |
| [drawing_font_mgr.h](capi-drawing-font-mgr-h.md) | Declares functions related to system font management, used to match and obtain fonts preset in the system. OH_Drawing_FontMgr (font manager) manages the font families preset in the system. Each font family corresponds to a font style set {@link OH_Drawing_FontStyleSet}, and each style set contains multiple typeface objects<br>{@link OH_Drawing_Typeface}. |
| [drawing_text_typography.h](capi-drawing-text-typography-h.md) | This file declares the functions related to typography in the drawing module. |
| [drawing_path.h](capi-drawing-path-h.md) | This file declares the functions related to the path in the drawing module. |
| [drawing_color_filter.h](capi-drawing-color-filter-h.md) | This file declares the functions related to the color filter in the drawing module. |
| [drawing_register_font.h](capi-drawing-register-font-h.md) | Defines functions related to the font manager in the drawing module, providing capabilities for registering and unregistering custom fonts as well as detecting font formats, and supporting multiple font file formats such as ttf, otf, ttc, and otc. |
| [drawing_image.h](capi-drawing-image-h.md) | This file declares the functions related to the image in the drawing module. |
| [drawing_image_filter.h](capi-drawing-image-filter-h.md) | This file declares the functions related to the image filter in the drawing module. |
| [drawing_path_effect.h](capi-drawing-path-effect-h.md) | This file declares the functions related to the path effect in the drawing module. |
| [drawing_region.h](capi-drawing-region-h.md) | This file declares the functions related to the region in the drawing module, including creating a region, setting the boundary, and destroying a region. |
