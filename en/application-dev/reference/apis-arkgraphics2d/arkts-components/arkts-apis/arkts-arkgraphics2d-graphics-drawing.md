# @ohos.graphics.drawing(Drawing Module)

During application development, you often need to draw different elements. Typically, you can use ArkUI components to draw the desired elements or effects. However, sometimes these components cannot meet the needs for custom graphics or effects. In such cases, you can turn to the Drawing module for flexible custom drawing. This module provides basic drawing capabilities, such as drawing rectangles, circles, points, straight lines, custom paths, and fonts.

> **NOTE:** 
> 
> - This module uses the physical pixel unit, px.
> 
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Brush](arkts-arkgraphics2d-drawing-brush-c.md) | Defines a brush, which is used to describe the style and color to fill in a shape. |
| [Canvas](arkts-arkgraphics2d-drawing-canvas-c.md) | A carrier that carries the drawn content and drawing status. |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Defines a color filter. |
| [Font](arkts-arkgraphics2d-drawing-font-c.md) | Describes the attributes used for text rendering, such as size and typeface. |
| [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) | Implements an image filter. |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | Lattice object. which is used to divide an image by lattice. |
| [MaskFilter](arkts-arkgraphics2d-drawing-maskfilter-c.md) | Implements a mask filter. |
| [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Implements a matrix. A 3 x 3 matrix is shown as below.![matrix_3x3](../../../reference/apis-arkgraphics2d/figures/matrix3X3.PNG) Elements in the matrix from left to right and from top to bottom respectively represent a horizontal scale coefficient, a horizontal skew coefficient, a horizontal translation coefficient, a vertical skew coefficient, a vertical scale coefficient, a vertical translation coefficient, an X-axis perspective coefficient, a Y-axis perspective coefficient, and a perspective scale coefficient. If (x&lt;sub&gt;1&lt;/sub&gt;, y&lt;sub&gt;1&lt;/sub&gt;) is the source coordinate point, (x&lt;sub&gt;2&lt;/sub&gt;, y&lt;sub&gt;2&lt;/sub&gt;) is the coordinate point obtained by transforming the source coordinate point using the matrix, then the relationship between the two coordinate points is as follows:![matrix_xy](../../../reference/apis-arkgraphics2d/figures/matrix_xy.PNG) |
| [Path](arkts-arkgraphics2d-drawing-path-c.md) | A compound geometric path consisting of line segments, arcs, quadratic Bezier curves, and cubic Bezier curves. |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | Implements a path effect. |
| [PathIterator](arkts-arkgraphics2d-drawing-pathiterator-c.md) | Implements a path operation iterator. You can read path operation instructions by traversing the iterator. |
| [Pen](arkts-arkgraphics2d-drawing-pen-c.md) | Defines a pen, which is used to describe the style and color to outline a shape. |
| [PointUtils](arkts-arkgraphics2d-drawing-pointutils-c.md) | This class offers a comprehensive set of operations for handling common2D Point objects. |
| [RecordCmdUtils](arkts-arkgraphics2d-drawing-recordcmdutils-c.md) | This class offers a set of operations to generate drawing commands. |
| [RectUtils](arkts-arkgraphics2d-drawing-rectutils-c.md) | This module provides tools for processing rectangles. Use scenarios: |
| [Region](arkts-arkgraphics2d-drawing-region-c.md) | Describes a region, which is used to describe the region where the shape can be drawn. |
| [RoundRect](arkts-arkgraphics2d-drawing-roundrect-c.md) | Rounded rectangle. |
| [SamplingOptions](arkts-arkgraphics2d-drawing-samplingoptions-c.md) | Implements sampling options. |
| [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) | Implements the shader effect. After a shader effect is set for a pen or brush, the shader effect instead of the color attribute is used for drawing. In this case, the alpha value set for the pen or brush still takes effect. |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | Implements a shadow layer. |
| [TextBlob](arkts-arkgraphics2d-drawing-textblob-c.md) | Defines a block consisting of one or more characters with the same font. |
| [Tool](arkts-arkgraphics2d-drawing-tool-c.md) | A utility class that provides only static methods to convert data structs defined in other modules and [common2D](arkts-arkgraphics2d-graphics-common2d.md). |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | Describes the style of a typeface, such as SimSun or KaiTi. |
| [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | This module defines a struct for setting typeface arguments. |

### Interfaces

| Name | Description |
| --- | --- |
| [FontFeature](arkts-arkgraphics2d-drawing-fontfeature-i.md) | Defines font features, which are typesetting rules within a font that determine how glyphs look, such as ligatures, alternates, and superscripts/subscripts. |
| [FontMetrics](arkts-arkgraphics2d-drawing-fontmetrics-i.md) | Describes the attributes that describe the font size and layout. A typeface has similar font metrics. |
| [RecordCmd](arkts-arkgraphics2d-drawing-recordcmd-i.md) | Describes a list of recorded drawing commands. |
| [TextBlobRunBuffer](arkts-arkgraphics2d-drawing-textblobrunbuffer-i.md) | Describes a series of consecutive glyphs with the same attributes in a text blob. |
| [TypefaceFallbackInfo](arkts-arkgraphics2d-drawing-typefacefallbackinfo-i.md) | Defines the typeface fallback info structure for a run of glyphs that share the same fallback typeface. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AtlasImage](arkts-arkgraphics2d-drawing-atlasimage-i-sys.md) | Defines the atlas frame parameters for sprite sheet frame animation. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BlendMode](arkts-arkgraphics2d-drawing-blendmode-e.md) | Enumerates the blend modes. A blend mode combines two colors (source color and destination color) in a specific way to create a new color. This is commonly used in graphics operations like overlaying, filtering, and masking. The blending process applies the same logic to the red, green, and blue color channels separately. The alpha channel, however, is handled according to the specific definitions of each blend mode. For brevity, the following abbreviations are used: s: source. d: destination. sa: source alpha. da: destination alpha. The following abbreviations are used in the calculation result: r: used when the calculation method is the same for the four channels (alpha, red, green, and blue channels). ra: used when only the alpha channel is manipulated. **rc**: used when the other three color channels are manipulated. The table below shows the effect of each blend mode, where the yellow rectangle is the source and the blue circle is the destination. |
| [BlurType](arkts-arkgraphics2d-drawing-blurtype-e.md) | Enumerates the blur types of a mask filter. |
| [CapStyle](arkts-arkgraphics2d-drawing-capstyle-e.md) | Enumerates the cap styles of a pen. The cap style defines the style of both ends of a line segment drawn by the pen. |
| [ClipOp](arkts-arkgraphics2d-drawing-clipop-e.md) | Enumerates the canvas clipping modes. |
| [CornerPos](arkts-arkgraphics2d-drawing-cornerpos-e.md) | Enumerates the corner positions of a rounded rectangle. |
| [FilterMode](arkts-arkgraphics2d-drawing-filtermode-e.md) | Enumerates the filter modes. |
| [FontEdging](arkts-arkgraphics2d-drawing-fontedging-e.md) | Enumerates the font edging types. |
| [FontHinting](arkts-arkgraphics2d-drawing-fonthinting-e.md) | Enumerates the font hinting types. |
| [FontMetricsFlags](arkts-arkgraphics2d-drawing-fontmetricsflags-e.md) | Enumerates the font measurement flags, which is used to specify whether a field in the [FontMetrics](arkts-arkgraphics2d-drawing-fontmetrics-i.md) struct is valid. |
| [JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md) | Enumerates the join styles of a pen. The join style defines the shape of the joints of a polyline segment drawn by the pen. |
| [PathDashStyle](arkts-arkgraphics2d-drawing-pathdashstyle-e.md) | Enumerates the drawing styles for path effects. |
| [PathDirection](arkts-arkgraphics2d-drawing-pathdirection-e.md) | Enumerates the directions of a closed contour. |
| [PathFillType](arkts-arkgraphics2d-drawing-pathfilltype-e.md) | Enumerates the fill types of a path. |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | Enumerates the path operation types contained in an iterator. It is used to read path operation instructions. |
| [PathMeasureMatrixFlags](arkts-arkgraphics2d-drawing-pathmeasurematrixflags-e.md) | Enumerates the dimensions of matrix information in path measurement. It is often used in animation scenarios where objects move along a path. |
| [PathOp](arkts-arkgraphics2d-drawing-pathop-e.md) | Enumerates the path operation types. It is often used in path combination and clipping scenarios. |
| [PointMode](arkts-arkgraphics2d-drawing-pointmode-e.md) | Enumerates the modes for drawing multiple points in an array. |
| [RectType](arkts-arkgraphics2d-drawing-recttype-e.md) | Enumerates the types of rectangles used to fill the lattices. Used only in [Lattice](arkts-arkgraphics2d-graphics-drawing.md). |
| [RegionOp](arkts-arkgraphics2d-drawing-regionop-e.md) | Enumerates the operations for combining two regions. |
| [ScaleToFit](arkts-arkgraphics2d-drawing-scaletofit-e.md) | Enumerates the modes of scaling a source rectangle into a destination rectangle. |
| [ShadowFlag](arkts-arkgraphics2d-drawing-shadowflag-e.md) | Enumerates the shadow drawing behaviors. |
| [SrcRectConstraint](arkts-arkgraphics2d-drawing-srcrectconstraint-e.md) | Enumerates the constraints on the source rectangle. It is used to specify whether to limit the sampling range within the source rectangle when drawing an image on a canvas. |
| [TextEncoding](arkts-arkgraphics2d-drawing-textencoding-e.md) | Enumerates the text encoding types. |
| [TileMode](arkts-arkgraphics2d-drawing-tilemode-e.md) | Enumerates the tile modes of the shader effect. |
| [VertexMode](arkts-arkgraphics2d-drawing-vertexmode-e.md) | Enumerates the connection modes for vertex drawing. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AtlasInterpolationMode](arkts-arkgraphics2d-drawing-atlasinterpolationmode-e-sys.md) | Defines the interpolation mode for sprite sheet frame animation. |
<!--DelEnd-->
