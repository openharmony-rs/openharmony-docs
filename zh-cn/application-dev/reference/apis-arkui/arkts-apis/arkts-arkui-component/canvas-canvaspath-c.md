# CanvasPath

Path object, which provides basic methods for drawing paths.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class CanvasPath--><!--Device-unnamed-export declare class CanvasPath-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arc

```TypeScript
arc(x: double, y: double, radius: double, startAngle: double, endAngle: double, counterclockwise?: boolean): void
```

Draw an arc path

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-arc(x: double, y: double, radius: double, startAngle: double, endAngle: double, counterclockwise?: boolean): void--><!--Device-CanvasPath-arc(x: double, y: double, radius: double, startAngle: double, endAngle: double, counterclockwise?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | The x-axis coordinate of the center (center of the circle) of the arc. |
| y | double | 是 | The y-axis coordinate of the center (center of the circle) of the arc. |
| radius | double | 是 | Radius of the arc. |
| startAngle | double | 是 | Start point of an arc, which starts to be calculated in the x-axis direction.The unit is radian. |
| endAngle | double | 是 | The end point of the arc, in radians. |
| counterclockwise | boolean | 否 | If the value is true, the arc is drawn counterclockwise. Otherwise,the arc is drawn clockwise. The default value is false. |

## arcTo

```TypeScript
arcTo(x1: double, y1: double, x2: double, y2: double, radius: double): void
```

Draw arc paths based on control points and radius

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-arcTo(x1: double, y1: double, x2: double, y2: double, radius: double): void--><!--Device-CanvasPath-arcTo(x1: double, y1: double, x2: double, y2: double, radius: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x1 | double | 是 | The x-axis coordinate of the first control point. |
| y1 | double | 是 | The y-axis coordinate of the first control point. |
| x2 | double | 是 | The x-axis coordinate of the second control point. |
| y2 | double | 是 | The y-axis coordinate of the second control point. |
| radius | double | 是 | Radius of the arc. |

## bezierCurveTo

```TypeScript
bezierCurveTo(cp1x: double, cp1y: double, cp2x: double, cp2y: double, x: double, y: double): void
```

Drawing Cubic Bessel Curve Paths

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-bezierCurveTo(cp1x: double, cp1y: double, cp2x: double, cp2y: double, x: double, y: double): void--><!--Device-CanvasPath-bezierCurveTo(cp1x: double, cp1y: double, cp2x: double, cp2y: double, x: double, y: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cp1x | double | 是 | The x-axis coordinate of the first control point. |
| cp1y | double | 是 | The y-axis coordinate of the first control point. |
| cp2x | double | 是 | The x-axis coordinate of the second control point. |
| cp2y | double | 是 | The y-axis coordinate of the second control point. |
| x | double | 是 | x-axis coordinate of the end point. |
| y | double | 是 | y-axis coordinate of the end point. |

## closePath

```TypeScript
closePath(): void
```

Returns the pen point to the start point of the current sub-path

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-closePath(): void--><!--Device-CanvasPath-closePath(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ellipse

```TypeScript
ellipse(x: double, y: double, radiusX: double, radiusY: double, rotation: double, startAngle: double,
    endAngle: double, counterclockwise?: boolean): void
```

Draw an Elliptic Path

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-ellipse(x: double, y: double, radiusX: double, radiusY: double, rotation: double, startAngle: double,    endAngle: double, counterclockwise?: boolean): void--><!--Device-CanvasPath-ellipse(x: double, y: double, radiusX: double, radiusY: double, rotation: double, startAngle: double,    endAngle: double, counterclockwise?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | x-axis coordinate of the center of the ellipse. |
| y | double | 是 | y-axis coordinate of the center of the ellipse. |
| radiusX | double | 是 | Radius of the major axis of the ellipse. |
| radiusY | double | 是 | Radius of the minor axis of the ellipse. |
| rotation | double | 是 | The rotation angle of the ellipse, in radians (not angular degrees). |
| startAngle | double | 是 | The angle of the starting point to be drawn, measured from the x-axis in radians(not angular degrees). |
| endAngle | double | 是 | The angle, in radians, at which the ellipse is to be drawn (not angular degrees). |
| counterclockwise | boolean | 否 | If the value is true, the ellipse is drawn counterclockwise. Otherwise,the ellipse is drawn clockwise. The default value is false. |

## lineTo

```TypeScript
lineTo(x: double, y: double): void
```

Connect sub-path using straight lines

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-lineTo(x: double, y: double): void--><!--Device-CanvasPath-lineTo(x: double, y: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | The x-axis coordinate of the end point of the line. |
| y | double | 是 | The y-axis coordinate of the end point of the line. |

## moveTo

```TypeScript
moveTo(x: double, y: double): void
```

Moves the start point of a new sub-path to the (x, y) coordinate.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-moveTo(x: double, y: double): void--><!--Device-CanvasPath-moveTo(x: double, y: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | The x-axis coordinate of the point. |
| y | double | 是 | The y-axis coordinate of the point. |

## quadraticCurveTo

```TypeScript
quadraticCurveTo(cpx: double, cpy: double, x: double, y: double): void
```

Draw quadratic Bezier curve paths

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-quadraticCurveTo(cpx: double, cpy: double, x: double, y: double): void--><!--Device-CanvasPath-quadraticCurveTo(cpx: double, cpy: double, x: double, y: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cpx | double | 是 | The x-axis coordinate of the control point. |
| cpy | double | 是 | The y-axis coordinate of the control point. |
| x | double | 是 | x-axis coordinate of the end point. |
| y | double | 是 | y-axis coordinate of the end point. |

## rect

```TypeScript
rect(x: double, y: double, w: double, h: double): void
```

Draw Rectangular Paths

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-rect(x: double, y: double, w: double, h: double): void--><!--Device-CanvasPath-rect(x: double, y: double, w: double, h: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | The x-axis coordinate of the start point of the rectangle. |
| y | double | 是 | The y-axis coordinate of the start point of the rectangle. |
| w | double | 是 | Width of the rectangle. |
| h | double | 是 | Height of the rectangle. |

## roundRect

```TypeScript
roundRect(x: double, y: double, w: double, h: double, radii?: double | Array<double>): void
```

Draw rounded Rectangular Paths

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPath-roundRect(x: double, y: double, w: double, h: double, radii?: double | Array<double>): void--><!--Device-CanvasPath-roundRect(x: double, y: double, w: double, h: double, radii?: double | Array<double>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | The x-axis coordinate of the start point of the rectangle. |
| y | double | 是 | The y-axis coordinate of the start point of the rectangle. |
| w | double | 是 | Width of the rectangle. |
| h | double | 是 | Height of the rectangle. |
| radii | double \| Array&lt;double&gt; | 否 | A number or list specifying the radii of the circular arc to be used for the corners of the rectangle. The default value is 0. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103701](../../errorcode-canvas.md#103701-参数错误) | Parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 1. The param radii is a list that has zero or more than four elements.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. The param radii contains negative value. |

