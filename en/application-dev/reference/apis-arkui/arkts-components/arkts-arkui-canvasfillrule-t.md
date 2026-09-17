# CanvasFillRule

```TypeScript
declare type CanvasFillRule = "evenodd" | "nonzero"
```

Defines the fill pattern algorithm used to determine whether a point is inside or outside a path. The value type is a union of the types listed in the table below.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| "evenodd" | The inside part of a shape is determined based on whether the counting result is an odd number or not. This rule determines whether a point is inside a shape by casting a ray from the point on the canvas in any direction and counting the number of intersections between the ray and the shape path. If the number of intersections is odd, the point is inside the shape. Otherwise, the point is outside the shape. |
| "nonzero" | The inside part of a shape is determined based on whether the counting result is zero or not. This rule determines whether a point is inside a shape by casting a ray from the point on the canvas in any direction and checking the intersections between the ray and the shape path. The initial count is **0**: assign a direction value to each segment of the path, add 1 each time the path crosses the ray from left to right, and subtract 1 each time it crosses the ray from right to left. If the final result is **0**, the point is outside the shape. Otherwise, the point is inside the shape. |
