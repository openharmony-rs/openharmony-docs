# Class (RecordCmdUtils)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8ce668ad94101a68cd0e3c33de2da76aa75a68f0 translatedAt=2026-10-21T03:06:11.552Z pushedAt=2026-10-21T09:33:07.087Z -->

A command recording utility object used to generate replayable record drawing commands. Obtain a recording-type canvas through [beginRecording](#beginrecording); the drawing interfaces called on that canvas are recorded as commands. After recording is complete, generate a [RecordCmd](arkts-apis-graphics-drawing-i.md#recordcmd) object through [finishRecording](#finishrecording), and then call [Canvas.drawRecordCmd](arkts-apis-graphics-drawing-Canvas.md#drawrecordcmd) to replay the recorded drawing commands.

> **NOTE**
>
> - Since version: 26.0.1.
>
> - This module uses the screen physical pixel unit px.
>
> - This module adopts a single-threaded model policy, and the caller is required to manage thread safety and context state switching.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## beginRecording

beginRecording(width: number, height: number): Canvas

Obtains the canvas object used to record drawing commands. After that, all drawing interfaces called on the returned canvas are recorded as drawing commands. The returned canvas object is valid only during recording. After recording ends, call [finishRecording](#finishrecording) to finish recording.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since:** 26.0.1

**Parameters**

| Name | Type   | Mandatory | Description                                                           |
| ------ | ------ | ---- | -------------------------------------------------------------- |
| width  | number | Yes   | Width of the recording canvas, in physical pixels (px). The value must be a positive integer within the int range. If a floating-point number is input, it is rounded down. |
| height | number | Yes   | Height of the recording canvas, in physical pixels (px). The value must be a positive integer within the int range. If a floating-point number is input, it is rounded down. |

**Return value**

| Type           | Description            |
| -------------- | -------------- |
| [Canvas](arkts-apis-graphics-drawing-Canvas.md) | Returns the canvas object used to record drawing commands. All drawing interfaces called on this canvas are recorded as drawing commands. |

**Error codes**

For details about the following error code, see [Drawing and Display Error Codes](errorcode-drawing.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 25900001 | Parameter error. Possible causes: Incorrect parameter range. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const recordCmdUtils = new drawing.RecordCmdUtils();
    const recordCanvas = recordCmdUtils.beginRecording(200, 200);
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({ alpha: 255, red: 255, green: 0, blue: 0 });
    recordCanvas.attachPen(pen);
    recordCanvas.drawRect({ left : 0, right : 100, top : 0, bottom : 100 });
    recordCanvas.detachPen();
    const recordCmd = recordCmdUtils.finishRecording();
    canvas.drawRecordCmd(recordCmd);
  }
}
```

## finishRecording

finishRecording(): RecordCmd

Ends recording and returns the recorded drawing command object [RecordCmd](arkts-apis-graphics-drawing-i.md#recordcmd). Before calling this API, you need to call [beginRecording](#beginrecording) to start recording. All drawing commands recorded on the canvas during recording are encapsulated into the returned RecordCmd object.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since:** 26.0.1

**Return value**

| Type                                            | Description                                       |
| ----------------------------------------------- | ------------------------------------------ |
| [RecordCmd](arkts-apis-graphics-drawing-i.md#recordcmd) | Returns the recorded drawing command object, which can be used to replay drawing commands through [Canvas.drawRecordCmd](arkts-apis-graphics-drawing-Canvas.md#drawrecordcmd). |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const recordCmdUtils = new drawing.RecordCmdUtils();
    const recordCanvas = recordCmdUtils.beginRecording(200, 200);
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({ alpha: 255, red: 255, green: 0, blue: 0 });
    recordCanvas.attachPen(pen);
    recordCanvas.drawRect({ left : 0, right : 100, top : 0, bottom : 100 });
    recordCanvas.detachPen();
    const recordCmd = recordCmdUtils.finishRecording();
    canvas.drawRecordCmd(recordCmd);
  }
}
```

## getHeight

getHeight(): number

Obtains the height of the recording canvas.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since:** 26.0.1

**Return value**

| Type | Description |
| ---- | ----------------------------------------------------- |
| number | Returns the height of the recording canvas, in physical pixels (px). It is the same as the height value passed in through [beginRecording](#beginrecording) when recording starts. |

**Example**

```ts
const recordCmdUtils = new drawing.RecordCmdUtils();
recordCmdUtils.beginRecording(200, 100);
let height = recordCmdUtils.getHeight();
recordCmdUtils.finishRecording();
```

## getWidth

getWidth(): number

Obtains the width of the recording canvas.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since:** 26.0.1

**Return value**

| Type | Description                                                  |
| ---- | ----------------------------------------------------- |
| number  | Returns the width of the recording canvas, in physical pixels (px), which is the same as the width value passed in through [beginRecording](#beginrecording) when recording starts. |

**Example**

```ts
const recordCmdUtils = new drawing.RecordCmdUtils();
recordCmdUtils.beginRecording(200, 100);
let width = recordCmdUtils.getWidth();
recordCmdUtils.finishRecording();
```
<!--no_check-->