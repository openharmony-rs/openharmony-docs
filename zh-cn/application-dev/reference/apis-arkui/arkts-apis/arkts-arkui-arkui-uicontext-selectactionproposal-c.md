# SelectActionProposal

智慧手势选中动作处理。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会使目标组件被选中。

**继承/实现关系：** SelectActionProposal extends [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export class SelectActionProposal extends TargetedGestureProposal--><!--Device-unnamed-export class SelectActionProposal extends TargetedGestureProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(node: FrameNode)
```

智慧手势选中动作处理的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectActionProposal-constructor(node: FrameNode)--><!--Device-SelectActionProposal-constructor(node: FrameNode)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 响应选中动作的目标节点。 |

