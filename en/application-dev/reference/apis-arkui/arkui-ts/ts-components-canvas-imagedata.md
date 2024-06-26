# ImageData

An **ImageData** object stores pixel data rendered on a canvas.

>  **NOTE**
>
>  The APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## APIs

constructor(width: number, height: number, data?: Uint8ClampedArray);

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

## Attributes

| Name    | Type               | Description                                      |
| ------ | ----------------- | ---------------------------------------- |
| width | number | Actual width of the rectangle on the canvas, in px. Read-only.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| height | number | Actual height of the rectangle on the canvas, in px. Read-only.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|
| data | Uint8ClampedArray | A one-dimensional array of color values in the range from 0 to 255. Read-only.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.|

>  **NOTE**
>
>  You can use the [px2vp](ts-pixel-units.md#pixel-unit-conversion) API to convert the unit.

**Example**

  ```ts
  // xxx.ets
  @Entry
  @Component
  struct Translate {
    private settings: RenderingContextSettings = new RenderingContextSettings(true)
    private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings)
    private img:ImageBitmap = new ImageBitmap("common/images/1234.png")

    build() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
        Canvas(this.context)
          .width('100%')
          .height('100%')
          .backgroundColor('#ffff00')
          .onReady(() =>{
            this.context.drawImage(this.img,0,0,130,130)
            let imagedata = this.context.getImageData(50,50,130,130)
            this.context.putImageData(imagedata,150,150)
          })
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

  ![en-us_image_000000127777780](figures/en-us_image_000000127777780.png)
