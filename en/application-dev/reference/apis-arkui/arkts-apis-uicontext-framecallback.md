# Class (FrameCallback)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=6b08011c092d34059e19744a8f7cabfbde4edcb7 translatedAt=2026-08-05T03:10:13.383Z pushedAt=2026-08-05T06:43:04.568Z -->

Defines a frame callback task that can be executed during the rendering phase of the next frame or in the idle phase after the frame rendering task is completed.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - This API can be used only in the stage model.
>
> - The following APIs must be used in conjunction with [postFrameCallback](arkts-apis-uicontext-uicontext.md#postframecallback12) and [postDelayedFrameCallback](arkts-apis-uicontext-uicontext.md#postdelayedframecallback12) in [UIContext](arkts-apis-uicontext-uicontext.md). You need to inherit this class and override the [onFrame](#onframe12) or [onIdle](#onidle12) method to implement specific service logic.

## onFrame<sup>12+</sup>

onFrame(frameTimeInNano: number): void

Called when the next frame is rendered.

After inheriting the FrameCallback class and overriding this method, it can be used together with [postFrameCallback](arkts-apis-uicontext-uicontext.md#postframecallback12) or [postDelayedFrameCallback](arkts-apis-uicontext-uicontext.md#postdelayedframecallback12) in [UIContext](arkts-apis-uicontext-uicontext.md).

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                | Mandatory| Description                                                   |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------------------------- |
| frameTimeInNano | number | Yes | Time at which the next frame rendering starts, in nanoseconds. This parameter is passed by the system during callback and does not need to be manually passed in.<br>Value range: [0, +∞) |

**Example**

```ts
import { FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeInNano: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeInNano.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('Invoke postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyFrameCallback('normTask'));
          })
        Button('Invoke postDelayedFrameCallback')
          .onClick(() => {
            this.getUIContext().postDelayedFrameCallback(new MyFrameCallback('delayTask'), 5);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## onIdle<sup>12+</sup>

onIdle(timeLeftInNano: number): void

After the next frame rendering task is completed, if the remaining time from the current moment to the next VSync signal is greater than 1 ms, this callback is executed. If the remaining time is less than or equal to 1 ms, the callback is deferred to a subsequent frame and executed when the remaining time from the current moment to the next VSync signal is greater than 1 ms. If no next frame has been requested, the system automatically requests one.

After inheriting the FrameCallback class and overriding this method, it can be used together with [postFrameCallback](arkts-apis-uicontext-uicontext.md#postframecallback12) or [postDelayedFrameCallback](arkts-apis-uicontext-uicontext.md#postdelayedframecallback12) in [UIContext](arkts-apis-uicontext-uicontext.md).

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                | Mandatory| Description                                                   |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------------------------- |
| timeLeftInNano | number | Yes | Remaining idle time of this frame, in nanoseconds. This value is passed in by the system during callback and does not need to be manually passed in.<br>Value range: [0, +∞) |

**Example**

```ts
import { FrameCallback } from '@kit.ArkUI';

class MyIdleCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onIdle(timeLeftInNano: number) {
    console.info('MyIdleCallback ' + this.tag + ' ' + timeLeftInNano.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('Invoke postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyIdleCallback('normTask'));
          })
        Button('Invoke postDelayedFrameCallback')
          .onClick(() => {
            this.getUIContext().postDelayedFrameCallback(new MyIdleCallback('delayTask'), 5);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```