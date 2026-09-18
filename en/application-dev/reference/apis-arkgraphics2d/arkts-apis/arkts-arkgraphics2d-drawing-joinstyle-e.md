# JoinStyle

Enumerates the join styles of a pen. The join style defines the shape of the joints of a polyline segment drawn by the pen.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## MITER_JOIN

```TypeScript
MITER_JOIN = 0
```

Mitered corner. If the angle of a polyline is small, its miter length may be inappropriate. In this case, you need to use the miter limit to limit the miter length.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## ROUND_JOIN

```TypeScript
ROUND_JOIN = 1
```

Round corner.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## BEVEL_JOIN

```TypeScript
BEVEL_JOIN = 2
```

Beveled corner.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing
