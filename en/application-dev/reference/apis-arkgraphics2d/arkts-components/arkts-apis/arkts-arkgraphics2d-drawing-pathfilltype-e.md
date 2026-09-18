# PathFillType

Enumerates the fill types of a path.

> **NOTE:** 

> ![image_PathFillType_Winding_Even_Odd.png](../../../reference/apis-arkgraphics2d/figures/zh-ch_image_PathFillType_Winding_Even_Odd.png)

> As shown in the above figure, the path is a circle, the arrow indicates the path direction, **p** is any point "
> inside" the path, the blue line is the ray emitted from **p**, and the black arrow indicates the fill result
> using blue under the corresponding fill type. Under the **WINDING** fill rule, the number of intersection points
> of the ray and path is 2 (not 0), and therefore **p** is colored. Under the **EVEN_ODD** filling rule, the number
> of intersection points of the ray and path is 2 (an even number), and therefore **p** is not colored.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## WINDING

```TypeScript
WINDING = 0
```

Specifies that "inside" is computed by a non-zero sum of signed edge crossings. Specifically, draws a point and emits a ray in any direction. A count is used to record the number of intersection points of the ray and path, and the initial count is 0. When encountering a clockwise intersection point (the path passes from the left to the right of the ray), the count increases by 1. When encountering a counterclockwise intersection point (the path passes from the right to the left of the ray), the count decreases by 1. If the final count is not 0, the point is inside the path and needs to be colored. If the final count is 0, the point is not colored.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## EVEN_ODD

```TypeScript
EVEN_ODD = 1
```

Specifies that "inside" is computed by an odd number of edge crossings. Specifically, draws a point and emits a ray in any direction. If the number of intersection points of the ray and path is an odd number, the point is considered to be inside the path and needs to be colored. If the number is an even number, the point is not colored.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## INVERSE_WINDING

```TypeScript
INVERSE_WINDING = 2
```

Same as **WINDING**, but draws outside of the path, rather than inside.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## INVERSE_EVEN_ODD

```TypeScript
INVERSE_EVEN_ODD = 3
```

Same as **EVEN_ODD**, but draws outside of the path, rather than inside.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing
