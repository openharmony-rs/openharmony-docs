# Class (MaskFilter)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9d24e15ef82b33c8322a412e3fad5e8314ad7c4e translatedAt=2026-08-24T07:59:07.853Z pushedAt=2026-08-25T06:53:58.048Z -->

Mask filter object, used to apply a blur effect to the drawn content.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - This module uses the physical pixel unit, px.
>
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## createBlurMaskFilter<sup>12+</sup>

static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter

Creates a mask filter with a blur effect.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type                  | Mandatory| Description                                |
| ---------- | --------------------- | ---- | ----------------------------------- |
| blurType   | [BlurType](arkts-apis-graphics-drawing-e.md#blurtype12) | Yes   | Blur type, which specifies the blur operation mode of the mask filter.                           |
| sigma      | number                | Yes   | Standard deviation of the Gaussian blur. It must be a floating point number greater than 0, in physical pixels (px). |

**Returns**

| Type                     | Description               |
| ------------------------- | ------------------ |
| [MaskFilter](arkts-apis-graphics-drawing-MaskFilter.md) | **Maskfilter** object created.|

**Error codes** 

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md). 

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10);
  }
}
```