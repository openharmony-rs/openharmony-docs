# drawing_canvas.h

## Overview

This file declares the functions related to the canvas in the drawing module. By default, the canvas has a black brush with anti-aliasing enabled and without any other style. This brush takes effect only when no brush or pen is proactively set in the canvas.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_SrcRectConstraint](#oh_drawing_srcrectconstraint) | OH_Drawing_SrcRectConstraint | Enumerates the constraint types of the source rectangle. |
| [OH_Drawing_PointMode](#oh_drawing_pointmode) | OH_Drawing_PointMode | Enumerates the modes of drawing multiple points. The modes include discrete points, line segments, and open polygons. |
| [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) | OH_Drawing_CanvasClipOp | Enumerates the canvas clipping modes. |
| [OH_Drawing_CanvasShadowFlags](#oh_drawing_canvasshadowflags) | OH_Drawing_CanvasShadowFlags | Enumerates the shadow flags. |
| [OH_Drawing_VertexMode](#oh_drawing_vertexmode) | OH_Drawing_VertexMode | Enumerates the modes of interpreting the geometry of a given vertex. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_Canvas* OH_Drawing_CanvasCreate(void)](#oh_drawing_canvascreate) | Creates an **OH_Drawing_Canvas** object. |
| [OH_Drawing_Canvas* OH_Drawing_CanvasCreateWithPixelMap(OH_Drawing_PixelMap* pixelMap)](#oh_drawing_canvascreatewithpixelmap) | Binds a pixel map to a canvas so that the content drawn on the canvas is output to the pixel map. (This process is called CPU rendering.) A canvas bound to a pixel map is a non-recording canvas. You should unbind the pixel map object by calling {@link OH_Drawing_PixelMapDissolve} after the canvas object is destroyed. |
| [void OH_Drawing_CanvasDestroy(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasdestroy) | Destroys an **OH_Drawing_Canvas** object and reclaims the memory occupied by the object. |
| [void OH_Drawing_CanvasBind(OH_Drawing_Canvas* canvas, OH_Drawing_Bitmap* bitmap)](#oh_drawing_canvasbind) | Binds a bitmap to a canvas so that the content drawn on the canvas is output to the bitmap. (This process is called CPU rendering.) A canvas bound to a bitmap is a non-recording canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasAttachPen(OH_Drawing_Canvas* canvas, const OH_Drawing_Pen* pen)](#oh_drawing_canvasattachpen) | Attaches a pen to a canvas so that the canvas can use the style and color of the pen to outline a shape. If the pen effect changes after this function is called, you must call the function again to use the new effect in the subsequent drawing. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDetachPen(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasdetachpen) | Detaches the pen from a canvas so that the canvas can no longer use the style and color of the pen to outline a shape. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasAttachBrush(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)](#oh_drawing_canvasattachbrush) | Attaches a brush to a canvas so that the canvas can use the style and color of the brush to fill in a shape. If the brush effect changes after this function is called, you must call the function again to use the new effect in the subsequent drawing. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDetachBrush(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasdetachbrush) | Detaches the brush from a canvas so that the canvas can no longer use the previously set brush to fill in a shape. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasSave(OH_Drawing_Canvas* canvas)](#oh_drawing_canvassave) | Saves the current canvas status (canvas matrix) to the top of the stack. This function works with [OH_Drawing_CanvasRestore](capi-drawing-canvas-h.md#oh_drawing_canvasrestore). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasSaveLayer(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, const OH_Drawing_Brush* brush)](#oh_drawing_canvassavelayer) | Saves the matrix and cropping region, and allocates a bitmap for subsequent drawing. If you call [OH_Drawing_CanvasRestore](capi-drawing-canvas-h.md#oh_drawing_canvasrestore), changes made to the matrix and clipping region are discarded, and the bitmap is drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasRestore(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasrestore) | Restores the canvas status (canvas matrix) saved on the top of the stack. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [uint32_t OH_Drawing_CanvasGetSaveCount(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasgetsavecount) | Obtains the number of canvas statuses (canvas matrices) saved in the stack. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasRestoreToCount(OH_Drawing_Canvas* canvas, uint32_t saveCount)](#oh_drawing_canvasrestoretocount) | Restores to a given number of canvas statuses (canvas matrices). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawLine(OH_Drawing_Canvas* canvas, float x1, float y1, float x2, float y2)](#oh_drawing_canvasdrawline) | Draws a line segment. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path)](#oh_drawing_canvasdrawpath) | Draws a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapMesh(OH_Drawing_Canvas* cCanvas, OH_Drawing_PixelMap* pixelMap, uint32_t meshWidth, uint32_t meshHeight, const float* vertices, uint32_t verticesSize, uint32_t vertOffset, const uint32_t* colors, uint32_t colorsSize, uint32_t colorOffset)](#oh_drawing_canvasdrawpixelmapmesh) | Draws a PixelMap based on a mesh, where mesh vertices are evenly distributed across the PixelMap. (This API works with brushes but not pens.) |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapNine(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* center, const OH_Drawing_Rect* dst, OH_Drawing_FilterMode mode)](#oh_drawing_canvasdrawpixelmapnine) | Splits a pixel map into nine sections using two horizontal and two vertical lines: four edge sections, four corner sections, and a central section. If the four corner sections are smaller than the target rectangle, they will be drawn in the target rectangle without scaling. Otherwise, they will be scaled to fit the target rectangle. Any remaining space will be filled by stretching or compressing the other five sections to cover the entire target rectangle. |
| [void OH_Drawing_CanvasDrawPixelMapRect(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_canvasdrawpixelmaprect) | Draws a portion of a pixel map onto a specified area of the canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **pixelMap**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapRectConstraint(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions, OH_Drawing_SrcRectConstraint constraint)](#oh_drawing_canvasdrawpixelmaprectconstraint) | Draws a portion of a pixel map onto a specified area of the canvas. |
| [void OH_Drawing_CanvasDrawBackground(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)](#oh_drawing_canvasdrawbackground) | Draws a background filled with a brush. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region)](#oh_drawing_canvasdrawregion) | Draws a region. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **region** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPoint(OH_Drawing_Canvas* canvas, const OH_Drawing_Point2D* point)](#oh_drawing_canvasdrawpoint) | Draws a point. |
| [void OH_Drawing_CanvasDrawPoints(OH_Drawing_Canvas* canvas, OH_Drawing_PointMode mode, uint32_t count, const OH_Drawing_Point2D* point2D)](#oh_drawing_canvasdrawpoints) | Draws multiple points. You can draw a single point, a line segment, or an open polygon. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **point2D** is NULL, or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **mode** is not within the enumerated range, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_CanvasDrawBitmap(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap, float left, float top)](#oh_drawing_canvasdrawbitmap) | Draws a bitmap. A bitmap, also referred to as a dot matrix image, a pixel map image, or a grid image, includes single points called pixels (image elements). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawBitmapRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_canvasdrawbitmaprect) | Draws a portion of a bitmap onto a specified area of the canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **bitmap**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)](#oh_drawing_canvasdrawrect) | Draws a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **OH_Drawing_Rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawCircle(OH_Drawing_Canvas* canvas, const OH_Drawing_Point* point, float radius)](#oh_drawing_canvasdrawcircle) | Draws a circle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **point** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **radius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawColor(OH_Drawing_Canvas* canvas, uint32_t color, OH_Drawing_BlendMode blendMode)](#oh_drawing_canvasdrawcolor) | Fills the entire canvas with the specified color and blend mode. |
| [void OH_Drawing_CanvasDrawOval(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)](#oh_drawing_canvasdrawoval) | Draws an oval. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawArc(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)](#oh_drawing_canvasdrawarc) | Draws an arc. If the absolute value of the sweep angle exceeds 360 degrees, an ellipse is drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawArcWithCenter(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle, bool useCenter)](#oh_drawing_canvasdrawarcwithcenter) | Draws an arc. It enables you to define the start angle, sweep angle, and whether the arc's endpoints should connect to its center. |
| [void OH_Drawing_CanvasDrawRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect)](#oh_drawing_canvasdrawroundrect) | Draws a rounded rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawNestedRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* outer, const OH_Drawing_RoundRect* inner)](#oh_drawing_canvasdrawnestedroundrect) | Draws two nested rounded rectangles. The outer rectangle boundary must contain the inner rectangle boundary. Otherwise, there is no drawing effect. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacter(OH_Drawing_Canvas* canvas, const char* str, const OH_Drawing_Font* font, float x, float y)](#oh_drawing_canvasdrawsinglecharacter) | Draws a single character. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacterWithFeatures(OH_Drawing_Canvas* canvas, const char* str, const OH_Drawing_Font* font, float x, float y, OH_Drawing_FontFeatures* fontFeatures)](#oh_drawing_canvasdrawsinglecharacterwithfeatures) | Draws a single character with font features. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character. |
| [void OH_Drawing_CanvasDrawTextBlob(OH_Drawing_Canvas* canvas, const OH_Drawing_TextBlob* textBlob, float x, float y)](#oh_drawing_canvasdrawtextblob) | Draws a text blob. If the typeface used to construct **OH_Drawing_TextBlob** does not support a character, that character will not be drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawGlyphs(const OH_Drawing_Canvas* canvas, const int* glyphIds, int glyphIdCount, int glyphIdOffset, const OH_Drawing_Point2D* positions, int positionCount, int positionOffset, int glyphCount, const OH_Drawing_Font* font)](#oh_drawing_canvasdrawglyphs) | Draws the array of glyphs with specified font. Nothing is drawn if glyphCount is smaller than or equals to 0. |
| [void OH_Drawing_CanvasClipRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)](#oh_drawing_canvascliprect) | Clips a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_CanvasClipRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect, OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)](#oh_drawing_canvascliproundrect) | Clips a rounded rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_CanvasClipPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path, OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)](#oh_drawing_canvasclippath) | Clips a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasClipRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region, OH_Drawing_CanvasClipOp clipOp)](#oh_drawing_canvasclipregion) | Clips a rectangle. |
| [void OH_Drawing_CanvasRotate(OH_Drawing_Canvas* canvas, float degrees, float px, float py)](#oh_drawing_canvasrotate) | Rotates a canvas by a given angle. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasTranslate(OH_Drawing_Canvas* canvas, float dx, float dy)](#oh_drawing_canvastranslate) | Translates a canvas by a given distance. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasScale(OH_Drawing_Canvas* canvas, float sx, float sy)](#oh_drawing_canvasscale) | Scales a canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasSkew(OH_Drawing_Canvas* canvas, float sx, float sy)](#oh_drawing_canvasskew) | Skews a canvas. This function premultiplies the current canvas matrix by a skew transformation matrix and applies the resulting matrix to the canvas. The skew transformation matrix is as follows:
\|1 sx 0\|
\|sy 1 0\|
\|0 0 1\| This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [int32_t OH_Drawing_CanvasGetWidth(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasgetwidth) | Obtains the canvas width. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [int32_t OH_Drawing_CanvasGetHeight(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasgetheight) | Obtains the canvas height. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasGetLocalClipBounds(OH_Drawing_Canvas* canvas, OH_Drawing_Rect* rect)](#oh_drawing_canvasgetlocalclipbounds) | Obtains the bounds of the cropping region of the canvas. This function cannot be used for a canvas of the recording type. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasGetTotalMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)](#oh_drawing_canvasgettotalmatrix) | Obtains the 3x3 matrix of a canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasConcatMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)](#oh_drawing_canvasconcatmatrix) | Preconcats the existing matrix of the canvas with the passed-in matrix. The drawing operation triggered before this API is called is not affected. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawShadow(OH_Drawing_Canvas* canvas, OH_Drawing_Path* path, OH_Drawing_Point3D planeParams, OH_Drawing_Point3D devLightPos, float lightRadius, uint32_t ambientColor, uint32_t spotColor, OH_Drawing_CanvasShadowFlags flag)](#oh_drawing_canvasdrawshadow) | Draws a spot shadow and uses a given path to outline the ambient shadow. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **flag** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_CanvasClear(OH_Drawing_Canvas* canvas, uint32_t color)](#oh_drawing_canvasclear) | Clears a canvas by using a given color. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasSetMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)](#oh_drawing_canvassetmatrix) | Sets the matrix status for a canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasResetMatrix(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasresetmatrix) | Resets the matrix of this canvas to an identity matrix. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasResetClip(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasresetclip) | Reset the clip status. |
| [void OH_Drawing_CanvasDrawImageRectWithSrc(OH_Drawing_Canvas* canvas, const OH_Drawing_Image* image, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions, OH_Drawing_SrcRectConstraint srcRectConstraint)](#oh_drawing_canvasdrawimagerectwithsrc) | Draws a portion of an image onto a specified area of the canvas. The area selected by the source rectangle is scaled and translated to the destination rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **image**, **src**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawImageRect(OH_Drawing_Canvas* canvas, OH_Drawing_Image* image, OH_Drawing_Rect* rect, OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_canvasdrawimagerect) | Draws an image onto a specified area of the canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **image**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_CanvasDrawVertices(OH_Drawing_Canvas* canvas, OH_Drawing_VertexMode vertexMmode, int32_t vertexCount, const OH_Drawing_Point2D* positions, const OH_Drawing_Point2D* texs, const uint32_t* colors, int32_t indexCount, const uint16_t* indices, OH_Drawing_BlendMode mode)](#oh_drawing_canvasdrawvertices) | Draws a triangular grid described by a vertex array. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **positions** is NULL, **vertexCount** is less than 3, or **indexCount** is less than 3 but not 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If either **vertexMmode** or **mode** is not set to one of the enumerated values, **<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [bool OH_Drawing_CanvasReadPixels(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo, void* dstPixels, uint32_t dstRowBytes, int32_t srcX, int32_t srcY)](#oh_drawing_canvasreadpixels) | Copies pixel data from a canvas to a specified address. This function cannot be used for a canvas of the recording type. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **imageInfo**, or **dstPixels** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_CanvasReadPixelsToBitmap(OH_Drawing_Canvas* canvas, OH_Drawing_Bitmap* bitmap, int32_t srcX, int32_t srcY)](#oh_drawing_canvasreadpixelstobitmap) | Copies pixel data from a canvas to an image. This function cannot be used for a canvas of the recording type. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasIsClipEmpty(OH_Drawing_Canvas* canvas, bool* isClipEmpty)](#oh_drawing_canvasisclipempty) | Checks whether the region that can be drawn is empty after clipping. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasGetImageInfo(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo)](#oh_drawing_canvasgetimageinfo) | Obtains the image information of a canvas. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmd(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)](#oh_drawing_canvasdrawrecordcmd) | Draws an **OH_Drawing_RecordCmd** object. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmdNesting(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)](#oh_drawing_canvasdrawrecordcmdnesting) | Draws an **OH_Drawing_RecordCmd** object. This API supports nesting. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path, bool* quickReject)](#oh_drawing_canvasquickrejectpath) | Checks whether the path is not intersecting with the canvas area. The canvas area includes its boundaries. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, bool* quickReject)](#oh_drawing_canvasquickrejectrect) | Checks whether the rectangle is not intersecting with the canvas area. The canvas area includes its boundaries. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasIsOpaque(const OH_Drawing_Canvas* canvas, bool* isOpaque)](#oh_drawing_canvasisopaque) | Checks if the current layer that drawn into the device is opaque. |

## Enum type description

### OH_Drawing_SrcRectConstraint

```c
enum OH_Drawing_SrcRectConstraint
```

**Description**

Enumerates the constraint types of the source rectangle.

**Since**: 12

| Enum item | Description |
| -- | -- |
| STRICT_SRC_RECT_CONSTRAINT | The source rectangle must be completely contained in the image. |
| FAST_SRC_RECT_CONSTRAINT | The source rectangle can be partly outside the image. |

### OH_Drawing_PointMode

```c
enum OH_Drawing_PointMode
```

**Description**

Enumerates the modes of drawing multiple points. The modes include discrete points, line segments, and open polygons.

**Since**: 12

| Enum item | Description |
| -- | -- |
| POINT_MODE_POINTS | Draws each point separately. |
| POINT_MODE_LINES | Draws every two points as a line segment. |
| POINT_MODE_POLYGON | Draws an array of points as an open polygon. |

### OH_Drawing_CanvasClipOp

```c
enum OH_Drawing_CanvasClipOp
```

**Description**

Enumerates the canvas clipping modes.

**Since**: 11

| Enum item | Description |
| -- | -- |
| DIFFERENCE | Clips a specified area. That is, the difference set is obtained. |
| INTERSECT | Retains a specified area. That is, the intersection is obtained. |

### OH_Drawing_CanvasShadowFlags

```c
enum OH_Drawing_CanvasShadowFlags
```

**Description**

Enumerates the shadow flags.

**Since**: 12

| Enum item | Description |
| -- | -- |
| SHADOW_FLAGS_NONE | There is no shadow flag. |
| SHADOW_FLAGS_TRANSPARENT_OCCLUDER | The occluding object is transparent. |
| SHADOW_FLAGS_GEOMETRIC_ONLY | No analysis on the shadows is required. |
| SHADOW_FLAGS_ALL | All the preceding shadow flags are used. |

### OH_Drawing_VertexMode

```c
enum OH_Drawing_VertexMode
```

**Description**

Enumerates the modes of interpreting the geometry of a given vertex.

**Since**: 12

| Enum item | Description |
| -- | -- |
| VERTEX_MODE_TRIANGLES | Draws a triangle list. Specifically, a list of isolated triangles are drawn using every three vertices. If the number of vertices is not a multiple of 3, the extra vertices will be ignored. |
| VERTEX_MODE_TRIANGLES_STRIP | Draws a triangle strip. Specifically, the first triangle is drawn between the first 3 vertices, and all subsequent triangles use the previous 2 vertices plus the next additional vertex. |
| VERTEX_MODE_TRIANGLE_FAN | Draws a triangle fan. A triangle fan is similar to a triangle strip, except that all the triangles share one vertex (the first vertex). |


## Function description

### OH_Drawing_CanvasCreate()

```c
OH_Drawing_Canvas* OH_Drawing_CanvasCreate(void)
```

**Description**

Creates an **OH_Drawing_Canvas** object.

**Since**: 8

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Canvas* | Returns the pointer to the OH_Drawing_Canvas object created. |

### OH_Drawing_CanvasCreateWithPixelMap()

```c
OH_Drawing_Canvas* OH_Drawing_CanvasCreateWithPixelMap(OH_Drawing_PixelMap* pixelMap)
```

**Description**

Binds a pixel map to a canvas so that the content drawn on the canvas is output to the pixel map. (This process is called CPU rendering.) A canvas bound to a pixel map is a non-recording canvas. You should unbind the pixel map object by calling {@link OH_Drawing_PixelMapDissolve} after the canvas object is destroyed.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_PixelMap* pixelMap | Pointer to the {@link OH_Drawing_PixelMap} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Canvas* | Pointer to the created canvas object {@link OH_Drawing_Canvas}. If the returned object is NULL, the creation  fails due to insufficient memory or an empty pixel map object. |

### OH_Drawing_CanvasDestroy()

```c
void OH_Drawing_CanvasDestroy(OH_Drawing_Canvas* canvas)
```

**Description**

Destroys an **OH_Drawing_Canvas** object and reclaims the memory occupied by the object.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |

### OH_Drawing_CanvasBind()

```c
void OH_Drawing_CanvasBind(OH_Drawing_Canvas* canvas, OH_Drawing_Bitmap* bitmap)
```

**Description**

Binds a bitmap to a canvas so that the content drawn on the canvas is output to the bitmap. (This process is called CPU rendering.) A canvas bound to a bitmap is a non-recording canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |

### OH_Drawing_CanvasAttachPen()

```c
void OH_Drawing_CanvasAttachPen(OH_Drawing_Canvas* canvas, const OH_Drawing_Pen* pen)
```

**Description**

Attaches a pen to a canvas so that the canvas can use the style and color of the pen to outline a shape. If the pen effect changes after this function is called, you must call the function again to use the new effect in the subsequent drawing. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **pen** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Pen* pen | Pointer to an **OH_Drawing_Pen** object. |

### OH_Drawing_CanvasDetachPen()

```c
void OH_Drawing_CanvasDetachPen(OH_Drawing_Canvas* canvas)
```

**Description**

Detaches the pen from a canvas so that the canvas can no longer use the style and color of the pen to outline a shape. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |

### OH_Drawing_CanvasAttachBrush()

```c
void OH_Drawing_CanvasAttachBrush(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)
```

**Description**

Attaches a brush to a canvas so that the canvas can use the style and color of the brush to fill in a shape. If the brush effect changes after this function is called, you must call the function again to use the new effect in the subsequent drawing. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Brush* brush | Pointer to an **OH_Drawing_Brush** object. |

### OH_Drawing_CanvasDetachBrush()

```c
void OH_Drawing_CanvasDetachBrush(OH_Drawing_Canvas* canvas)
```

**Description**

Detaches the brush from a canvas so that the canvas can no longer use the previously set brush to fill in a shape. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |

### OH_Drawing_CanvasSave()

```c
void OH_Drawing_CanvasSave(OH_Drawing_Canvas* canvas)
```

**Description**

Saves the current canvas status (canvas matrix) to the top of the stack. This function works with [OH_Drawing_CanvasRestore](capi-drawing-canvas-h.md#oh_drawing_canvasrestore). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |

### OH_Drawing_CanvasSaveLayer()

```c
void OH_Drawing_CanvasSaveLayer(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, const OH_Drawing_Brush* brush)
```

**Description**

Saves the matrix and cropping region, and allocates a bitmap for subsequent drawing. If you call [OH_Drawing_CanvasRestore](capi-drawing-canvas-h.md#oh_drawing_canvasrestore), changes made to the matrix and clipping region are discarded, and the bitmap is drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object, which is used to limit the layer size. A null pointer means no limit. |
| const OH_Drawing_Brush* brush | Pointer to an {@link OH_Drawing_Brush} object. The alpha value, filter effect, and blend mode of the brush are applied when the bitmap is drawn. If NULL is passed in, no effect is applied. |

### OH_Drawing_CanvasRestore()

```c
void OH_Drawing_CanvasRestore(OH_Drawing_Canvas* canvas)
```

**Description**

Restores the canvas status (canvas matrix) saved on the top of the stack. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |

### OH_Drawing_CanvasGetSaveCount()

```c
uint32_t OH_Drawing_CanvasGetSaveCount(OH_Drawing_Canvas* canvas)
```

**Description**

Obtains the number of canvas statuses (canvas matrices) saved in the stack. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns a 32-bit value that describes the number of canvas statuses (canvas matrices). The initial number is  1. |

### OH_Drawing_CanvasRestoreToCount()

```c
void OH_Drawing_CanvasRestoreToCount(OH_Drawing_Canvas* canvas, uint32_t saveCount)
```

**Description**

Restores to a given number of canvas statuses (canvas matrices). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| uint32_t saveCount | Number of canvas statuses (canvas matrices). If the value is less than or equal to 1, the canvas is restored to the initial state. If the value is greater than the number of canvas statuses that have been saved, no operation is performed. |

### OH_Drawing_CanvasDrawLine()

```c
void OH_Drawing_CanvasDrawLine(OH_Drawing_Canvas* canvas, float x1, float y1, float x2, float y2)
```

**Description**

Draws a line segment. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| float x1 | X coordinate of the start point of the line segment. |
| float y1 | Y coordinate of the start point of the line segment. |
| float x2 | X coordinate of the end point of the line segment. |
| float y2 | Y coordinate of the end point of the line segment. |

### OH_Drawing_CanvasDrawPath()

```c
void OH_Drawing_CanvasDrawPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path)
```

**Description**

Draws a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |

### OH_Drawing_CanvasDrawPixelMapMesh()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapMesh(OH_Drawing_Canvas* cCanvas, OH_Drawing_PixelMap* pixelMap, uint32_t meshWidth, uint32_t meshHeight, const float* vertices, uint32_t verticesSize, uint32_t vertOffset, const uint32_t* colors, uint32_t colorsSize, uint32_t colorOffset)
```

**Description**

Draws a PixelMap based on a mesh, where mesh vertices are evenly distributed across the PixelMap. (This API works with brushes but not pens.)

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* cCanvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_PixelMap* pixelMap | Pointer to the {@link OH_Drawing_PixelMap} object. |
| uint32_t meshWidth | Number of columns in the mesh. The value is an integer greater than 0. |
| uint32_t meshHeight | Number of rows in the mesh. The value is an integer greater than 0. |
| const float* vertices | Pointer to the mesh vertex array. |
| uint32_t verticesSize | Size of the mesh vertex array. The value must be ((meshWidth + 1) * (meshHeight + 1) + vertoffset) * 2. |
| uint32_t vertOffset | Number of vertices to skip before drawing. The value is an integer greater than or equal to 0. |
| const uint32_t* colors | Pointer to the mesh color array, which can be null. |
| uint32_t colorsSize | Size of the mesh color array. If the array exists, the size must be (meshWidth + 1) * (meshHeight + 1) + colorOffset. |
| uint32_t colorOffset | Number of colors to skip before drawing. The value is an integer greater than or equal to 0. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if any of the parameters, such as cCanvas, pixelMap, and vertices  , is empty or the input parameter does not meet the value rule. |

### OH_Drawing_CanvasDrawPixelMapNine()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapNine(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* center, const OH_Drawing_Rect* dst, OH_Drawing_FilterMode mode)
```

**Description**

Splits a pixel map into nine sections using two horizontal and two vertical lines: four edge sections, four corner sections, and a central section. If the four corner sections are smaller than the target rectangle, they will be drawn in the target rectangle without scaling. Otherwise, they will be scaled to fit the target rectangle. Any remaining space will be filled by stretching or compressing the other five sections to cover the entire target rectangle.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_PixelMap* pixelMap | Pointer to the {@link OH_Drawing_PixelMap} object. |
| const OH_Drawing_Rect* center | Pointer to the {@link OH_Drawing_Rect} object, which indicates the central rectangle splitting the pixel map. It divides the image into nine sections by extending its four edges. |
| const OH_Drawing_Rect* dst | Pointer to the {@link OH_Drawing_Rect} object, which indicates the target region on the canvas. |
| OH_Drawing_FilterMode mode | Enumeration of filter modes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if canvas, pixelMap, or dst is NULL. |

### OH_Drawing_CanvasDrawPixelMapRect()

```c
void OH_Drawing_CanvasDrawPixelMapRect(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Draws a portion of a pixel map onto a specified area of the canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **pixelMap**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_PixelMap* pixelMap | Pointer to the {@link OH_Drawing_PixelMap} object. |
| const OH_Drawing_Rect* src | Pointer to a rectangle on the pixel map. If NULL is passed in, it refers to the entire pixel map. |
| const OH_Drawing_Rect* dst | Pointer to a rectangle on the canvas. |
| const OH_Drawing_SamplingOptions* samplingOptions | Pointer to the {@link OH_Drawing_SamplingOptions} object. A null pointer means that the default sampling options are used. |

### OH_Drawing_CanvasDrawPixelMapRectConstraint()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapRectConstraint(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions, OH_Drawing_SrcRectConstraint constraint)
```

**Description**

Draws a portion of a pixel map onto a specified area of the canvas.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_PixelMap* pixelMap | Pointer to the {@link OH_Drawing_PixelMap} object. |
| const OH_Drawing_Rect* src | Pointer to a rectangle on the pixel map. If NULL is passed in, it refers to the entire pixel map. |
| const OH_Drawing_Rect* dst | Pointer to a rectangle on the canvas. |
| const OH_Drawing_SamplingOptions* samplingOptions | Pointer to the {@link OH_Drawing_SamplingOptions} object. A null pointer means that the default sampling options are used. |
| [OH_Drawing_SrcRectConstraint](capi-drawing-canvas-h.md#oh_drawing_srcrectconstraint) constraint | Constraint type. For details about the available options, see [OH_Drawing_SrcRectConstraint](capi-drawing-canvas-h.md#oh_drawing_srcrectconstraint). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if canvas, pixelMap, or dst is NULL. |

### OH_Drawing_CanvasDrawBackground()

```c
void OH_Drawing_CanvasDrawBackground(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)
```

**Description**

Draws a background filled with a brush. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Brush* brush | Pointer to an **OH_Drawing_Brush** object. |

### OH_Drawing_CanvasDrawRegion()

```c
void OH_Drawing_CanvasDrawRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region)
```

**Description**

Draws a region. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **region** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Region* region | Pointer to an **OH_Drawing_Region** object. |

### OH_Drawing_CanvasDrawPoint()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPoint(OH_Drawing_Canvas* canvas, const OH_Drawing_Point2D* point)
```

**Description**

Draws a point.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Point2D* point | Pointer to the {@link OH_Drawing_Point2D} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or point is NULL. |

### OH_Drawing_CanvasDrawPoints()

```c
void OH_Drawing_CanvasDrawPoints(OH_Drawing_Canvas* canvas, OH_Drawing_PointMode mode, uint32_t count, const OH_Drawing_Point2D* point2D)
```

**Description**

Draws multiple points. You can draw a single point, a line segment, or an open polygon. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **point2D** is NULL, or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **mode** is not within the enumerated range, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| [OH_Drawing_PointMode](capi-drawing-canvas-h.md#oh_drawing_pointmode) mode | Mode for drawing multiple points. For details, see [OH_Drawing_PointMode](capi-drawing-canvas-h.md#oh_drawing_pointmode). |
| uint32_t count | Number of vertices, that is, the number of vertices in the vertex array. |
| const OH_Drawing_Point2D* point2D | Pointer to an array holding the vertices. |

### OH_Drawing_CanvasDrawBitmap()

```c
void OH_Drawing_CanvasDrawBitmap(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap, float left, float top)
```

**Description**

Draws a bitmap. A bitmap, also referred to as a dot matrix image, a pixel map image, or a grid image, includes single points called pixels (image elements). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Bitmap* bitmap | Pointer to an **OH_Drawing_Bitmap** object. |
| float left | X coordinate of the upper left corner of the bitmap. |
| float top | Y coordinate of the upper left corner of the bitmap. |

### OH_Drawing_CanvasDrawBitmapRect()

```c
void OH_Drawing_CanvasDrawBitmapRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Draws a portion of a bitmap onto a specified area of the canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **bitmap**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Bitmap* bitmap | Pointer to the {@link OH_Drawing_Bitmap} object. |
| const OH_Drawing_Rect* src | Pointer to a rectangle on the bitmap. If NULL is passed in, it refers to the entire bitmap. |
| const OH_Drawing_Rect* dst | Pointer to a rectangle on the canvas. |
| const OH_Drawing_SamplingOptions* samplingOptions | Pointer to the {@link OH_Drawing_SamplingOptions} object. A null pointer means that the default sampling options are used. |

### OH_Drawing_CanvasDrawRect()

```c
void OH_Drawing_CanvasDrawRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)
```

**Description**

Draws a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **OH_Drawing_Rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

### OH_Drawing_CanvasDrawCircle()

```c
void OH_Drawing_CanvasDrawCircle(OH_Drawing_Canvas* canvas, const OH_Drawing_Point* point, float radius)
```

**Description**

Draws a circle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **point** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **radius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Point* point | Pointer to an **OH_Drawing_Point** object, which indicates the center of the circle. |
| float radius | Radius of the circle. The value is invalid if it is less than or equal to 0. |

### OH_Drawing_CanvasDrawColor()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawColor(OH_Drawing_Canvas* canvas, uint32_t color, OH_Drawing_BlendMode blendMode)
```

**Description**

Fills the entire canvas with the specified color and blend mode.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| uint32_t color | Color, represented by a 32-bit (ARGB) variable. |
| OH_Drawing_BlendMode blendMode | Blend mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if canvas is NULL.  OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if blendMode is not set to one of the enumerated values. |

### OH_Drawing_CanvasDrawOval()

```c
void OH_Drawing_CanvasDrawOval(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)
```

**Description**

Draws an oval. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

### OH_Drawing_CanvasDrawArc()

```c
void OH_Drawing_CanvasDrawArc(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)
```

**Description**

Draws an arc. If the absolute value of the sweep angle exceeds 360 degrees, an ellipse is drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| float startAngle | Start angle. When the degree is 0, the start point is located at the right end of the oval. A positive number indicates that the start point is placed clockwise, and a negative number indicates that the start point is placed counterclockwise. |
| float sweepAngle | Angle to sweep, in degrees. A positive number indicates a clockwise sweep, and a negative value indicates a counterclockwise swipe. The valid range is from -360 degrees to 360 degrees. If the absolute value of the sweep angle exceeds 360 degrees, an ellipse is drawn. |

### OH_Drawing_CanvasDrawArcWithCenter()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawArcWithCenter(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle, bool useCenter)
```

**Description**

Draws an arc. It enables you to define the start angle, sweep angle, and whether the arc's endpoints should connect to its center.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| float startAngle | Start angle, in degrees. The value is a floating point number. When the degree is 0, the start point is located at the right end of the oval. A positive number indicates that the start point is placed clockwise, and a negative number indicates that the start point is placed counterclockwise. |
| float sweepAngle | Angle to sweep, in degrees. The value is a floating point number. A positive number indicates a clockwise sweep, and a negative value indicates a counterclockwise swipe. The swipe angle can exceed 360 degrees, and a complete ellipse is drawn. |
| bool useCenter | Whether the start point and end point of the arc are connected to its center. The value **true**<br>means that they are connected to the center; the value **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or rect is NULL. |

### OH_Drawing_CanvasDrawRoundRect()

```c
void OH_Drawing_CanvasDrawRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect)
```

**Description**

Draws a rounded rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_RoundRect* roundRect | Pointer to an **OH_Drawing_RoundRect** object. |

### OH_Drawing_CanvasDrawNestedRoundRect()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawNestedRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* outer, const OH_Drawing_RoundRect* inner)
```

**Description**

Draws two nested rounded rectangles. The outer rectangle boundary must contain the inner rectangle boundary. Otherwise, there is no drawing effect.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_RoundRect* outer | Pointer to the {@link OH_Drawing_RoundRect} object, indicating the outer rounded rectangle. |
| const OH_Drawing_RoundRect* inner | Pointer to the {@link OH_Drawing_RoundRect} object, indicating the inner rounded rectangle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if canvas, outer, or inner is NULL. |

### OH_Drawing_CanvasDrawSingleCharacter()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacter(OH_Drawing_Canvas* canvas, const char* str, const OH_Drawing_Font* font, float x, float y)
```

**Description**

Draws a single character. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const char* str | Pointer to the single character to draw. A string can be passed in, but only the first character in the string is parsed and drawn in UTF-8 encoding. |
| const OH_Drawing_Font* font | Pointer to the {@link OH_Drawing_Font} object. |
| float x | X coordinate of the left point of the character baseline. |
| float y | Y coordinate of the left point of the character baseline. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if at least one of the parameters canvas, str, or font is NULL,  or the length of str is 0. |

### OH_Drawing_CanvasDrawSingleCharacterWithFeatures()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacterWithFeatures(OH_Drawing_Canvas* canvas, const char* str, const OH_Drawing_Font* font, float x, float y, OH_Drawing_FontFeatures* fontFeatures)
```

**Description**

Draws a single character with font features. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const char* str | Pointer to the single character to draw. A string can be passed in, but only the first character in the string is parsed and drawn in UTF-8 encoding. |
| const OH_Drawing_Font* font | Pointer to the {@link OH_Drawing_Font} object. |
| float x | X coordinate of the left point of the character baseline. |
| float y | Y coordinate of the left point of the character baseline. |
| OH_Drawing_FontFeatures* fontFeatures | Pointer to the {@link OH_Drawing_FontFeatures} object. If no font feature is set, the preset font feature in the TrueType fonts (TTF) file is used. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if at least one of the parameters canvas, str, font, or   fontFeatures is NULL, or the length of str is 0. |

### OH_Drawing_CanvasDrawTextBlob()

```c
void OH_Drawing_CanvasDrawTextBlob(OH_Drawing_Canvas* canvas, const OH_Drawing_TextBlob* textBlob, float x, float y)
```

**Description**

Draws a text blob. If the typeface used to construct **OH_Drawing_TextBlob** does not support a character, that character will not be drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_TextBlob* textBlob | Pointer to an **OH_Drawing_TextBlob** object. |
| float x | X coordinate of the left point of the text baseline. |
| float y | Y coordinate of the left point of the text baseline. |

### OH_Drawing_CanvasDrawGlyphs()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawGlyphs(const OH_Drawing_Canvas* canvas, const int* glyphIds, int glyphIdCount, int glyphIdOffset, const OH_Drawing_Point2D* positions, int positionCount, int positionOffset, int glyphCount, const OH_Drawing_Font* font)
```

**Description**

Draws the array of glyphs with specified font. Nothing is drawn if glyphCount is smaller than or equals to 0.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Canvas* canvas | Indicates the pointer to an <b>OH_Drawing_Canvas</b> object. |
| const int* glyphIds | Indicates an array of glyph IDs. |
| int glyphIdCount | Indicates the size of glyphId array. |
| int glyphIdOffset | Indicates the number of elements to skip before drawing in glyphIds array. |
| const OH_Drawing_Point2D* positions | Indicates an array of positions. |
| int positionCount | Indicates the size of position array. |
| int positionOffset | Indicates the number of elements to skip before drawing in positions array. |
| int glyphCount | Indicates the number of glyphs to be drawn. |
| const OH_Drawing_Font* font | Indicates the font used for drawing. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.  Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if any of canvas, glyphIds, positions and font is nullptr.<br>Returns {@link OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE} if glyphIdOffset or positionOffset is less than 0, or if  glyphIdCount is less than (glyphIdOffset + glyphCount) or positionCount is less than (positionOffset + glyphCount). |

### OH_Drawing_CanvasClipRect()

```c
void OH_Drawing_CanvasClipRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)
```

**Description**

Clips a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop) clipOp | Clip mode. For details about the available options, see [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop). |
| bool doAntiAlias | Whether to enable anti-aliasing. The value **true** means to enable anti-aliasing, and **false**<br>means the opposite. |

### OH_Drawing_CanvasClipRoundRect()

```c
void OH_Drawing_CanvasClipRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect, OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)
```

**Description**

Clips a rounded rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_RoundRect* roundRect | Pointer to an **OH_Drawing_RoundRect** object. |
| [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop) clipOp | Clip mode. For details about the available options, see [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop). |
| bool doAntiAlias | Whether to perform anti-aliasing. The value **true** means to perform anti-aliasing, and **false**<br>means the opposite. |

### OH_Drawing_CanvasClipPath()

```c
void OH_Drawing_CanvasClipPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path, OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)
```

**Description**

Clips a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| const OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |
| [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop) clipOp | Clip mode. For details about the available options, see [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop). |
| bool doAntiAlias | Whether to enable anti-aliasing. The value **true** means to enable anti-aliasing, and **false**<br>means the opposite. |

### OH_Drawing_CanvasClipRegion()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasClipRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region, OH_Drawing_CanvasClipOp clipOp)
```

**Description**

Clips a rectangle.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Region* region | Pointer to the {@link OH_Drawing_Region} object. |
| [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop) clipOp | Clip mode. For details about the available options, see [OH_Drawing_CanvasClipOp](capi-drawing-canvas-h.md#oh_drawing_canvasclipop). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or region is NULL.  OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if clipOp is not set to one of the enumerated values. |

### OH_Drawing_CanvasRotate()

```c
void OH_Drawing_CanvasRotate(OH_Drawing_Canvas* canvas, float degrees, float px, float py)
```

**Description**

Rotates a canvas by a given angle. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| float degrees | Rotation angle. |
| float px | X coordinate of the rotation point. |
| float py | Y coordinate of the rotation point. |

### OH_Drawing_CanvasTranslate()

```c
void OH_Drawing_CanvasTranslate(OH_Drawing_Canvas* canvas, float dx, float dy)
```

**Description**

Translates a canvas by a given distance. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| float dx | Distance to translate on the X axis. |
| float dy | Distance to translate on the Y axis. |

### OH_Drawing_CanvasScale()

```c
void OH_Drawing_CanvasScale(OH_Drawing_Canvas* canvas, float sx, float sy)
```

**Description**

Scales a canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| float sx | Scale ratio on the X axis. |
| float sy | Scale ratio on the Y axis. |

### OH_Drawing_CanvasSkew()

```c
void OH_Drawing_CanvasSkew(OH_Drawing_Canvas* canvas, float sx, float sy)
```

**Description**

Skews a canvas. This function premultiplies the current canvas matrix by a skew transformation matrix and applies the resulting matrix to the canvas. The skew transformation matrix is as follows:
\|1 sx 0\|
\|sy 1 0\|
\|0 0 1\| This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| float sx | Amount of tilt on the X axis. A positive number tilts the drawing rightwards along the positive direction of the Y axis, and a negative number tilts the drawing leftwards along the positive direction of the Y axis. |
| float sy | Amount of tilt on the Y axis. A positive number tilts the drawing downwards along the positive direction of the X axis, and a negative number tilts the drawing upwards along the positive direction of the X axis. |

### OH_Drawing_CanvasGetWidth()

```c
int32_t OH_Drawing_CanvasGetWidth(OH_Drawing_Canvas* canvas)
```

**Description**

Obtains the canvas width. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the width. |

### OH_Drawing_CanvasGetHeight()

```c
int32_t OH_Drawing_CanvasGetHeight(OH_Drawing_Canvas* canvas)
```

**Description**

Obtains the canvas height. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the height. |

### OH_Drawing_CanvasGetLocalClipBounds()

```c
void OH_Drawing_CanvasGetLocalClipBounds(OH_Drawing_Canvas* canvas, OH_Drawing_Rect* rect)
```

**Description**

Obtains the bounds of the cropping region of the canvas. This function cannot be used for a canvas of the recording type. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. You can call {@link OH_Drawing_RectCreate} to create a rectangle object. |

### OH_Drawing_CanvasGetTotalMatrix()

```c
void OH_Drawing_CanvasGetTotalMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)
```

**Description**

Obtains the 3x3 matrix of a canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Matrix* matrix | Pointer to the {@link OH_Drawing_Matrix} object. You can call {@link OH_Drawing_MatrixCreate} to create a matrix object. |

### OH_Drawing_CanvasConcatMatrix()

```c
void OH_Drawing_CanvasConcatMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)
```

**Description**

Preconcats the existing matrix of the canvas with the passed-in matrix. The drawing operation triggered before this API is called is not affected. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Matrix* matrix | Pointer to the {@link OH_Drawing_Matrix} object. |

### OH_Drawing_CanvasDrawShadow()

```c
void OH_Drawing_CanvasDrawShadow(OH_Drawing_Canvas* canvas, OH_Drawing_Path* path, OH_Drawing_Point3D planeParams, OH_Drawing_Point3D devLightPos, float lightRadius, uint32_t ambientColor, uint32_t spotColor, OH_Drawing_CanvasShadowFlags flag)
```

**Description**

Draws a spot shadow and uses a given path to outline the ambient shadow. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **flag** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object, which is used to generate shadows. |
| OH_Drawing_Point3D planeParams | Z-axis offset of an occluder relative to the canvas, based on its x and y coordinates. |
| OH_Drawing_Point3D devLightPos | Position of the light relative to the canvas. |
| float lightRadius | Radius of the light source. The value must be greater than or equal to 0. |
| uint32_t ambientColor | Ambient shadow color, which is represented by a 32-bit (ARGB) variable. |
| uint32_t spotColor | Point shadow color, which is represented by a 32-bit (ARGB) variable. |
| [OH_Drawing_CanvasShadowFlags](capi-drawing-canvas-h.md#oh_drawing_canvasshadowflags) flag | Enumeration of shadow flags. |

### OH_Drawing_CanvasClear()

```c
void OH_Drawing_CanvasClear(OH_Drawing_Canvas* canvas, uint32_t color)
```

**Description**

Clears a canvas by using a given color. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| uint32_t color | Color, which is a 32-bit (ARGB) variable. |

### OH_Drawing_CanvasSetMatrix()

```c
void OH_Drawing_CanvasSetMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)
```

**Description**

Sets the matrix status for a canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Matrix* matrix | Pointer to the {@link OH_Drawing_Matrix} object. You can call {@link OH_Drawing_MatrixCreate} to create a matrix object. |

### OH_Drawing_CanvasResetMatrix()

```c
void OH_Drawing_CanvasResetMatrix(OH_Drawing_Canvas* canvas)
```

**Description**

Resets the matrix of this canvas to an identity matrix. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |

### OH_Drawing_CanvasResetClip()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasResetClip(OH_Drawing_Canvas* canvas)
```

**Description**

Reset the clip status.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Indicates the pointer to an <b>OH_Drawing_Canvas</b> object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INVALID_PARAMETER} if canvas is nullptr. |

### OH_Drawing_CanvasDrawImageRectWithSrc()

```c
void OH_Drawing_CanvasDrawImageRectWithSrc(OH_Drawing_Canvas* canvas, const OH_Drawing_Image* image, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions, OH_Drawing_SrcRectConstraint srcRectConstraint)
```

**Description**

Draws a portion of an image onto a specified area of the canvas. The area selected by the source rectangle is scaled and translated to the destination rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **image**, **src**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Image* image | Pointer to the {@link OH_Drawing_Image} object. |
| const OH_Drawing_Rect* src | Pointer to the {@link OH_Drawing_Rect} object. |
| const OH_Drawing_Rect* dst | Pointer to the {@link OH_Drawing_Rect} object. |
| const OH_Drawing_SamplingOptions* samplingOptions | Pointer to the {@link OH_Drawing_SamplingOptions} object. A null pointer means that the default sampling options are used. |
| [OH_Drawing_SrcRectConstraint](capi-drawing-canvas-h.md#oh_drawing_srcrectconstraint) srcRectConstraint | Constraint type. For details about the available options, see [OH_Drawing_SrcRectConstraint](capi-drawing-canvas-h.md#oh_drawing_srcrectconstraint). |

### OH_Drawing_CanvasDrawImageRect()

```c
void OH_Drawing_CanvasDrawImageRect(OH_Drawing_Canvas* canvas, OH_Drawing_Image* image, OH_Drawing_Rect* rect, OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Draws an image onto a specified area of the canvas. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **image**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Image* image | Pointer to the {@link OH_Drawing_Image} object. |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| OH_Drawing_SamplingOptions* samplingOptions | Pointer to the {@link OH_Drawing_SamplingOptions} object. A null pointer means that the default sampling options are used. |

### OH_Drawing_CanvasDrawVertices()

```c
void OH_Drawing_CanvasDrawVertices(OH_Drawing_Canvas* canvas, OH_Drawing_VertexMode vertexMmode, int32_t vertexCount, const OH_Drawing_Point2D* positions, const OH_Drawing_Point2D* texs, const uint32_t* colors, int32_t indexCount, const uint16_t* indices, OH_Drawing_BlendMode mode)
```

**Description**

Draws a triangular grid described by a vertex array. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **positions** is NULL, **vertexCount** is less than 3, or **indexCount** is less than 3 but not 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If either **vertexMmode** or **mode** is not set to one of the enumerated values, **<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to an **OH_Drawing_Canvas** object. |
| [OH_Drawing_VertexMode](capi-drawing-canvas-h.md#oh_drawing_vertexmode) vertexMmode | Mode for drawing vertices. For details about the available options, see [OH_Drawing_VertexMode](capi-drawing-canvas-h.md#oh_drawing_vertexmode). |
| int32_t vertexCount | Number of elements in the vertex array. The value must be greater than or equal to 3. |
| const OH_Drawing_Point2D* positions | Pointer to the array that holds the position of every vertex. The array cannot be null and its length must be equal to the value of **vertexCount**. |
| const OH_Drawing_Point2D* texs | Pointer to the array that holds the texture space coordinate corresponding to each vertex. The array can be null. If the array is not null, its length must be equal to the value of **vertexCount**. |
| const uint32_t* colors | Pointer to the array that holds the color corresponding to each vertex. It is used for interpolation in a triangle. The array can be null. If the array is not null, its length must be equal to the value of **<br>vertexCount**. |
| int32_t indexCount | Number of indices. The value can be 0 or a value greater than or equal to 3. |
| const uint16_t* indices | Pointer to the array that holds the index of each vertex. The array can be null. If the array is not null, its length must be equal to the value of **indexCount**. |
| OH_Drawing_BlendMode mode | Enumeration of blend modes. For details about the available options, see {@link OH_Drawing_BlendMode}. |

### OH_Drawing_CanvasReadPixels()

```c
bool OH_Drawing_CanvasReadPixels(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo, void* dstPixels, uint32_t dstRowBytes, int32_t srcX, int32_t srcY)
```

**Description**

Copies pixel data from a canvas to a specified address. This function cannot be used for a canvas of the recording type. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If one of **canvas**, **imageInfo**, or **dstPixels** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Image_Info* imageInfo | Pointer to the {@link OH_Drawing_Image_Info} object. |
| void* dstPixels | Pointer to the start address for storing the pixel data. |
| uint32_t dstRowBytes | Number of bytes in each row of pixels. The value is invalid if it is less than or equal to 0. |
| int32_t srcX | X offset of the pixels on the canvas, in px. |
| int32_t srcY | Y offset of the pixels on the canvas, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the pixel data is copied to the start address of the storage; returns false  otherwise. |

### OH_Drawing_CanvasReadPixelsToBitmap()

```c
bool OH_Drawing_CanvasReadPixelsToBitmap(OH_Drawing_Canvas* canvas, OH_Drawing_Bitmap* bitmap, int32_t srcX, int32_t srcY)
```

**Description**

Copies pixel data from a canvas to an image. This function cannot be used for a canvas of the recording type. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Bitmap* bitmap | Pointer to the {@link OH_Drawing_Bitmap} object. |
| int32_t srcX | X offset of the pixels on the canvas, in px. |
| int32_t srcY | Y offset of the pixels on the canvas, in px. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the pixel data is copied to the image; returns false otherwise. |

### OH_Drawing_CanvasIsClipEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasIsClipEmpty(OH_Drawing_Canvas* canvas, bool* isClipEmpty)
```

**Description**

Checks whether the region that can be drawn is empty after clipping.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| bool* isClipEmpty | Pointer to the variable that specifies whether the region is empty. The value **true** means that the region is empty, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or isClipEmpty is NULL. |

### OH_Drawing_CanvasGetImageInfo()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasGetImageInfo(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo)
```

**Description**

Obtains the image information of a canvas.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| OH_Drawing_Image_Info* imageInfo | Pointer to the {@link OH_Drawing_Image_Info} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or imageInfo is NULL. |

### OH_Drawing_CanvasDrawRecordCmd()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmd(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)
```

**Description**

Draws an **OH_Drawing_RecordCmd** object.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. Only the canvas of the recording type is supported. |
| OH_Drawing_RecordCmd* recordCmd | Pointer to the {@link OH_Drawing_RecordCmd} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or recordCmd is NULL. |

### OH_Drawing_CanvasDrawRecordCmdNesting()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmdNesting(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)
```

**Description**

Draws an **OH_Drawing_RecordCmd** object. This API supports nesting.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. Only the canvas of the recording type is supported. |
| OH_Drawing_RecordCmd* recordCmd | Pointer to the {@link OH_Drawing_RecordCmd} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Operation code.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or recordCmd is NULL. |

### OH_Drawing_CanvasQuickRejectPath()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path, bool* quickReject)
```

**Description**

Checks whether the path is not intersecting with the canvas area. The canvas area includes its boundaries.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool* quickReject | Pointer to the check result. The value **true** means that the path is not intersecting with the canvas area, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if canvas, path, or quickReject is NULL. |

### OH_Drawing_CanvasQuickRejectRect()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, bool* quickReject)
```

**Description**

Checks whether the rectangle is not intersecting with the canvas area. The canvas area includes its boundaries.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Canvas* canvas | Pointer to the {@link OH_Drawing_Canvas} object. |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| bool* quickReject | Pointer to the check result. The value **true** means that the rectangle is not intersecting with the canvas area, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if canvas, rect, or quickReject is NULL. |

### OH_Drawing_CanvasIsOpaque()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasIsOpaque(const OH_Drawing_Canvas* canvas, bool* isOpaque)
```

**Description**

Checks if the current layer that drawn into the device is opaque.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Canvas* canvas | Indicates the pointer to an <b>OH_Drawing_Canvas</b> object. |
| bool* isOpaque | Indicates if the canvas is opaque. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if canvas or isOpaque is nullptr. |


