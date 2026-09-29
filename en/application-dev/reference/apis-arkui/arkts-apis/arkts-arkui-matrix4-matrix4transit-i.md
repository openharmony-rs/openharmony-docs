# Matrix4Transit

```TypeScript
interface Matrix4Transit
```

Implements a matrix object. It supports combining multiple transformation effects by chained calls of the **translate**, **scale**, **rotate**, and **skew** APIs.

> **NOTE:** 
> 
> When multiple transformation APIs are called in chain mode, the order of transformations affects the final
> result. For example, translating first and then scaling produces a different transformation effect from scaling
> first and then translating. Select the correct call order based on the expected effect.
> 
> The **translate**, **scale**, **rotate**, **skew**, **combine**, and **invert** APIs modify the original matrix
> on which they are called. To keep the original matrix unchanged, call **copy()** before performing the
> transformation, for example, **matrix.copy().translate({x:100})**.

**Since:** 7

<!--Device-matrix4-interface Matrix4Transit--><!--Device-matrix4-interface Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## combine

```TypeScript
combine(options: Matrix4Transit): Matrix4Transit
```

Combines the effects of two matrices to generate a new matrix object. The matrix that calls this API will be changed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Matrix4Transit-combine(options: Matrix4Transit): Matrix4Transit--><!--Device-Matrix4Transit-combine(options: Matrix4Transit): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Yes | Matrix object to be combined. Its transformation effect is combined on the current matrix (matrix multiplication) to generate a new transformation matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Object after matrix combination. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().translate({ x: 200 });
  private matrix2 = matrix4.identity().scale({ x: 2 });

  build() {
    Column() {
      // Before matrix transformation
      // Replace $r("app.media.icon") with the image resource file you use.
      Image($r("app.media.icon"))
        .width('40%')
        .height(100)
        .margin({ top: 50 })
      // Translate the x-axis by 200px, and then scale it twice to obtain the resultant matrix.
      // Replace $r("app.media.icon") with the image resource file you use.
      Image($r("app.media.icon"))
        .transform(this.matrix1.copy().combine(this.matrix2))
        .width("40%")
        .height(100)
        .margin({ top: 50 })
    }
  }
}
```

## copy

```TypeScript
copy(): Matrix4Transit
```

Copies this matrix object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Matrix4Transit-copy(): Matrix4Transit--><!--Device-Matrix4Transit-copy(): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Copy object of the current matrix. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

let matrix1 = matrix4.identity().scale({ x: 1.5 });
let matrix2 = matrix1.copy().translate({ x: 200 });

@Entry
@Component
struct Test {
  imageSize: Length = '300px';

  build() {
    Column({ space: '50px' }) {
      // Replace $r("app.media.testImage") with the image resource file you use.
      Image($r("app.media.testImage"))
        .width(this.imageSize)
        .height(this.imageSize)
      // Replace $r("app.media.testImage") with the image resource file you use.
      Image($r("app.media.testImage"))
        .width(this.imageSize)
        .height(this.imageSize)
        .transform(matrix1)
      // Replace $r("app.media.testImage") with the image resource file you use.
      Image($r("app.media.testImage"))
        .width(this.imageSize)
        .height(this.imageSize)
        .transform(matrix2)
    }.alignItems(HorizontalAlign.Center)
    .height('100%').width('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

## invert

```TypeScript
invert(): Matrix4Transit
```

Inverts this matrix object. The matrix that calls this API will be changed and transformed into its inverse matrix, which is then returned. The product of the inverse matrix and the original matrix is the identity matrix.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Matrix4Transit-invert(): Matrix4Transit--><!--Device-Matrix4Transit-invert(): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Inverse matrix object of the current matrix. |

**Examples**

```TypeScript
import { matrix4 } from '@kit.ArkUI';

// The effect of matrix 1 (width scaled up by 2x) is opposite to that of matrix 2 (width scaled down by 2x).
let matrix1 = matrix4.identity().scale({ x: 2 });
let matrix2 = matrix1.copy().invert();

@Entry
@Component
struct Tests {
  build() {
    Column() {
      // Replace $r("app.media.zh") with the image resource file you use.
      Image($r("app.media.zh"))
        .width(200)
        .height(100)
        .transform(matrix1)
        .margin({ top: 100 })
      // Replace $r("app.media.zh") with the image resource file you use.
      Image($r("app.media.zh"))
        .width(200)
        .height(100)
        .margin({ top: 150 })
        .transform(matrix2)
    }
  }
}
```

## rotate

```TypeScript
rotate(options: RotateOption): Matrix4Transit
```

Rotates this matrix object along the x, y, and z axes. The matrix that calls this API will be changed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Matrix4Transit-rotate(options: RotateOption): Matrix4Transit--><!--Device-Matrix4Transit-rotate(options: RotateOption): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RotateOption](arkts-arkui-matrix4-rotateoption-i.md) | Yes | Rotation configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after the rotation. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .rotate({
      x: 1,
      y: 1,
      z: 2,
      angle: 30
    });

  build() {
    Column() {
      // Replace $r("app.media.bg1") with the image resource file you use.
      Image($r("app.media.bg1")).transform(this.matrix1)
        .width('40%')
        .height(100)
    }.width("100%").margin({ top: 50 })
  }
}
```

## scale

```TypeScript
scale(options: ScaleOption): Matrix4Transit
```

