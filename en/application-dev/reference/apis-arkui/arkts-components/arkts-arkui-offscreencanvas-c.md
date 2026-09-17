# OffscreenCanvas

The **OffscreenCanvas** component is used to draw custom graphics.

When the Canvas component or **CanvasRenderingContext2D** object is used, rendering, animation, and user interaction usually occur on the main thread of the application. Calculations related to canvas animation and rendering may affect application performance. **OffscreenCanvas** allows for rendering off the screen. This means that some tasks can be run in a separate thread to reduce the load on the main thread.

> **NOTE:** 
> 
> **OffscreenCanvas** cannot be used in ServiceExtensionAbility. It is recommended
> that you use the
> [drawing module](../../../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing.md)
> for offscreen drawing in ServiceExtensionAbility.

@extends CanvasRenderer [since 8 - 10]

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(width: number, height: number)
```

Constructs an OffscreenCanvas for creating an offscreen canvas object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the offscreen canvas.<br> **NaN** and **Infinity** are treated as invalid values.<br>Default unit: vp |
| height | number | Yes | Height of the offscreen canvas.<br> **NaN** and **Infinity** are treated as invalid values.<br>Default unit: vp |

## constructor

```TypeScript
constructor(width: number, height: number, unit: LengthMetricsUnit)
```

Constructs an **OffscreenCanvas** object for creating an offscreen canvas object. The unit mode is configurable for the **OffscreenCanvas** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the offscreen canvas.<br> **NaN** and **Infinity** are treated as invalid values.<br>Default unit: vp |
| height | number | Yes | Height of the offscreen canvas.<br> **NaN** and **Infinity** are treated as invalid values.<br>Default unit: vp |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | Yes | Unit mode of the OffscreenCanvas object. The value cannot be dynamically changed once set. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md).<br> Invalid values **NaN** and **Infinity** are treated as the default value.<br> Default value: **DEFAULT**. |

## getContext

```TypeScript
getContext(contextType: "2d", options?: RenderingContextSettings): OffscreenCanvasRenderingContext2D
```

Obtains the drawing context of the offscreen canvas.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contextType | "2d" | Yes | Type of the drawing context of the offscreen canvas. The value can only be **"2d"**.<br> **"2d"**: creates an **OffscreenCanvasRenderingContext2D** object that represents a two-dimensional rendering context.<br> The values **undefined** and **null** are considered as invalid values, and **undefined** is returned. |
| options | [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) | No | Parameters of the **OffscreenCanvasRenderingContext2D** object. For details, see [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md).<br> **undefined** and **null** values are processed based on the default value of [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md).<br> Default value: **null**. |

**Return value:**

| Type | Description |
| --- | --- |
| [OffscreenCanvasRenderingContext2D](arkts-arkui-offscreencanvasrenderingcontext2d-c.md) | Drawing context of the offscreen canvas. If the input parameter contextType of the **getContext** method is not **"2d"** (including null or undefined), **undefined** will be returned. Before using the method, check whether the return value is **undefined**. |

## transferToImageBitmap

```TypeScript
transferToImageBitmap(): ImageBitmap
```

Creates an **ImageBitmap** object from the most recently rendered image of the offscreen canvas.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ImageBitmap](arkts-arkui-imagebitmap-c.md) | **ImageBitmap** object created. |

## height

```TypeScript
height: number
```

Height of the offscreen canvas.

Default unit: vp

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

Width of the offscreen canvas.

Default unit: vp

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
