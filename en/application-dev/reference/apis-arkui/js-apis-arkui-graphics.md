# Graphics
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sunbees-->
<!--Designer: @sunbees-->
<!--Tester: @khq-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=033859cddd4818ba4c62bad26b6ee850b2b31a63 translatedAt=2026-08-29T09:37:03.025Z pushedAt=2026-08-31T11:48:54.203Z -->

Defines the graphics attributes of custom nodes (RenderNode), including geometric transformations (scaling, rotation, and translation), unified representation of colors and lengths, shapes, graphics masking and clipping, and blur effects. It is suitable for scenarios that require refined graphics drawing and visual effect processing on custom nodes.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { DrawContext, Size, Offset, Position, Pivot, Scale, Translation, Matrix4, Rotation, Frame, LengthMetricsUnit } from '@kit.ArkUI';
```

## Size

Returns the width and height of the component. The default unit is vp, but APIs that use the Size type may specify a different unit, in which case the unit specified by the API takes precedence.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type  | Read-Only| Optional| Description                  |
| ------ | ------ | ---- | ---- | ---------------------- |
| width  | number | No   | No   | Width of the component.<br>Unit: vp<br>Value range: [0, +∞)<br>A negative value is treated as the default value. |
| height | number | No   | No   | Height of the component.<br>Unit: vp<br>Value range: [0, +∞)<br>A negative value is treated as the default value. |

## Position

type Position = Vector2

Sets or returns the position of the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type               | Description                               |
| ------------------- | ----------------------------------- |
| [Vector2](#vector2) | Vector containing two values: x and y.<br>Unit: vp |

## PositionT\<T><sup>12+</sup>

type PositionT\<T> = Vector2T\<T>

Sets or returns the position of the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                        | Description                               |
| ---------------------------- | ----------------------------------- |
| [Vector2T\<T>](#vector2tt12) | Vector containing two values: x and y.<br>Unit: vp |

## Frame

Sets or returns the layout size and position of the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type  | Read-Only| Optional| Description                       |
| ------ | ------ | ---- | ---- | --------------------------- |
| x      | number | No   | No   | Horizontal position.<br>Unit: vp<br>Value range: (-∞, +∞) |
| y      | number | No   | No   | Vertical position.<br>Unit: vp<br>Value range: (-∞, +∞) |
| width  | number | No   | No   | Width of the component.<br>Unit: vp<br>Value range: [0, +∞)<br>A negative value is treated as the default value.   |
| height | number | No   | No   | Height of the component.<br>Unit: vp<br>Value range: [0, +∞)<br>A negative value is treated as the default value.   |

## Pivot

type Pivot = Vector2

Sets the pivot of the component. As the rotation or scaling center of the component, the pivot affects the rotation and scaling effects.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type               | Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| [Vector2](#vector2) | X and Y coordinates of the pivot. This parameter is a floating point number. The default value is **0.5**, and the value range is [0.0, 1.0]. A value out of range is treated as the default value **0.5**. |

## Scale

type Scale = Vector2

Sets the scale factor of the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type               | Description                                           |
| ------------------- | ----------------------------------------------- |
| [Vector2](#vector2) | Scale factor along the x- and y-axis. The value is a floating point number, and the default value is **1.0**.|

## Translation

type Translation = Vector2

Sets the translation amount of the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type               | Description                         |
| ------------------- | ----------------------------- |
| [Vector2](#vector2) | Translation amount along the x- and y-axis.<br>Unit: px |

## Rotation

type Rotation = Vector3

Sets the rotation angle of the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| [Vector3](#vector3) | Rotation angles around the x-, y-, and z-axis.<br>Unit: degree |

## Offset

type Offset = Vector2

Sets the offset of the component or effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type               | Description                             |
| ------------------- | --------------------------------- |
| [Vector2](#vector2) | Offset along the x- and y-axis.<br>Unit: vp |

## Matrix4

type Matrix4 = [number,number,number,number,number,number,number,number,number,number,number,number,number,number,number,number]

Sets a 4 x 4 matrix.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                                                        | Description                                |
| ------------------------------------------------------------ | ------------------------------------ |
| [number,number,number,number,<br>number,number,number,number,<br>number,number,number,number,<br>number,number,number,number] | 16-element array representing a 4 x 4 matrix.<br>Value range of each number: (-∞, +∞) |

This type is a 4 x 4 matrix represented by `number[]` of length 16, which is used to set transformation information for components. The following is an example:
```ts
const transform: Matrix4 = [
  1, 0, 45, 0,
  0, 1,  0, 0,
  0, 0,  1, 0,
  0, 0,  0, 1
];
```

## Vector2

Defines a vector that contains the x and y coordinate values.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type  | Read-Only| Optional| Description             |
| ---- | ------ | ---- | ---- | ----------------- |
| x    | number | No   | No   | Value of the vector along the x-axis.<br>Value range: (-∞, +∞) |
| y    | number | No   | No   | Value of the vector along the y-axis.<br>Value range: (-∞, +∞) |

## Vector3

Represents a vector including three values: x, y, and z.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type   | Read-Only | Optional | Description                |
| ---- | ------ | ---- | ---- | ------------------- |
| x    | number | No   | No   | Value of the vector along the x-axis.<br>Value range: (-∞, +∞) |
| y    | number | No   | No   | Value of the vector along the y-axis.<br>Value range: (-∞, +∞) |
| z    | number | No   | No   | Value of the vector along the z-axis.<br>Value range: (-∞, +∞) |

## Vector4

Defines a vector that contains the x, y, z, and w coordinate values.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type  | Read-Only| Optional| Description    |
| ---- | ------ | ---- | ---- | -------- |
| x    | number | No  | No   | Value of the vector along the x-axis.<br>Value range: (-∞, +∞) |
| y    | number | No  | No   | Value of the vector along the y-axis.<br>Value range: (-∞, +∞) |
| z    | number | No  | No   | Value of the vector along the z-axis.<br>Value range: (-∞, +∞) |
| w    | number | No  | No   | Value of the vector along the w-axis.<br>Value range: (-∞, +∞) |

## Vector2T\<T><sup>12+</sup>

Represents a vector of the T type that contains two values: x and y.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type  | Read-Only| Optional| Description             |
| ---- | ------ | ---- | ---- | ----------------- |
| x    | T | No | No | X coordinate value of the vector.|
| y    | T | No | No | Y coordinate value of the vector.|

## DrawContext

Graphics drawing context, which provides the canvas used for drawing and its width and height.

### size

get size(): Size

Obtains the width and height of the canvas.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [Size](#size) | Width and height of the canvas.|

### sizeInPixel<sup>12+</sup>

get sizeInPixel(): Size

Obtains the width and height of the canvas in px.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [Size](#size) | Width and height of the canvas, in px.|

### canvas

get canvas(): drawing.Canvas

Obtains the canvas used for drawing.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [drawing.Canvas](../apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md) | Canvas for drawing.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, DrawContext } from '@kit.ArkUI';

class MyRenderNode extends RenderNode {

  draw(context: DrawContext) {
    const size = context.size;
    const canvas = context.canvas;
    const sizeInPixel = context.sizeInPixel;
  }
}

const renderNode = new MyRenderNode();
renderNode.frame = { x: 0, y: 0, width: 100, height: 100 };
renderNode.backgroundColor = 0xff519db4;

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```
![](figures/canvas_demo.png)

