# Class (FrameCallback)

用于设置下一帧渲染时需要执行的任务。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 以下API需要配合[UIContext](arkts-apis-uicontext-uicontext.md)中的[postFrameCallback](arkts-apis-uicontext-uicontext.md#postframecallback12)和[postDelayedFrameCallback](arkts-apis-uicontext-uicontext.md#postdelayedframecallback12)使用。开发者需要继承该类并重写[onFrame](#onframe12)或[onIdle](#onidle12)方法，实现具体的业务逻辑。

## onFrame<sup>12+</sup>

onFrame(frameTimeInNano: number): void

在下一帧进行渲染时，该方法将被执行。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                                    |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------------------------- |
| frameTimeInNano | number | 是   | 下一帧渲染开始执行的时间，以纳秒为单位。<br/>取值范围：[0, +∞) |

**示例：**

```ts
import { FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('点击触发postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyFrameCallback("normTask"));
          })
        Button('点击触发postDelayedFrameCallback')
          .onClick(() => {
            this.getUIContext().postDelayedFrameCallback(new MyFrameCallback("delayTask"), 5);
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

在下一帧渲染结束时，如果距离下一个Vsync信号到来还有1ms以上的剩余时间，该方法将被执行，否则将顺延至后面的帧。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                                    |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------------------------- |
| timeLeftInNano | number | 是   | 这一帧剩余的空闲时间，以纳秒为单位。<br/>取值范围：[0, +∞) |

**示例：**

```ts
import { FrameCallback } from '@ohos.arkui.UIContext';

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
        Button('点击触发postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyIdleCallback("normTask"));
          })
        Button('点击触发postDelayedFrameCallback')
          .onClick(() => {
            this.getUIContext().postDelayedFrameCallback(new MyIdleCallback("delayTask"), 5);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
