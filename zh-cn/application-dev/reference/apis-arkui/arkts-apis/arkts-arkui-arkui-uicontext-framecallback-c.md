# FrameCallback

用于设置下一帧渲染时需要执行的任务。
> **说明：**  
>  
> - 以下API需要配合[UIContext](arkts-arkui-uicontext.md)中的[postFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postframecallback)和  
> [postDelayedFrameCallback](arkts-arkui-arkui-uicontext-uicontext-c.md#postdelayedframecallback)使用。开发者需要继承该类并重写  
> [onFrame](arkts-arkui-arkui-uicontext-framecallback-c.md#onframe)或[onIdle](arkts-arkui-arkui-uicontext-framecallback-c.md#onidle)方法，实现具体的业务逻辑。

**起始版本：** 12

<!--Device-unnamed-export abstract class FrameCallback--><!--Device-unnamed-export abstract class FrameCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## onFrame

```TypeScript
onFrame(frameTimeInNano: number): void
```

在下一帧进行渲染时，该方法将被执行。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameCallback-onFrame(frameTimeInNano: number): void--><!--Device-FrameCallback-onFrame(frameTimeInNano: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameTimeInNano | number | 是 | 下一帧渲染开始执行的时间，以纳秒为单位。<br/>取值范围：[0, +∞) |

## onIdle

```TypeScript
onIdle(timeLeftInNano: number): void
```

在下一帧渲染结束时，如果距离下一个Vsync信号到来还有1ms以上的剩余时间，该方法将被执行，否则将顺延至后面的帧。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameCallback-onIdle(timeLeftInNano: number): void--><!--Device-FrameCallback-onIdle(timeLeftInNano: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeLeftInNano | number | 是 | 这一帧剩余的空闲时间，以纳秒为单位。<br/>取值范围：[0, +∞) |

