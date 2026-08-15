# CanvasPattern

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=814c7cb9af37d443e12a84b71f28815df508c584 translatedAt=2026-07-30T02:31:10.934Z pushedAt=2026-08-01T06:42:55.872Z -->

The **CanvasPattern** object is created using the [createPattern](ts-components-canvas-common-method.md#createpattern) method. It generates an image-filled template by specifying an image and a repetition mode. It is suitable for scenarios where pattern filling or background textures are needed on a canvas, simplifying pattern filling implementation and improving drawing efficiency.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Methods

### setTransform

setTransform(transform?: Matrix2D): void

Applies a matrix transformation to the current **CanvasPattern** using a **Matrix2D** object as the parameter. This is suitable for scenarios where geometric transformations such as translation, scaling, and rotation need to be applied to the pattern fill. If no parameter is passed, no matrix transformation is applied to the **CanvasPattern**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type | Mandatory| Description  |
| --------- | -------------- | ------ | ---------- |
| transform | [Matrix2D](ts-components-canvas-matrix2d.md) | No | Transformation matrix used to perform geometric transformations such as translation, scaling, and rotation on the **CanvasPattern**.<br>Note: No matrix transformation is performed when the parameter is **undefined** or **null**.<br>Default value: **null** |

## Example

Create a **CanvasPattern** object via **createPattern**, set the matrix parameter in the **onReady** callback and on button click respectively, and call the **setTransform** method to apply the matrix transformation.

> **NOTE**
>
> The resources used in this example are not located in the **src** > **main** > **resource** directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the **resources** directory are not packaged by default when a project or module is created. To package these resources, go to **buildOption** > **resOptions** > **copyCodeResource** in the module's **build-profile.json5** file, and set **enable** to **true**. For details, see the description of [copyCodeResource](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348) in **resOptions**.

```ts
// xxx.ets
@Entry
@Component
struct CanvasPatternPage {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();
  // Replace "common/pattern.jpg" with the image resource file you use.
  private img: ImageBitmap = new ImageBitmap('common/pattern.jpg');
  private pattern: CanvasPattern | null = null;

  build() {
      Column() {
        Button('Click to set transform')
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
          .width('45%')
          .margin('5px')
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
