# ImageBitmap

```TypeScript
declare class ImageBitmap
```

An **ImageBitmap** object stores pixel data rendered on a canvas. Since API version 11, when an application creates a [worker thread](../../../arkts-utils/worker-introduction.md), it can use **postMessage** to transfer the **ImageBitmap** instance to the worker thread for drawing, and use **onmessage** to receive the drawing results sent by the worker thread for display.

> **NOTE:** 
> 
> The **ImageBitmap** object only supports loading static images. To play animated
> images, use the Image component.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
close(): void
```

Releases all image resources associated with the **ImageBitmap** object and sets its width and height to **0**.

> **NOTE:** 
> 
> - This method must be used together with the [constructor()](#constructor)method. After creating an **ImageBitmap** object, call **close()** to release resources when they are no longer needed. Failure to call **close()** may cause image resource leaks and affect app performance.
> - It is recommended to call this method after **Canvas** drawing is complete, for example, at the end of the [onReady](arkts-arkui-canvas-comp-attribute.md#onready)callback.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(src: string)
```

Creates an **ImageBitmap** object using an image data source.

> **NOTE:** 
> 
> Call the **close()** method to release resources after use to avoid image
> resource leaks.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Image data source. Supports local images.<br> 1. The string format is used to load local images, for example,   **ImageBitmap("common/images/example.jpg")**. For modules of the "entry" and"feature" types, the starting point of the image loading path is the **ets** folder of the current module. For modules of the "har" and "shared" types, the starting point of the image loading path is the **ets** folder of the currently built "entry" or "feature" type module.<br> For modules of the "har" and "shared" types, it is recommended to use [ImageSource](../../../media/image/image-decoding.md) to decode resource images into a unified **PixelMap** for loading.<br> 2. Supported local image types: bmp, jpg, png, svg, and webp.<br>   **NOTE:** <br> - In ArkTS widgets, strings with network-related path prefixes such as **http://**, the **datashare://** path prefix, and the **file://data/storage** path prefix are not supported. |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(src: string, unit: LengthMetricsUnit)
```

Creates an **ImageBitmap** object using an image data source. This API supports configuring the unit mode of the **ImageBitmap** object with **unit**.

> **NOTE:** 
> 
> Call the **close()** method to release resources after use to avoid image
> resource leaks.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Image data source, which supports local images.<br> 1. The string format is used to load local images, for example,   **ImageBitmap("common/images/example.jpg")**. For modules of the "entry" and"feature" types, the image loading path starts from the **ets** folder of the current module. For modules of the "har" and "shared" types, the image loading path starts from the **ets** folder of the currently built "entry" or "feature"type module.<br> For modules of the "har" and "shared" types, you are advised to use [ImageSource](../../../media/image/image-decoding.md) to decode resource images into a unified **PixelMap** for loading.<br> 2. Supported local image types: bmp, jpg, png, svg, and webp.<br>   **NOTE:** <br> - ArkTS widgets do not support strings with network-related path prefixes such as **http://**, the **datashare://** path prefix, or the **file://data/storage** path prefix. |
| unit | LengthMetricsUnit | Yes | Unit mode for configuring the **ImageBitmap** object. The mode cannot be dynamically changed after configuration. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).<br> Default value: **LengthMetricsUnit.DEFAULT**.<br> Abnormal values such as **undefined**, **NaN**, and **Infinity** are processed as the default value. |

<a id="constructor-2"></a>

## constructor

```TypeScript
constructor(data: PixelMap)
```

Creates an **ImageBitmap** object using a **PixelMap** object.

> **NOTE:** 
> 
> Call the **close()** method to release resources after use to avoid image
> resource leaks.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Image data source, set through a **PixelMap** object. Applicable to scenarios where images need to be decoded and processed before drawing, which can improve image loading performance. |

<a id="constructor-3"></a>

## constructor

```TypeScript
constructor(data: PixelMap, unit: LengthMetricsUnit)
```

Creates an **ImageBitmap** object using a **PixelMap** object. This API supports configuring the unit mode of the **ImageBitmap** object with **unit**.

> **NOTE:** 
> 
> Call the **close()** method to release resources after use to avoid image
> resource leaks.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Image data source, set through a **PixelMap** object. This is suitable for scenarios where images need to be decoded and processed before drawing, which can improve image loading performance. |
| unit | LengthMetricsUnit | Yes | Unit mode for configuring the **ImageBitmap** object. Once configured, it cannot be changed dynamically. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).<br> Default value: **LengthMetricsUnit.DEFAULT**.<br> Abnormal values such as **undefined**, **NaN**, and **Infinity** are processed as the default value. |

<a id="constructor-4"></a>

## constructor

```TypeScript
constructor(data: Resource, unit?: LengthMetricsUnit)
```

Creates an **ImageBitmap** object using a **Resource** object. This API supports configuring the unit mode of the **ImageBitmap** object with **unit**.

> **NOTE:** 
> 
> Call the **close()** method to release resources after use to avoid image
> resource leaks.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Image data source, set by referencing a **Resource** object. This is used to reference image resources in the app resource directory, for example, **$r('app.media.example')**, which avoids hardcoding paths.<br> Supported image types: bmp, jpg, png, svg, and webp. |
| unit | LengthMetricsUnit | No | Unit mode of the **ImageBitmap** object. Once configured, it cannot be changed dynamically. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvas-comp-canvasrenderingcontext2d-c.md).<br> Default value: **LengthMetricsUnit.DEFAULT**.<br> Abnormal values **undefined**, **NaN**, and **Infinity** are processed as the default value. |

## height

```TypeScript
readonly height: number
```

Height of the **ImageBitmap**.<br>Unit: vp.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

Width of the **ImageBitmap**.<br>Unit: vp.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
