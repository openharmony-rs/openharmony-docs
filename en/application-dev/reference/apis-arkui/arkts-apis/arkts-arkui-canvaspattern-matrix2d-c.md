# Matrix2D

2D transformation matrix, supporting rotation, translation, and scaling of the X-axis and Y-axis

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

Constructs a 2D change matrix object. The default value is the unit matrix.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## identity

```TypeScript
identity(): Matrix2D
```

Transforms the current 2D matrix back to the identity matrix (i.e., without any rotational translation scaling effect)

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) |  |

## invert

```TypeScript
invert(): Matrix2D
```

Transform the current 2D matrix into an inverse matrix (that is, the transformation effect is the opposite effect of the original)

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) |  |

## multiply

```TypeScript
multiply(other?: Matrix2D): Matrix2D
```

The matrix is superimposed in right multiplication mode. When the input parameter is empty, the matrix is superimposed.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | No | Matrix to be superimposed |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) |  |

## rotate

```TypeScript
rotate(rx?: number, ry?: number): Matrix2D
```

Adds the rotation effect of the X and Y axes to the current matrix.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rx | number | No | Rotation effect of the X axis |
| ry | number | No | Rotation effect of the Y-axis |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) |  |

## scale

```TypeScript
scale(sx?: number, sy?: number): Matrix2D
```

Adds the scaling effect of the X and Y axes to the current matrix.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | No | X-axis scaling effect |
| sy | number | No | Y-axis scaling effect |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) |  |

## translate

```TypeScript
translate(tx?: number, ty?: number): Matrix2D
```

Adds the translation effect of the X and Y axes to the current matrix.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tx | number | No | X-axis translation effect |
| ty | number | No | Y-axis translation effect |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) |  |

## rotateX

```TypeScript
rotateX?: number
```

Horizontal Tilt

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotateY

```TypeScript
rotateY?: number
```

Vertical Tilt

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleX

```TypeScript
scaleX?: number
```

Horizontal Zoom

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleY

```TypeScript
scaleY?: number
```

Vertical Zoom

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translateX

```TypeScript
translateX?: number
```

Horizontal movement

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translateY

```TypeScript
translateY?: number
```

Vertical movement

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
