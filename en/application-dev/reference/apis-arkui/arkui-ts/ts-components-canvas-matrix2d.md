# Matrix2D

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=814c7cb9af37d443e12a84b71f28815df508c584 translatedAt=2026-07-30T02:35:05.573Z pushedAt=2026-08-01T06:42:55.882Z -->

A matrix object used for graphic transformation in [CanvasRenderingContext2D](ts-canvasrenderingcontext2d.md), [OffscreenCanvasRenderingContext2D](ts-offscreencanvasrenderingcontext2d.md), [CanvasPattern](ts-components-canvas-canvaspattern.md), and [Path2D](ts-components-canvas-path2d.md). It can perform scaling, rotation, translation, and other transformations on the matrix.

**Matrix2D** is used in the following scenarios:

1. In [CanvasRenderingContext2D](ts-canvasrenderingcontext2d.md) and [OffscreenCanvasRenderingContext2D](ts-offscreencanvasrenderingcontext2d.md), call [getTransform](ts-components-canvas-common-method.md#gettransform) to obtain the canvas graphic transformation **Matrix2D** object, and call [setTransform](ts-components-canvas-common-method.md#settransform-1) to apply the graphic transformation corresponding to the **Matrix2D** object to subsequent drawing content.

2. In [CanvasPattern](ts-components-canvas-canvaspattern.md), call [setTransform](ts-components-canvas-canvaspattern.md#settransform) to apply the graphic transformation corresponding to the **Matrix2D** object to the [CanvasPattern](ts-components-canvas-canvaspattern.md) object.

3. In [Path2D](ts-components-canvas-path2d.md), call [addPath](ts-components-canvas-path2d.md#addpath) to apply the graphic transformation corresponding to the **Matrix2D** object to the [Path2D](ts-components-canvas-path2d.md) object.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## constructor<sup>10+</sup>

constructor()

Constructs a two-dimensional transformation matrix object. The default value is a matrix whose attributes are all 0.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## constructor<sup>12+</sup>

constructor(unit: LengthMetricsUnit)

Constructs a two-dimensional transformation matrix object. The default value is a matrix whose attributes are all 0. The unit mode of the Matrix2D object can be configured.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description                             |
| ------ | -------- | ---- | ------------------------------------- |
| unit | [LengthMetricsUnit](../js-apis-arkui-graphics.md#lengthmetricsunit12) | Yes | Unit mode of the **Matrix2D** object. The configuration cannot be dynamically changed after being set. The configuration method is the same as that of [CanvasRenderingContext2D](./ts-canvasrenderingcontext2d.md).<br>Default value: **DEFAULT**<br>If the invalid values **NaN** and **Infinity** are passed in, the default value is used. |

## Attributes

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type | Read-Only | Optional | Description |
| ----- | ----- | --------------- | ------ | ------------------------ |
| scaleX         | number | No | Yes | Horizontal scale factor. The value range is unlimited. Values greater than 1 enlarge, less than 1 shrink, and negative values flip horizontally.<br>Default: **1**<br>The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting. |
| scaleY         | number | No | Yes | Vertical scale factor. The value range is unlimited. Values greater than 1 enlarge, less than 1 shrink, and negative values flip vertically.<br>Default: **1**<br>The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting. |
| rotateX       | number | No | Yes | Horizontal skew factor. The value range is unlimited.<br>Default: **0**<br>The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting. |
| rotateY       | number | No | Yes | Vertical skew factor. The value range is unlimited.<br>Default: **0**<br>The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting. |
| translateX | number | No | Yes | Horizontal translation distance. The value range is unlimited.<br>Default: **0**<br>The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.<br>Default unit: vp |
| translateY | number | No | Yes | Vertical translation distance. The value range is unlimited.<br>Default: **0**<br>The value **undefined** is treated as invalid. **NaN** and **Infinity** cause **Matrix2D** to behave abnormally, and drawn content will not be displayed after setting.<br>Default unit: vp |

> **NOTE**
>  
>  You can use the [px2vp](../arkts-apis-uicontext-uicontext.md#px2vp12) API for unit conversion.

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Parameter {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('240vp')
        .height('180vp')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(100, 20, 50, 50)
          this.matrix.scaleX = 1
          this.matrix.scaleY = 1
          this.matrix.rotateX = -0.5
          this.matrix.rotateY = 0.5
          this.matrix.translateX = 10
          this.matrix.translateY = 10
          this.context.setTransform(this.matrix)
          this.context.fillRect(100, 20, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![matrix-parameters.png](figures/matrix-parameters.png)

## identity

identity(): Matrix2D

Creates an identity matrix. It is commonly used to reset the transformation matrix, clearing all previous transformation operations so that subsequent drawing content is not affected by previous transformations.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                 | Description      |
| --------------------- | ---------- |
| Matrix2D | Identity matrix, which can be used to initialize or reset the graphics transformation state. |

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Identity {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('240vp')
        .height('180vp')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(100, 20, 50, 50)
          this.matrix = this.matrix.identity()
          this.context.setTransform(this.matrix)
          this.context.fillRect(100, 100, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![matrix-identity.png](figures/matrix-identity.png)

## invert

invert(): Matrix2D

Obtains the inverse of the current matrix. It is commonly used to undo previous transformation operations or calculate reverse transformations, enabling reverse mapping of the coordinate system.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                 | Description        |
| --------------------- | ------------ |
| Matrix2D | Inverse matrix result, which can be used for reverse transformation or to undo previous transformation operations. |

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Invert {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('240vp')
        .height('180vp')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(100, 110, 50, 50)
          this.matrix.scaleX = 1
          this.matrix.scaleY = 1
          this.matrix.rotateX = -0.5
          this.matrix.rotateY = 0.5
          this.matrix.translateX = 10
          this.matrix.translateY = 10
          this.matrix.invert()
          this.context.setTransform(this.matrix)
          this.context.fillRect(100, 110, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![matrix-invert.png](figures/matrix-invert.png)

## multiply<sup>(deprecated)</sup>

multiply(other?: Matrix2D): Matrix2D

Multiplies the current matrix by the target matrix. This API is an empty API and has no actual effect.

This API is deprecated since API version 10 and has no actual drawing effect, so no example is provided.

**Widget capability**: This API can be used in ArkTS widgets since API version 9. This API is an empty API.

**Parameters**

| Name | Type    | Mandatory|  Description  |
| ----- | -------- | ---- | ---------- |
| other | Matrix2D | No| Target matrix.<br>Invalid values **undefined** and **null** are treated as invalid inputs.<br>Default value: **null**.|

**Return value**

| Type                 | Description          |
| --------------------- | -------------- |
| Matrix2D | This API is an empty implementation, and its return value has no practical meaning. |

## rotate<sup>(deprecated)</sup>

rotate(rx?: number, ry?: number): Matrix2D

Performs a rotation operation on the current matrix. This API is an empty API and has no actual effect.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 10. You are advised to use [rotate](#rotate10) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9. This API is an empty API.

**Parameters**

| Name| Type  | Mandatory| Description                         |
| ---- | ------ | ---- | -------------------------------- |
| rx | number | No | Horizontal coordinate of the rotation point. The value range is unlimited.<br>Default unit: vp<br>The abnormal values **undefined** and **null** are processed as invalid values, and **NaN** and **Infinity** cause **Matrix2D** exceptions.<br>Default value: **0** |
| ry | number | No | Vertical coordinate of the rotation point. The value range is unlimited.<br>Default unit: vp<br>The abnormal values **undefined** and **null** are processed as invalid values, and **NaN** and **Infinity** cause **Matrix2D** exceptions.<br>Default value: **0** |

**Return value**

| Type                 | Description                |
| --------------------- | -------------------- |
| Matrix2D | Result matrix object after rotation, which can be used to perform rotation transformation on graphics. |

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Rotate {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('240vp')
        .height('180vp')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(50, 110, 50, 50)
          this.matrix.scaleX = 1
          this.matrix.scaleY = 1
          this.matrix.rotateX = -0.5
          this.matrix.rotateY = 0.5
          this.matrix.translateX = 10
          this.matrix.translateY = 10
          this.matrix.rotate(5, 5)
          this.context.setTransform(this.matrix)
          this.context.fillRect(50, 110, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![matrix-rotate.png](figures/matrix-rotate.png)

## rotate<sup>10+</sup>

rotate(degree: number, rx?: number, ry?: number): Matrix2D

Performs a left-multiply rotation operation on the current matrix, centered at the rotation point. It is commonly used in scenarios such as graphic rotation animation or image rotation processing.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| degree | number | Yes | Rotation angle (in radians). The value range is unlimited. A positive value indicates clockwise rotation. You can convert an angle to radians using `angle * Math.PI / 180` and pass it to this API.<br>Invalid values **undefined** and **null** are treated as invalid values. **NaN** and **Infinity** will cause **Matrix2D** exceptions.<br>Default unit: radians|
| rx     | number | No | Horizontal coordinate of the rotation point. The value range is not limited.<br>Default unit: vp.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default value: **0**.   |
| ry     | number | No | Vertical coordinate of the rotation point. The value range is not limited.<br>Default unit: vp.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default value: **0**.   |

**Return value**

| Type                 | Description                |
| --------------------- | -------------------- |
| Matrix2D | Resulting matrix object after rotation, which can be used to perform rotation transformation on graphics. |

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Rotate {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('240vp')
        .height('180vp')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(60, 80, 50, 50)
          this.matrix.scaleX = 1
          this.matrix.scaleY = 1
          this.matrix.rotateX = -0.5
          this.matrix.rotateY = 0.5
          this.matrix.translateX = 10
          this.matrix.translateY = 10
          this.matrix.rotate(-60 * Math.PI / 180, 5, 5)
          this.context.setTransform(this.matrix)
          this.context.fillRect(60, 80, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![matrix-rotate10+.png](figures/matrix-rotate10+.png)

## translate

translate(tx?: number, ty?: number): Matrix2D

Performs a left-multiply translation operation on the current matrix. It is commonly used in scenarios such as adjusting graphic positions, implementing displacement animations, or offsetting the canvas coordinate system.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                 |
| ---- | ------ | ---- | ---------------------------- |
| tx   | number | No  | Horizontal translation distance. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default unit: vp.<br>Default value: **0**.|
| ty   | number | No  | Vertical translation distance. The value range is not limited.<br>Invalid values **undefined** and **null** are treated as invalid inputs. **NaN** and **Infinity** values will trigger **Matrix2D** exceptions.<br>Default unit: vp.<br>Default value: **0**.|

**Return value**

| Type                 | Description                |
| --------------------- | -------------------- |
| Matrix2D | Result matrix object after translation, which can be used to perform translation transformation on graphics. |

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Translate {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('240vp')
        .height('180vp')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(40, 20, 50, 50)
          this.matrix.scaleX = 1
          this.matrix.scaleY = 1
          this.matrix.rotateX = 0
          this.matrix.rotateY = 0
          this.matrix.translateX = 0
          this.matrix.translateY = 0
          this.matrix.translate(100, 100)
          this.context.setTransform(this.matrix)
          this.context.fillRect(40, 20, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![matrix-translate.png](figures/matrix-translate.png)

## scale

scale(sx?: number, sy?: number): Matrix2D

Performs a left-multiply scaling operation on the current matrix. It is commonly used in scenarios such as graphic scaling or flipping.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory | Description               |
| ---- | ------ | ---- | ------------------ |
| sx   | number | No   | Horizontal scaling ratio coefficient. The value range is not limited. A value greater than 1 indicates magnification, less than 1 indicates reduction, and a negative value indicates horizontal flipping.<br>Abnormal values **undefined** and **null** are treated as invalid input. **NaN** and **Infinity** cause **Matrix2D** exceptions.<br>Default value: **1.0** |
| sy   | number | No   | Vertical scaling ratio coefficient. The value range is not limited. A value greater than 1 indicates magnification, less than 1 indicates reduction, and a negative value indicates vertical flipping.<br>Abnormal values **undefined** and **null** are treated as invalid input. **NaN** and **Infinity** cause **Matrix2D** exceptions.<br>Default value: **1.0** |

**Return value**

| Type                 | Description              |
| --------------------- | ------------------ |
| Matrix2D | Scaling result matrix object, which can be used to scale graphics. |

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Scale {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private matrix: Matrix2D = new Matrix2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('240vp')
        .height('180vp')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.context.fillRect(120, 70, 50, 50)
          this.matrix.scaleX = 1
          this.matrix.scaleY = 1
          this.matrix.rotateX = -0.5
          this.matrix.rotateY = 0.5
          this.matrix.translateX = 10
          this.matrix.translateY = 10
          this.matrix.scale(0.5, 0.5)
          this.context.setTransform(this.matrix)
          this.context.fillRect(120, 70, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![matrix-scale.png](figures/matrix-scale.png)
<!--no_check-->