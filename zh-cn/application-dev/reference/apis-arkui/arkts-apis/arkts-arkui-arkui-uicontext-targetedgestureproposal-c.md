# TargetedGestureProposal

带目标节点的智慧手势处理基类。

**继承/实现关系：** TargetedGestureProposal extends [BaseGestureHandlingProposal](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-basegesturehandlingproposal-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export abstract class TargetedGestureProposal--><!--Device-unnamed-export abstract class TargetedGestureProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## node

```TypeScript
node: FrameNode
```

处理当前智慧手势的目标节点。

**类型：** FrameNode

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TargetedGestureProposal-node: FrameNode--><!--Device-TargetedGestureProposal-node: FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