Scales this matrix object along the x, y, and z axes. The matrix that calls this API will be changed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Matrix4Transit-scale(options: ScaleOption): Matrix4Transit--><!--Device-Matrix4Transit-scale(options: ScaleOption): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ScaleOption](arkts-arkui-matrix4-scaleoption-i.md) | Yes | Scaling configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after the scaling. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .scale({
      x: 2,
      y: 3,
      z: 4,
      centerX: 50,
      centerY: 50
    });

  build() {
    Column() {
      // Replace $r("app.media.testImage") with the image resource file you use.
      Image($r("app.media.testImage")).transform(this.matrix1)
        .width('300px')
        .height("300px")
    }.width("100%").height("100%").justifyContent(FlexAlign.Center)
  }
}
```

## setPolyToPoly

```TypeScript
setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit
```

Maps the vertex coordinates of a polygon to those of another polygon. This API is applicable to scenarios requiring custom deformation, such as image perspective correction, 3D visual effects, and card flip effects.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Matrix4Transit-setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit--><!--Device-Matrix4Transit-setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PolyToPolyOptions](arkts-arkui-matrix4-polytopolyoptions-i.md) | Yes | Options for polygon mapping, which specify the mapping relationship between the source polygon vertex coordinates and the target polygon vertex coordinates. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after the mapping. |

**Examples**

```TypeScript
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private matrix1 = matrix4.identity().setPolyToPoly({
    src: [{ x: 0, y: 0 }, { x: 500, y: 0 }, { x: 0, y: 500 }, { x: 500, y: 500 }],
    dst: [{ x: 0, y: 0 }, { x: 500, y: 0 }, { x: 0, y: 500 }, { x: 750, y: 1000 }], pointCount: 4
  });

  build() {
    Stack() {
      Column().backgroundColor(Color.Blue)
        .width('500px')
        .height('500px')
      // Replace $r("app.media.transition_image1") with the image resource file you use.
      Image($r('app.media.transition_image1'))
        .scale({ centerX: 0, centerY: 0, x: 1 })
        .transform(this.matrix1)
        .width('500px')
        .height('500px')
    }.width('100%').height('100%').opacity(0.5)
  }
}
```

## skew

```TypeScript
skew(x: number, y: number): Matrix4Transit
```

Skews this matrix object along the x and y axes. The matrix that calls this API will be changed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Matrix4Transit-skew(x: number, y: number): Matrix4Transit--><!--Device-Matrix4Transit-skew(x: number, y: number): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Skew on the x-axis. The value is the shear factor (that is, the tan value).<br>The value **0** indicates no skew, a positive value indicates the skew along the positive direction of the x-axis, and a negative value indicates the skew along the negative direction of the x-axis. |
| y | number | Yes | Skew on the y-axis. The value is the shear factor (that is, the tan value).<br>The value **0** indicates no skew, a positive value indicates the skew along the positive direction of the y-axis, and a negative value indicates the skew along the negative direction of the y-axis. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after the skewing. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().skew(2, 3);

  build() {
    Column() {
      // Replace $r("app.media.bg1") with the image resource file you use.
      Image($r("app.media.bg1")).transform(this.matrix1)
        .height(100)
        .margin({
          top: 300
        })
    }
    .width('100%')
    .height("100%")
  }
}
```

## transformPoint

```TypeScript
transformPoint(options: [number, number]): [number, number]
```

Applies the current transformation effect to a coordinate point.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Matrix4Transit-transformPoint(options: [number, number]): [number, number]--><!--Device-Matrix4Transit-transformPoint(options: [number, number]): [number, number]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [number, number] | Yes | Coordinate point to be transformed, in the format of [x, y], where **x** is the horizontal coordinate and **y** is the vertical coordinate, in px. |

**Return value:**

| Type | Description |
| --- | --- |
| [number, number] | Coordinate point after matrix transformation, in the format of [x, y]. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private originPoint: number[] = [50, 50];
  private matrix1 = matrix4.identity().translate({ x: 150, y: -50 });
  private transformPoint = this.matrix1.transformPoint([this.originPoint[0], this.originPoint[1]]);
  private matrix2 = matrix4.identity().translate({ x: this.transformPoint[0], y: this.transformPoint[1] });

  build() {
    Column() {
      Text(`Coordinates before matrix transformation: [${this.originPoint}]`)
        .fontSize(16)
      // Replace $r("app.media.image") with the image resource file you use.
      Image($r("app.media.image"))
        .width('600px')
        .height('300px')
        .margin({ top: 50 })
      Text(`Coordinates after matrix transformation: [${this.transformPoint}]`)
        .fontSize(16)
        .margin({ top: 100 })
      // Replace $r("app.media.image") with the image resource file you use.
      Image($r("app.media.image"))
        .width('600px')
        .height('300px')
        .margin({ top: 50 })
        .transform(this.matrix2)
    }.width('100%').padding(50)
  }
}
```

## translate

```TypeScript
translate(options: TranslateOption): Matrix4Transit
```

Translates this matrix object along the x, y, and z axes. The matrix that calls this API will be changed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Matrix4Transit-translate(options: TranslateOption): Matrix4Transit--><!--Device-Matrix4Transit-translate(options: TranslateOption): Matrix4Transit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TranslateOption](arkts-arkui-matrix4-translateoption-i.md) | Yes | Translation configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| [Matrix4Transit](arkts-arkui-matrix4-matrix4transit-i.md) | Matrix object after the translation. |

**Examples**

```TypeScript
// xxx.ets
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity().translate({ x: 100, y: 200, z: 30 });

  build() {
    Column() {
      // Replace $r("app.media.bg1") with the image resource file you use.
      Image($r("app.media.bg1")).transform(this.matrix1)
        .width('40%')
        .height(100)
    }
  }
}
```
