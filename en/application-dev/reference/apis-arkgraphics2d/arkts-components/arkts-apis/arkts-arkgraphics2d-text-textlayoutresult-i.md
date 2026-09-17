# TextLayoutResult

Represents the text layout result.

**Since:** 24

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## correctRect

```TypeScript
correctRect: TextRectSize
```

Rectangle size of the paragraph after layout.

**Type:** [TextRectSize](arkts-arkgraphics2d-text-textrectsize-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

## fitStrRange

```TypeScript
fitStrRange: Array<Range>
```

Array of character ranges that can be completely displayed after text layout calculation.

**Type:** Array&lt;[Range](arkts-arkgraphics2d-text-range-i.md)&gt;

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing
