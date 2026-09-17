# CanvasPath

Path object, which provides basic methods for drawing paths. For details about the path-related APIs, see the description in **CanvasRenderingContext2D**.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arc

```TypeScript
arc(x: number, y: number, radius: number, startAngle: number, endAngle: number, counterclockwise?: boolean): void
```

Draws an arc on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the center point of the arc.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the center point of the arc.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| radius | number | Yes | Radius of the arc.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| startAngle | number | Yes | Start radian of the arc.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Unit: radian |
| endAngle | number | Yes | End radian of the arc.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Unit: radian |
| counterclockwise | boolean | No | Whether to draw the arc counterclockwise.<br>**true**: Draw the arc counterclockwise.<br>**false**: Draw the arc clockwise.<br>The default value is **false**. If this parameter is set to **null** or **undefined**, the default value is used. |

## arcTo

```TypeScript
arcTo(x1: number, y1: number, x2: number, y2: number, radius: number): void
```

Creates a circular arc using the given control points and radius.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x1 | number | Yes | X-coordinate of the first control point.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y1 | number | Yes | Y-coordinate of the first control point.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| x2 | number | Yes | X-coordinate of the second control point.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y2 | number | Yes | Y-coordinate of the second control point.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| radius | number | Yes | Radius of the arc.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## bezierCurveTo

```TypeScript
bezierCurveTo(cp1x: number, cp1y: number, cp2x: number, cp2y: number, x: number, y: number): void
```

Draws a cubic Bezier curve on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cp1x | number | Yes | X-coordinate of the first parameter of the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| cp1y | number | Yes | Y-coordinate of the first parameter of the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| cp2x | number | Yes | X-coordinate of the second parameter of the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| cp2y | number | Yes | Y-coordinate of the second parameter of the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| x | number | Yes | X-coordinate of the end point on the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the end point on the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## closePath

```TypeScript
closePath(): void
```

Moves the current point of the path back to the start point of the path, and draws a straight line between the current point and the start point. If the shape has already been closed or has only one point, this method does nothing.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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
    counterclockwise?: boolean,
  ): void
```

Draws an ellipse in the specified rectangular region on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the ellipse center.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the ellipse center.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| radiusX | number | Yes | Radius of the ellipse on the x-axis.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| radiusY | number | Yes | Radius of the ellipse on the y-axis.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| rotation | number | Yes | Rotation angle of the ellipse.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Unit: radian |
| startAngle | number | Yes | Angle of the start point for drawing the ellipse.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Unit: radian |
| endAngle | number | Yes | Angle of the end point for drawing the ellipse.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Unit: radian |
| counterclockwise | boolean | No | Whether to draw the ellipse counterclockwise.<br>**true**: Draw the ellipse counterclockwise.<br>**false**: Draw the ellipse clockwise.<br>The default value is **false**. If this parameter is set to **null** or **undefined**, the default value is used. |

## lineTo

```TypeScript
lineTo(x: number, y: number): void
```

Connects the current point to a target position using a line.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the target position.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the target position.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## moveTo

```TypeScript
moveTo(x: number, y: number): void
```

Moves a drawing path from the current position to a target position on the canvas.  
> **NOTE:** 
> 
> In versions earlier than API version 18, if the **moveTo** API is not called or invalid arguments
> are passed to it, the path starts from (0,0).
> 
> Starting from API version 18, if the **moveTo** API is not executed or invalid arguments are passed
> to it, the path will begin at the start point of the first valid call to **lineTo**, **arcTo**,
> **bezierCurveTo**, or **quadraticCurveTo**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the target position.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the target position.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## quadraticCurveTo

```TypeScript
quadraticCurveTo(cpx: number, cpy: number, x: number, y: number): void
```

Creates a path for a quadratic Bezier curve.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cpx | number | Yes | X-coordinate of the Bezier curve parameter.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| cpy | number | Yes | Y-coordinate of the Bezier curve parameter.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| x | number | Yes | X-coordinate of the end point on the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the end point on the Bezier curve.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## rect

```TypeScript
rect(x: number, y: number, w: number, h: number): void
```

Creates a rectangle on the canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the rectangle's top-left corner.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the rectangle's top-left corner.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| w | number | Yes | Width of the rectangle.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |
| h | number | Yes | Height of the rectangle.<br>In versions earlier than API version 18, **NaN** or **Infinity** value prevents the entire path from rendering, and **null** or **undefined** value causes the current API to have no effect. Since API version 18, **NaN**, **Infinity**, **null**, or **undefined** causes the current API to have no effect, and other path APIs with valid arguments continue to render correctly.<br>Default unit: vp |

## roundRect

```TypeScript
roundRect(x: number, y: number, w: number, h: number, radii?: number | Array<number>): void
```

Creates a rounded rectangle path. This API does not directly render content. To draw the rounded rectangle on the canvas, use **fill** or **stroke**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate of the rectangle's top-left corner.<br>The value **null** is treated as **0**, and **undefined** is treated as an invalid value, indicating no rendering.<br> To draw a complete rectangle, the value range is [0, Canvas width).<br>Default unit: vp |
| y | number | Yes | Y-coordinate of the rectangle's top-left corner.<br>The value **null** is treated as **0**, and **undefined** is treated as an invalid value, indicating no rendering.<br>To draw a complete rectangle, the value range is [0, Canvas height).<br>Default unit: vp |
| w | number | Yes | Width of the rectangle. A negative value indicates that the rectangle is drawn from right to left.<br>The value **null** is treated as **0**, and **undefined** is treated as an invalid value, indicating no rendering.<br>To draw a complete rectangle, the value range is [-x, Canvas width - x].<br>Default unit: vp |
| h | number | Yes | Height of the rectangle. A negative value indicates upward drawing.<br>The value **null** is treated as **0**, and **undefined** is treated as an invalid value, indicating no rendering.<br>To draw a complete rectangle, the value range is [-y, Canvas height - y].<br> Default unit: vp |
| radii | number &#124; Array&lt;number&gt; | No | Number or list of arc radii used for the rectangle corners.<br>If the parameter type is number, it applies to the arc radius of all rectangle corners. <br>If the parameter type is Array&lt;number&gt;, the array contains 1 to 4 numbers, interpreted as follows:<br>[Arc radius of all rectangle corners]<br>[Arc radius of the top-left and bottom-right rectangle corners, and arc radius of the top-right and bottom-left rectangle corners]<br>[Arc radius of the top-left rectangle corner, arc radius of the top-right and bottom-left rectangle corners, and arc radius of the bottom-right rectangle corner]<br>[Arc radius of the top-left rectangle corner, arc radius of the top-right rectangle corner, arc radius of the bottom-right rectangle corner, and arc radius of the bottom-left rectangle corner]<br>If **radii** contains a negative number or the number of items in the list is not within [1,4], error code 103701 is reported.<br>Default value: **0**. **null** and **undefined** are treated as the default value.<br>If the arc radius exceeds the width and height of the rectangle, it will be proportionally scaled down to match the corresponding dimensions.<br>Default unit: vp |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [103701](../errorcode-canvas.md#103701-parameter-error) | Parameter error. Possible causes:<br> 1. The param radii is a list that has zero or more than four elements. <br> 2. The param radii contains negative value. |
