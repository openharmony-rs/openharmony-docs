# Shape Clipping
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-09-02T12:08:22.466Z -->

Shape clipping changes the visible portion of a component through clipping or masking.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.

## clip<sup>12+</sup>

clip(value: boolean): T

Whether to clip the areas of child components that extend beyond this component's bounds. If **value** is set to **true**, the areas of child components that extend beyond this component's bounds are clipped and become invisible. If **value** is set to **false**, child components are not clipped. If this attribute is not set, the areas of child components that extend beyond this component's bounds are not clipped by default.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes   | Whether to clip child components based on the edge contour of the current component.<br>The value **true** means to clip child components based on the edge contour of the current component, and **false** means not to clip child components. <br>**Note:** When this parameter is set to **true**, the areas of child components outside the current component range do not respond to bound gesture events. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## clip<sup>18+</sup>

clip(clip: Optional\<boolean>): T

Whether to clip the areas of child components that extend beyond this component's bounds. If this attribute is not set, the areas of child components that extend beyond this component's bounds are not clipped by default. Compared with [clip<sup>12+</sup>](#clip12), this API adds support for the **undefined** type.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Parameters**

| Name| Type              | Mandatory                                                        | Description|
| ------ | ------------------ | ------------------------------------------------------------ | ---- |
| clip   | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes | Sets whether to clip child components based on the outline of the current component edge. The value true means to clip child components based on the outline of the current component edge, and false means not to clip child components.<br>**Note:** After this attribute is set to true, the area of child components outside the current component range does not respond to the bound gesture events.<br>When the value of clip is undefined, the area of child components outside the current component range is not clipped.    |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## clip<sup>(deprecated)</sup>

clip(value: boolean | CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute): T

Clips the current component based on the specified shape, or sets whether to clip based on the edge contour of the current component.

> **NOTE** 
>
> This API is supported since API version 7 and deprecated since API version 12. You are advised to use [clipShape](#clipshape12) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | boolean&nbsp;\|&nbsp;[CircleAttribute](ts-drawing-components-circle.md)&nbsp;\|&nbsp;[EllipseAttribute](ts-drawing-components-ellipse.md)&nbsp;\|&nbsp;[PathAttribute](ts-drawing-components-path.md)&nbsp;\|&nbsp;[RectAttribute](ts-drawing-components-rect.md) | Yes   | When the parameter is a component of the corresponding type, clips the current component and its child components according to the specified shape. When the parameter is of the boolean type, sets whether to clip according to the edge contour of the current component.<br>Default value: false <br>true means to clip according to the edge contour of the current component, and false means not to clip.<br>**Note:** When the parameter is a component of the corresponding type, clipping does not prevent the clipped area from responding to bound gesture events. When the parameter is of the boolean type, clipping prevents the clipped area from responding to bound gesture events. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## clipShape<sup>12+</sup>

clipShape(value: CircleShape | EllipseShape | PathShape | RectShape): T

Clips the current component based on the specified shape (which may contain position information), clipping away the areas of the component that extend beyond the shape so that they become invisible. Unlike [maskShape](#maskshape12), **clipShape** clips away the areas of the component that extend beyond the shape (making them invisible), whereas **maskShape** overlays a mask layer of the specified shape on the component.

> **NOTE** 
>
> Different shapes support different ranges of attributes. A path is one type of shape, along with others like ellipses and rectangles.
>
> Path shapes do not support setting width and height attributes. For details about the supported attributes, see the specific shape documentation.
>
> The [fill](../js-apis-arkui-shape.md#fill) attribute of shapes has no effect on the **clipShape** API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [CircleShape](#circleshape12)&nbsp;\|&nbsp;[EllipseShape](#ellipseshape12)&nbsp;\|&nbsp;[PathShape](#pathshape12)&nbsp;\|&nbsp;[RectShape](#rectshape12) | Yes   | Component of the corresponding type. Clips the current component according to the specified shape (the shape can contain position information).<br>**Note:** Clipping does not prevent the clipped area from responding to bound gesture events. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## clipShape<sup>18+</sup>

clipShape(shape: Optional\<CircleShape | EllipseShape | PathShape | RectShape>): T

Clips this component according to the specified shape (which may include position information). Compared with [clipShape<sup>12+</sup>](#clipshape12), this API supports the **undefined** type.

> **NOTE** 
>
> Different shapes support different ranges of attributes. A path is one type of shape, along with others like ellipses and rectangles.
>
> Path shapes do not support setting width and height attributes. For details about the supported attributes, see the specific shape documentation.
>
> The [fill](../js-apis-arkui-shape.md#fill) attribute of shapes has no effect on the **clipShape** API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| shape  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[CircleShape](#circleshape12)&nbsp;\|&nbsp;[EllipseShape](#ellipseshape12)&nbsp;\|&nbsp;[PathShape](#pathshape12)&nbsp;\|&nbsp;[RectShape](#rectshape12)> | Yes   | The parameter is a component of the corresponding type, which clips the current component according to the specified shape (the shape can contain position information).<br>**Note:** Clipping does not prevent the clipped area from responding to bound gesture events.<br>When the value of shape is undefined, the mask with the specified shape is removed. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## CircleShape<sup>12+</sup>

type CircleShape = import('../api/@ohos.arkui.shape').CircleShape

Defines the CircleShape type.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                    |
| ------ | ------------------------ |
| import('../api/@ohos.arkui.shape').[CircleShape](../js-apis-arkui-shape.md#circleshape) | Circular shape. |

## EllipseShape<sup>12+</sup>

type EllipseShape = import('../api/@ohos.arkui.shape').EllipseShape

Defines the EllipseShape type.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                    |
| ------ | ------------------------ |
| import('../api/@ohos.arkui.shape').[EllipseShape](../js-apis-arkui-shape.md#ellipseshape) | Ellipse shape. |

## PathShape<sup>12+</sup>

type PathShape = import('../api/@ohos.arkui.shape').PathShape

Defines the PathShape type.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                    |
| ------ | ------------------------ |
| import('../api/@ohos.arkui.shape').[PathShape](../js-apis-arkui-shape.md#pathshape) | Path shape. |

## RectShape<sup>12+</sup>

type RectShape = import('../api/@ohos.arkui.shape').RectShape

Defines the RectShape type.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type  | Description                    |
| ------ | ------------------------ |
| import('../api/@ohos.arkui.shape').[RectShape](../js-apis-arkui-shape.md#rectshape) | Rectangular shape. |

## mask<sup>12+</sup>

mask(value: ProgressMask): T

Adds a mask with adjustable progress to the component. The mask is overlaid on the component content, and the display range of the mask is controlled by the progress value.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type                           | Mandatory| Description                                                |
| ------ | ------------------------------- | ---- | ---------------------------------------------------- |
| value  | [ProgressMask](#progressmask10) | Yes  | Mask to add to the component, which allows for dynamic adjustment of progress, maximum value, and color settings.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## mask<sup>18+</sup>

mask(mask: Optional\<ProgressMask>): T

Adds a mask with adjustable progress to the component. The mask is overlaid on the component content, and the display range of the mask is controlled by the progress value. Compared with [mask<sup>12+</sup>](#mask12), this API adds support for the **undefined** type.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 18.

**Parameters**

| Name| Type                                                        | Mandatory| Description                            |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------- |
| mask | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[ProgressMask](#progressmask10)> | Yes | Adds a mask to the current component that allows dynamically setting the progress and color. The maximum value (total) of the mask is set when the ProgressMask object is constructed and cannot be dynamically modified. You can call updateProgress() of the ProgressMask object to update the progress value, updateColor() to update the color, and enableBreathingAnimation() to enable or disable the breathing halo animation.<br>When the value of mask is undefined, the no-progress mask effect is restored. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## mask<sup>(deprecated)</sup>

mask(value: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute | ProgressMask): T

Adds a mask of the specified shape or adjustable progress to the component.

> **NOTE** 
>
> This API is supported since API version 7 and deprecated since API version 12. You are advised to use [maskShape](#maskshape12) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                            |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------- |
| value  | [CircleAttribute](ts-drawing-components-circle.md)&nbsp;\|&nbsp;[EllipseAttribute](ts-drawing-components-ellipse.md)&nbsp;\|&nbsp;[PathAttribute](ts-drawing-components-path.md)&nbsp;\|&nbsp;[RectAttribute](ts-drawing-components-rect.md) \|&nbsp;[ProgressMask](#progressmask10)<sup>10+</sup> | Yes   | When the parameter is a component of the corresponding shape type, adds a mask of the specified shape (circle, ellipse, path, or rectangle) to the current component; when the parameter is ProgressMask, adds a mask whose progress and color can be dynamically set to the current component. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## maskShape<sup>12+</sup>

maskShape(value: CircleShape | EllipseShape | PathShape | RectShape): T

Adds a mask of the specified shape to the component, overlaying a cover layer of the specified shape on the component.

> **NOTE**
>
> - Different shapes support different attribute ranges. A path is a shape, and in addition there are shapes such as ellipses and rectangles.
>
> - A path shape does not support setting the width and height. For the attributes supported by a specific shape, see the documentation of that shape.
>
> - The **fill** attribute in a shape takes effect on the **maskShape** API and is used to set the color of the mask.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Parameters**

| Name| Type                                                        | Mandatory| Description                            |
| ------ | ------------------------------------------------------------ | ---- | -------------------------------- |
| value  | [CircleShape](#circleshape12)&nbsp;\|&nbsp;[EllipseShape](#ellipseshape12)&nbsp;\|&nbsp;[PathShape](#pathshape12)&nbsp;\|&nbsp;[RectShape](#rectshape12) | Yes   | Adds a mask of the specified shape or a mask with adjustable progress to the current component. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## maskShape<sup>18+</sup>

maskShape(shape: Optional\<CircleShape | EllipseShape | PathShape | RectShape>): T

Adds a mask of the specified shape to the component, overlaying a cover layer of the specified shape on the component. Compared with [maskShape<sup>12+</sup>](#maskshape12), this API adds support for the **undefined** type.

> **NOTE**
>
> Different shapes support different attribute ranges. A path is a shape, and in addition there are shapes such as ellipses and rectangles.
>
> A path shape does not support setting the width and height. For the attributes supported by a specific shape, see the documentation of that shape.
>
> The **fill** attribute in a shape takes effect on the **maskShape** API and is used to set the color of the mask.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| shape  | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[CircleShape](#circleshape12)&nbsp;\|&nbsp;[EllipseShape](#ellipseshape12)&nbsp;\|&nbsp;[PathShape](#pathshape12)&nbsp;\|&nbsp;[RectShape](#rectshape12)> | Yes   | When the parameter is a component of the corresponding shape type, a mask of the specified shape (circle, ellipse, path, or rectangle) is added to the current component. When the parameter is ProgressMask, a mask whose progress, maximum value, and color can be dynamically set is added to the current component.<br>When the value of shape is undefined, the current value is reset to restore the effect of no specified shape mask. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## ProgressMask<sup>10+</sup>

**ProgressMask** is used to set the progress, maximum value, and color of the mask.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor<sup>10+</sup>

constructor(value: number, total: number, color: ResourceColor)

Constructs a **ProgressMask** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                  | Mandatory| Description          |
| ------ | ------------------------------------------ | ---- | ------------------ |
| value  | number                                     | Yes   | Current value of the progress mask. It is used together with total to determine the progress ratio. When value equals total, the progress is full.<br>Value range: [0.0, +∞). If a negative number is passed in, it is automatically corrected to 0. |
| total  | number                                     | Yes   | Maximum value of the progress mask.<br> Value range: [0.0, +∞). If a negative number is passed in, it is automatically corrected to 100. |
| color  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Color of the progress mask.  |

### updateProgress<sup>10+</sup>

updateProgress(value: number): void

Updates the progress value of the progress mask.

**Usage**
- You must first apply the **ProgressMask** object to the component through the [mask()](#mask12) method. After this method is called, the progress value of the mask is dynamically updated.
- If the **ProgressMask** object has not been applied to the component through the mask() method, calling this method only updates the internal state of the **ProgressMask** object and does not produce any visible change in the mask effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description          |
| ------ | -------- | ---- | ------------------ |
| value  | number   | Yes   | Current value of the progress mask.<br>Value range: [0.0, +∞). If a negative number is passed in, it is automatically corrected to 0. |

### updateColor<sup>10+</sup>

updateColor(value: ResourceColor): void

Updates the color of the progress mask.

**Usage**
- You must first apply the ProgressMask object to a component through the [mask()](#mask12) method. After this method is called, the mask color is dynamically updated.
- If the ProgressMask object has not been applied to a component through the mask() method, calling this method only updates the internal state of the ProgressMask object and does not produce any visible change in the mask effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                  | Mandatory| Description        |
| ------ | ------------------------------------------ | ---- | ---------------- |
| value  | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Color of the progress mask.|

### enableBreathingAnimation<sup>12+</sup>

enableBreathingAnimation(value: boolean): void

Switch for the breathing glow animation when the progress is full. When enabled, a periodic brightening and dimming glow effect appears at the mask edge when the progress is full. When not set, the breathing glow animation is disabled by default.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                  | Mandatory| Description        |
| ------ | ------------------------------------------ | ---- | ---------------- |
| value  | boolean | Yes   | Whether to enable the breathing halo animation when the progress is full.<br>true: enables the breathing halo animation.<br>false: disables the breathing halo animation. |


## Example

### Example 1: Using Different Clipping Attributes

This example demonstrates how to clip and mask an image using [clipShape](#clipshape12), [clip](#clip12), and [maskShape](#maskshape12).

```ts
// xxx.ets
import { CircleShape, RectShape } from '@kit.ArkUI';

@Entry
@Component
struct ClipAndMaskExample {
  build() {
    Column({ space: 15 }) {
      Text('clip').fontSize(12).width('75%').fontColor('#DCDCDC')
      Row() {
        // Replace $r("app.media.testImg") with the image resource file you use.
        Image($r('app.media.testImg')).width('500px').height('280px')
      }
      .clip(true) // If clip is not set to true, the image is not confined by the rounded corners of the <Row> component and may extend beyond the <Row> component.
      .borderRadius(20)

      // Clip the image based on a circle with a diameter of 280 px.
      // Replace $r("app.media.testImg") with the image resource file you use.
      Image($r('app.media.testImg'))
        .clipShape(new CircleShape({ width: '280px', height: '280px' }))
        .width('500px').height('280px')

      Text('mask').fontSize(12).width('75%').fontColor('#DCDCDC')
      // Add a 500 × 280 px square mask to the image.
      // Replace $r("app.media.testImg") with the image resource file you use.
      Image($r('app.media.testImg'))
        .maskShape(new RectShape({ width: '500px', height: '280px' }).fill(Color.Gray))
        .width('500px').height('280px')

      // Add a 280 × 280 px circular mask to the image.
      // Replace $r("app.media.testImg") with the image resource file you use.
      Image($r('app.media.testImg'))
        .maskShape(new CircleShape({ width: '280px', height: '280px' }).fill(Color.Gray))
        .width('500px').height('280px')
    }
    .width('100%')
    .margin({ top: 15 })
  }
}
```

![clipAndMask](figures/clipAndMask.PNG)

### Example 2: Implementing Component Masking

This example demonstrates how to mask an image using [mask](#mask12).

```ts
@Entry
@Component
struct ProgressMaskExample {
  @State isRedColor: boolean = true;
  @State value: number = 10.0;
  @State enableBreathingAnimation: boolean = false;
  @State progress: ProgressMask = new ProgressMask(10.0, 100.0, Color.Gray);

  build() {
    Column({ space: 15 }) {
      Text('progress mask').fontSize(12).width('75%').fontColor('#DCDCDC')
      // Add a progress mask to the image.
      // Replace $r("app.media.testImg") with the image resource file you use.
      Image($r('app.media.testImg'))
        .width('500px').height('280px')
        .mask(this.progress)
        .animation({
          duration: 2000, // Animation duration.
          curve: Curve.Linear, // Animation curve.
          delay: 0, // Animation delay.
          iterations: 1, // Number of playback times.
          playMode: PlayMode.Normal // Animation playback mode.
        }) // Configure the animation for the mask progress change of the Image component.

      // Update the progress value of the progress mask.
      Button('updateProgress')
        .onClick((event?: ClickEvent) => {
          this.value += 10;
          this.progress.updateProgress(this.value);
        }).width(200).height(50).margin(20)

      // Update the color of the progress mask.
      Button('updateColor')
        .onClick((event?: ClickEvent) => {
          if (this.isRedColor) {
            this.progress.updateColor(0x9fff0000);
          } else {
            this.progress.updateColor(0x9f0000ff);
          }
          this.isRedColor = !this.isRedColor;
        }).width(200).height(50).margin(20)

      // Enable or disable the breathing animation.
      Button('enableBreathingAnimation:' + this.enableBreathingAnimation)
        .onClick((event?: ClickEvent) => {
          this.enableBreathingAnimation = !this.enableBreathingAnimation;
          this.progress.enableBreathingAnimation(this.enableBreathingAnimation);
        }).width(200).height(50).margin(20)

      // Restore the progress mask.
      Button('click reset')
        .onClick((event?: ClickEvent) => {
          this.value = 0;
          this.progress.updateProgress(this.value);
        }).width(200).height(50).margin(20)
    }
    .width('100%')
    .margin({ top: 15 })
  }
}
```

![progressMask](figures/progressMask.gif)
