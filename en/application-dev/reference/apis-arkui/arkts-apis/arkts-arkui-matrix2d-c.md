# Matrix2D

```TypeScript
declare class Matrix2D
```

A matrix object used for graphic transformation in CanvasRenderingContext2D, OffscreenCanvasRenderingContext2D, CanvasPattern, and Path2D. It can perform scaling, rotation, translation, and other transformations on the matrix.

**Matrix2D** is used in the following scenarios:

1. In CanvasRenderingContext2D and
OffscreenCanvasRenderingContext2D, call [getTransform](../arkts-components/arkts-arkui-canvas-comp-canvasrenderer-c.md#gettransform) to obtain the canvas graphic transformation **Matrix2D** object, and call setTransform to apply the graphic transformation corresponding to the **Matrix2D** object to subsequent drawing content.
2. In CanvasPattern, call
setTransform to apply the graphic transformation corresponding to the **Matrix2D** object to the CanvasPattern object.
3. In Path2D, call
addPath to apply the graphic transformation corresponding to the **Matrix2D** object to the Path2D object.

> **NOTE:** 
> 
> You can use the [px2vp](arkts-arkui-arkui-uicontext-uicontext-c.md#px2vp) API for unit
> conversion.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

Constructs a two-dimensional transformation matrix object. The default value is a matrix whose attributes are all 0.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

Constructs a two-dimensional transformation matrix object. The default value is a matrix whose attributes are all
0. The unit mode of the Matrix2D object can be configured.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unit | [LengthMetricsUnit](arkts-arkui-lengthmetricsunit-t.md) | Yes | Unit mode of the **Matrix2D** object. The configuration cannot be dynamically changed after being set. The configuration method is the same as that of CanvasRenderingContext2D.<br>Default value: **DEFAULT** <br>If the invalid values **NaN** and **Infinity** are passed in, the default value is used. |

## identity

```TypeScript
identity(): Matrix2D
```

Creates an identity matrix. It is commonly used to reset the transformation matrix, clearing all previous transformation operations so that subsequent drawing content is not affected by previous transformations.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Identity matrix, which can be used to initialize or reset the graphics transformation state. |

## invert

```TypeScript
invert(): Matrix2D
```

Obtains the inverse of the current matrix. It is commonly used to undo previous transformation operations or calculate reverse transformations, enabling reverse mapping of the coordinate system.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Inverse matrix result, which can be used for reverse transformation or to undo previous transformation operations. |

## multiply

```TypeScript
multiply(other?: Matrix2D): Matrix2D
```

Multiplies the current matrix by the target matrix. This API is an empty API and has no actual effect.

This API is deprecated since API version 10 and has no actual drawing effect, so no example is provided.

**Since:** 8

**Deprecated since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [Matrix2D](arkts-arkui-matrix2d-c.md) | No | Target matrix.<br>Invalid values **undefined** and **null** are treated as invalid inputs. <br>Default value: **null**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | This API is an empty implementation, and its return value has no practical meaning. |

## rotate

```TypeScript
rotate(rx?: number, ry?: number): Matrix2D
```

Performs a rotation operation on the current matrix. This API is an empty API and has no actual effect.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [rotate](#rotate)

**Model restriction:** This API can be used in both the stage model and FA model.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rx | number | No | Horizontal coordinate of the rotation point. The value range is unlimited.<br>Default unit: vp <br>The abnormal values **undefined** and **null** are processed as invalid values, and **NaN** and **Infinity** cause **Matrix2D** exceptions. <br>Default value: **0** |
| ry | number | No | Vertical coordinate of the rotation point. The value range is unlimited.<br>Default unit: vp <br>The abnormal values **undefined** and **null** are processed as invalid values, and **NaN** and **Infinity** cause **Matrix2D** exceptions. <br>Default value: **0** |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Result matrix object after rotation, which can be used to perform rotation transformation on graphics. |

<a id="rotate-1"></a>

## rotate

```TypeScript
rotate(degree: number, rx?: number, ry?: number): Matrix2D
```

Performs a left-multiply rotation operation on the current matrix, centered at the rotation point. It is commonly used in scenarios such as graphic rotation animation or image rotation processing.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| degree | number | Yes | Rotation angle (in radians). The value range is unlimited. A positive value indicates clockwise rotation. You can convert an angle to radians using `angle * Math.PI / 180` and pass it to this API. <br>Invalid values **undefined** and **null** are treated as invalid values. **NaN** and **Infinity** will cause **Matrix2D** exceptions. <br>Default unit: radians |
| rx | number | No | Horizontal coordinate of the rotation point. The value range is not limited.<br>Default unit: vp. <br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions. <br>Default value: **0**. |
| ry | number | No | Vertical coordinate of the rotation point. The value range is not limited.<br>Default unit: vp. <br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions. <br>Default value: **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Resulting matrix object after rotation, which can be used to perform rotation transformation on graphics. |

## scale

```TypeScript
scale(sx?: number, sy?: number): Matrix2D
```

Performs a left-multiply scaling operation on the current matrix. It is commonly used in scenarios such as graphic scaling or flipping.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | No | Horizontal scaling ratio coefficient. The value range is not limited. A value greater than 1 indicates magnification, less than 1 indicates reduction, and a negative value indicates horizontal flipping.<br>Abnormal values **undefined** and **null** are treated as invalid input. **NaN** and **Infinity** cause **Matrix2D** exceptions. <br>Default value: **1.0** |
| sy | number | No | Vertical scaling ratio coefficient. The value range is not limited. A value greater than 1 indicates magnification, less than 1 indicates reduction, and a negative value indicates vertical flipping.<br>Abnormal values **undefined** and **null** are treated as invalid input. **NaN** and **Infinity** cause **Matrix2D** exceptions. <br>Default value: **1.0** |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Scaling result matrix object, which can be used to scale graphics. |

## translate

```TypeScript
translate(tx?: number, ty?: number): Matrix2D
```

Performs a left-multiply translation operation on the current matrix. It is commonly used in scenarios such as adjusting graphic positions, implementing displacement animations, or offsetting the canvas coordinate system.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tx | number | No | Horizontal translation distance. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions. <br>Default unit: vp. <br>Default value: **0**. |
| ty | number | No | Vertical translation distance. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions. <br>Default unit: vp. <br>Default value: **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Result matrix object after translation, which can be used to perform translation transformation on graphics. |

## rotateX

```TypeScript
rotateX?: number
```

Horizontal skew factor. The value range is unlimited.

Default: **0**

The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotateY

```TypeScript
rotateY?: number
```

Vertical skew factor. The value range is unlimited.

Default: **0**

The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleX

```TypeScript
scaleX?: number
```

Horizontal scale factor. The value range is unlimited. Values greater than 1 enlarge, less than 1 shrink, and negative values flip horizontally.

Default: **1**

The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleY

```TypeScript
scaleY?: number
```

Vertical scale factor. The value range is unlimited. Values greater than 1 enlarge, less than 1 shrink, and negative values flip vertically.

Default: **1**

The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translateX

```TypeScript
translateX?: number
```

Horizontal translation distance. The value range is unlimited.

Default: **0**

The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.

Default unit: vp

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translateY

```TypeScript
translateY?: number
```

Vertical translation distance. The value range is unlimited.

Default: **0**

The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.

Default unit: vp

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
