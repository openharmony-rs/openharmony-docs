# ShadowLayer

```TypeScript
class ShadowLayer
```

Implements a shadow layer.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - This module uses the physical pixel unit, px.
> 
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## create

```TypeScript
static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer
```

Creates a **ShadowLayer** object.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurRadius | number | Yes | Radius of the shadow layer. The value must be a floating point number greater than 0. |
| x | number | Yes | Offset on the X axis. The value is a floating point number. |
| y | number | Yes | Offset on the Y axis. The value is a floating point number. |
| color | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | Yes | Color in ARGB format. The value of each color channel is an integer ranging from 0 to 255. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | **ShadowLayer** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
  }
}
```

<a id="create-2"></a>

## create

```TypeScript
static create(blurRadius: number, x: number, y: number, color: common2D.Color | number): ShadowLayer
```

Creates a **ShadowLayer** object.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurRadius | number | Yes | Radius of the shadow layer. The value must be a floating point number greater than 0. |
| x | number | Yes | Offset on the X axis. The value is a floating point number. |
| y | number | Yes | Offset on the Y axis. The value is a floating point number. |
| color | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) &#124; number | Yes | Color, represented by an unsigned integer in hexadecimal ARGB format. |

**Return value:**

| Type | Description |
| --- | --- |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | **ShadowLayer** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, 0xff00ff00);
  }
}
```
