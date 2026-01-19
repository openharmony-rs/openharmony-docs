# Immediate Delivery of Explicit Animation (animateToImmediately)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **animateToImmediately** API implements immediate delivery for [explicit animations](ts-explicit-animation.md). When multiple property animations are loaded at once, you can call this API to immediately execute the transition animation for state changes caused by the specified closure function.

Unlike [animateTo](../arkts-apis-uicontext-uicontext.md#animateto), which waits for the VSync signal, **animateToImmediately** instantly sends animation commands to the rendering layer for execution. This is particularly useful in scenarios where you need to prioritize certain animations or update part of the UI in advance, especially when your application's main thread is occupied with time-consuming operations. Note that **animateToImmediately** is limited to property animations on the rendering layer, and cannot be used for frame-by-frame animations on the UI side.

In addition, this API captures the current state at the time of the call and sends it alongside the newly generated animation to the rendering layer. This means that the rendering output will reflect the state at the time of the call. Ensure that the state is complete when the API is called. Otherwise, rendering exceptions may occur in the first few frames.

Therefore, you are advised to use [animateTo](../arkts-apis-uicontext-uicontext.md#animateto) to prevent interference with the display timing of the framework and avoid potential display errors caused by incomplete state settings at the start of the animation.

> **NOTE**
>
> This API is deprecated since API version 22. You are advised to use [animateToImmediately](../arkts-apis-uicontext-uicontext.md#animatetoimmediately22) instead.
>
> The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>

## APIs

## animateToImmediately<sup>(deprecated)</sup>

animateToImmediately(value: AnimateParam , event: () => void): void

Delivers an explicit animation immediately.

> **NOTE**
>
> This API is supported since API version 12 and deprecated since API version 22. You are advised to use [animateToImmediately](../arkts-apis-uicontext-uicontext.md#animatetoimmediately22) instead.
>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| value  | [AnimateParam](ts-explicit-animation.md#animateparam) | Yes      | Animation settings.                                      |
| event  | () => void                                                   | Yes      | Closure function that displays the animation. The system automatically inserts a transition animation for state changes caused by the closure function.|

## Example

This example demonstrates how to use the [animateToImmediately](#animatetoimmediatelydeprecated) API to deliver an explicit animation immediately.

```ts
// xxx.ets
@Entry
@Component
struct AnimateToImmediatelyExample {
  @State widthSize: number = 250;
  @State heightSize: number = 100;
  @State opacitySize: number = 0;
  private flag: boolean = true;

  build() {
    Column() {
      Column()
      .width(this.widthSize)
      .height(this.heightSize)
      .backgroundColor(Color.Green)
      .opacity(this.opacitySize)
      Button('change size')
        .margin(30)
        .onClick(() => {
          if (this.flag) {
            animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.opacitySize = 1;
            })
            this.getUIContext()?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.widthSize = 150;
              this.heightSize = 60;
            })
          } else {
            animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.widthSize = 250;
              this.heightSize = 100;
            })
            this.getUIContext()?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.opacitySize = 0;
            })
          }
          this.flag = !this.flag;
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

![animation1](figures/animateToImmediately1.gif)
