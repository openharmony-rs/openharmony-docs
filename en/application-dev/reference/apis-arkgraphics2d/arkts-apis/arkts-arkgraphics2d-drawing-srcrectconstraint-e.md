# SrcRectConstraint

```TypeScript
enum SrcRectConstraint
```

Enumerates the constraints on the source rectangle. It is used to specify whether to limit the sampling range within the source rectangle when drawing an image on a canvas.

**Since:** 12

<!--Device-drawing-enum SrcRectConstraint--><!--Device-drawing-enum SrcRectConstraint-End-->

**System capability:** SystemCapability.Graphics.Drawing

## FAST

```TypeScript
FAST = 1
```

The sampling range is not limited to the source rectangle and can extend beyond it, allowing for a high sampling speed.

**Since:** 12

<!--Device-SrcRectConstraint-FAST = 1--><!--Device-SrcRectConstraint-FAST = 1-End-->

**System capability:** SystemCapability.Graphics.Drawing

## STRICT

```TypeScript
STRICT = 0
```

The sampling range is strictly confined to the source rectangle, resulting in a slow sampling speed.

**Since:** 12

<!--Device-SrcRectConstraint-STRICT = 0--><!--Device-SrcRectConstraint-STRICT = 0-End-->

**System capability:** SystemCapability.Graphics.Drawing
