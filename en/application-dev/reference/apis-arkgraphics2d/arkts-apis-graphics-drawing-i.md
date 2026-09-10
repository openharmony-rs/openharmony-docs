# Interfaces (Others)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=f6eea2d708fe9f614f443984915f3f68367b709a translatedAt=2026-08-24T07:56:29.964Z pushedAt=2026-08-25T06:41:08.669Z -->

Provides other interfaces related to graphics drawing.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## TextBlobRunBuffer

Describes a series of consecutive glyphs with the same attributes in a text blob.

**System capability**: SystemCapability.Graphics.Drawing

| Name     | Type  | Read-Only| Optional| Description                     |
| --------- | ------ | ---- | ---- | ------------------------- |
| glyph     | number | No  | No  | Index of the glyph. The value is an integer. If a floating point number is passed in, the value is rounded down.|
| positionX | number | No | No | X-axis coordinate of the text start point. This parameter is a floating-point number. The unit is physical pixels (px). |
| positionY | number | No | No | Y-axis coordinate of the text start point. This parameter is a floating-point number. The unit is physical pixels (px). |

## FontMetrics

Describes the attributes that describe the font size and layout. A typeface has similar font metrics.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

| Name   | Type  | Read-Only| Optional| Description                                                        |
| ------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| flags<sup>12+</sup>   | [FontMetricsFlags](arkts-apis-graphics-drawing-e.md#fontmetricsflags12) | No  | Yes  | Font measurement flags that are valid.       |
| top     | number | No   | No   | Maximum distance by which any glyph edge bounding box in the font extends above the baseline. The value is a floating-point number. The unit is physical pixels (px). |
| ascent  | number | No   | No   | Distance from the highest point of the text to the baseline. The value is a floating-point number. The unit is physical pixels (px).                             |
| descent | number | No   | No   | Distance from the baseline to the lowest point of the text. The value is a floating-point number. The unit is physical pixels (px).                             |
| bottom  | number | No   | No   | Maximum distance by which any glyph edge bounding box in the font extends below the baseline. The value is a floating-point number. The unit is physical pixels (px). |
| leading | number | No   | No   | Line spacing, that is, the distance from the descent of the previous line to the ascent of the next line. The value is a floating-point number. The unit is physical pixels (px). |
| avgCharWidth<sup>12+</sup> | number | No | Yes | Average character width. The value is a floating-point number. The unit is physical pixels (px). |
| maxCharWidth<sup>12+</sup> | number | No | Yes | Maximum character width. The value is a floating-point number. The unit is physical pixels (px). |
| xMin<sup>12+</sup> | number | No   | Yes   | Horizontal distance from the leftmost edge of any glyph edge bounding box in the font to the origin. This value is usually less than zero, indicating the minimum horizontal boundary of the glyph. The unit is physical pixels (px).                |
| xMax<sup>12+</sup> | number | No   | Yes   | Horizontal distance from the rightmost edge of any glyph edge bounding box in the font to the origin. The value is a floating-point number and is mostly positive, indicating the maximum horizontal extent of the glyph. The unit is physical pixels (px).        |
| xHeight<sup>12+</sup> | number | No   | Yes   | Vertical offset of the top of the lowercase letter x relative to the baseline. The value is a floating-point number and is usually negative. The unit is physical pixels (px). |
| capHeight<sup>12+</sup> | number | No   | Yes   | Vertical offset of the top of an uppercase letter relative to the baseline. The value is a floating-point number and is usually negative. The unit is physical pixels (px). |
| underlineThickness<sup>12+</sup> | number | No   | Yes   | Thickness of the underline. The value is a floating-point number. The unit is physical pixels (px).                                          |
| underlinePosition<sup>12+</sup>  | number | No   | Yes   | Vertical distance from the text baseline to the top of the underline. The value is a floating-point number and is usually positive. The unit is physical pixels (px).             |
| strikethroughThickness<sup>12+</sup>  | number | No   | Yes   | Thickness of the strikethrough line, that is, the width of the horizontal line that runs through the text characters. The value is a floating-point number. The unit is physical pixels (px).    |
| strikethroughPosition<sup>12+</sup>  | number | No | Yes | Vertical distance from the text baseline to the strikethrough line. The value is a floating-point number and is usually negative. The unit is physical pixels (px). |

## FontFeature<sup>20+</sup>

Defines font features, which are typesetting rules within a font that determine how glyphs look, such as ligatures, alternates, and superscripts/subscripts.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

| Name   | Type  | Read-Only| Optional| Description  |
| ------- | ------ | ---- | ---- | ------------------ |
| name   | string | No   | No   | Name of the font feature. It is usually a tag consisting of four ASCII characters (for example, liga, frac, and case), and it takes effect only when the corresponding TTF file supports it. You are advised to use a font viewer tool or refer to the font documentation to determine a valid name.|
| value | number | No | No | Value of the font feature, which is a floating-point number. It takes effect only when the corresponding TTF file supports it. You are advised to use a font viewer tool or refer to the font documentation to determine the valid value range.|