## Edges\<T><sup>12+</sup>

Describes the edges.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type| Read-Only| Optional| Description            |
| ------ | ---- | ---- | ---- | ---------------- |
| left   | T    | No  | No  | Left edge.|
| top    | T    | No  | No  | Top edge.|
| right  | T    | No  | No  | Right edge.|
| bottom | T    | No  | No  | Bottom edge.|

## LengthUnit<sup>12+</sup>

Enumerates length units.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| PX | 0 | Length type used to describe the length in units of px. |
| VP | 1 | Length type used to describe the length in units of vp. |
| FP | 2 | Length type used to describe the length in units of fp. |
| PERCENT | 3 | Length type used to describe the length in units of %. |
| LPX | 4 | Length type used to describe the length in units of lpx. |

## SizeT\<T><sup>12+</sup>

Sets the width and height attributes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type| Read-Only| Optional| Description            |
| ------ | ---- | ---- | ---- | ---------------- |
| width   | T    | No  | No  | Width.|
| height    | T    | No  | No  | Height.|

## LengthMetricsUnit<sup>12+</sup>

Enumerates length units.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| DEFAULT | 0 | Length type, used to describe the length in units of the default vp. |
| PX | 1 | Length type, used to describe the length in units of px. |

## LengthMetrics<sup>12+</sup>

