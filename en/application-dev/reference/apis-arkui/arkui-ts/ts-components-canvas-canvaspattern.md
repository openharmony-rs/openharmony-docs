# CanvasPattern
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

A **CanvasPattern** object is created via the [createPattern](ts-components-canvas-common-method.md#createpattern) method. It is a pattern for image filling based on a specified image and repeat mode.

>  **NOTE**
>
>  This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## Methods

### setTransform

setTransform(transform?: Matrix2D): void

Uses a **Matrix2D** object as a parameter to perform matrix transformation on the current **CanvasPattern** object.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type | Mandatory| Description  |
| --------- | -------------- | ------ | ---------- |
| transform | [Matrix2D](ts-components-canvas-matrix2d.md) | No | Transformation matrix.<br>**undefined** and **null** are treated as invalid values, and no matrix transformation is performed.<br>Default value: no matrix transformation|

## Example

This example demonstrates how to apply matrix transformations to a **CanvasPattern** object using the **setTransform** API.

> **NOTE**
>
> The resources used in this example are not located in the **src** > **main** > **resource** directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the **resources** directory are not packaged by default when a project or module is created. To package these resources, go to **buildOption** in the module's **build-profile.json5** file > **resOptions** > **copyCodeResource**, and set **enable** to **true**. For details, see the description of [copyCodeResource](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348) in **resOptions**.

```ts
// xxx.ets
@Entry
@Component
struct CanvasPatternPage {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();
  // Replace "common/pattern.jpg" with the image resource file you use.
  private img: ImageBitmap = new ImageBitmap("common/pattern.jpg");
  private pattern: CanvasPattern | null = null;

  build() {
      Column() {
        Button("Click to set transform")
          .onClick(() => {
            this.matrix.scaleY = 1
            this.matrix.scaleX = 1
            this.matrix.translateX = 50
            this.matrix.translateY = 200
            if (this.pattern) {
              this.pattern.setTransform(this.matrix)
            }
            this.context.fillRect(0, 0, 480, 720)
          })
          .width("45%")
          .margin("5px")
        Canvas(this.context)
          .width('100%')
          .height('80%')
          .backgroundColor('#FFFFFF')
          .onReady(() => {
            this.pattern = this.context.createPattern(this.img, 'no-repeat')
            this.matrix.scaleY = 0.5
            this.matrix.scaleX = 0.5
            this.matrix.translateX = 50
            this.matrix.translateY = 50
            if (this.pattern) {
              this.context.fillStyle = this.pattern
              this.pattern.setTransform(this.matrix)
            }
            this.context.fillRect(0, 0, 480, 720)
          })
      }
      .width('100%')
      .height('100%')
  }
}
```

![CanvasPattern](./figures/canvas_pattern.gif)

<!--no_check-->