# Path2D

```TypeScript
declare class Path2D extends CanvasPath
```

A path object that supports path description and combination through its APIs, and can be drawn through the **stroke** or **fill** API of **Canvas**. **Path2D** supports path reuse, combination of multiple paths, and creation of paths based on SVG path strings. It is suitable for scenarios where the same path needs to be drawn multiple times, complex graphics need to be dynamically combined, or graphics need to be drawn based on SVG path data.

> **NOTE:** 
> 
> The **Path2D** object does not support resetting an already set path. To create a
> new path, create an empty **Path2D** object.
> 
> The methods of the **Path2D** object cannot take effect on paths set in the
> [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md)
> and
> [OffscreenCanvasRenderingContext2D](arkts-arkui-canvas-comp-offscreencanvasrenderingcontext2d-c.md)
> objects.

@extends CanvasPath

**Inheritance/Implementation:** Path2D extends [CanvasPath](arkts-arkui-canvas-comp-canvaspath-c.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addPath

```TypeScript
addPath(path: Path2D, transform?: Matrix2D): void
```

Adds a path to this path.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | Yes | Path object to be added to the current path.<br> The abnormal values **undefined** and **null** are treated as invalid values. |
| transform | Matrix2D | No | Transformation matrix object for the added path, used to perform transformations such as translation, rotation, and scaling on the added path. Pass this parameter when graphic transformation is needed for the added path; it can be omitted when no transformation is required. If not passed, the default value is **null**, indicating that no transformation is applied to the path.<br> The abnormal values **undefined** and **null** are treated as invalid values.<br> Default value: **null** |

## constructor

```TypeScript
constructor()
```

Constructs an empty **Path2D** object.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor-1"></a>

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
| unit | LengthMetricsUnit | Yes | Unit mode of the **Path2D** object. Once configured, it cannot be dynamically changed. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).<br> Abnormal values **NaN** and **Infinity** are processed as the default value.<br> Default value: **DEFAULT** |

<a id="constructor-2"></a>

## constructor

```TypeScript
constructor(path: Path2D)
```

Constructs a Path2D object using a path object.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | Yes | Path object to be copied. The newly created **Path2D** object will contain the same path data as the original path. An empty path object is created when the value is **null** or **undefined**. |

<a id="constructor-3"></a>

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
| path | [Path2D](arkts-arkui-canvas-comp-path2d-c.md) | Yes | **Path2D** path object to be copied. Used to create a new **Path2D** object based on an existing path. The incoming path object is not modified, and the newly created object contains a complete copy of the path. |
| unit | LengthMetricsUnit | Yes | Unit mode for configuring the **Path2D** object. It cannot be dynamically changed after configuration. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).<br> Abnormal values **NaN** and **Infinity** are treated as the default value.<br> Default value: **DEFAULT** |

<a id="constructor-4"></a>

## constructor

```TypeScript
constructor(d: string)
```

Constructs a Path2D object using a path string that complies with the SVG path description specifications.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| d | string | Yes | Path string that complies with the SVG path description specification. For the format, see SVG Path Syntax. Abnormal values are treated as invalid values. |

<a id="constructor-5"></a>

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
| description | string | Yes | Path string that conforms to the SVG path description specification. For details about the format, see SVG Path Syntax. Abnormal values are handled as invalid values. |
| unit | LengthMetricsUnit | Yes | Unit mode for configuring the **Path2D** object. After configuration, it cannot be dynamically changed. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).<br> Invalid values **NaN** and **Infinity** are handled as the default value.<br> Default value: **DEFAULT** |
