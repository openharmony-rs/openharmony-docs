# GestureObserverConfigs

该参数用于指定需要监听的手势回调阶段（传入空数组将无效），仅当手势触发指定阶段时才会发送通知。

**起始版本：** 20

<!--Device-unnamed-export interface GestureObserverConfigs--><!--Device-unnamed-export interface GestureObserverConfigs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## actionPhases

```TypeScript
actionPhases: Array<GestureActionPhase>
```

手势事件对象。

**类型：** Array&lt;GestureActionPhase&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GestureObserverConfigs-actionPhases: Array<GestureActionPhase>--><!--Device-GestureObserverConfigs-actionPhases: Array<GestureActionPhase>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

