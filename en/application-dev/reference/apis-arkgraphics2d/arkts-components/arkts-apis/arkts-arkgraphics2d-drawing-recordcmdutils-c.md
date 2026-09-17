# RecordCmdUtils

This class offers a set of operations to generate drawing commands.

**Since:** 26.1.0

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## beginRecording

```TypeScript
beginRecording(width: number, height: number): Canvas
```

Gets the canvas that records the drawing commands.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Indicates the width of the canvas object.<br>Unit: px. <br>Value range: An integer greater than 0. <br>The width value must be greater than 0. |
| height | number | Yes | Indicates the height of the canvas object.<br>Unit: px. <br>Value range: An integer greater than 0. <br>The height value must be greater than 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [Canvas](arkts-arkgraphics2d-drawing-canvas-c.md) | Returns the canvas that records the drawing commands. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-abnormal-parameter-value) | Parameter error. Possible causes: Incorrect parameter range. |

## finishRecording

```TypeScript
finishRecording(): RecordCmd
```

Finishes recording and returns the recorded command object.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [RecordCmd](arkts-arkgraphics2d-drawing-recordcmd-i.md) | Returns the recorded drawing commands. |

## getHeight

```TypeScript
getHeight(): number
```

Gets the height of the recording canvas.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the height of recording canvas. |

## getWidth

```TypeScript
getWidth(): number
```

Gets the width of the recording canvas.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the width of recording canvas. |