Defines the length attribute. When the length unit is PERCENT, the value **1** indicates 100%.

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type| Read-Only| Optional| Description            |
| ------------ | ---------------------------------------- | ---- | ---- | ------ |
| value       | number | No   | No   | Value of the length property.<br>Value range: (-∞, +∞).<br>When **unit** is set to **PERCENT**, **value** indicates a percentage (1 indicates 100%), and the reference size depends on the specific usage scenario; for other units, **value** indicates the absolute length in the corresponding unit. |
| unit | [LengthUnit](#lengthunit12)                                   | No  | No  | Unit of the length property. The default value is VP.|

### constructor<sup>12+</sup>

constructor(value: number, unit?: LengthUnit)

A constructor used to create a **LengthMetrics** instance. If the **unit** parameter is omitted or explicitly set to **undefined**, the default unit VP is used. If it is set to a value that is not of the LengthUnit type, the default value 0 VP is used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | number | Yes   | Value of the length property.<br>Value range: (-∞, +∞) |
| unit   | [LengthUnit](#lengthunit12) | No   | Unit of the length property. The default value is vp. |

### px<sup>12+</sup>

static px(value: number): LengthMetrics

Creates a length property in px.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | number | Yes   | Value of the length property.<br>Value range: (-∞, +∞) |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [LengthMetrics](#lengthmetrics12) | Length property object in units of px. |

### vp<sup>12+</sup>

static vp(value: number): LengthMetrics

Creates a length property in vp.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | number | Yes   | Value of the length property.<br>Value range: (-∞, +∞) |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [LengthMetrics](#lengthmetrics12) | Length property object in units of vp. |

### fp<sup>12+</sup>

static fp(value: number): LengthMetrics

Creates a length property in fp.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | number | Yes   | Value of the length property.<br>Value range: (-∞, +∞) |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [LengthMetrics](#lengthmetrics12) | Length property object in units of fp. |

### percent<sup>12+</sup>

static percent(value: number): LengthMetrics

Creates a length property in percent. The value **1** indicates 100%.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | number | Yes   | Value of the length property.<br>Value range: [0, 1]<br>A value out of range is treated as a boundary value. |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [LengthMetrics](#lengthmetrics12) | Length property object in units of percentage, where a value of **1** indicates 100%. |

### lpx<sup>12+</sup>

static lpx(value: number): LengthMetrics

Creates a length property in lpx.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | number | Yes   | Value of the length property.<br>Value range: (-∞, +∞) |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [LengthMetrics](#lengthmetrics12) | Length property object in units of lpx. |

### resource<sup>12+</sup>

static resource(value: Resource): LengthMetrics

Represents the length of a resource of the Resource type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | [Resource](arkui-ts/ts-types.md#resource) | Yes   | Value of the length property. |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [LengthMetrics](#lengthmetrics12) | Length property object of a Resource-type resource. |

**Example**

Use LengthMetrics to set the padding and margin attributes of Row.
```ts
import { LengthMetrics, LengthUnit } from '@kit.ArkUI';

@Entry
@Component
struct SizeExample {
  build() {
    Column({ space: 10 }) {
      Text('margin and padding:')
        .fontSize(12)
        .fontColor(0xCCCCCC)
        .width('90%')
      Row() {
        Row() {
          Row()
            .size({ width: '100%', height: '100%' })
            .backgroundColor('#ffd5d5d5')
        }
        .width(80)
        .height(80)
        .padding({
          top: new LengthMetrics(20, LengthUnit.VP),
          bottom: LengthMetrics.px(15),
          start: LengthMetrics.vp(10),
          end: LengthMetrics.fp(20)
        })
        .margin({
          top: LengthMetrics.percent(0.1),
          bottom: LengthMetrics.lpx(20),
          start: LengthMetrics.resource($r('app.float.row_margin_start')),
          end: LengthMetrics.vp(10)
        })
        .backgroundColor(Color.White)
      }
      .backgroundColor('#ff2787d9')
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```
![image](figures/lengthMetricsDemo.png)

### autoRefresh

autoRefresh?(value: boolean): LengthMetrics

Sets whether the **LengthMetrics** object automatically updates with system configuration changes.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
|-------|------|------|------|
| value | boolean | Yes| Whether the **LengthMetrics** object constructed using [resource](#resource12) automatically refreshes the value when the system configuration changes.<br>**true**: The object proactively listens to the system configuration changes, and refreshes the value to the resource value corresponding to the configuration when the configuration changes.<br>**false**: The object does not proactively listen to the system configuration changes.|

**Return value**

| Type| Description|
|------|------|
| [LengthMetrics](#lengthmetrics12) | **LengthMetrics** object after the auto-refresh property is set. |

**Example**

```ts
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State lengthMetrics: LengthMetrics = LengthMetrics.resource($r('sys.float.ohos_id_button_min_width')).autoRefresh!(true);

  build() {
    Column() {
      Button('Test LengthMetrics')
        .padding({ top: this.lengthMetrics })
    }
  }
}
```

## ColorMetrics<sup>12+</sup>

Provides a unified representation and encapsulation of colors. It supports color mixing as well as obtaining the color components in the R, G, B, and Alpha channels.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### numeric<sup>12+</sup>

static numeric(value: number): ColorMetrics

Instantiates the **ColorMetrics** class using a color in HEX format.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| value   | number | Yes   | Color in HEX format. RGB and ARGB color values are supported.<br>Value range: [0, 0xffffffff]<br>A value out of range is treated as a boundary value. |

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics12) | Color object corresponding to a color in HEX format. |

### rgba<sup>12+</sup>

static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the **ColorMetrics** class using colors in RGB or RGBA format.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| red   | number | Yes  | Red component of the color. The value is an integer ranging from 0 to 255. A value out of range is treated as a boundary value. |
| green | number | Yes  | Green component of the color. The value is an integer ranging from 0 to 255. A value out of range is treated as a boundary value. |
| blue  | number | Yes  | Blue component of the color. The value is an integer ranging from 0 to 255. A value out of range is treated as a boundary value. |
| alpha | number | No  | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1.0. The default value is 1.0 (fully opaque).<br> **Note:** If alpha is less than 0, the color is fully transparent. If alpha is greater than 1, the color is opaque.|

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics12) | Color object corresponding to the color in RGB or RGBA format. |

### colorWithSpace<sup>20+</sup>

static colorWithSpace(colorSpace: ColorSpace, red: number, green: number, blue: number, alpha?: number): ColorMetrics

Instantiates the **ColorMetrics** class using [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) and RGBA colorS. Only the red, green, and blue attributes support color configuration in the display-p3 color space, and the alpha attribute is not affected by the color space.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| colorSpace   | [ColorSpace](./arkui-ts/ts-appendix-enums.md#colorspace20) | Yes   | Color space. To use ColorSpace.DISPLAY_P3, call [setWindowColorSpace](./arkts-apis-window-Window.md#setwindowcolorspace9-1) on the corresponding window to set the current window to wide color gamut mode. |
| red   | number | Yes   | Red component of the color. The value is a floating point number ranging from 0 to 1. A value out of range is treated as a boundary value. |
| green | number | Yes   | Green component of the color. The value is a floating point number ranging from 0 to 1. A value out of range is treated as a boundary value. |
| blue  | number | Yes   | Blue component of the color. The value is a floating point number ranging from 0 to 1. A value out of range is treated as a boundary value. |
| alpha | number | No   | Alpha component of the color. The value is a floating point number ranging from 0.0 to 1.0. The default value is 1.0 (fully opaque).<br> **Note:** If alpha is less than 0, the color is fully transparent. If alpha is greater than 1, the color is opaque.|

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics12) | color object corresponding to a color in RGBA format in the specified color space.|

### resourceColor<sup>12+</sup>

static resourceColor(color: ResourceColor): ColorMetrics

Instantiates the **ColorMetrics** class using a color in Resource format.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| color | [ResourceColor](arkui-ts/ts-types.md#resourcecolor) | Yes| Color in Resource format.|

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics12) | Color object corresponding to the color in Resource format. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [System Resource Error Codes](errorcode-system-resource.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401   | Parameter error. Possible cause:1.The type of the input color parameter is not ResourceColor;2.The format of the input color string is not RGB or RGBA.             |
| 180003   | Failed to obtain the color resource.         |

### blendColor<sup>12+</sup>

blendColor(overlayColor: ColorMetrics): ColorMetrics

Blends a specified color (**overlayColor**) with the current color and returns the resulting color.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| overlayColor | [ColorMetrics](#colormetrics12) | Yes| Color to overlay. The alpha value determines the blending strength: **1.0** indicates complete opacity (fully covers the base color), and **0.0** indicates complete transparency (returns the original color).|

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| [ColorMetrics](#colormetrics12) |  New color object with red, green, blue, and alpha channels representing the blended result of the current color and overlay color.|

**Blending formula**:

The resulting alpha is fully opaque. The RGB values are calculated using the following formula:

result_rgb = overlay_rgb*(overlay_alpha) + (1 - overlay_alpha) * base_rgb

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401   | Parameter error. The type of the input parameter is not ColorMetrics.                |

### color<sup>12+</sup>

get color(): string

Obtains the color of **ColorMetrics**. The return value is a string indicating an RGBA color value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| string | String indicating an RGBA color value. Example: **'rgba(255, 100, 255, 0.5)'**|

### red<sup>12+</sup>

get red(): number

Obtains the red component of the ColorMetrics color.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Red component of the color. The value is an integer ranging from 0 to 255.|

### green<sup>12+</sup>

get green(): number

Obtains the green component of the ColorMetrics color.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Green component of the color. The value is an integer ranging from 0 to 255.|

### blue<sup>12+</sup>

get blue(): number

Obtains the blue component of the ColorMetrics color.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Blue component of the color. The value is an integer ranging from 0 to 255.|

### alpha<sup>12+</sup>

get alpha(): number

Obtains the alpha component of the ColorMetrics color.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type         | Description            |
| ------------- | ---------------- |
| number | Alpha component (opacity) of the color, which is an integer ranging from 0 to 255. When set through the **rgba()** or **colorWithSpace()** API, the alpha value ranges from 0.0 to 1.0 as a floating point number, and is internally converted to an integer ranging from 0 to 255 for storage. |

**Example**

```ts
import { ColorMetrics } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

function getBlendColor(baseColor: ResourceColor): ColorMetrics {
  let sourceColor: ColorMetrics;
  try {
    // When resourceColor and blendColor of ColorMetrics are used, add exception handling.
    // Error codes 401 and 180003 of the ArkUI subsystem may be returned.
    // 61 157 180
    sourceColor = ColorMetrics.resourceColor(baseColor).blendColor(ColorMetrics.resourceColor('#083d9db4'));
    console.info(`current color is ${sourceColor.color} r:${sourceColor.red} g:${sourceColor.green} b:${sourceColor.blue} a :${sourceColor.alpha}`);
  } catch (error) {
    console.error(`getBlendColor failed. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
    sourceColor = ColorMetrics.resourceColor('#19000000');
  }
  return sourceColor;
}

@Entry
@Component
struct ColorMetricsSample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('ColorMetrics blendColor')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(getBlendColor('#ff3d9db4').color)
        .margin(10)
      Button('ColorMetrics numeric')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(ColorMetrics.numeric(0xff707070).color)
        .margin(10)
      Button('ColorMetrics rgba')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(ColorMetrics.rgba(0, 74, 175, 1.0).color)
        .margin(10)
      Button('ColorMetrics colorWithSpace')
        .width('80%')
        .align(Alignment.Center)
        .height(50)
        .backgroundColor(ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.4392, 0.4392, 0.4392).color)
        .margin(10)
    }
    .width('100%')
    .height('100%')
  }
}
```
![image](figures/colorMetricsDemo.png)

### autoRefresh

autoRefresh?(value: boolean): ColorMetrics

Sets whether the **ColorMetrics** object automatically updates with system configuration changes.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
|-------|------|------|------|
| value | boolean | Yes| Whether the **ColorMetrics** object constructed using [resourceColor](#resourcecolor12) automatically refreshes the color value when the system configuration changes.<br>**true**: The object proactively listens to the system configuration changes, and refreshes the value to the resource value corresponding to the configuration when the configuration changes.<br>**false**: The object does not proactively listen to the system configuration changes.|

**Return value**

| Type| Description|
|------|------|
| [ColorMetrics](#colormetrics12) | **ColorMetrics** object after the auto-refresh property is set. |

**Example**

```ts
import { ColorMetrics } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State colorMetrics: ColorMetrics = ColorMetrics.resourceColor($r('sys.color.font_primary')).autoRefresh!(true);

  build() {
    Column() {
      Text('Test ColorMetrics')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(this.colorMetrics)
  }
}
```

## Corners\<T><sup>12+</sup>

Describes the four corners.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type| Read-Only| Optional| Description                  |
| ----------- | ---- | ---- | ---- | ---------------------- |
| topLeft     | T    | No  | No  | Radius of the upper left corner.  |
| topRight    | T    | No  | No  | Radius of the upper right corner.|
| bottomLeft  | T    | No  | No  | Radius of the lower left corner.  |
| bottomRight | T    | No  | No  | Radius of the lower right corner.  |

## CornerRadius<sup>12+</sup>

type CornerRadius = Corners\<Vector2>

Sets the semi-axis lengths for the x-axis and y-axis of the rounded corners.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                                        | Description              |
| -------------------------------------------- | ------------------ |
| [Corners](#cornerst12)\<[Vector2](#vector2)> | Semi-axis lengths of the four corners along the x- and y-axis.<br>Unit: px |

## BorderRadiuses<sup>12+</sup>

type BorderRadiuses = Corners\<number>

Sets the uniform radius of the four corners.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                           | Description              |
| ------------------------------- | ------------------ |
| [Corners](#cornerst12)\<number> | Corner radius of the four corners.<br>Unit: vp |

## Rect<sup>12+</sup>

type Rect = common2D.Rect

Describes a rectangle.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                                                        | Description      |
| ------------------------------------------------------------ | ---------- |
| [common2D.Rect](../apis-arkgraphics2d/js-apis-graphics-common2D.md#rect) | Rectangle.|

## RoundRect<sup>12+</sup>

Describes a rectangle with rounded corners.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                         | Read-Only| Optional| Description            |
| ------- | ----------------------------- | ---- | ---- | ---------------- |
| rect    | [Rect](#rect12)                 | No  | No  | Attributes of the rectangle.|
| corners | [CornerRadius](#cornerradius12) | No  | No  | Attributes of rounded corners.|

## Circle<sup>12+</sup>

Describes a circle.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type  | Read-Only| Optional| Description                     |
| ------- | ------ | ---- | ---- | ------------------------- |
| centerX | number | No  | No  | X-coordinate of the center of the circle, in px.<br>Value range: (-∞, +∞) |
| centerY | number | No  | No  | Y-coordinate of the center of the circle, in px.<br>Value range: (-∞, +∞) |
| radius  | number | No  | No  | Radius of the circle, in px.<br>Value range: [0, +∞)<br>A negative value is treated as the default value.  |

## CommandPath<sup>12+</sup>

Describes the command for drawing a path.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                                        | Type  | Read-Only| Optional| Description                                                        |
| ------------------------------------------------------------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| [commands](./arkui-ts/ts-drawing-components-path.md#commands) | string | No   | No   | Commands for drawing a path. For details about how to convert pixel units, see [Pixel Units](./arkui-ts/ts-pixel-units.md).<br>Unit: px |

## ShapeMask<sup>12+</sup>

Sets a graphics mask, which supports multiple shapes such as rectangles, rounded rectangles, circles, ellipses, and custom paths. It can be applied to a RenderNode to implement a shape mask effect.

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type   | Read-Only| Optional| Description                                               |
| --------------- | ------ | ---- | ---- | -------------------------------------------------- |
| fillColor       | number | No   | No   | Fill color of the mask, in ARGB format. Default value: `0XFF000000`.<br>Value range: [0, 0xffffffff]<br>A value out of range is treated as the default value.<br> A color containing only transparency is generated based on the transparency and brightness of **fillColor**. The higher the brightness, the more transparent the color. Then, the color is blended with the color of the RenderNode itself using [BlendMode.SRC_IN](../apis-arkgraphics2d/arkts-apis-graphics-drawing-e.md#blendmode) to generate the final color. |
| strokeColor     | number | No   | No   | Stroke color for the mask, in ARGB format. Default value: `0XFF000000`.<br>Value range: [0, 0xffffffff]<br>A value out of range is treated as the default value.<br>  A color containing only transparency is generated based on the transparency and brightness of **strokeColor**. The higher the brightness, the more transparent the color. Then, the color is blended with the color of the RenderNode itself using [BlendMode.SRC_IN](../apis-arkgraphics2d/arkts-apis-graphics-drawing-e.md#blendmode) to generate the final color. |
| strokeWidth     | number | No   | No   | Stroke width for the mask, in px. Default value: **0**.<br>Value range: [0, +∞)<br>A negative value is treated as the default value.   |

### constructor<sup>12+</sup>

constructor()

A constructor used to create a **ShapeMask** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### setRectShape<sup>12+</sup>

setRectShape(rect: Rect): void

Sets a rectangle mask.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| rect   | [Rect](#rect12) | Yes  | Shape of the rectangle.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeMask } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const mask = new ShapeMask();
    mask.setRectShape({
      left: 0,
      right: uiContext.vp2px(150),
      top: 0,
      bottom: uiContext.vp2px(150)
    });
    mask.fillColor = 0X55FF0000;

    const renderNode = new RenderNode();
    renderNode.frame = {
      x: 0,
      y: 0,
      width: 150,
      height: 150
    };
    renderNode.backgroundColor = 0XFF00FF00;
    renderNode.shapeMask = mask;

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```
![](figures/setRectShape_demo.png)

### setRoundRectShape<sup>12+</sup>

setRoundRectShape(roundRect: RoundRect): void

Sets the mask in the shape of a rectangle with rounded corners.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                   | Mandatory| Description            |
| --------- | ----------------------- | ---- | ---------------- |
| roundRect | [RoundRect](#roundrect12) | Yes  | Shape of the rectangle with rounded corners.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeMask, RoundRect } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const mask = new ShapeMask();
    const roundRect: RoundRect = {
      rect: { left: 0, top: 0, right: uiContext.vp2px(150), bottom: uiContext.vp2px(150) },
      corners: {
        topLeft: { x: 32, y: 32 },
        topRight: { x: 32, y: 32 },
        bottomLeft: { x: 32, y: 32 },
        bottomRight: { x: 32, y: 32 }
      }
    };
    mask.setRoundRectShape(roundRect);
    mask.fillColor = 0X55FF0000;

    const renderNode = new RenderNode();
    renderNode.frame = { x: 0, y: 0, width: 150, height: 150 };
    renderNode.backgroundColor = 0XFF00FF00;
    renderNode.shapeMask = mask;

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```
![](figures/setRoundRectShape_demo.png)

### setCircleShape<sup>12+</sup>

setCircleShape(circle: Circle): void

Sets a round mask.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type             | Mandatory| Description        |
| ------ | ----------------- | ---- | ------------ |
| circle | [Circle](#circle12) | Yes  | Round shape.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeMask } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const mask = new ShapeMask();
    mask.setCircleShape({ centerY: uiContext.vp2px(75), centerX: uiContext.vp2px(75), radius: uiContext.vp2px(75) });
    mask.fillColor = 0X55FF0000;

    const renderNode = new RenderNode();
    renderNode.frame = {
      x: 0,
      y: 0,
      width: 150,
      height: 150
    };
    renderNode.backgroundColor = 0XFF00FF00;
    renderNode.shapeMask = mask;

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```
![](figures/setCircleShape_demo.png)

### setOvalShape<sup>12+</sup>

setOvalShape(oval: Rect): void

Sets an oval mask.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description          |
| ------ | ------------- | ---- | -------------- |
| oval   | [Rect](#rect12) | Yes  | Oval shape.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeMask } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const mask = new ShapeMask();
    mask.setOvalShape({ left: 0, right: uiContext.vp2px(150), top: 0, bottom: uiContext.vp2px(100) });
    mask.fillColor = 0X55FF0000;

    const renderNode = new RenderNode();
    renderNode.frame = { x: 0, y: 0, width: 150, height: 150 };
    renderNode.backgroundColor = 0XFF00FF00;
    renderNode.shapeMask = mask;

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```
![](figures/setOvalShape_demo.png)

### setCommandPath<sup>12+</sup>

setCommandPath(path: CommandPath): void

Sets the command for drawing a path.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                       | Mandatory| Description          |
| ------ | --------------------------- | ---- | -------------- |
| path   | [CommandPath](#commandpath12) | Yes  | Command for drawing a path.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeMask } from '@kit.ArkUI';

const mask = new ShapeMask();
mask.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });
mask.fillColor = 0X55FF0000;

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0XFF00FF00;
renderNode.shapeMask = mask;


class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```
![](figures/setCommandPath_demo.png)

## ShapeClip<sup>12+</sup>

Sets graphics clipping, which supports multiple shapes such as rectangles, rounded rectangles, circles, ellipses, and custom paths. It can clip a RenderNode by shape so that only the content within the clipping area is displayed.

### constructor<sup>12+</sup>

constructor()

A constructor used to create a **ShapeClip** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### setRectShape<sup>12+</sup>

setRectShape(rect: Rect): void

Sets a rectangle for shape clipping.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description        |
| ------ | ------------- | ---- | ------------ |
| rect   | [Rect](#rect12) | Yes  | Shape of the rectangle.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeClip } from '@kit.ArkUI';

const clip = new ShapeClip();
clip.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0xff519db4;
renderNode.shapeClip = clip;
const shapeClip = renderNode.shapeClip;

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .margin({ bottom: 20 })
      Button('setRectShape')
        .onClick(() => {
          shapeClip.setRectShape({
            left: 0,
            right: 150,
            top: 0,
            bottom: 150
          });
          renderNode.shapeClip = shapeClip;
        })
    }.margin(20)
  }
}
```
![](figures/setRectShape_demo2.gif)

### setRoundRectShape<sup>12+</sup>

setRoundRectShape(roundRect: RoundRect): void

Sets a rounded rectangle for shape clipping.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                   | Mandatory| Description            |
| --------- | ----------------------- | ---- | ---------------- |
| roundRect | [RoundRect](#roundrect12) | Yes  | Shape of the rectangle with rounded corners.|

**Example**
```ts
import { RenderNode, FrameNode, NodeController, ShapeClip } from '@kit.ArkUI';

const clip = new ShapeClip();
clip.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0XFF00FF00;
renderNode.shapeClip = clip;

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
      Button('setRoundRectShape')
        .onClick(() => {
          renderNode.shapeClip.setRoundRectShape({
            rect: {
              left: 0,
              top: 0,
              right: this.getUIContext().vp2px(150),
              bottom: this.getUIContext().vp2px(150)
            },
            corners: {
              topLeft: { x: 32, y: 32 },
              topRight: { x: 32, y: 32 },
              bottomLeft: { x: 32, y: 32 },
              bottomRight: { x: 32, y: 32 }
            }
          });
        })
    }
  }
}
```

### setCircleShape<sup>12+</sup>

setCircleShape(circle: Circle): void

Sets a circle for shape clipping.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type             | Mandatory| Description        |
| ------ | ----------------- | ---- | ------------ |
| circle | [Circle](#circle12) | Yes  | Round shape.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeClip } from '@kit.ArkUI';

const clip = new ShapeClip();
clip.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0XFF00FF00;
renderNode.shapeClip = clip;

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
      Button('setCircleShape')
        .onClick(() => {
          renderNode.shapeClip.setCircleShape({ centerY: 75, centerX: 75, radius: 75 });

        })
    }
  }
}
```

### setOvalShape<sup>12+</sup>

setOvalShape(oval: Rect): void

Sets an oval shape for shape clipping.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type         | Mandatory| Description          |
| ------ | ------------- | ---- | -------------- |
| oval   | [Rect](#rect12) | Yes  | Oval shape.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeClip } from '@kit.ArkUI';

const clip = new ShapeClip();
clip.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0XFF00FF00;
renderNode.shapeClip = clip;

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
      Button('setOvalShape')
        .onClick(() => {
          renderNode.shapeClip.setOvalShape({
            left: 0,
            right: this.getUIContext().vp2px(150),
            top: 0,
            bottom: this.getUIContext().vp2px(100)
          });
        })
    }
  }
}
```

### setCommandPath<sup>12+</sup>

setCommandPath(path: CommandPath): void

Sets the command for drawing a path.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                       | Mandatory| Description          |
| ------ | --------------------------- | ---- | -------------- |
| path   | [CommandPath](#commandpath12) | Yes  | Command for drawing a path.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, ShapeClip } from '@kit.ArkUI';

const clip = new ShapeClip();
clip.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0XFF00FF00;
renderNode.shapeClip = clip;

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
      Button('setCommandPath')
        .onClick(() => {
          renderNode.shapeClip.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });
        })
    }
  }
}
```

