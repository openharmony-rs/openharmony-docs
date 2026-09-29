# ClipOp

```TypeScript
enum ClipOp
```

Enumerates the canvas clipping modes.

> **NOTE:** 
> 
> The diagrams show the result of cropping a circle based on different enumerated values after a rectangle is
> cropped in INTERSECT mode. The green area is the final area obtained.

**Since:** 12

<!--Device-drawing-enum ClipOp--><!--Device-drawing-enum ClipOp-End-->

**System capability:** SystemCapability.Graphics.Drawing

## DIFFERENCE

```TypeScript
DIFFERENCE = 0
```

Clips a specified area. That is, the difference set is obtained.

**Since:** 12

<!--Device-ClipOp-DIFFERENCE = 0--><!--Device-ClipOp-DIFFERENCE = 0-End-->

**System capability:** SystemCapability.Graphics.Drawing

## INTERSECT

```TypeScript
INTERSECT = 1
```

Retains a specified area. That is, the intersection is obtained.

**Since:** 12

<!--Device-ClipOp-INTERSECT = 1--><!--Device-ClipOp-INTERSECT = 1-End-->

**System capability:** SystemCapability.Graphics.Drawing
