# ImageData
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=236b1482bf31e926fd91d5f29276a56a58780a2f translatedAt=2026-06-22T07:52:04.618Z pushedAt=2026-06-23T02:29:07.650Z -->

>  **NOTE**
>
>  This component is supported since API version 4. Updates will be marked with a superscript to indicate their earliest API version.

The **ImageData** object is an object that stores pixel data rendered on a [canvas](js-components-canvas-canvas.md).


## Attributes

| Name    | Type                       | Description                          |
| ------ | ------------------------- | ---------------------------- |
| width  | number                    | Actual width of the rectangle on the canvas, in pixels.                 |
| height | number                    | Actual height of the rectangle on the canvas, in pixels.                 |
| data   | &lt;Uint8ClampedArray&gt; | A one-dimensional array of color values. The values range from 0 to 255.|


## Example

```html
<!-- xxx.hml -->
<div>
  <canvas ref="canvas" style="width: 500px; height: 500px; background-color: #ffff00;"></canvas>
</div>
```

```js
// xxx.js
import promptAction from '@ohos.promptAction';
export default {
  onShow() {
    const el =this.$refs.canvas;
    const ctx = el.getContext('2d');
    ctx.fillRect(0,0,200,200);
    var imageData = ctx.createImageData(1,1);
    promptAction.showToast({
      message:imageData,
      duration:5000
    })
  }
}
```