# Path2D

Path2D

@interface Path2D

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addPath

```TypeScript
addPath(path: Path2D): void
```

Add another path to current path.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-viewmodel-path2d-i.md) | Yes | another created Path2D object. |

## arc

```TypeScript
arc(x: number, y: number, radius: number, startAngle: number, endAngle: number, counterclockwise?: boolean): void
```

Draws an arc on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the center point of the arc. |
| y | number | Yes | Y-coordinate of the center point of the arc. |
| radius | number | Yes | Radius of the arc. |
| startAngle | number | Yes | Start radian of the arc. |
| endAngle | number | Yes | End radian of the arc. |
| counterclockwise | boolean | No | Whether to draw the arc counterclockwise. |

## arcTo

```TypeScript
arcTo(x1: number, y1: number, x2: number, y2: number, radius: number): void
```

Draws an arc based on the radius and points on the arc.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x1 | number | Yes | X-coordinate of the first point on the arc. |
| y1 | number | Yes | Y-coordinate of the first point on the arc. |
| x2 | number | Yes | X-coordinate of the second point on the arc. |
| y2 | number | Yes | Y-coordinate of the second point on the arc. |
| radius | number | Yes | Radius of the arc. |

## bezierCurveTo

```TypeScript
bezierCurveTo(cp1x: number, cp1y: number, cp2x: number, cp2y: number, x: number, y: number): void
```

Draws a cubic bezier curve on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cp1x | number | Yes | X-coordinate of the first parameter of the bezier curve. |
| cp1y | number | Yes | Y-coordinate of the first parameter of the bezier curve. |
| cp2x | number | Yes | X-coordinate of the second parameter of the bezier curve. |
| cp2y | number | Yes | Y-coordinate of the second parameter of the bezier curve. |
| x | number | Yes | End point x-coordinate of the bezier curve. |
| y | number | Yes | End point y-coordinate of the bezier curve. |

## closePath

```TypeScript
closePath(): void
```

Draws a closed path.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ellipse

```TypeScript
ellipse(
    x: number,
    y: number,
    radiusX: number,
    radiusY: number,
    rotation: number,
    startAngle: number,
    endAngle: number,
    counterclockwise?: number,
  ): void
```

Draws an ellipse based on the coordinate and radius.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the center point on the ellipse. |
| y | number | Yes | Y-coordinate of the center point on the ellipse. |
| radiusX | number | Yes | X-coordinate of the radius Length on the ellipse. |
| radiusY | number | Yes | Y-coordinate of the radius Length on the ellipse. |
| rotation | number | Yes | The rotation angle of the ellipse, in radians. |
| startAngle | number | Yes | Angle of the start point for ellipse drawing. |
| endAngle | number | Yes | End Point Angle for Ellipse Drawing. |
| counterclockwise | number | No | Indicates whether to draw an ellipse counterclockwise. 0: clockwise; 1: counterclockwise. The default value is 0. |

## lineTo

```TypeScript
lineTo(x: number, y: number): void
```

Connects the current point to a target position using a straight line.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the target position. |
| y | number | Yes | Y-coordinate of the target position. |

## moveTo

```TypeScript
moveTo(x: number, y: number): void
```

Moves a drawing path to a target position on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the target position. |
| y | number | Yes | Y-coordinate of the target position. |

## quadraticCurveTo

```TypeScript
quadraticCurveTo(cpx: number, cpy: number, x: number, y: number): void
```

Draws a quadratic curve on the canvas.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cpx | number | Yes | X-coordinate of the bezier curve parameter. |
| cpy | number | Yes | Y-coordinate of the bezier curve parameter. |
| x | number | Yes | End point x-coordinate of the bezier curve. |
| y | number | Yes | End point y-coordinate of the bezier curve. |

## rect

```TypeScript
rect(x: number, y: number, width: number, height: number): void
```

Creates a rectangular.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the upper left corner of the rectangle. |
| y | number | Yes | Y-coordinate of the upper left corner of the rectangle. |
| width | number | Yes | Width of the rectangle. |
| height | number | Yes | Height of the rectangle. |

## setTransform

```TypeScript
setTransform(
    scaleX: number,
    skewX: number,
    skewY: number,
    scaleY: number,
    translateX: number,
    translateY: number,
  ): void
```

Uses same parameters as the transform() function to reset the existing transformation matrix and create a new transformation matrix.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scaleX | number | Yes | X-axis scale. |
| skewX | number | Yes | X-axis skew. |
| skewY | number | Yes | Y-axis skew. |
| scaleY | number | Yes | Y-axis scale. |
| translateX | number | Yes | X-axis translation. |
| translateY | number | Yes | Y-axis translation. |
