# Class (ColorFilter)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9d24e15ef82b33c8322a412e3fad5e8314ad7c4e translatedAt=2026-08-24T07:53:11.229Z pushedAt=2026-08-25T03:21:12.004Z -->

A color filter is used to transform and process the colors of images or graphics. It supports creating various types of color filters, including blend mode color filters, composite color filters, matrix color filters, gamma color space conversion filters, luma color filters, and lighting color filters.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.
>
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## createBlendModeColorFilter

static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode) : ColorFilter

Creates a **ColorFilter** object with a given color and blend mode.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | [common2D.Color](js-apis-graphics-common2D.md#color) | Yes   | Color in ARGB format. The value of each color channel is an integer in the range [0, 255]. |
| mode   | [BlendMode](arkts-apis-graphics-drawing-e.md#blendmode)                              | Yes   | Blend mode, which specifies the color blending algorithm used when two shaders are overlaid. |

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns a color filter created based on the specified color and blend mode. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let colorFilter = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.SRC);
```

## createBlendModeColorFilter<sup>18+</sup>

static createBlendModeColorFilter(color: common2D.Color | number, mode: BlendMode) : ColorFilter

Creates a color filter with the specified color and blend mode.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                                | Mandatory| Description            |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | [common2D.Color](js-apis-graphics-common2D.md#color) \| number | Yes   | Color. When the type is common2D.Color, the value of each color channel is an integer in the range [0, 255]; when the type is number, the color is represented by an unsigned integer in hexadecimal ARGB format, with a value range of [0, 0xFFFFFFFF]. |
| mode   | [BlendMode](arkts-apis-graphics-drawing-e.md#blendmode)                              | Yes   | Blend mode, which specifies the color blending algorithm used when two shaders are overlaid. |

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns a color filter created based on the specified color and blend mode. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createBlendModeColorFilter(0xffff0000, drawing.BlendMode.SRC);
```

## createComposeColorFilter

static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter) : ColorFilter

Creates a **ColorFilter** object by combining another two color filters.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                       | Mandatory| Description                            |
| ------ | --------------------------- | ---- | -------------------------------- |
| outer  | [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Yes  | Color filter that takes effect later in the new filter.|
| inner  | [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Yes  | Color filter that takes effect first in the new filter.|

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns the created combined color filter. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let colorFilter1 = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.SRC);
let colorFilter2 = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.DST);
let colorFilter = drawing.ColorFilter.createComposeColorFilter(colorFilter1, colorFilter2);
```

## createLinearToSRGBGamma

static createLinearToSRGBGamma() : ColorFilter

Creates a **ColorFilter** object that applies the sRGB gamma curve to the RGB channels.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns the created color filter. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
```

## createSRGBGammaToLinear

static createSRGBGammaToLinear() : ColorFilter

Creates a **ColorFilter** object that applies the RGB channels to the sRGB gamma curve.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns the created color filter. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createSRGBGammaToLinear();
```

## createLumaColorFilter

static createLumaColorFilter() : ColorFilter

Creates a color filter that multiplies the luma of its input by the alpha channel value and sets the red, green, and blue channels to zero.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Color filter created. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createLumaColorFilter();
```

## createMatrixColorFilter<sup>12+</sup>

static createMatrixColorFilter(matrix: Array\<number>): ColorFilter

Creates a color filter that transforms colors through a 4x5 color matrix.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| matrix | Array\<number> | Yes | Array of length 20, representing a 4×5 matrix for color transformation. |

**Returns**

| Type                       | Description              |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns the created color filter. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let matrix: Array<number> = [
  1, 0, 0, 0, 0,
  0, 1, 0, 0, 0,
  0, 0, 100, 0, 0,
  0, 0, 0, 1, 0
];
let colorFilter = drawing.ColorFilter.createMatrixColorFilter(matrix);
```

## createLightingColorFilter<sup>20+</sup>

static createLightingColorFilter(mutColor: common2D.Color | number, addColor: common2D.Color | number): ColorFilter

Creates a lighting color filter that multiplies the RGB channel color values by the multiplication color (mutColor) and adds the addition color (addColor). The result is clamped to the range of 0 to 255.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| mutColor | [common2D.Color](js-apis-graphics-common2D.md#color) \| number | Yes | Color used for multiplication. When the value is of the common2D.Color type, the value of each color channel is an integer in the range [0, 255]. When the value is of the number type, it is represented by an unsigned integer in hexadecimal ARGB format, with a value range of [0, 0xFFFFFFFF]. |
| addColor | [common2D.Color](js-apis-graphics-common2D.md#color) \| number | Yes | Color used for addition. When the value is of the common2D.Color type, the value of each color channel is an integer in the range [0, 255]. When the value is of the number type, it is represented by an unsigned integer in hexadecimal ARGB format, with a value range of [0, 0xFFFFFFFF]. |

**Returns**

| Type                       | Description               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | Returns the created lighting color filter. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';
let mulColor : common2D.Color = { alpha: 0, red: 0, green: 0, blue: 20 };
let addColor : common2D.Color = { alpha: 0, red: 0, green: 0, blue: 125 };
let colorFilter = drawing.ColorFilter.createLightingColorFilter(mulColor, addColor);
```