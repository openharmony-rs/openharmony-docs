# ImageData

An **ImageData** object stores pixel data rendered on a canvas.

> **NOTE:** 
> 
> A constructor used to create an **ImageData** object. To ensure successful drawing,
> make sure the object's area does not exceed 16000 x 16000, with its width and height
> not greater than 16384 px. If the created area exceeds 536870911 px, the returned
> width and height are both 0 px, and **data** is **undefined**.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(width: number, height: number, data?: Uint8ClampedArray)
```

Creates an **ImageData** object with the specified width, height, and color. If data is not defined, it is populated with a one-dimensional array of 0s.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the rectangle.<br>Default unit: vp<br> Invalid values **NaN** and **Infinity** are treated as **0**. |
| height | number | Yes | Height of the rectangle.<br>Default unit: vp<br> Invalid values **NaN** and **Infinity** are treated as **0**. |
| data | Uint8ClampedArray | No | A one-dimensional array of color values. The values range from 0 to 255.<br> If the value specified is **undefined**, **data** is **undefined**.<br> Default value: a one-dimensional array of all 0s |

## constructor

```TypeScript
constructor(width: number, height: number, data?: Uint8ClampedArray, unit?: LengthMetricsUnit)
```

Creates an **ImageData** object with the specified width, height, and color. If data is not defined, it is populated with a one-dimensional array of 0s. The unit of the **ImageData** object can be configured using **unit**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the rectangle.<br>Default unit: vp<br> Invalid values **NaN** and **Infinity** are treated as **0**. |
| height | number | Yes | Height of the rectangle.<br>Default unit: vp<br> Invalid values **NaN** and **Infinity** are treated as **0**. |
| data | Uint8ClampedArray | No | A one-dimensional array of color values. The values range from 0 to 255.<br> If the value specified is **undefined**, **data** is **undefined**.<br> Default value: a one-dimensional array of all 0s |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | No | Unit mode of the **ImageData** object. The value cannot be dynamically changed once set. The configuration method is the same as that of [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md).<br> Invalid values **undefined**, **NaN** and **Infinity** are treated as the default value.<br> Default value: **DEFAULT**. |

## data

```TypeScript
readonly data: Uint8ClampedArray
```

A one-dimensional array of color values. The values range from 0 to 255.

**Type:** Uint8ClampedArray

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
readonly height: number
```

Actual height of the rectangle on the canvas.

The unit is px.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

Actual width of the rectangle on the canvas.

The unit is px.

> **NOTE:** 
> 
> The px2vp
> API can be used for unit conversion.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
