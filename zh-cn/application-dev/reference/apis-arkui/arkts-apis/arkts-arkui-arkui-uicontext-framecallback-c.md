# FrameCallback

用于定义帧回调任务，可在下一帧渲染阶段或帧渲染任务结束后的空闲阶段执行。

> **说明：**
> 
> - 以下API需要配合[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[postFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postframecallback)和
> [postDelayedFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postdelayedframecallback)使用。开发者需要继承该类并重写
> [onFrame](#onframe)或[onIdle](#onidle)方法，实现具体的业务逻辑。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## onFrame

```TypeScript
onFrame(frameTimeInNano: number): void
```

在下一帧进行渲染时，该方法将被执行。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameTimeInNano | number | 是 | 下一帧渲染开始执行的时间，以纳秒为单位。取值范围：[0, +∞) |

**示例**

```TypeScript
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
        Button('点击触发postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyFrameCallback('normTask'));
          })
        Button('点击触发postDelayedFrameCallback')
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

## onIdle

```TypeScript
onIdle(timeLeftInNano: number): void
```

在下一帧渲染结束时，如果距离下一个Vsync信号到来还有1ms以上的剩余时间，该方法将被执行，否则将顺延至后面的帧。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeLeftInNano | number | 是 | 这一帧剩余的空闲时间，以纳秒为单位。取值范围：[0, +∞) |

**示例**

```TypeScript
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
        Button('点击触发postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyIdleCallback('normTask'));
          })
        Button('点击触发postDelayedFrameCallback')
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
