# OffscreenCanvas

```TypeScript
declare class OffscreenCanvas
```

The **OffscreenCanvas** component is used to draw custom graphics.

When the [Canvas](arkts-arkui-canvas-comp.md#canvas) component or **CanvasRenderingContext2D** object is used, rendering, animation, and user interaction usually occur on the main thread of the application. Calculations related to canvas animation and rendering may affect application performance. **OffscreenCanvas** allows for rendering off the screen. This means that some tasks can be run in a separate thread to reduce the load on the main thread.

> **NOTE:** 
> 
> **OffscreenCanvas** cannot be used in **ServiceExtensionAbility**. For offscreen
> drawing in **ServiceExtensionAbility**, use the
> [drawing module](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-graphics-drawing.md) instead.

## Child Components

Not supported.

@extends CanvasRenderer [since 8 - 10]

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(width: number, height: number)
```

Constructs an **OffscreenCanvas** object.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the **OffscreenCanvas** component.<br>Abnormal values **NaN** and **Infinity** are treated as invalid values, and negative numbers are treated as 0. <br>Unit: vp. |
| height | number | Yes | Height of the **OffscreenCanvas** component.<br>Abnormal values **NaN** and **Infinity** are treated as invalid values, and negative numbers are treated as 0. <br>Unit: vp. |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(width: number, height: number, unit: LengthMetricsUnit)
```

Creates an **OffscreenCanvas** object, with support for configuring the unit mode.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the **OffscreenCanvas** component.<br>Abnormal values **NaN** and **Infinity** are treated as invalid values, and negative numbers are treated as 0. <br>The unit is determined by the unit parameter. Default unit: vp. |
| height | number | Yes | Height of the **OffscreenCanvas** component.<br>Abnormal values **NaN** and **Infinity** are treated as invalid values, and negative numbers are treated as 0. <br>The unit is determined by the unit parameter. Default unit: vp. |
| unit | LengthMetricsUnit | Yes | Unit mode of the **OffscreenCanvas** object. Once configured, it cannot be changed dynamically. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md). Optional values: **DEFAULT** (default unit mode, which uses vp as the unit and automatically adapts based on the screen density) and PX (px pixel unit, which is suitable for scenarios requiring precise pixel control, where the width and height values are calculated based on physical pixels). <br>Abnormal values **NaN** and **Infinity** are treated as the default value. <br>Default value: **DEFAULT**. |

## getContext

```TypeScript
getContext(contextType: "2d", options?: RenderingContextSettings): OffscreenCanvasRenderingContext2D
```

Obtains the drawing context of the offscreen canvas.

> **NOTE:** 
> 
> - After the **OffscreenCanvas** object uses **getContext** to obtain the drawing context, the object cannot be passed to any other thread through **postMessage**.Otherwise, an exception is thrown.
> 
> - After the **OffscreenCanvas** object has been passed to a Worker thread through
> **postMessage**, the original thread (sender) is not allowed to call the
> **getContext** method of the object. Otherwise, an exception is thrown.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contextType | "2d" | Yes | Type of the drawing context of the **OffscreenCanvas** component. Currently, only the "2d" type is supported.<br>"2d": Creates an **OffscreenCanvasRenderingContext2D** object that represents a 2D rendering context. <br>The abnormal values **undefined** and **null** are treated as invalid values, and the API returns **undefined**. |
| options | [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md) | No | Parameters used to configure the **OffscreenCanvasRenderingContext2D** object. See [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md). This parameter is passed when custom rendering context settings (such as enabling antialiasing) are required. If not passed, the default settings are used (**antialias** defaults to **false**). <br>The abnormal values **undefined** and **null** are treated as the default values of [RenderingContextSettings](arkts-arkui-canvas-comp-renderingcontextsettings-c.md). <br>Default value: **null**. |

**Return value:**

| Type | Description |
| --- | --- |
| [OffscreenCanvasRenderingContext2D](arkts-arkui-canvas-comp-offscreencanvasrenderingcontext2d-c.md) | Drawing context of the offscreen canvas. If the input parameter contextType of the **getContext** method is not **"2d"** (including null or undefined), **undefined** will be returned. Before using the method, check whether the return value is **undefined**. |

## transferToImageBitmap

```TypeScript
transferToImageBitmap(): ImageBitmap
```

Creates an **ImageBitmap** object from the current content of the **OffscreenCanvas** component.

> **NOTE:** 
> 
> After the **OffscreenCanvas** object has been passed to a Worker thread through
> **postMessage**, the original thread (sender) is not allowed to call the
> **transferToImageBitmap** method of the object. Otherwise, an exception is thrown.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [ImageBitmap](arkts-arkui-canvas-comp-imagebitmap-c.md) | **ImageBitmap** object created. |

## height

```TypeScript
height: number
```

Height of the **OffscreenCanvas** component. <br>Abnormal values **NaN** and **Infinity** are treated as invalid values, and negative numbers are treated as 0. <br>Unit: vp.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

Width of the **OffscreenCanvas** component. <br>Abnormal values **NaN** and **Infinity** are treated as invalid values, and negative numbers are treated as 0. <br>Unit: vp.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
