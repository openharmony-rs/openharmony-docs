# Property Animation (animation)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-28T01:36:23.529Z pushedAt=2026-08-28T08:18:58.650Z -->

When certain universal attributes of a component change, if no animation is set, the attribute values will jump directly to the target values. Attribute animation can be used to achieve a gradient transition effect, making UI changes more natural and smooth. Supported attributes include [width](ts-universal-attributes-size.md#width), [height](ts-universal-attributes-size.md#height), [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), [opacity](ts-universal-attributes-opacity.md#opacity), [scale](ts-universal-attributes-transformation.md#scale), [rotate](ts-universal-attributes-transformation.md#rotate), [translate](ts-universal-attributes-transformation.md#translate), and others. For animations of attributes that change the layout (such as width and height), the content usually jumps directly to the final state, for example, text or content in [Canvas](ts-components-canvas-canvas.md). If you want the content to follow the width and height changes, you can use the [renderFit](ts-universal-attributes-renderfit.md#renderfit) attribute for configuration.

> **NOTE**
>
> This feature is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.

## animation

animation(value:AnimateParam): T

Sets a property animation for the component. When the universal attributes of the component change, the attribute change process is gradually transitioned based on the configuration in the **AnimateParam** parameter.

> **NOTE**
>
> - When a single page contains dozens or more components with animations applied, use [renderGroup](ts-universal-attributes-image-effect.md#rendergroup10) to resolve frame freezing and improve animation performance. For best practices, see [Animation Usage Guide - Using renderGroup](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-fair-use-animation#section1223162922415).
>
> - This API cannot be called in [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier). Calling **animation** in **attributeModifier** does not produce an animation effect. To animate attribute changes in **attributeModifier**, use [explicit animation](ts-explicit-animation.md) (**animateTo**) instead.
> - It takes effect only on some universal attributes (including **width**, **height**, **backgroundColor**, **opacity**, **scale**, **rotate**, and **translate**). For animations that change layout attributes (such as width and height), the component content (such as text or content in Canvas) usually jumps directly to the final state. To make the content transition smoothly with the width and height changes, use the [renderFit](ts-universal-attributes-renderfit.md#renderfit) attribute together. It is recommended to set **renderFit** to a value such as **RenderFit.CENTER** or **RenderFit.TOP_LEFT** so that the content changes synchronously with the component size during the animation.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                               | Mandatory| Description                                   |
| ----- | --------------------------------- | ---- | ------------------------------------- |
| value | [AnimateParam](ts-explicit-animation.md#animateparam) | Yes    | Animation effect parameters. For details about the value range and meaning of each attribute, see [AnimateParam](ts-explicit-animation.md#animateparam).                           |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

A property animation takes effect only on the attributes written before **animation**, producing a gradual transition effect. Attribute changes written after animation do not have a gradual animation effect but jump directly to the target value. Attributes of the component constructor (such as the **space** parameter of the **Column** constructor and the **initialIndex** parameter of the **List** constructor, which are passed in when the component is constructed) do not support animation effects. The animation takes effect only on attributes set through attribute methods (such as **.width()**, **.height()**, and **.backgroundColor()**).

```ts
@Entry
@Component
struct AnimationExample {
  @State widthSize: number = 250;
  @State heightSize: number = 100;
  @State rotateAngle: number = 0;
  @State flag: boolean = true;
  @State space: number = 10;
  
  build() {
    Column() {
      Column({ space: this.space }) // Changing space in the Column constructor will not be animated.
        .onClick(() => {
          if (this.flag) {
            this.widthSize = 150;
            this.heightSize = 60;
            this.space = 20; // Changing this.space will not be animated.
          } else {
            this.widthSize = 250;
            this.heightSize = 100;
            this.space = 10; //  Changing this.space will not be animated.
          }
          this.flag = !this.flag;
        })
        .backgroundColor(Color.Black)
        .margin(30)
        .width(this.widthSize) // Only effective if specified before the animation API.
        .height(this.heightSize) // Only effective if specified before the animation API.
        // Configure an ease-out curve for the button size change and repeat three times.
        .animation({
          duration: 2000,
          curve: Curve.EaseOut,
          iterations: 3,
          playMode: PlayMode.Normal
        })
        // .width(this.widthSize) // The animation API does not take effect here.
        // .height(this.heightSize) //  The animation API does not take effect here.
    }
  }
}
```

## Example

This example demonstrates property animations using the animation API.

```ts
// xxx.ets
@Entry
@Component
struct AttrAnimationExample {
  @State widthSize: number = 250
  @State heightSize: number = 100
  @State rotateAngle: number = 0
  @State flag: boolean = true

  build() {
    Column() {
      Button('change size')
        .onClick(() => {
          if (this.flag) {
            this.widthSize = 150
            this.heightSize = 60
          } else {
            this.widthSize = 250
            this.heightSize = 100
          }
          this.flag = !this.flag
        })
        .margin(30)
        .width(this.widthSize)
        .height(this.heightSize)
        .animation({
          duration: 2000,
          curve: Curve.EaseOut,
          iterations: 3,
          playMode: PlayMode.Normal
        })
      Button('change rotate angle')
        .onClick(() => {
          this.rotateAngle = 90
        })
        .margin(50)
        .rotate({ angle: this.rotateAngle })
        // Configure a damping curve for the rotation angle change, with a 500 ms delay before starting, and alternating playback in an infinite loop.
        .animation({
          duration: 1200,
          curve: Curve.Friction,
          delay: 500,
          iterations: -1, // The value -1 indicates that the animation is played for an unlimited number of times.
          playMode: PlayMode.Alternate,
          expectedFrameRateRange: {
            min: 20,
            max: 120,
            expected: 90,
          }
        })
    }.width('100%').margin({ top: 20 })
  }
}
```

![animation](figures/animation.gif)