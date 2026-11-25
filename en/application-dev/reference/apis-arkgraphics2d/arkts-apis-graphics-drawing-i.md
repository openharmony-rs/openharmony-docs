# Interfaces (Others)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8ce668ad94101a68cd0e3c33de2da76aa75a68f0 translatedAt=2026-11-16T06:08:15.848Z pushedAt=2026-11-16T06:31:14.299Z nl=1 -->

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
| glyph     | number | No   | No   | Stores the glyph index. This parameter is an integer. If a floating-point number is passed in, it is rounded down. |
| positionX | number | No   | No   | X-axis coordinate of the text start point. This parameter is a floating-point number. The unit is physical pixel px. |
| positionY | number | No   | No   | Y-axis coordinate of the text start point. This parameter is a floating-point number. The unit is physical pixel px. |

## FontMetrics

Describes the attributes that describe the font size and layout. A typeface has similar font metrics.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

| Name   | Type  | Read-Only| Optional| Description                                                        |
| ------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| flags<sup>12+</sup>   | [FontMetricsFlags](arkts-apis-graphics-drawing-e.md#fontmetricsflags12) | No  | Yes  | Font measurement flags that are valid.       |
| top     | number | No   | No   | Maximum distance above the baseline that the bounding box of any glyph in the font extends, a floating-point number. The unit is physical pixel px. |
| ascent  | number | No   | No   | Distance from the highest point of the text to the baseline, a floating-point number. The unit is physical pixel px.                             |
| descent | number | No   | No   | Distance from the baseline to the lowest point of the text, a floating-point number. The unit is physical pixel px.                             |
| bottom  | number | No   | No   | Maximum distance below the baseline that the bounding box of any glyph in the font extends, a floating-point number. The unit is physical pixel px. |
| leading | number | No   | No   | Line spacing, the distance from the descent of the previous line of text to the ascent of the next line of text, a floating-point number. The unit is physical pixel px. |
| avgCharWidth<sup>12+</sup> | number | No | Yes | Average character width, a floating-point number. The unit is physical pixel px. |
| maxCharWidth<sup>12+</sup> | number | No | Yes | Maximum character width, a floating-point number. The unit is physical pixel px. |
| xMin<sup>12+</sup> | number | No   | Yes   | Horizontal distance from the leftmost edge of the bounding box of any glyph in the font to the origin. This value is often less than zero, indicating the minimum horizontal boundary of the glyph. The unit is physical pixel px.                |
| xMax<sup>12+</sup> | number | No   | Yes   | Horizontal distance from the rightmost edge of the bounding box of any glyph in the font to the origin, a floating-point number. This value is mostly positive, indicating the maximum horizontal extent of the glyph. The unit is physical pixel px.        |
| xHeight<sup>12+</sup> | number | No   | Yes   | Vertical offset of the top of the lowercase letter x relative to the baseline, a floating-point number, usually a negative value. The unit is physical pixel px. |
| capHeight<sup>12+</sup> | number | No   | Yes   | Vertical offset of the top of uppercase letters relative to the baseline, a floating-point number, usually a negative value. The unit is physical pixel px. |
| underlineThickness<sup>12+</sup> | number | No   | Yes   | Thickness of the underline, a floating-point number. The unit is physical pixel px.                                          |
| underlinePosition<sup>12+</sup>  | number | No   | Yes   | Vertical distance from the text baseline to the top of the underline, a floating-point number, usually a positive value. The unit is physical pixel px.             |
| strikethroughThickness<sup>12+</sup>  | number | No   | Yes   | Thickness of the text strikethrough, that is, the width of the horizontal line through the text characters, a floating-point number. The unit is physical pixel px.    |
| strikethroughPosition<sup>12+</sup>  | number | No | Yes | Vertical distance from the text baseline to the strikethrough line, a floating-point number, usually a negative value. The unit is physical pixel px. |

## FontFeature<sup>20+</sup>

Defines font features, which are typesetting rules within a font that determine how glyphs look, such as ligatures, alternates, and superscripts/subscripts.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

| Name   | Type  | Read-Only| Optional| Description  |
| ------- | ------ | ---- | ---- | ------------------ |
| name   | string | No   | No   | Name of the font feature. It is usually a tag consisting of four ASCII characters (for example, liga, frac, and case), and it takes effect only when the corresponding TTF file supports it. You are advised to use a font viewer tool or refer to the font documentation to determine a valid name.|
| value | number | No | No | Value of the font feature, which is a floating-point number. It takes effect only when the corresponding TTF file supports it. You are advised to use a font viewer tool or refer to the font documentation to determine the specific valid value range.|

## RecordCmd

Describes a set of recorded draw commands. This object is immutable. It is created by [RecordCmdUtils.finishRecording](arkts-apis-graphics-drawing-RecordCmdUtils.md#finishrecording) and can be passed to [Canvas.drawRecordCmd](arkts-apis-graphics-drawing-Canvas.md#drawrecordcmd) for command playback, thereby reproducing the recorded draw operations.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since:** 26.0.1
## TypefaceFallbackInfo

Defines the structure for font fallback information, which indicates a set of glyph fragments that use the same fallback font.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since:** 26.0.1

| Name    | Type   | Read-Only | Optional | Description   |
| ------- | ------ | ---- | ---- | ------------------ |
| glyphIds   | Array\<number> | No   | No   | Glyph ID array of the glyph fragment. |
| typeface | [Typeface](arkts-apis-graphics-drawing-Typeface.md) | No | No | Font object matched by the glyph fragment. |
