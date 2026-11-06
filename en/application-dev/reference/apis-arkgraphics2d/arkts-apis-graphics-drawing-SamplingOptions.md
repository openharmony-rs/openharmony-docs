# Class (SamplingOptions)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=960a46736a988e57d30a506752d1dcf0426ef09d translatedAt=2026-08-24T08:13:20.191Z pushedAt=2026-08-29T07:02:53.664Z -->

Sampling options object, used to configure the filter mode for image sampling and control the pixel sampling method during image scaling or transformation. A typical use case is to determine the sampling quality and rendering effect of an image with different filter modes when drawing the image on a canvas (for example, drawImage).

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

## constructor<sup>12+</sup>

constructor()

Creates a **SamplingOptions** object, where the default value of [FilterMode](arkts-apis-graphics-drawing-e.md#filtermode12) is **FILTER_MODE_NEAREST**.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let samplingOptions = new drawing.SamplingOptions();
  }
}
```

## constructor<sup>12+</sup>

constructor(filterMode: FilterMode)

Constructs a new sampling options object. You can specify the filterMode parameter to adapt to different image sampling scenarios.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type                  | Mandatory| Description                                |
| ---------- | --------------------- | ---- | ----------------------------------- |
| filterMode | [FilterMode](arkts-apis-graphics-drawing-e.md#filtermode12)    | Yes   | Filter mode, which specifies the filtering algorithm used for image sampling.                    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let samplingOptions = new drawing.SamplingOptions(drawing.FilterMode.FILTER_MODE_NEAREST);
  }
}
```