# CanvasLineCap

```TypeScript
declare type CanvasLineCap = "butt" | "round" | "square"
```

Specifies the attribute of drawing the end of each line segment.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| "butt" | The ends of the line are squared off, and the line does not extend beyond its two endpoints. |
| "round" | The line is extended at the endpoints by a half circle whose diameter is equal to the line width. |
| "square" | The line is extended at the endpoints by a rectangle whose width is equal to half the line width and height equal to the line width. |