## edgeColors<sup>12+</sup>

edgeColors(all: number): Edges\<number>

Generates an **edgeColors** object with the specified edge color for all edges.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| all    | number | Yes   | Edge color, in ARGB format, for example, **0xffff00ff**.<br>Value range: [0, 0xffffffff]<br>A value out of range is treated as a boundary value. |

**Return value**

| Type                    | Description                                  |
| ------------------------ | -------------------------------------- |
| [Edges](#edgest12)\<number> | **edgeColors** object whose edge colors are all at the specified value.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, edgeColors } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = { x: 0, y: 0, width: 150, height: 150 };
renderNode.backgroundColor = 0xffd5d5d5;
renderNode.borderWidth = { left: 8, top: 8, right: 8, bottom: 8 };
renderNode.borderColor = edgeColors(0xff519db4);


class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }.margin(30)
  }
}
```
![](figures/edgeColors_demo.png)

## edgeWidths<sup>12+</sup>

edgeWidths(all: number): Edges\<number>

Generates an **edgeWidths** object with the specified edge width for all edges.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| all    | number | Yes   | Edge width, in vp.<br>Value range: [0, +∞)<br>A negative value is treated as the default value. |

**Return value**

| Type                    | Description                                  |
| ------------------------ | -------------------------------------- |
| [Edges](#edgest12)\<number> | **edgeWidths** object whose edge widths are all at the specified value.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, edgeWidths } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0xffd5d5d5;
renderNode.borderWidth = edgeWidths(8);
renderNode.borderColor = {
  left: 0xff519db4,
  top: 0xff519db4,
  right: 0xff519db4,
  bottom: 0xff519db4
};


class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }.margin(30)
  }
}
```
![](figures/edgeWidths_demo.png)

