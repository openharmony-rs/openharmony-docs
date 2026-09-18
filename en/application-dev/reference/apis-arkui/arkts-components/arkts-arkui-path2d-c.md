# Path2D

**Path2D** allows you to describe a path through an existing path. This path can be drawn through the **stroke** or **fill** API of **Canvas**.

> **NOTE:** 
> 
> The Path2D object does not support the resetting of an existing path. If a new path
> is required, you can create an empty Path2D object.
> 
> The methods of the Path2D object do not take effect for the paths set in the
> [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)
> and
> [OffscreenCanvasRenderingContext2D](arkts-arkui-offscreencanvasrenderingcontext2d-c.md)
> objects.

@extends CanvasPath

**Inheritance/Implementation:** Path2D extends [CanvasPath](arkts-arkui-canvaspath-c.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addPath

```TypeScript
addPath(path: Path2D, transform?: Matrix2D): void
```

Adds a path to this path.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | Yes | Path to be added to this path. Unit: px.<br> The **undefined** and **null** values are treated as invalid. |
| transform | [Matrix2D](../arkts-apis/arkts-arkui-matrix2d-c.md) | No | Transformation matrix of the new path.<br> The **undefined** and **null** values are treated as invalid.<br> Default value: **null**. |

## constructor

```TypeScript
constructor()
```

Constructs an empty **Path2D** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

Constructs an empty Path2D object. The unit mode of the Path2D object can be configured.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | Yes | Unit mode of the Path2D object. The value cannot be dynamically changed once set. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md).<br> Invalid values **NaN** and **Infinity** are treated as the default value.<br> Default value: **DEFAULT** |

## constructor

```TypeScript
constructor(path: Path2D)
```

Constructs a Path2D object using a path object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | Yes | **Path** object. |

## constructor

```TypeScript
constructor(path: Path2D, unit: LengthMetricsUnit)
```

When a path object is used to construct a Path2D object, the unit mode of the Path2D object can be configured.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | Yes | **Path** object. |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | Yes | Unit mode of the Path2D object. The value cannot be dynamically changed once set. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md).<br> Invalid values **NaN** and **Infinity** are treated as the default value.<br> Default value: **DEFAULT** |

## constructor

```TypeScript
constructor(d: string)
```

Constructs a Path2D object using a path string that complies with the SVG path description specifications.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| d | string | Yes | Path that complies with the [SVG path syntax](arkts-arkui-path2d-c.md). Invalid values are treated as invalid inputs. |

## constructor

```TypeScript
constructor(description: string, unit: LengthMetricsUnit)
```

Constructs a Path2D object using a path string that complies with the SVG path specifications. The unit mode of the Path2D object can be configured.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| description | string | Yes | Path that complies with the [SVG path syntax](arkts-arkui-path2d-c.md). Invalid values are treated as invalid inputs. |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | Yes | Unit mode of the Path2D object. The value cannot be dynamically changed once set. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md).<br> Invalid values **NaN** and **Infinity** are treated as the default value.<br> Default value: **DEFAULT** |
