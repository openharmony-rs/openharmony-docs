# Property Animation (animation)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bbc6406dab71d9f75b4831661ca1204731bcdd0c translatedAt=2026-07-30T02:27:57.304Z pushedAt=2026-08-01T06:42:55.861Z -->

When certain universal attributes of a component change, if no animation is set, the attribute values will jump directly to the target values. Attribute animation can be used to achieve a gradient transition effect, making UI changes more natural and smooth. Supported attributes include [width](ts-universal-attributes-size.md#width), [height](ts-universal-attributes-size.md#height), [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), [opacity](ts-universal-attributes-opacity.md#opacity), [scale](ts-universal-attributes-transformation.md#scale), [rotate](ts-universal-attributes-transformation.md#rotate), [translate](ts-universal-attributes-transformation.md#translate), and others. For animations of attributes that change the layout (such as width and height), the content usually jumps directly to the final state, for example, text or content in [Canvas](ts-components-canvas-canvas.md). If you want the content to follow the width and height changes, you can use the [renderFit](ts-universal-attributes-renderfit.md#renderfit) attribute for configuration.

> **NOTE**
>
> This feature is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.

## animation

animation(value:AnimateParam): T

Sets a property animation for the component.

> **NOTE**
>
>  - When a single page contains a large number of components with animations, use [renderGroup](ts-universal-attributes-image-effect.md#rendergroup10) to minimize frame freezing and improve animation performance. For best practices, see [Animation Usage Guide – Using RenderGroup](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-fair-use-animation#section1223162922415).
>
>  - This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

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
| T | Current component.|

Property animations only affect attributes that are specified before the **animation** API and do not affect properties of the component constructor.

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