## borderStyles<sup>12+</sup>

borderStyles(all: BorderStyle): Edges\<BorderStyle>

Generates a border style object with the specified border style color for all borders.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                      | Mandatory| Description      |
| ------ | ---------------------------------------------------------- | ---- | ---------- |
| all    | [BorderStyle](./arkui-ts/ts-appendix-enums.md#borderstyle) | Yes  | Border style.|

**Return value**

| Type                                                                       | Description                                  |
| --------------------------------------------------------------------------- | -------------------------------------- |
| [Edges](#edgest12)\<[BorderStyle](./arkui-ts/ts-appendix-enums.md#borderstyle)> | **borderStyles** object whose borders are all in the specified style. |

**Example**

```ts
import { RenderNode, FrameNode, NodeController, borderStyles } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0xffd5d5d5;
renderNode.borderWidth = {
  left: 8,
  top: 8,
  right: 8,
  bottom: 8
};
renderNode.borderColor = {
  left: 0xff519db4,
  top: 0xff519db4,
  right: 0xff519db4,
  bottom: 0xff519db4
};
renderNode.borderStyle = borderStyles(BorderStyle.Dotted);


class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }.margin(30)
  }
}
```
![](figures/borderStyles_demo.png)

## borderRadiuses<sup>12+</sup>

borderRadiuses(all: number): BorderRadiuses

Generates a **borderRadiuses** object with the specified radius for all border corners.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| all    | number | Yes   | Radius of the border corners.<br>Unit: vp<br>Value range: [0, +∞)<br>A negative value is treated as the default value. |

**Return value**

| Type                             | Description                                  |
| --------------------------------- | -------------------------------------- |
| [BorderRadiuses](#borderradiuses12) | **borderRadiuses** object whose border corners all have the specified radius.|

**Example**

```ts
import { RenderNode, FrameNode, NodeController, borderRadiuses } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0xff519db4;
renderNode.borderRadius = borderRadiuses(32);


class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }.margin(20)
  }
}
```
![](figures/borderRadiuses_demo.png)

## BackgroundBlur

Sets the background blur effect. The blur radius can be used to control the blur degree, and the grayscale parameter can be used to adjust the levels of black and white pixels in the image.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type    | Read-Only| Optional| Description                                    |
| -------- | -------- | ---- | ---- | ---------------------------------------- |
| radius   | number   | No   | No   | Blur radius.<br>Unit: px<br>Value range: [0, +∞). Default value: **0**. A negative value, **NaN**, and **Infinity** are invalid and treated as the default value. A larger value indicates a more obvious background blur effect. If the value is **0**, the background is not blurred. |
| grayscale | [number, number] | No   | Yes   | Grayscale blur, with two parameters in the value range of [0, 127]. The default value is [0, 0].  A value out of range is treated as the default value. The levels of black and white in the image are adjusted to make them tend toward gray for a softer and more pleasing appearance. It has no effect on the adjustment of colors in the image. The first parameter indicates the degree of brightening the black color, and the second parameter indicates the degree of darkening the white color. A larger value indicates a more obvious adjustment (black and white become more gray). For example, if the value specified is (20, 20), the RGB value [0, 0, 0] (black) is adjusted to [20, 20, 20] (0+20), RGB value [255, 255, 255] (white) is adjusted to [235, 235, 235] (255-20), and the color pixels remain unchanged in the image.      |

## ContentBlur

Sets the content blur effect. The blur radius can be used to control the blur degree, and the grayscale parameter can be used to adjust the levels of black and white pixels in the image.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type    | Read-Only| Optional| Description                                    |
| -------- | -------- | ---- | ---- | ---------------------------------------- |
| radius   | number   | No   | No   | Blur radius.<br>Unit: px<br>Value range: [0, +∞). Default value: **0**. A negative value, **NaN**, and **Infinity** are invalid and treated as the default value. A larger value indicates a more obvious background blur effect. If the value is **0**, the background is not blurred. |
| grayscale | [number, number] | No   | Yes   | Grayscale blur, with two parameters in the value range of [0, 127]. The default value is [0, 0].  A value out of range is treated as the default value. The levels of black and white in the image are adjusted to make them tend toward gray for a softer and more pleasing appearance. It has no effect on the adjustment of colors in the image. The first parameter indicates the degree of brightening the black color, and the second parameter indicates the degree of darkening the white color. A larger value indicates a more obvious adjustment (black and white become more gray). For example, if the value specified is (20, 20), the RGB value [0, 0, 0] (black) is adjusted to [20, 20, 20] (0+20), RGB value [255, 255, 255] (white) is adjusted to [235, 235, 235] (255-20), and the color pixels remain unchanged in the image.      |

## ForegroundBlur

Sets the foreground blur effect. The blur radius can be used to control the blur degree.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type  | Read-Only| Optional| Description                               |
| ------ | ------ | ---- | ---- | ----------------------------------- |
| radius | number | No | No | Blur radius.<br>Unit: px<br>Value range: [0, +∞). Default value: **0**. A negative value, **NaN**, and **Infinity** are invalid and treated as the default value. A larger value indicates a more obvious background blur effect. If the value is **0**, the background is not blurred. |