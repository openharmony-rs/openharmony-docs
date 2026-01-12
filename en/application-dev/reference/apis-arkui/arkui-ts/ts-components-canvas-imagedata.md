# ImageData
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

An **ImageData** object stores pixel data rendered on a canvas.

>  **NOTE**
>
>  This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> To ensure successful drawing, make sure the object's area does not exceed 16000 x 16000, with its width and height not greater than 16384 px. If the created area exceeds 536870911 px, the returned width and height are both 0 px, and **data** is **undefined**.

## constructor

constructor(width: number, height: number, data?: Uint8ClampedArray)

Creates an **ImageData** object with the specified width, height, and data. If data is not provided, a one-dimensional array filled with zeros is used.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name| Type | Mandatory | Description|
| ------ | ----- | ----- | ----- |
| width | number |Yes| Width of the rectangle.<br>Default unit: vp<br>Invalid values **NaN** and **Infinity** are treated as **0**.|
| height | number |Yes| Height of the rectangle.<br>Default unit: vp<br>Invalid values **NaN** and **Infinity** are treated as **0**.|
| data | [Uint8ClampedArray](../../apis-arkts/arkts-apis-arkts-collections-Uint8ClampedArray.md) |No| A one-dimensional array of color values. The values range from 0 to 255.<br>If the value specified is **undefined**, **data** is **undefined**.<br>Default value: a one-dimensional array of all zeros|

## constructor<sup>12+</sup>

constructor(width: number, height: number, data?: Uint8ClampedArray, unit?: LengthMetricsUnit)

Creates an **ImageData** object with the specified width, height, and data. If data is not provided, a one-dimensional array filled with zeros is used. The unit parameter configures the unit mode for the **ImageData** object.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type | Mandatory | Description|
| ------ | ----- | ----- | ----- |
| width | number |Yes| Width of the rectangle.<br>Default unit: vp<br>Invalid values **NaN** and **Infinity** are treated as **0**.|
| height | number |Yes| Height of the rectangle.<br>Default unit: vp<br>Invalid values **NaN** and **Infinity** are treated as **0**.|
| data | [Uint8ClampedArray](../../apis-arkts/arkts-apis-arkts-collections-Uint8ClampedArray.md) |No| A one-dimensional array of color values. The values range from 0 to 255.<br>If the value specified is **undefined**, **data** is **undefined**.<br>Default value: a one-dimensional array of all zeros|
| unit  | [LengthMetricsUnit](../js-apis-arkui-graphics.md#lengthmetricsunit12) | No  |  Unit mode of the **ImageData** object. The value cannot be dynamically changed once set. The configuration method is the same as that of [CanvasRenderingContext2D](ts-canvasrenderingcontext2d.md).<br>Invalid values **undefined**, **NaN** and **Infinity** are treated as the default value.<br>Default value: **DEFAULT**.|

## Attributes

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type  | Read-Only| Optional| Description|
| ------ | -------- | --------- | ---------- | ------------------------------ |
| width | number | Yes| No| Actual width of the rectangle on the canvas.<br>The unit is px.|
| height | number | Yes| No| Actual height of the rectangle on the canvas.<br>The unit is px.|
| data | [Uint8ClampedArray](../../apis-arkts/arkts-apis-arkts-collections-Uint8ClampedArray.md) | Yes| No| A one-dimensional array of color values. The values range from 0 to 255.|

>  **NOTE**
>
>  You can use the [px2vp](ts-pixel-units.md#px2vpdeprecated) API for unit conversion.

## Example

This example shows how to use the **getImageData** API to obtain an **ImageData** object.

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Translate {
    private settings: RenderingContextSettings = new RenderingContextSettings(true);
    private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
    // Replace "common/images/1234.png" with the image resource file you use.
    private img: ImageBitmap = new ImageBitmap("common/images/1234.png");

    build() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
        Canvas(this.context)
          .width('100%')
          .height('100%')
          .backgroundColor('#ffff00')
          .onReady(() => {
            this.context.drawImage(this.img, 0, 0, 130, 130)
            let imageData = this.context.getImageData(50, 50, 130, 130)
            this.context.putImageData(imageData, 150, 150)
          })
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

  ![en-us_image_000000127777780](figures/en-us_image_000000127777780.png)
