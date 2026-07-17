# BaseGestureHandlingProposal

智慧手势处理基类。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，其回调参数类型为具体的子类类型实例。

**起始版本：** 26.0.0

<!--Device-unnamed-export abstract class BaseGestureHandlingProposal--><!--Device-unnamed-export abstract class BaseGestureHandlingProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## action

```TypeScript
action: SmartGestureAction
```

智慧手势最终执行动作。

**类型：** SmartGestureAction

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseGestureHandlingProposal-action: SmartGestureAction--><!--Device-BaseGestureHandlingProposal-action: SmartGestureAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operateIntention

```TypeScript
operateIntention: OperateIntention
```

智慧手势底层操作意图。

**类型：** OperateIntention

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-BaseGestureHandlingProposal-operateIntention: OperateIntention--><!--Device-BaseGestureHandlingProposal-operateIntention: OperateIntention-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

