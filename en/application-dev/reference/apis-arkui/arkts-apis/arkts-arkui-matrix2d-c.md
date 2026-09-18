# Matrix2D

**Matrix2D** allows you to perform matrix transformation, such as scaling, rotating, and translating.

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

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

Constructs a two-dimensional transformation matrix object. The default value is a matrix whose attributes are all 0. The unit mode of the Matrix2D object can be configured.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unit | [LengthMetricsUnit](arkts-arkui-lengthmetricsunit-t.md) | Yes | Unit mode of the **Matrix2D** object. The value cannot be dynamically changed once set. The configuration method is the same as that of CanvasRenderingContext2D.<br>For abnormal values NaN and Infinity, the default values are used.<br>Default value: DEFAULT. |

## identity

```TypeScript
identity(): Matrix2D
```

Transforms the current 2D matrix back to the identity matrix (i.e., without any rotational translation scaling effect)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Identity matrix. |

## invert

```TypeScript
invert(): Matrix2D
```

Transform the current 2D matrix into an inverse matrix (that is, the transformation effect is the opposite effect of the original)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Inverse of the current matrix. |

## multiply

```TypeScript
multiply(other?: Matrix2D): Matrix2D
```

The matrix is superimposed in right multiplication mode. When the input parameter is empty, the matrix is superimposed.

**Since:** 8

**Deprecated since:** 10

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [Matrix2D](arkts-arkui-matrix2d-c.md) | No | Target matrix.<br>Invalid values **undefined** and **null** are treated as invalid inputs.<br>Default value: **null**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Matrix of the multiplication result. |

## rotate

```TypeScript
rotate(rx?: number, ry?: number): Matrix2D
```

Adds the rotation effect of the X and Y axes to the current matrix.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [rotate](#rotate)

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rx | number | No | Horizontal coordinate of the rotation point. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default unit: vp. |
| ry | number | No | Vertical coordinate of the rotation point. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default unit: vp. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) |  |

## rotate

```TypeScript
rotate(degree: number, rx?: number, ry?: number): Matrix2D
```

Adds the rotation effect of the X and Y axes to the current matrix.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| degree | number | Yes | Rotation angle. The value range is not limited. Positive angles represent clockwise rotation. You can convert the angle to radians using the following formula: degree * Math.PI/180.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default unit: radian. |
| rx | number | No | Horizontal coordinate of the rotation point. The value range is not limited.<br>Default unit: vp.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default value: **0**. |
| ry | number | No | Vertical coordinate of the rotation point. The value range is not limited.<br>Default unit: vp.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default value: **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) |  |

## scale

```TypeScript
scale(sx?: number, sy?: number): Matrix2D
```

Adds the scaling effect of the X and Y axes to the current matrix.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | No | Horizontal scaling ratio coefficient. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default value: **1.0**. |
| sy | number | No | Vertical scaling ratio coefficient. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default value: **1.0**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) |  |

## translate

```TypeScript
translate(tx?: number, ty?: number): Matrix2D
```

Performs a left multiplication translation operation on this matrix.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tx | number | No | Horizontal translation distance. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default unit: vp.<br>Default value: **0**. |
| ty | number | No | Vertical translation distance. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default unit: vp.<br>Default value: **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-matrix2d-c.md) | Matrix of the translation result. |

## rotateX

```TypeScript
rotateX?: number
```

Horizontal skew coefficient. The value range is not limited.<br>If the value is undefined, it is regarded as an invalid value. If the value is NaN or Infinity, the Matrix2D will be abnormal.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotateY

```TypeScript
rotateY?: number
```

Vertical skew coefficient. The value range is not limited.<br>If the value is undefined, it is regarded as an invalid value. If the value is NaN or Infinity, the Matrix2D will be abnormal.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleX

```TypeScript
scaleX?: number
```

Horizontal scaling coefficient. The value range is not limited.<br>If the value is undefined, it is regarded as an invalid value. If the value is NaN or Infinity, the Matrix2D will be abnormal.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleY

```TypeScript
scaleY?: number
```

Vertical scaling coefficient. The value range is not limited.<br>If the value is undefined, it is regarded as an invalid value. If the value is NaN or Infinity, the Matrix2D will be abnormal.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translateX

```TypeScript
translateX?: number
```

Horizontal translation distance. The value range is unlimited. <br>The abnormal value undefined is processed as an invalid value. NaN and Infinity will cause Matrix2D exceptions. After the setting, the drawn content is not displayed. <br>Default unit: vp.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translateY

```TypeScript
translateY?: number
```

Vertical translation distance. The value range is unlimited. <br>The abnormal value undefined is processed as an invalid value. NaN and Infinity will cause Matrix2D exceptions. After the setting, the drawn content is not displayed. <br>Default unit: vp.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
