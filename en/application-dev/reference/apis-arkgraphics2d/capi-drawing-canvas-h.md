# drawing_canvas.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=19992cfe2df5744678be8760e29a40e1754bec58 translatedAt=2026-08-24T08:26:38.732Z pushedAt=2026-08-31T03:31:59.439Z -->

## Overview

The file defines the functions for creating, binding, drawing, transforming, clipping, and state management of a canvas. The canvas is the core component for 2D graphics rendering in ArkGraphics 2D. It supports drawing shapes, paths, images, pixel maps, and text, and provides capabilities such as canvas transformation (rotation, translation, scaling, and skewing), clipping, and matrix operations.<br>The canvas has a built-in default brush, which is black, enables anti-aliasing, and does not have any other style. It takes effect if and only if neither the brush nor the pen actively set on the canvas exists.<br>This module uses a single-thread model. The caller must manage thread safety and context state switching.

<!--RP1-->

**Sample**: [NDKAPIDrawing (API Version 20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include**: <native_drawing/drawing_canvas.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_SrcRectConstraint](#oh_drawing_srcrectconstraint) | OH_Drawing_SrcRectConstraint | Defines an enum for the constraint types of the source rectangle.|
| [OH_Drawing_PointMode](#oh_drawing_pointmode) | OH_Drawing_PointMode | Defines an enum for the modes of drawing multiple points. The modes include discrete points, line segments, and open polygons.|
| [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) | OH_Drawing_CanvasClipOp | Defines an enum for the canvas clipping modes.|
| [OH_Drawing_CanvasShadowFlags](#oh_drawing_canvasshadowflags) | OH_Drawing_CanvasShadowFlags | Defines an enum for the shadow flags.|
| [OH_Drawing_VertexMode](#oh_drawing_vertexmode) | OH_Drawing_VertexMode | Defines an enum for the modes of interpreting the geometry of a given vertex.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas* OH_Drawing_CanvasCreate(void)](#oh_drawing_canvascreate) | Creates a canvas object. The canvas has a built-in default brush, which is black, has anti-aliasing enabled, and does not have any other style. It takes effect if and only if neither the brush nor the pen actively set on the canvas exists. After the created canvas object is used, you must call [OH_Drawing_CanvasDestroy](#oh_drawing_canvasdestroy) to destroy the canvas object and release resources. Otherwise, memory leaks will occur. |
| [OH_Drawing_Canvas* OH_Drawing_CanvasCreateWithPixelMap(OH_Drawing_PixelMap* pixelMap)](#oh_drawing_canvascreatewithpixelmap) | Binds a pixel map object to the canvas so that the content drawn on the canvas is output to the pixel map (that is, CPU rendering). The canvas bound with a pixel map object is a non-recording canvas.<br>The pixel map object should be unbound by calling [OH_Drawing_PixelMapDissolve](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapdissolve) after the canvas object is destroyed by calling [OH_Drawing_CanvasDestroy](#oh_drawing_canvasdestroy). |
| [void OH_Drawing_CanvasDestroy(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasdestroy) | Destroys the canvas object and reclaims the memory occupied by the object. |
| [void OH_Drawing_CanvasBind(OH_Drawing_Canvas* canvas, OH_Drawing_Bitmap* bitmap)](#oh_drawing_canvasbind) | Binds a bitmap to a canvas so that the content drawn on the canvas is output to the bitmap. (This process is called CPU rendering.) A canvas bound to a bitmap is a non-recording canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasAttachPen(OH_Drawing_Canvas* canvas, const OH_Drawing_Pen* pen)](#oh_drawing_canvasattachpen) | Sets a pen for the canvas. The canvas will use the style and color of the pen to draw the outline of a shape. After this method is executed, if the pen effect changes and the developer expects the change to take effect on subsequent drawing operations, this method must be executed again to ensure that the change takes effect.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or pen is NULL. |
| [void OH_Drawing_CanvasDetachPen(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasdetachpen) | Removes the pen from the canvas. After this, the canvas will not draw the outline of a shape.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if canvas is NULL. |
| [void OH_Drawing_CanvasAttachBrush(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)](#oh_drawing_canvasattachbrush) | Sets a brush for the canvas. The canvas will use the style and color of the brush to fill the drawn shape. After this method is executed, if the brush effect changes and the developer expects the change to take effect on subsequent drawing operations, this method must be executed again to ensure that the change takes effect.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or brush is NULL. |
| [void OH_Drawing_CanvasDetachBrush(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasdetachbrush) | Removes the brush from the canvas. After this, the canvas will not use the previously set brush to fill the shape.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if canvas is NULL. |
| [void OH_Drawing_CanvasSave(OH_Drawing_Canvas* canvas)](#oh_drawing_canvassave) | Saves the current canvas state (canvas matrix) to the top of a stack. It must be used together with the restore API [OH_Drawing_CanvasRestore](#oh_drawing_canvasrestore).<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if canvas is NULL. |
| [void OH_Drawing_CanvasSaveLayer(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, const OH_Drawing_Brush* brush)](#oh_drawing_canvassavelayer) | Saves the matrix and clip region, and allocates a bitmap for subsequent drawing. After the restore API [OH_Drawing_CanvasRestore](#oh_drawing_canvasrestore) is called, the changes made to the matrix and clip region are discarded, and the bitmap is drawn.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if canvas is NULL. |
| [void OH_Drawing_CanvasRestore(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasrestore) | Restores the canvas status (canvas matrix) saved on the top of the stack.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [uint32_t OH_Drawing_CanvasGetSaveCount(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasgetsavecount) | Obtains the number of canvas statuses (canvas matrices) saved in the stack.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasRestoreToCount(OH_Drawing_Canvas* canvas, uint32_t saveCount)](#oh_drawing_canvasrestoretocount) | Restores to a given number of canvas statuses (canvas matrices).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasDrawLine(OH_Drawing_Canvas* canvas, float x1, float y1, float x2, float y2)](#oh_drawing_canvasdrawline) | Draws a line segment.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasDrawPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path)](#oh_drawing_canvasdrawpath) | Draws a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapNine(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap,const OH_Drawing_Rect* center, const OH_Drawing_Rect* dst, OH_Drawing_FilterMode mode)](#oh_drawing_canvasdrawpixelmapnine) | Divides the pixel map into nine parts by drawing two horizontal lines and two vertical lines: four edges, four corners, and the center.<br>If the sizes of the four corner regions do not exceed the destination rectangle, they are drawn in the destination rectangle without scaling. Otherwise, they are drawn in the destination rectangle after being scaled proportionally.<br>If there is remaining space, the remaining five regions are drawn by stretching or compressing so that they can completely cover the destination rectangle. |
| [void OH_Drawing_CanvasDrawPixelMapRect(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap,const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_canvasdrawpixelmaprect) | Draws the specified region of the pixel map to the specified region of the canvas. The difference from [OH_Drawing_CanvasDrawPixelMapRectConstraint](#oh_drawing_canvasdrawpixelmaprectconstraint) is that this API does not support specifying the source rectangle constraint type.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if any of canvas, pixelMap, or dst is NULL. |
| [void OH_Drawing_CanvasDrawBackground(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)](#oh_drawing_canvasdrawbackground) | Fills the current clip region of the canvas with the brush as the background.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or brush is NULL. |
| [void OH_Drawing_CanvasDrawRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region)](#oh_drawing_canvasdrawregion) | Draws a region, using the brush to fill the interior of the region and the pen to draw the outline of the region.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or region is NULL. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPoint(OH_Drawing_Canvas* canvas, const OH_Drawing_Point2D* point)](#oh_drawing_canvasdrawpoint) | Draws a point. The visual size of the point is determined by the pen stroke width currently set on the canvas, and the color is determined by the pen color. |
| [void OH_Drawing_CanvasDrawPoints(OH_Drawing_Canvas* canvas, OH_Drawing_PointMode mode,uint32_t count, const OH_Drawing_Point2D* point2D)](#oh_drawing_canvasdrawpoints) | Draws multiple points. You can draw a single point, a line segment, or an open polygon.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **point2D** is NULL, or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **mode** is not within the enumerated range, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [void OH_Drawing_CanvasDrawBitmap(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap, float left, float top)](#oh_drawing_canvasdrawbitmap) | Draws a bitmap. A bitmap, also referred to as a dot matrix image, a pixel map image, or a grid image, includes single points called pixels (image elements).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasDrawBitmapRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap,const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_canvasdrawbitmaprect) | Draws a portion of a bitmap onto a specified area of the canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If one of **canvas**, **bitmap**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasDrawRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)](#oh_drawing_canvasdrawrect) | Draws a rectangle.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or rect is NULL. |
| [void OH_Drawing_CanvasDrawCircle(OH_Drawing_Canvas* canvas, const OH_Drawing_Point* point, float radius)](#oh_drawing_canvasdrawcircle) | Draws a circle.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or point is NULL;<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE is returned if radius is less than or equal to 0. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawColor(OH_Drawing_Canvas* canvas, uint32_t color,OH_Drawing_BlendMode blendMode)](#oh_drawing_canvasdrawcolor) | Fills the entire canvas with the specified color and blend mode. This function composites the specified color with the existing content on the canvas according to the blend rule defined by blendMode. Different blend modes produce different visual effects. |
| [void OH_Drawing_CanvasDrawOval(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)](#oh_drawing_canvasdrawoval) | Draws an oval inscribed in the rectangle specified by the rect parameter. This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or rect is NULL. |
| [void OH_Drawing_CanvasDrawArc(OH_Drawing_Canvas* canvas,const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)](#oh_drawing_canvasdrawarc) | Draws an arc inscribed in the ellipse defined by the rect parameter. When the absolute value of the sweep angle is greater than 360 degrees, this API draws an ellipse. The difference from [OH_Drawing_CanvasDrawArcWithCenter](#oh_drawing_canvasdrawarcwithcenter) is that this API does not support specifying whether the start point and end point of the arc are connected to the center of the arc.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or rect is NULL. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawArcWithCenter(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect,float startAngle, float sweepAngle, bool useCenter)](#oh_drawing_canvasdrawarcwithcenter) | Draws an arc inscribed in the ellipse defined by the rect parameter. This API allows specifying the start angle, sweep angle of the arc, and whether the start point and end point of the arc are connected to the center of the ellipse (that is, the center of rect). |
| [void OH_Drawing_CanvasDrawRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect)](#oh_drawing_canvasdrawroundrect) | Draws a rounded rectangle. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawNestedRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* outer,const OH_Drawing_RoundRect* inner)](#oh_drawing_canvasdrawnestedroundrect) | Draws two nested round rectangles. The boundary of the outer rectangle must contain the boundary of the inner rectangle; otherwise, nothing is drawn. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacter(OH_Drawing_Canvas* canvas, const char* str,const OH_Drawing_Font* font, float x, float y)](#oh_drawing_canvasdrawsinglecharacter) | Draws a single character. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character.|
| [void OH_Drawing_CanvasDrawTextBlob(OH_Drawing_Canvas* canvas, const OH_Drawing_TextBlob* textBlob, float x, float y)](#oh_drawing_canvasdrawtextblob) | Draws a text blob. If the typeface used to construct **OH_Drawing_TextBlob** does not support a character, that character will not be drawn.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasClipRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect,OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)](#oh_drawing_canvascliprect) | Clips a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [void OH_Drawing_CanvasClipRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect,OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)](#oh_drawing_canvascliproundrect) | Clips a rounded rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [void OH_Drawing_CanvasClipPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path,OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)](#oh_drawing_canvasclippath) | Clips a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasClipRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region,OH_Drawing_CanvasClipOp clipOp)](#oh_drawing_canvasclipregion) | Clips a rectangle.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasResetClip(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasresetclip) | Resets the clip state of the current canvas to the initial state. |
| [void OH_Drawing_CanvasRotate(OH_Drawing_Canvas* canvas, float degrees, float px, float py)](#oh_drawing_canvasrotate) | Rotates the canvas.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if canvas is NULL. |
| [void OH_Drawing_CanvasTranslate(OH_Drawing_Canvas* canvas, float dx, float dy)](#oh_drawing_canvastranslate) | Translates a canvas by a given distance.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasScale(OH_Drawing_Canvas* canvas, float sx, float sy)](#oh_drawing_canvasscale) | Scales a canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasSkew(OH_Drawing_Canvas* canvas, float sx, float sy)](#oh_drawing_canvasskew) | Skews a canvas. This function premultiplies the current canvas matrix by a skew transformation matrix and applies the resulting matrix to the canvas. The skew transformation matrix is as follows:<br>\|1 sx 0\|  <br>\|sy 1 0\|  <br>\|0  0 1\|.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [int32_t OH_Drawing_CanvasGetWidth(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasgetwidth) | Obtains the canvas width.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [int32_t OH_Drawing_CanvasGetHeight(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasgetheight) | Obtains the canvas height.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasGetLocalClipBounds(OH_Drawing_Canvas* canvas, OH_Drawing_Rect* rect)](#oh_drawing_canvasgetlocalclipbounds) | Obtains the bounds of the cropping region of the canvas. This function cannot be used for a canvas of the recording type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasGetTotalMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)](#oh_drawing_canvasgettotalmatrix) | Obtains the 3x3 matrix of a canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasConcatMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)](#oh_drawing_canvasconcatmatrix) | Preconcats the existing matrix of the canvas with the passed-in matrix. The drawing operation triggered before this API is called is not affected.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasDrawShadow(OH_Drawing_Canvas* canvas, OH_Drawing_Path* path, OH_Drawing_Point3D planeParams,OH_Drawing_Point3D devLightPos, float lightRadius, uint32_t ambientColor, uint32_t spotColor,OH_Drawing_CanvasShadowFlags flag)](#oh_drawing_canvasdrawshadow) | Draws a spotlight-type shadow, using the path to describe the outline of the ambient light shadow.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or path is NULL;<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE is returned if flag is outside the enum range. |
| [void OH_Drawing_CanvasClear(OH_Drawing_Canvas* canvas, uint32_t color)](#oh_drawing_canvasclear) | Clears the canvas with the specified color. The difference from [OH_Drawing_CanvasDrawColor](#oh_drawing_canvasdrawcolor) is that this API directly replaces all content on the canvas with the specified color, whereas OH_Drawing_CanvasDrawColor blends the color with the existing content on the canvas through a blend mode.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if canvas is NULL. |
| [void OH_Drawing_CanvasSetMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)](#oh_drawing_canvassetmatrix) | Sets the matrix state of the canvas, replacing the current matrix of the canvas with the passed-in matrix, which affects the coordinate transformation of subsequent drawing operations.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if either canvas or matrix is NULL. |
| [void OH_Drawing_CanvasResetMatrix(OH_Drawing_Canvas* canvas)](#oh_drawing_canvasresetmatrix) | Resets the matrix of this canvas to an identity matrix.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasDrawImageRectWithSrc(OH_Drawing_Canvas* canvas, const OH_Drawing_Image* image,const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions,OH_Drawing_SrcRectConstraint srcRectConstraint)](#oh_drawing_canvasdrawimagerectwithsrc) | Draws a portion of an image onto a specified area of the canvas. The area selected by the source rectangle is scaled and translated to the destination rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If one of **canvas**, **image**, **src**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_CanvasDrawImageRect(OH_Drawing_Canvas* canvas, OH_Drawing_Image* image,OH_Drawing_Rect* rect, OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_canvasdrawimagerect) | Draws an image to the specified region of the canvas. The difference from [OH_Drawing_CanvasDrawImageRectWithSrc](#oh_drawing_canvasdrawimagerectwithsrc) is that this API does not support specifying the source rectangle constraint type.<br>This API generates an error code, which can be obtained by calling [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if any of canvas, image, or rect is NULL. |
| [void OH_Drawing_CanvasDrawVertices(OH_Drawing_Canvas* canvas, OH_Drawing_VertexMode vertexMmode,int32_t vertexCount, const OH_Drawing_Point2D* positions, const OH_Drawing_Point2D* texs,const uint32_t* colors, int32_t indexCount, const uint16_t* indices, OH_Drawing_BlendMode mode)](#oh_drawing_canvasdrawvertices) | Draws a triangular grid described by a vertex array.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **positions** is NULL, **vertexCount** is less than 3, or **indexCount** is less than 3 but not 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If either **vertexMmode** or **mode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [bool OH_Drawing_CanvasReadPixels(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo,void* dstPixels, uint32_t dstRowBytes, int32_t srcX, int32_t srcY)](#oh_drawing_canvasreadpixels) | Copies pixel data from a canvas to a specified address. This function cannot be used for a canvas of the recording type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If one of **canvas**, **imageInfo**, or **dstPixels** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_CanvasReadPixelsToBitmap(OH_Drawing_Canvas* canvas,OH_Drawing_Bitmap* bitmap, int32_t srcX, int32_t srcY)](#oh_drawing_canvasreadpixelstobitmap) | Copies pixel data from a canvas to an image. This function cannot be used for a canvas of the recording type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasIsClipEmpty(OH_Drawing_Canvas* canvas, bool* isClipEmpty)](#oh_drawing_canvasisclipempty) | Checks whether the drawable region is empty after clipping. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasGetImageInfo(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo)](#oh_drawing_canvasgetimageinfo) | Obtains the image information of the canvas. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmd(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)](#oh_drawing_canvasdrawrecordcmd) | Draws a recording command object. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmdNesting(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)](#oh_drawing_canvasdrawrecordcmdnesting) | Draws an **OH_Drawing_RecordCmd** object. This API supports nesting.<br> Specifically, it can use the canvas object generated by [OH_Drawing_RecordCmdUtilsBeginRecording](capi-drawing-record-cmd-h.md#oh_drawing_recordcmdutilsbeginrecording) as the input parameter. However, multi-layer nesting is not recommended because it affects performance.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path,bool* quickReject)](#oh_drawing_canvasquickrejectpath) | Checks whether the path and the canvas region do not intersect. The canvas region includes the boundary. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect,bool* quickReject)](#oh_drawing_canvasquickrejectrect) | Checks whether the rectangle and the canvas region do not intersect. The canvas region includes the boundary. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapRectConstraint(OH_Drawing_Canvas* canvas,OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst,const OH_Drawing_SamplingOptions* samplingOptions, OH_Drawing_SrcRectConstraint constraint)](#oh_drawing_canvasdrawpixelmaprectconstraint) | Draws a portion of a pixel map onto a specified area of the canvas.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacterWithFeatures(OH_Drawing_Canvas* canvas, const char* str,const OH_Drawing_Font* font, float x, float y, OH_Drawing_FontFeatures* fontFeatures)](#oh_drawing_canvasdrawsinglecharacterwithfeatures) | Draws a single character with font features. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character.|
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapMesh(OH_Drawing_Canvas* cCanvas, OH_Drawing_PixelMap* pixelMap, uint32_t meshWidth, uint32_t meshHeight, const float* vertices, uint32_t verticesSize, uint32_t vertOffset, const uint32_t* colors, uint32_t colorsSize, uint32_t colorOffset)](#oh_drawing_canvasdrawpixelmapmesh) | Draws the pixel map on a mesh that is evenly distributed over the pixel map. (Only the brush is supported; using the pen has no drawing effect.) |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasIsOpaque(const OH_Drawing_Canvas* canvas, bool* isOpaque)](#oh_drawing_canvasisopaque) | Checks whether the layer currently drawn to the device is opaque. |
| [OH_Drawing_ErrorCode OH_Drawing_CanvasDrawGlyphs(const OH_Drawing_Canvas* canvas, const int* glyphIds, int glyphIdCount, int glyphIdOffset, const OH_Drawing_Point2D* positions, int positionCount, int positionOffset, int glyphCount, const OH_Drawing_Font* font)](#oh_drawing_canvasdrawglyphs) | Draws an array of glyphs with the specified font. If the glyph count is less than or equal to 0, nothing is drawn. |

## Enum Description

### OH_Drawing_SrcRectConstraint

```c
enum OH_Drawing_SrcRectConstraint
```

**Description**

Enumerates the constraint types of the source rectangle.

**Since**: 12

| Value| Description|
| -- | -- |
| STRICT_SRC_RECT_CONSTRAINT | The source rectangle must be completely contained in the image.|
| FAST_SRC_RECT_CONSTRAINT | The source rectangle can be partly outside the image.|

### OH_Drawing_PointMode

```c
enum OH_Drawing_PointMode
```

**Description**

Enumerates the modes of drawing multiple points. The modes include discrete points, line segments, and open polygons.

**Since**: 12

| Value| Description|
| -- | -- |
| POINT_MODE_POINTS | Draws each point separately.|
| POINT_MODE_LINES | Draws every two points as a line segment.|
| POINT_MODE_POLYGON | Draws an array of points as an open polygon.|

### OH_Drawing_CanvasClipOp

```c
enum OH_Drawing_CanvasClipOp
```

**Description**

Enumerates the canvas clipping modes.

**Since**: 11

| Value| Description|
| -- | -- |
| DIFFERENCE | Clips a specified area. That is, the difference set is obtained.|
| INTERSECT | Retains a specified area. That is, the intersection is obtained.|

### OH_Drawing_CanvasShadowFlags

```c
enum OH_Drawing_CanvasShadowFlags
```

**Description**

Enumerates the shadow flags.

**Since**: 12

| Value| Description|
| -- | -- |
| SHADOW_FLAGS_NONE | There is no shadow flag.|
| SHADOW_FLAGS_TRANSPARENT_OCCLUDER | The occluding object is transparent.|
| SHADOW_FLAGS_GEOMETRIC_ONLY | No analysis on the shadows is required.|
| SHADOW_FLAGS_ALL | All the preceding shadow flags are used.|

### OH_Drawing_VertexMode

```c
enum OH_Drawing_VertexMode
```

**Description**

Enumerates the modes of interpreting the geometry of a given vertex.

**Since**: 12

| Value| Description|
| -- | -- |
| VERTEX_MODE_TRIANGLES | Draws a triangle list. Specifically, a list of isolated triangles are drawn using every three vertices. If the number of vertices is not a multiple of 3, the extra vertices will be ignored. |
| VERTEX_MODE_TRIANGLES_STRIP | Draws a triangle strip. Specifically, the first triangle is drawn between the first 3 vertices, and all subsequent triangles use the previous 2 vertices plus the next additional vertex.|
| VERTEX_MODE_TRIANGLE_FAN | Draws a triangle fan. A triangle fan is similar to a triangle strip, except that all the triangles share one vertex (the first vertex).|

## Function Description

### OH_Drawing_CanvasDrawSingleCharacterWithFeatures()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacterWithFeatures(OH_Drawing_Canvas* canvas, const char* str, const OH_Drawing_Font* font, float x, float y, OH_Drawing_FontFeatures* fontFeatures)
```

**Description**

Draws a single character with font features. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const char* str | Pointer to the single character to draw. A string can be passed in, but only the first character in the string is parsed and drawn in UTF-8 encoding.|
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object.|
| float x | Horizontal coordinate of the left endpoint of the character object baseline (near the lower-left corner of the character), in physical pixels (px). |
| float y | Vertical coordinate of the left endpoint of the character object baseline (near the lower-left corner of the character), in physical pixels (px). |
| [OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md)* fontFeatures | Pointer to the font feature container object [OH_Drawing_FontFeatures](capi-drawing-oh-drawing-fontfeatures.md). When no font feature is added to the container, the preset font features in the TTF (TrueType Font) file are used. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if at least one of the parameters **canvas**, **str**, **font**, or **fontFeatures** is NULL, or the length of **str** is **0**.|

### OH_Drawing_CanvasDrawPixelMapRectConstraint()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapRectConstraint(OH_Drawing_Canvas* canvas,OH_Drawing_PixelMap* pixelMap, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions, OH_Drawing_SrcRectConstraint constraint)
```

**Description**

Draws a portion of a pixel map onto a specified area of the canvas.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | Pointer to the [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object.|
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* src | Pointer to a rectangle on the pixel map. If NULL is passed in, it refers to the entire pixel map.|
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to a rectangle on the canvas.|
| [const OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | Pointer to the [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) object. A null pointer means that the default sampling options are used.|
| [OH_Drawing_SrcRectConstraint](#oh_drawing_srcrectconstraint) constraint | Constraint type. For the supported optional types, see the [OH_Drawing_SrcRectConstraint](#oh_drawing_srcrectconstraint) enum. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if **canvas**, **pixelMap**, or **dst** is NULL.|

### OH_Drawing_CanvasDrawRecordCmdNesting()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmdNesting(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)
```

**Description**

Draws a recording command object and supports nesting.<br> This API supports the canvas object generated by [OH_Drawing_RecordCmdUtilsBeginRecording](capi-drawing-record-cmd-h.md#oh_drawing_recordcmdutilsbeginrecording) as the input parameter for nested calls. Multi-level nesting is not recommended because it affects performance.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 19

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object. Only recording-type canvases are supported. |
| [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md)* recordCmd | Pointer to an [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md) object. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if canvas or recordCmd is null. |

### OH_Drawing_CanvasCreate()

```c
OH_Drawing_Canvas* OH_Drawing_CanvasCreate(void)
```

**Description**

Creates a canvas object. The canvas has a built-in default brush, which is black, enables anti-aliasing, and does not have any other style. It takes effect if and only if neither the brush nor the pen actively set on the canvas exists. After the created canvas object is used, you must call [OH_Drawing_CanvasDestroy](#oh_drawing_canvasdestroy) to destroy the canvas object and release resources. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* | Pointer to the created canvas object [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md). If the value is NULL, the creation fails, possibly due to insufficient available memory. |

### OH_Drawing_CanvasCreateWithPixelMap()

```c
OH_Drawing_Canvas* OH_Drawing_CanvasCreateWithPixelMap(OH_Drawing_PixelMap* pixelMap)
```

**Description**

Binds a pixel map object to a canvas so that the content drawn on the canvas is output to the pixel map (that is, CPU rendering). A canvas bound to a pixel map object is a non-recording canvas.<br>After the canvas object is destroyed by calling [OH_Drawing_CanvasDestroy](#oh_drawing_canvasdestroy), call [OH_Drawing_PixelMapDissolve](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapdissolve) to unbind the pixel map object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | Pointer to the pixel map [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md). The pixel map object should be unbound by calling [OH_Drawing_PixelMapDissolve](capi-drawing-pixel-map-h.md#oh_drawing_pixelmapdissolve) after the canvas object is destroyed. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* | Pointer to the created canvas object [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md). If the returned object is NULL, the creation fails due to insufficient memory or an empty pixel map object.|

### OH_Drawing_CanvasDestroy()

```c
void OH_Drawing_CanvasDestroy(OH_Drawing_Canvas* canvas)
```

**Description**

Destroys a canvas object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|

### OH_Drawing_CanvasBind()

```c
void OH_Drawing_CanvasBind(OH_Drawing_Canvas* canvas, OH_Drawing_Bitmap* bitmap)
```

**Description**

Binds a bitmap to a canvas so that the content drawn on the canvas is output to the bitmap. (This process is called CPU rendering.) A canvas bound to a bitmap is a non-recording canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|

### OH_Drawing_CanvasAttachPen()

```c
void OH_Drawing_CanvasAttachPen(OH_Drawing_Canvas* canvas, const OH_Drawing_Pen* pen)
```

**Description**

Attaches a pen to a canvas so that the canvas uses the style and color of the pen to draw the outline of a shape. After this method is executed, if the pen effect changes and the developer expects the change to take effect on subsequent drawing operations, this method must be executed again to ensure that the change takes effect.<br>This API may generate an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>If either canvas or pen is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Pen](capi-drawing-oh-drawing-pen.md)* pen | Pointer to an **OH_Drawing_Pen** object.|

### OH_Drawing_CanvasDetachPen()

```c
void OH_Drawing_CanvasDetachPen(OH_Drawing_Canvas* canvas)
```

**Description**

Detaches the pen from a canvas so that the canvas no longer draws the outline of a shape.<br>This API may generate an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>If canvas is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|

### OH_Drawing_CanvasAttachBrush()

```c
void OH_Drawing_CanvasAttachBrush(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)
```

**Description**

Attaches a brush to a canvas so that the canvas uses the style and color of the brush to fill the drawn shape. After this method is executed, if the brush effect changes and the developer expects the change to take effect on subsequent drawing operations, this method must be executed again to ensure that the change takes effect.<br>This API may generate an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>If either canvas or brush is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|

### OH_Drawing_CanvasDetachBrush()

```c
void OH_Drawing_CanvasDetachBrush(OH_Drawing_Canvas* canvas)
```

**Description**

Detaches the brush from a canvas so that the canvas no longer uses the previously set brush to fill a shape.<br>This API may generate an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>If canvas is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|

### OH_Drawing_CanvasSave()

```c
void OH_Drawing_CanvasSave(OH_Drawing_Canvas* canvas)
```

**Description**

Saves the current canvas status (canvas matrix) to the top of the stack. This function must be used together with the restore function [OH_Drawing_CanvasRestore](#oh_drawing_canvasrestore).<br>This API may generate an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>If canvas is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|

### OH_Drawing_CanvasSaveLayer()

```c
void OH_Drawing_CanvasSaveLayer(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect, const OH_Drawing_Brush* brush)
```

**Description**

Saves the matrix and clipping region, and allocates a bitmap for subsequent drawing. After [OH_Drawing_CanvasRestore](#oh_drawing_canvasrestore) is called, the changes made to the matrix and clipping region are discarded, and the bitmap is drawn.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object, which is used to limit the layer size. A null pointer means no limit.|
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md) object. The alpha value, filter effect, and blend mode of the brush are applied when the bitmap is drawn. If NULL is passed in, no effect is applied.|

### OH_Drawing_CanvasRestore()

```c
void OH_Drawing_CanvasRestore(OH_Drawing_Canvas* canvas)
```

**Description**

Restores the canvas status (canvas matrix) saved on the top of the stack.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|

### OH_Drawing_CanvasGetSaveCount()

```c
uint32_t OH_Drawing_CanvasGetSaveCount(OH_Drawing_Canvas* canvas)
```

**Description**

Obtains the number of canvas statuses (canvas matrices) saved in the stack.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns a 32-bit value that describes the number of canvas statuses (canvas matrices). The initial number is **1**.|

### OH_Drawing_CanvasRestoreToCount()

```c
void OH_Drawing_CanvasRestoreToCount(OH_Drawing_Canvas* canvas, uint32_t saveCount)
```

**Description**

Restores to a given number of canvas statuses (canvas matrices).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| uint32_t saveCount | Number of canvas statuses (canvas matrices). If the value is less than or equal to 1, the canvas is restored to the initial state. If the value is greater than the number of canvas statuses that have been saved, no operation is performed.|

### OH_Drawing_CanvasDrawLine()

```c
void OH_Drawing_CanvasDrawLine(OH_Drawing_Canvas* canvas, float x1, float y1, float x2, float y2)
```

**Description**

Draws a line segment.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| float x1 | X-coordinate of the start point of the line segment, in physical pixels (px). |
| float y1 | Y-coordinate of the start point of the line segment, in physical pixels (px). |
| float x2 | X-coordinate of the end point of the line segment, in physical pixels (px). |
| float y2 | Y-coordinate of the end point of the line segment, in physical pixels (px). |

### OH_Drawing_CanvasDrawPath()

```c
void OH_Drawing_CanvasDrawPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path)
```

**Description**

Draws a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|

### OH_Drawing_CanvasDrawPixelMapNine()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapNine(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap,const OH_Drawing_Rect* center, const OH_Drawing_Rect* dst, OH_Drawing_FilterMode mode)
```

**Description**

Splits a pixel map into nine sections using two horizontal and two vertical lines: four edge sections, four corner sections, and a central section.<br>If the four corner sections are not larger than the target rectangle, they are drawn in the target rectangle without scaling; otherwise, they are scaled proportionally and drawn in the target rectangle.<br>If there is remaining space, the other five sections are drawn by stretching or compressing so that they completely cover the target rectangle.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | Pointer to the [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* center | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object, which indicates the central rectangle splitting the pixel map. It divides the image into nine sections by extending its four edges.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object, which indicates the target region on the canvas.|
| [OH_Drawing_FilterMode](capi-drawing-sampling-options-h.md#oh_drawing_filtermode) mode | Filter mode. Different modes affect the interpolation quality when scaling a pixel map. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **canvas**, **pixelMap**, or **dst** is NULL.|

### OH_Drawing_CanvasDrawPixelMapRect()

```c
void OH_Drawing_CanvasDrawPixelMapRect(OH_Drawing_Canvas* canvas, OH_Drawing_PixelMap* pixelMap,const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Draws a specified area of a pixel map onto a specified area of the canvas. Unlike [OH_Drawing_CanvasDrawPixelMapRectConstraint](#oh_drawing_canvasdrawpixelmaprectconstraint), this API does not support specifying the source rectangle constraint type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **canvas**, **pixelMap**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | Pointer to the [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* src | Pointer to a rectangle on the pixel map. If NULL is passed in, it refers to the entire pixel map.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to a rectangle on the canvas.|
| const [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | Pointer to the [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) object. A null pointer means that the default sampling options are used.|

### OH_Drawing_CanvasDrawBackground()

```c
void OH_Drawing_CanvasDrawBackground(OH_Drawing_Canvas* canvas, const OH_Drawing_Brush* brush)
```

**Description**

Fills the current clipping region of the canvas with a brush as the background.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **brush** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | Pointer to an **OH_Drawing_Brush** object.|

### OH_Drawing_CanvasDrawRegion()

```c
void OH_Drawing_CanvasDrawRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region)
```

**Description**

Draws a region, filling the interior of the region with a brush and drawing the outline of the region with a pen.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **region** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to an **OH_Drawing_Region** object.|

### OH_Drawing_CanvasDrawPoint()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPoint(OH_Drawing_Canvas* canvas, const OH_Drawing_Point2D* point)
```

**Description**

Draws a point. The visual size of the point is determined by the stroke width of the pen currently set on the canvas, and its color is determined by the pen color.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* point | Pointer to the [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **canvas** or **point** is NULL.|

### OH_Drawing_CanvasDrawPoints()

```c
void OH_Drawing_CanvasDrawPoints(OH_Drawing_Canvas* canvas, OH_Drawing_PointMode mode,uint32_t count, const OH_Drawing_Point2D* point2D)
```

**Description**

Draws multiple points. You can draw a single point, a line segment, or an open polygon.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **point2D** is NULL, or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **mode** is not within the enumerated range, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| [OH_Drawing_PointMode](#oh_drawing_pointmode) mode | Method for drawing multiple points. For supported methods, see [OH_Drawing_PointMode](#oh_drawing_pointmode). |
| uint32_t count | Number of points, that is, the number of points in the point array. The value must be greater than 0. |
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* point2D | Pointer to the array of multiple points. The array size must be equal to the value of the count parameter. |

### OH_Drawing_CanvasDrawBitmap()

```c
void OH_Drawing_CanvasDrawBitmap(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap, float left, float top)
```

**Description**

Draws a bitmap. A bitmap, also referred to as a dot matrix image, a pixel map image, or a grid image, includes single points called pixels (image elements).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to an **OH_Drawing_Bitmap** object.|
| float left | Horizontal coordinate of the upper-left corner of the bitmap object, in physical pixels (px). |
| float top | Vertical coordinate of the upper-left corner of the bitmap object, in physical pixels (px). |

### OH_Drawing_CanvasDrawBitmapRect()

```c
void OH_Drawing_CanvasDrawBitmapRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Bitmap* bitmap,const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Draws a portion of a bitmap onto a specified area of the canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If one of **canvas**, **bitmap**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to the [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* src | Pointer to a rectangle on the bitmap. If NULL is passed in, it refers to the entire bitmap.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to a rectangle on the canvas.|
| const [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | Pointer to the [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) object. A null pointer means that the default sampling options are used.|

### OH_Drawing_CanvasDrawRect()

```c
void OH_Drawing_CanvasDrawRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)
```

**Description**

Draws a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

### OH_Drawing_CanvasDrawCircle()

```c
void OH_Drawing_CanvasDrawCircle(OH_Drawing_Canvas* canvas, const OH_Drawing_Point* point, float radius)
```

**Description**

Draws a circle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **point** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **radius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an **OH_Drawing_Point** object, which indicates the center of the circle.|
| float radius | Radius of the circle, in physical pixels (px). The value must be greater than 0. |

### OH_Drawing_CanvasDrawColor()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawColor(OH_Drawing_Canvas* canvas, uint32_t color,OH_Drawing_BlendMode blendMode)
```

**Description**

Fills the entire canvas with the specified color and blend mode. This function composites the specified color with the existing content on the canvas according to the blending rules defined by **blendMode**. Different blend modes produce different visual effects.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| uint32_t color | Specified color, represented by a 32-bit (ARGB) parameter. The overall value range is [0x00000000, 0xFFFFFFFF], and the value range of each color channel (A, R, G, B) is [0, 255]. |
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) blendMode | Specified blend mode, used to control how colors are blended when filling the canvas. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **canvas** is NULL.<br> **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** if **blendMode** is not set to one of the enumerated values.|

### OH_Drawing_CanvasDrawOval()

```c
void OH_Drawing_CanvasDrawOval(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect)
```

**Description**

Draws an oval inscribed in the rectangular area specified by the **rect** parameter. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

### OH_Drawing_CanvasDrawArc()

```c
void OH_Drawing_CanvasDrawArc(OH_Drawing_Canvas* canvas,const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)
```

**Description**

Draws an arc inscribed in the ellipse defined by rect. If the absolute value of the sweep angle exceeds 360 degrees, an ellipse is drawn. Unlike [OH_Drawing_CanvasDrawArcWithCenter](#oh_drawing_canvasdrawarcwithcenter), this API does not support specifying whether the start point and end point of the arc are connected to the center of the arc.<br>This API will generate an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>If either canvas or rect is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object that defines the bounding rectangle of the ellipse on which the arc is drawn. The arc is drawn on the ellipse defined by this rectangle. |
| float startAngle | Start angle of the arc, in degrees. At 0 degrees, the start point is at the right endpoint of the ellipse. A positive value places the start point clockwise, and a negative value places it counterclockwise. |
| float sweepAngle | Sweep angle of the arc, in degrees. A positive value sweeps clockwise, and a negative value sweeps counterclockwise. Its valid range is from -360 degrees to 360 degrees. When the absolute value is greater than 360 degrees, this function draws an ellipse. |

### OH_Drawing_CanvasDrawArcWithCenter()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawArcWithCenter(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect,float startAngle, float sweepAngle, bool useCenter)
```

**Description**

Draws an arc inscribed in the ellipse defined by the rect parameter. This API allows you to specify the start angle, sweep angle, and whether the arc's start and end points connect to the center of the ellipse (that is, the center of rect).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md), which defines the bounding rectangle of the ellipse on which the arc lies. The arc is drawn on the ellipse defined by this rectangle. |
| float startAngle | Start angle of the arc, in degrees. At 0 degrees, the start point is at the right endpoint of the ellipse. A positive value places the start point clockwise, and a negative value places it counterclockwise. |
| float sweepAngle | Sweep angle of the arc, in degrees. A positive value sweeps clockwise, and a negative value sweeps counterclockwise. The valid range of the sweep angle is from -360 degrees to 360 degrees. If the absolute value is greater than 360 degrees, a complete ellipse is drawn. |
| bool useCenter | Whether the start point and end point of the arc are connected to its center. The value **true** means that they are connected to the center; the value **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **canvas** or **rect** is NULL.|

### OH_Drawing_CanvasDrawRoundRect()

```c
void OH_Drawing_CanvasDrawRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect)
```

**Description**

Draws a rounded rectangle. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to an **OH_Drawing_RoundRect** object.|

### OH_Drawing_CanvasDrawNestedRoundRect()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawNestedRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* outer,const OH_Drawing_RoundRect* inner)
```

**Description**

Draws two nested rounded rectangles. The outer rectangle boundary must contain the inner rectangle boundary. Otherwise, there is no drawing effect.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* outer | Pointer to the round rectangle object [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md), indicating the outer round rectangle boundary. The outer rectangle boundary must contain the inner rectangle boundary; otherwise, no drawing effect occurs. |
| const [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* inner | Pointer to the [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md) object, indicating the inner rounded rectangle.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **canvas**, **outer**, or **inner** is NULL.|

### OH_Drawing_CanvasDrawSingleCharacter()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawSingleCharacter(OH_Drawing_Canvas* canvas, const char* str,const OH_Drawing_Font* font, float x, float y)
```

**Description**

Draws a single character. If the typeface of the current font does not support the character to draw, the system typeface is used to draw the character. The difference from [OH_Drawing_CanvasDrawSingleCharacterWithFeatures](#oh_drawing_canvasdrawsinglecharacterwithfeatures) is that this API does not support setting font features. To specify font features (such as ligatures and kerning), use [OH_Drawing_CanvasDrawSingleCharacterWithFeatures](#oh_drawing_canvasdrawsinglecharacterwithfeatures).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const char* str | Pointer to the single character to draw. A string can be passed in, but only the first character in the string is parsed and drawn in UTF-8 encoding.|
| const [OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the [OH_Drawing_Font](capi-drawing-oh-drawing-font.md) object.|
| float x | Horizontal coordinate of the left endpoint of the baseline of the character object (near the lower-left corner of the character), in physical pixels (px). |
| float y | Vertical coordinate of the left endpoint of the baseline of the character object (near the lower-left corner of the character), in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br> Returns OH_DRAWING_SUCCESS if the operation is successful.<br> Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of canvas, str, or font is null or the length of str is 0. |

### OH_Drawing_CanvasDrawTextBlob()

```c
void OH_Drawing_CanvasDrawTextBlob(OH_Drawing_Canvas* canvas, const OH_Drawing_TextBlob* textBlob, float x, float y)
```

**Description**

Draws a text blob. If the typeface used to construct **OH_Drawing_TextBlob** does not support a character, that character will not be drawn.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **textBlob** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_TextBlob](capi-drawing-oh-drawing-textblob.md)* textBlob | Pointer to an **OH_Drawing_TextBlob** object.|
| float x | Horizontal coordinate of the left endpoint of the baseline of the text object (near the lower-left corner of the text), in physical pixels (px). |
| float y | Vertical coordinate of the left endpoint of the baseline of the text object (near the lower-left corner of the text), in physical pixels (px). |

### OH_Drawing_CanvasClipRect()

```c
void OH_Drawing_CanvasClipRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect,OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)
```

**Description**

Clips a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) clipOp | Clip mode. For the supported clip modes, see the [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) enum. |
| bool doAntiAlias | Whether to perform anti-aliasing. The value true means to perform anti-aliasing, and false means not to perform anti-aliasing. |

### OH_Drawing_CanvasClipRoundRect()

```c
void OH_Drawing_CanvasClipRoundRect(OH_Drawing_Canvas* canvas, const OH_Drawing_RoundRect* roundRect,OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)
```

**Description**

Clips a rounded rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to an **OH_Drawing_RoundRect** object.|
| [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) clipOp | Clipping mode. For the supported specific clipping modes, see the [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) enum. |
| bool doAntiAlias | Whether to perform anti-aliasing. The value true means to perform anti-aliasing, and false means not to perform anti-aliasing. |

### OH_Drawing_CanvasClipPath()

```c
void OH_Drawing_CanvasClipPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path,OH_Drawing_CanvasClipOp clipOp, bool doAntiAlias)
```

**Description**

Clips a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **clipOp** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|
| [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) clipOp | Clipping mode. For the supported specific clipping modes, see the [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) enum. |
| bool doAntiAlias | Whether to perform anti-aliasing. The value **true** means to perform anti-aliasing, and **false** means not to perform anti-aliasing. |

### OH_Drawing_CanvasClipRegion()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasClipRegion(OH_Drawing_Canvas* canvas, const OH_Drawing_Region* region,OH_Drawing_CanvasClipOp clipOp)
```

**Description**

Clips a rectangle.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Region](capi-drawing-oh-drawing-region.md)* region | Pointer to the [OH_Drawing_Region](capi-drawing-oh-drawing-region.md) object.|
| [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) clipOp | Clip type. For the supported clip modes, see the [OH_Drawing_CanvasClipOp](#oh_drawing_canvasclipop) enum. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **canvas** or **region** is NULL.<br> **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** if **clipOp** is not set to one of the enumerated values.|

### OH_Drawing_CanvasResetClip()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasResetClip(OH_Drawing_Canvas* canvas)
```

**Description**

Resets the clipping state of the current canvas to the initial state.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if canvas is nullptr. |

### OH_Drawing_CanvasRotate()

```c
void OH_Drawing_CanvasRotate(OH_Drawing_Canvas* canvas, float degrees, float px, float py)
```

**Description**

Rotates a canvas.<br>This API may generate an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if canvas is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| float degrees | Rotation angle, in degrees. A positive value indicates clockwise rotation, and a negative value indicates counterclockwise rotation. |
| float px | Horizontal coordinate of the rotation center, in physical pixels (px). |
| float py | Vertical coordinate of the rotation center, in physical pixels (px). |

### OH_Drawing_CanvasTranslate()

```c
void OH_Drawing_CanvasTranslate(OH_Drawing_Canvas* canvas, float dx, float dy)
```

**Description**

Translates a canvas by a given distance.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| float dx | Movement distance along the x-axis, in physical pixels (px). |
| float dy | Movement distance along the y-axis, in physical pixels (px). |

### OH_Drawing_CanvasScale()

```c
void OH_Drawing_CanvasScale(OH_Drawing_Canvas* canvas, float sx, float sy)
```

**Description**

Scales a canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| float sx | Scale ratio on the X axis.|
| float sy | Scale ratio on the Y axis.|

### OH_Drawing_CanvasSkew()

```c
void OH_Drawing_CanvasSkew(OH_Drawing_Canvas* canvas, float sx, float sy)
```

**Description**

Skews a canvas. This function premultiplies the current canvas matrix by a skew transformation matrix and applies the resulting matrix to the canvas. The skew transformation matrix is as follows:<br>|1 sx 0|  <br>|sy 1 0|  <br>|0  0 1|<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| float sx | Amount of tilt on the X axis. A positive number tilts the drawing rightwards along the positive direction of the Y axis, and a negative number tilts the drawing leftwards along the positive direction of the Y axis.|
| float sy | Amount of tilt on the Y axis. A positive number tilts the drawing downwards along the positive direction of the X axis, and a negative number tilts the drawing upwards along the positive direction of the X axis.|

### OH_Drawing_CanvasGetWidth()

```c
int32_t OH_Drawing_CanvasGetWidth(OH_Drawing_Canvas* canvas)
```

**Description**

Obtains the canvas width.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Canvas width, in physical pixels (px). |

### OH_Drawing_CanvasGetHeight()

```c
int32_t OH_Drawing_CanvasGetHeight(OH_Drawing_Canvas* canvas)
```

**Description**

Obtains the canvas height.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Height of the canvas, in physical pixels (px). |

### OH_Drawing_CanvasGetLocalClipBounds()

```c
void OH_Drawing_CanvasGetLocalClipBounds(OH_Drawing_Canvas* canvas, OH_Drawing_Rect* rect)
```

**Description**

Obtains the bounds of the cropping region of the canvas. This function cannot be used for a canvas of the recording type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object. You can call [OH_Drawing_RectCreate](capi-drawing-rect-h.md#oh_drawing_rectcreate) to create a rectangle object.|

### OH_Drawing_CanvasGetTotalMatrix()

```c
void OH_Drawing_CanvasGetTotalMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)
```

**Description**

Obtains the 3x3 matrix of a canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. You can call [OH_Drawing_MatrixCreate](capi-drawing-matrix-h.md#oh_drawing_matrixcreate) to create a matrix object.|

### OH_Drawing_CanvasConcatMatrix()

```c
void OH_Drawing_CanvasConcatMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)
```

**Description**

Preconcats the existing matrix of the canvas with the passed-in matrix. The drawing operation triggered before this API is called is not affected.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|

### OH_Drawing_CanvasDrawShadow()

```c
void OH_Drawing_CanvasDrawShadow(OH_Drawing_Canvas* canvas, OH_Drawing_Path* path, OH_Drawing_Point3D planeParams,OH_Drawing_Point3D devLightPos, float lightRadius, uint32_t ambientColor, uint32_t spotColor,OH_Drawing_CanvasShadowFlags flag)
```

**Description**

Draws a spotlight-type shadow, using a path to describe the outline of the ambient light shadow.<br>This API may generate an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or path is NULL;<br>returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if flag is outside the enum range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object, which is used to generate shadows.|
| [OH_Drawing_Point3D](capi-drawing-oh-drawing-point3d.md) planeParams | Z-axis offset of an occluder relative to the canvas, based on its x and y coordinates.|
| [OH_Drawing_Point3D](capi-drawing-oh-drawing-point3d.md) devLightPos | Position of the light relative to the canvas, where x and y indicate the coordinates of the light source on the canvas plane, and z indicates the height of the light source from the canvas plane. |
| float lightRadius | Radius of the light source, in physical pixels (px). The value range is greater than or equal to 0. |
| uint32_t ambientColor | Ambient shadow color, represented by a 32-bit (ARGB) parameter. The overall value range of the parameter is [0x00000000, 0xFFFFFFFF], and the value range of each color channel (A, R, G, B) is [0, 255]. |
| uint32_t spotColor | Spot shadow color, represented by a 32-bit (ARGB) parameter. The overall value range of the parameter is [0x00000000, 0xFFFFFFFF], and the value range of each color channel (A, R, G, B) is [0, 255]. |
| [OH_Drawing_CanvasShadowFlags](#oh_drawing_canvasshadowflags) flag | Shadow flag. |

### OH_Drawing_CanvasClear()

```c
void OH_Drawing_CanvasClear(OH_Drawing_Canvas* canvas, uint32_t color)
```

**Description**

Clears the canvas with a specified color. Unlike [OH_Drawing_CanvasDrawColor](#oh_drawing_canvasdrawcolor), this API directly replaces all content on the canvas with the specified color, whereas OH_Drawing_CanvasDrawColor blends the color with the existing content on the canvas through a blend mode.<br>This API may generate an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if canvas is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| uint32_t color | Indicates the specified color, represented by a 32-bit (ARGB) parameter. The overall value range of the parameter is [0x00000000, 0xFFFFFFFF], and the value range of each color channel (A, R, G, B) is [0, 255]. |

### OH_Drawing_CanvasSetMatrix()

```c
void OH_Drawing_CanvasSetMatrix(OH_Drawing_Canvas* canvas, OH_Drawing_Matrix* matrix)
```

**Description**

Sets the matrix state of the canvas, replacing the current matrix of the canvas with the passed-in matrix, which affects the coordinate transformation of subsequent drawing operations.<br>This API may generate an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either canvas or matrix is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. You can call [OH_Drawing_MatrixCreate](capi-drawing-matrix-h.md#oh_drawing_matrixcreate) to create a matrix object.|

### OH_Drawing_CanvasResetMatrix()

```c
void OH_Drawing_CanvasResetMatrix(OH_Drawing_Canvas* canvas)
```

**Description**

Resets the matrix of this canvas to an identity matrix.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **canvas** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|

### OH_Drawing_CanvasDrawImageRectWithSrc()

```c
void OH_Drawing_CanvasDrawImageRectWithSrc(OH_Drawing_Canvas* canvas, const OH_Drawing_Image* image,const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, const OH_Drawing_SamplingOptions* samplingOptions,OH_Drawing_SrcRectConstraint srcRectConstraint)
```

**Description**

Draws a portion of an image onto a specified area of the canvas. The area selected by the source rectangle is scaled and translated to the destination rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If one of **canvas**, **image**, **src**, or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | Pointer to the [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* src | Pointer to the source rectangle object [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md), used to specify the source area to be drawn in the image. |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to the destination rectangle object [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md), indicating the target drawing area on the canvas. |
| const [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | Pointer to the [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) object. A null pointer means that the default sampling options are used.|
| [OH_Drawing_SrcRectConstraint](#oh_drawing_srcrectconstraint) srcRectConstraint | Constraint type. |

### OH_Drawing_CanvasDrawImageRect()

```c
void OH_Drawing_CanvasDrawImageRect(OH_Drawing_Canvas* canvas, OH_Drawing_Image* image,OH_Drawing_Rect* rect, OH_Drawing_SamplingOptions* samplingOptions)
```

**Description**

Draws an image onto a specified area of the canvas. Unlike [OH_Drawing_CanvasDrawImageRectWithSrc](#oh_drawing_canvasdrawimagerectwithsrc), this API does not support specifying the source rectangle constraint type.<br>This API may generate an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of canvas, image, or rect is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | Pointer to the [OH_Drawing_Image](capi-drawing-oh-drawing-image.md) object.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to a rectangle object [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md), which represents the target area for drawing the image on the canvas. |
| [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | Pointer to the [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md) object. A null pointer means that the default sampling options are used.|

### OH_Drawing_CanvasDrawVertices()

```c
void OH_Drawing_CanvasDrawVertices(OH_Drawing_Canvas* canvas, OH_Drawing_VertexMode vertexMmode,int32_t vertexCount, const OH_Drawing_Point2D* positions, const OH_Drawing_Point2D* texs,const uint32_t* colors, int32_t indexCount, const uint16_t* indices, OH_Drawing_BlendMode mode)
```

**Description**

Draws a triangular grid described by a vertex array.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **positions** is NULL, **vertexCount** is less than 3, or **indexCount** is less than 3 but not 0, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If either **vertexMmode** or **mode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an **OH_Drawing_Canvas** object.|
| [OH_Drawing_VertexMode](#oh_drawing_vertexmode) vertexMmode | Connection mode for drawing vertices. For supported modes, see [OH_Drawing_VertexMode](#oh_drawing_vertexmode). |
| int32_t vertexCount | Number of elements in the vertex array. The value must be greater than or equal to 3.|
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* positions | Pointer to the array that holds the position of every vertex. The array cannot be null and its length must be equal to the value of **vertexCount**.|
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* texs | Pointer to the array that describes the texture space coordinates corresponding to the vertices. It can be null. When it is null, texture mapping is not applied, and drawing uses only colors or the default fill. When it is not null, the texture is mapped onto the triangle mesh according to the vertex texture coordinates, and its length must be equal to vertexCount. |
| const uint32_t* colors | Pointer to the array that describes the color corresponding to each vertex, used for color interpolation within triangles. It can be null. When it is null, per-vertex colors are not used, and drawing uses the default brush color. When it is not null, the colors of the vertices are interpolated and blended within the triangle mesh to produce a gradient effect, and its length must be equal to vertexCount. |
| int32_t indexCount | Number of indices. The value can be 0 or a value greater than or equal to 3.|
| const uint16_t* indices | Pointer to the array that describes the index corresponding to each vertex. It can be null. When it is null, triangles are drawn sequentially in the order of the vertex array. When it is not null, triangles are drawn in the order specified by the indices, which allows vertices to be reused to reduce the amount of data, and its length must be equal to indexCount. |
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) mode | Blend mode, used to control how vertex colors are blended. For supported modes, see [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode). |

### OH_Drawing_CanvasReadPixels()

```c
bool OH_Drawing_CanvasReadPixels(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo,void* dstPixels, uint32_t dstRowBytes, int32_t srcX, int32_t srcY)
```

**Description**

Copies pixel data from a canvas to a specified address. This function cannot be used for a canvas of the recording type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If one of **canvas**, **imageInfo**, or **dstPixels** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md)* imageInfo | Pointer to the [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) object.|
| void* dstPixels | Destination pixel storage start address. The buffer size must be at least dstRowBytes × image height. |
| uint32_t dstRowBytes | Size of one row of pixels, in bytes. The value range is greater than 0. Copy fails when it is equal to 0. |
| int32_t srcX | X-axis offset of the canvas pixel, in physical pixels (px). |
| int32_t srcY | Y-axis offset of the canvas pixel, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the pixel data is copied to the start address of the storage; returns **false** otherwise.|

### OH_Drawing_CanvasReadPixelsToBitmap()

```c
bool OH_Drawing_CanvasReadPixelsToBitmap(OH_Drawing_Canvas* canvas,OH_Drawing_Bitmap* bitmap, int32_t srcX, int32_t srcY)
```

**Description**

Copies pixel data from a canvas to an image. This function cannot be used for a canvas of the recording type.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **canvas** or **bitmap** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md)* bitmap | Pointer to the [OH_Drawing_Bitmap](capi-drawing-oh-drawing-bitmap.md) object.|
| int32_t srcX | X-axis offset of the canvas pixel, in physical pixels (px). |
| int32_t srcY | Y-axis offset of the canvas pixel, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the pixel data is copied to the image; returns **false** otherwise.|

### OH_Drawing_CanvasIsClipEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasIsClipEmpty(OH_Drawing_Canvas* canvas, bool* isClipEmpty)
```

**Description**

Checks whether the drawable area is empty after clipping.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| bool* isClipEmpty | Pointer to the variable that specifies whether the region is empty. The value **true** means that the region is empty, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **canvas** or **isClipEmpty** is NULL.|

### OH_Drawing_CanvasGetImageInfo()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasGetImageInfo(OH_Drawing_Canvas* canvas, OH_Drawing_Image_Info* imageInfo)
```

**Description**

Obtains the image information of the canvas.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md)* imageInfo | Pointer to the [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **canvas** or **imageInfo** is NULL.|

### OH_Drawing_CanvasDrawRecordCmd()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawRecordCmd(OH_Drawing_Canvas* canvas, OH_Drawing_RecordCmd* recordCmd)
```

**Description**

Draws a recorded command object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object. Only the canvas of the recording type is supported.|
| [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md)* recordCmd | Pointer to the [OH_Drawing_RecordCmd](capi-drawing-oh-drawing-recordcmd.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **canvas** or **recordCmd** is NULL.|

### OH_Drawing_CanvasQuickRejectPath()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectPath(OH_Drawing_Canvas* canvas, const OH_Drawing_Path* path,bool* quickReject)
```

**Description**

Checks whether the path and the canvas area do not intersect. The canvas area includes the boundary.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool* quickReject | Pointer to the check result. The value **true** means that the path is not intersecting with the canvas area, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **canvas**, **path**, or **quickReject** is NULL.|

### OH_Drawing_CanvasQuickRejectRect()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasQuickRejectRect(OH_Drawing_Canvas* canvas, const OH_Drawing_Rect* rect,bool* quickReject)
```

**Description**

Checks whether the rectangle and the canvas area do not intersect. The canvas area includes the boundary.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object.|
| bool* quickReject | Pointer to the check result. The value **true** means that the rectangle is not intersecting with the canvas area, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **canvas**, **rect**, or **quickReject** is NULL.|

### OH_Drawing_CanvasDrawPixelMapMesh()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawPixelMapMesh(OH_Drawing_Canvas* cCanvas, OH_Drawing_PixelMap* pixelMap, uint32_t meshWidth, uint32_t meshHeight, const float* vertices, uint32_t verticesSize, uint32_t vertOffset, const uint32_t* colors, uint32_t colorsSize, uint32_t colorOffset)
```

**Description**

Draws a pixel map on a mesh that is evenly distributed over the pixel map. (Only the brush is supported; the pen has no drawing effect.)

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* cCanvas | Pointer to an [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object. The canvas must have a brush set; using only a pen produces no drawing effect. |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | Pointer to the [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md) object.|
| uint32_t meshWidth | Number of columns in the mesh. The value is a positive integer. |
| uint32_t meshHeight | Number of rows in the mesh. The value is a positive integer. |
| const float* vertices | Pointer to the mesh vertex array.|
| uint32_t verticesSize | Size of the mesh vertex array. The size must be ((meshWidth + 1) * (meshHeight + 1) + vertOffset) * 2. |
| uint32_t vertOffset | Number of vertices to skip before drawing. The value is an integer greater than or equal to 0.|
| const uint32_t* colors | Pointer to the mesh color array. This parameter can be NULL. |
| uint32_t colorsSize | Size of the mesh color array. If the array exists, the size must be (meshWidth + 1) * (meshHeight + 1) + colorOffset.|
| uint32_t colorOffset | Number of colors to skip before drawing. The value is an integer greater than or equal to 0.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if any of the parameters, such as **cCanvas**, **pixelMap**, and **vertices**, is empty or the input parameter does not meet the value rule.|

### OH_Drawing_CanvasIsOpaque()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasIsOpaque(const OH_Drawing_Canvas* canvas, bool* isOpaque)
```

**Description**

Checks whether the layer currently drawn to the device is opaque.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to the canvas object [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md). |
| bool* isOpaque | Output parameter indicating whether the canvas is opaque. The value **true** indicates opaque, and **false** indicates transparent. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if **canvas** or **isOpaque** is null. |

### OH_Drawing_CanvasDrawGlyphs()

```c
OH_Drawing_ErrorCode OH_Drawing_CanvasDrawGlyphs(const OH_Drawing_Canvas* canvas, const int* glyphIds, int glyphIdCount, int glyphIdOffset, const OH_Drawing_Point2D* positions, int positionCount, int positionOffset, int glyphCount, const OH_Drawing_Font* font)
```

**Description**

Draws an array of glyphs with the specified font. If the glyph count is less than or equal to 0, nothing is drawn.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [const OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* canvas | Pointer to an OH_Drawing_Canvas object. |
| const int* glyphIds | Array of glyph IDs. |
| int glyphIdCount | Size of the glyph ID array. It must be less than or equal to the actual size of the array, and greater than or equal to the sum of glyphIdOffset and glyphCount. If it exceeds the array length, it cannot be verified and may cause drawing exceptions or lag. |
| int glyphIdOffset | Number of elements to skip in the glyph ID array before drawing.<br>If glyphCount is n and the skip length is m, the valid glyphIds array range is [glyphIds[m], glyphIds[m+n]). |
| [const OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* positions | Array of positions. |
| int positionCount | Size of the position array. It must be less than or equal to the actual size of the array, and greater than or equal to the sum of positionOffset and glyphCount. If it exceeds the array length, it cannot be verified and may cause drawing exceptions or lag. |
| int positionOffset | Number of elements to skip in the position array before drawing.<br>If glyphCount is n and the skip length is m, the valid positions array range is [positions[m], positions[m+n]). |
| int glyphCount | Number of glyphs to draw. If the count is less than or equal to 0, nothing is drawn and the error code OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE is returned.<br>If the sum of glyphCount and glyphIdOffset, or the sum of glyphCount and positionOffset, is greater than 0x7FFFFFFF, the calculation result is treated as 0x7FFFFFFF. |
| [const OH_Drawing_Font](capi-drawing-oh-drawing-font.md)* font | Pointer to the font object [OH_Drawing_Font](capi-drawing-oh-drawing-font.md). |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER. Possible cause: any of canvas, glyphIds, positions, and font is NULL.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE. Possible causes are as follows:<br> - glyphIdOffset or positionOffset is less than 0;<br> - glyphIdCount is less than glyphIdOffset + glyphCount;<br> - positionCount is less than positionOffset + glyphCount;<br> - glyphIdOffset is less than 0;<br> - positionOffset is less than 0;<br> - glyphCount is less than or equal to 0. |