# ColorFilter

```TypeScript
class ColorFilter
```

Defines a color filter.

> **NOTE:** 
> 
> - This module uses the physical pixel unit, px.
> 
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter
```

Creates a **ColorFilter** object with a given color and blend mode.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | Yes | Color in ARGB format. The value of each color channel is an integer ranging from 0 to 255. |
| mode | [BlendMode](arkts-arkgraphics2d-drawing-blendmode-e.md) | Yes | Blend mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let colorFilter = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.SRC);
```

<a id="createblendmodecolorfilter-2"></a>

## createBlendModeColorFilter

```TypeScript
static createBlendModeColorFilter(color: common2D.Color | number, mode: BlendMode): ColorFilter
```

Creates a **ColorFilter** object with a given color and blend mode.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) &#124; number | Yes | Color, represented by an unsigned integer in hexadecimal ARGB format. |
| mode | [BlendMode](arkts-arkgraphics2d-drawing-blendmode-e.md) | Yes | Blend mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createBlendModeColorFilter(0xffff0000, drawing.BlendMode.SRC);
```

## createComposeColorFilter

```TypeScript
static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter
```

Creates a **ColorFilter** object by combining another two color filters.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outer | [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Yes | Color filter that takes effect later in the new filter. |
| inner | [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Yes | Color filter that takes effect first in the new filter. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let colorFilter1 = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.SRC);
let colorFilter2 = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.DST);
let colorFilter = drawing.ColorFilter.createComposeColorFilter(colorFilter1, colorFilter2);
```

## createLightingColorFilter

```TypeScript
static createLightingColorFilter(mutColor: common2D.Color | number, addColor: common2D.Color | number): ColorFilter
```

Creates a lighting color filter. It multiplies the RGB channel values by one color and then adds another color value. The final output stays between 0 and 255.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mutColor | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) &#124; number | Yes | Color used for multiplication. The value is in the ARGB format, and each color channel is an integer ranging from 0 to 255. If the value is of the number type, it must be an unsigned integer in the hexadecimal ARGB format. |
| addColor | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) &#124; number | Yes | Color used for addition. The value is in the ARGB format, and each color channel is an integer ranging from 0 to 255. If the value is of the number type, it must be an unsigned integer in the hexadecimal ARGB format. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | **ColorFilter** object created. |

**Examples**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';
let mulColor : common2D.Color = { alpha: 0, red: 0, green: 0, blue: 20 };
let addColor : common2D.Color = { alpha: 0, red: 0, green: 0, blue: 125 };
let colorFilter = drawing.ColorFilter.createLightingColorFilter(mulColor, addColor);
```

## createLinearToSRGBGamma

```TypeScript
static createLinearToSRGBGamma(): ColorFilter
```

Creates a **ColorFilter** object that applies the sRGB gamma curve to the RGB channels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
```

## createLumaColorFilter

```TypeScript
static createLumaColorFilter(): ColorFilter
```

Creates a **ColorFilter** object that multiplies the luma into the alpha channel and sets the RGB channels to zero.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createLumaColorFilter();
```

## createMatrixColorFilter

```TypeScript
static createMatrixColorFilter(matrix: Array<number>): ColorFilter
```

Creates a color filter object with a 4*5 color matrix.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | Array&lt;number&gt; | Yes | An array of 20 numbers, indicating the 4*5 matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let matrix: Array<number> = [
  1, 0, 0, 0, 0,
  0, 1, 0, 0, 0,
  0, 0, 100, 0, 0,
  0, 0, 0, 1, 0
];
let colorFilter = drawing.ColorFilter.createMatrixColorFilter(matrix);
```

## createSRGBGammaToLinear

```TypeScript
static createSRGBGammaToLinear(): ColorFilter
```

Creates a **ColorFilter** object that applies the RGB channels to the sRGB gamma curve.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [ColorFilter](arkts-arkgraphics2d-drawing-colorfilter-c.md) | Color filter. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createSRGBGammaToLinear();
```
