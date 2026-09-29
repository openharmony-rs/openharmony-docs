# Graphics

Defines the graphics attributes of custom nodes (RenderNode), including geometric transformations (scaling, rotation,
 and translation), unified representation of colors and lengths, shapes, graphics masking and clipping, and blur
 effects. It is suitable for scenarios that require refined graphics drawing and visual effect processing on custom
 nodes.



## Summary

### Functions

| Name | Description |
| --- | --- |
| [borderRadiuses](arkts-arkui-graphics-borderradiuses-f.md) | Generates a **borderRadiuses** object with the specified radius for all border corners. |
| [borderStyles](arkts-arkui-graphics-borderstyles-f.md) | Generates a border style object with the specified border style color for all borders. |
| [edgeColors](arkts-arkui-graphics-edgecolors-f.md) | Generates an **edgeColors** object with the specified edge color for all edges. |
| [edgeWidths](arkts-arkui-graphics-edgewidths-f.md) | Generates an **edgeWidths** object with the specified edge width for all edges. |

### Classes

| Name | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md) | Provides a unified representation and encapsulation of colors. It supports color mixing as well as obtaining the color components in the R, G, B, and Alpha channels. |
| [DrawContext](arkts-arkui-graphics-drawcontext-c.md) | Graphics drawing context, which provides the canvas used for drawing and its width and height. |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Defines the length attribute. When the length unit is PERCENT, the value **1** indicates 100%. |
| [ShapeClip](arkts-arkui-graphics-shapeclip-c.md) | Sets graphics clipping, which supports multiple shapes such as rectangles, rounded rectangles, circles, ellipses, and custom paths. It can clip a RenderNode by shape so that only the content within the clipping area is displayed. |
| [ShapeMask](arkts-arkui-graphics-shapemask-c.md) | Sets a graphics mask, which supports multiple shapes such as rectangles, rounded rectangles, circles, ellipses, and custom paths. It can be applied to a RenderNode to implement a shape mask effect. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [ColorMetrics](arkts-arkui-graphics-colormetrics-c-sys.md) | Provides a unified representation and encapsulation of colors. It supports color mixing as well as obtaining the color components in the R, G, B, and Alpha channels. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BackgroundBlur](arkts-arkui-graphics-backgroundblur-i.md) | Sets the background blur effect. The blur radius can be used to control the blur degree, and the grayscale parameter can be used to adjust the levels of black and white pixels in the image. |
| [Circle](arkts-arkui-graphics-circle-i.md) | Describes a circle. |
| [CommandPath](arkts-arkui-graphics-commandpath-i.md) | Describes the command for drawing a path. |
| [ContentBlur](arkts-arkui-graphics-contentblur-i.md) | Sets the content blur effect. The blur radius can be used to control the blur degree, and the grayscale parameter can be used to adjust the levels of black and white pixels in the image. |
| [Corners](arkts-arkui-graphics-corners-i.md) | Describes the four corners. |
| [Edges](arkts-arkui-graphics-edges-i.md) | Describes the edges. |
| [ForegroundBlur](arkts-arkui-graphics-foregroundblur-i.md) | Sets the foreground blur effect. The blur radius can be used to control the blur degree. |
| [Frame](arkts-arkui-graphics-frame-i.md) | Sets or returns the layout size and position of the component. |
| [RoundRect](arkts-arkui-graphics-roundrect-i.md) | Describes a rectangle with rounded corners. |
| [Size](arkts-arkui-graphics-size-i.md) | Returns the width and height of the component. The default unit is vp, but APIs that use the Size type may specify a different unit, in which case the unit specified by the API takes precedence. |
| [SizeT](arkts-arkui-graphics-sizet-i.md) | Sets the width and height attributes. |
| [Vector2](arkts-arkui-graphics-vector2-i.md) | Defines a vector that contains the x and y coordinate values. |
| [Vector2T](arkts-arkui-graphics-vector2t-i.md) | Represents a vector of the T type that contains two values: x and y. |
| [Vector3](arkts-arkui-graphics-vector3-i.md) | Represents a vector including three values: x, y, and z. |
| [Vector4](arkts-arkui-graphics-vector4-i.md) | Defines a vector that contains the x, y, z, and w coordinate values. |

### Types

| Name | Description |
| --- | --- |
| [BorderRadiuses](arkts-arkui-borderradiuses-t.md) | Sets the uniform radius of the four corners. |
| [CornerRadius](arkts-arkui-cornerradius-t.md) | Sets the semi-axis lengths for the x-axis and y-axis of the rounded corners. |
| [Matrix4](arkts-arkui-matrix4-t.md) | Sets a 4 x 4 matrix. |
| [Offset](arkts-arkui-offset-t.md) | Sets the offset of the component or effect. |
| [Pivot](arkts-arkui-pivot-t.md) | Sets the pivot of the component. As the rotation or scaling center of the component, the pivot affects the rotation and scaling effects. |
| [Position](arkts-arkui-position-t.md) | Sets or returns the position of the component. |
| [PositionT](arkts-arkui-positiont-t.md) | Sets or returns the position of the component. |
| [Rect](arkts-arkui-rect-t.md) | Describes a rectangle. |
| [Rotation](arkts-arkui-rotation-t.md) | Sets the rotation angle of the component. |
| [Scale](arkts-arkui-scale-t.md) | Sets the scale factor of the component. |
| [Translation](arkts-arkui-translation-t.md) | Sets the translation amount of the component. |

### Enums

| Name | Description |
| --- | --- |
| [LengthMetricsUnit](arkts-arkui-graphics-lengthmetricsunit-e.md) | Enumerates length units. |
| [LengthUnit](arkts-arkui-graphics-lengthunit-e.md) | Enumerates length units. |
