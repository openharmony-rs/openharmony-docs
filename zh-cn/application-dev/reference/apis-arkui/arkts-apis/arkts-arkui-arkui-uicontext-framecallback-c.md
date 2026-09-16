# FrameCallback

用于定义帧回调任务，可在下一帧渲染阶段或帧渲染任务结束后的空闲阶段执行。

> **说明：** 
> 
> - 以下API需要配合[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[postFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postframecallback)和[postDelayedFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postdelayedframecallback)使用。开发者需要继承该类并重写[onFrame](#onframe)或[onIdle](#onidle)方法，实现具体的业务逻辑。

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

继承FrameCallback类并重写该方法后，可配合[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[postFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postframecallback)和[postDelayedFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postdelayedframecallback)使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameTimeInNano | number | 是 | 下一帧渲染开始执行的时间，以纳秒为单位，由系统回调时传入，开发者无需手动传入。<br>取值范围：[0, +∞) |

## onIdle

```TypeScript
onIdle(timeLeftInNano: number): void
```

下一帧渲染任务结束后，若当前时间到下一个VSync信号的剩余时间大于1ms，则执行该回调；若剩余时间小于等于1ms，则将回调顺延至后续某一帧，待当前时间到下一个VSync信号的剩余时间大于1ms时执行。若当前没有已请求的下一帧，系统会自动请求一帧。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeLeftInNano | number | 是 | 这一帧剩余的空闲时间，以纳秒为单位，由系统回调时传入，开发者无需手动传入。<br>取值范围：[0, +∞) |
