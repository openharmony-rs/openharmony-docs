# TransformObject

TransformObject

@interface TransformObject

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## matrix

```TypeScript
matrix(scaleX: number, skewX: number, skewY: number, scaleY: number, translateX: number, translateY: number): void
```

Defines a 2D transformation, using a matrix of six values..

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scaleX | number | Yes | the scale value for x-axis |
| skewX | number | Yes | the skew value for y-axis |
| skewY | number | Yes | the skew value for x-axis |
| scaleY | number | Yes | the scale value for y-axis |
| translateX | number | Yes | the translate value for x-axis |
| translateY | number | Yes | the translate value for y-axis |

## matrix3d

```TypeScript
matrix3d(
    n00: number,
    n01: number,
    n02: number,
    n03: number,
    n10: number,
    n11: number,
    n12: number,
    n13: number,
    n20: number,
    n21: number,
    n22: number,
    n23: number,
    n30: number,
    n31: number,
    n32: number,
    n33: number,
  ): void
```

Defines a 3D transformation using a 4x4 matrix of 16 values.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| n00 | number | Yes | the value of the 0 row and 0 column of the 4x4 matrix |
| n01 | number | Yes | the value of the 0 row and 1 column of the 4x4 matrix |
| n02 | number | Yes | the value of the 0 row and 2 column of the 4x4 matrix |
| n03 | number | Yes | the value of the 0 row and 3 column of the 4x4 matrix |
| n10 | number | Yes | the value of the 1 row and 0 column of the 4x4 matrix |
| n11 | number | Yes | the value of the 1 row and 1 column of the 4x4 matrix |
| n12 | number | Yes | the value of the 1 row and 2 column of the 4x4 matrix |
| n13 | number | Yes | the value of the 1 row and 3 column of the 4x4 matrix |
| n20 | number | Yes | the value of the 2 row and 0 column of the 4x4 matrix |
| n21 | number | Yes | the value of the 2 row and 1 column of the 4x4 matrix |
| n22 | number | Yes | the value of the 2 row and 2 column of the 4x4 matrix |
| n23 | number | Yes | the value of the 2 row and 3 column of the 4x4 matrix |
| n30 | number | Yes | the value of the 3 row and 0 column of the 4x4 matrix |
| n31 | number | Yes | the value of the 3 row and 1 column of the 4x4 matrix |
| n32 | number | Yes | the value of the 3 row and 2 column of the 4x4 matrix |
| n33 | number | Yes | the value of the 3 row and 3 column of the 4x4 matrix |

## perspective

```TypeScript
perspective(verticalDistance: number): void
```

Defines a perspective view for the 3D transformation element.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| verticalDistance | number | Yes | the vertical distance from the observation point to the component plane. |

## rotate

```TypeScript
rotate(angle: number): void
```

Define the 2D rotation and specify the angle in the parameters.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | the rotate value for z-axis |

## rotate3d

```TypeScript
rotate3d(x: number, y: number, z: number, angle: number): void
```

Defines a 3D transformation for rotating the X / Y / Z axes.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the vector value of the x-axis |
| y | number | Yes | the vector value of the y-axis |
| z | number | Yes | the vector value of the z-axis |
| angle | number | Yes | the rotate value for x & y & z vector. |

## rotateX

```TypeScript
rotateX(angle: number): void
```

Defines 3D transformations for rotating of the X axes.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | the scale value for x-axis |

## rotateY

```TypeScript
rotateY(angle: number): void
```

Defines 3D transformations for rotating of the Y axes.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | the scale value for y-axis |

## rotateZ

```TypeScript
rotateZ(angle: number): void
```

Defines 3D transformations for rotating of the Z axes.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | the scale value for z-axis |

## scale

```TypeScript
scale(x: number, y: number): void
```

Defines 2D transformations for scaling of the X and Y axes

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the scale value for x-axis |
| y | number | Yes | the scale value for y-axis |

## scale3d

```TypeScript
scale3d(x: number, y: number, z: number): void
```

Defines 3D transformations for scaling of the X / Y / Z axes

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the scale value for x-axis |
| y | number | Yes | the scale value for y-axis |
| z | number | Yes | the scale value for z-axis |

## scaleX

```TypeScript
scaleX(x: number): void
```

Defines 2D transformations for scaling of the X axes

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the scale value for x-axis |

## scaleY

```TypeScript
scaleY(y: number): void
```

Defines 2D transformations for scaling of the Y axes

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| y | number | Yes | the scale value for y-axis |

## scaleZ

```TypeScript
scaleZ(z: number): void
```

Defines 3D transformations for scaling of the Z axes

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| z | number | Yes | the scale value for z-axis |

## skew

```TypeScript
skew(xAngle: number, yAngle: number): void
```

Defines the 2D skew transition along the X and Y axes.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xAngle | number | Yes | the angle of inclination along the x axis. |
| yAngle | number | Yes | the angle of inclination along the y axis. |

## skewX

```TypeScript
skewX(angle: number): void
```

Defines the 2D skew transition along the X axes.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | the angle of inclination along the x axis. |

## skewY

```TypeScript
skewY(angle: number): void
```

Defines the 2D skew transition along the Y axes.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | the angle of inclination along the y axis. |

## translate

```TypeScript
translate(x: number, y: number): void
```

Defines 2D transformations for translation of the X and Y axes

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the translate value for x-axis |
| y | number | Yes | the translate value for y-axis |

## translate3d

```TypeScript
translate3d(x: number, y: number, z: number): void
```

Defines 3D transformations for translation of the X / Y / Z axes

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the translate value for x-axis |
| y | number | Yes | the translate value for y-axis |
| z | number | Yes | the translate value for z-axis |

## translateX

```TypeScript
translateX(x: number): void
```

Defines 2D transformations for translation of the X axes

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | the translate value for x-axis |

## translateY

```TypeScript
translateY(y: number): void
```

Defines 2D transformations for translation of the Y axes

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| y | number | Yes | the translate value for y-axis |

## translateZ

```TypeScript
translateZ(z: number): void
```

Defines 3D transformations for translation of the Z axes

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| z | number | Yes | the translate value for z-axis |
