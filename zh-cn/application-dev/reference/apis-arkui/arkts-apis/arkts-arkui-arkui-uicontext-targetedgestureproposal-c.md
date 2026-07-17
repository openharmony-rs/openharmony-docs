# TargetedGestureProposal

带目标节点的智慧手势处理基类。

**继承/实现关系：** TargetedGestureProposal extends [BaseGestureHandlingProposal](arkts-arkui-arkui-uicontext-basegesturehandlingproposal-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export abstract class TargetedGestureProposal extends BaseGestureHandlingProposal--><!--Device-unnamed-export abstract class TargetedGestureProposal extends BaseGestureHandlingProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
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

