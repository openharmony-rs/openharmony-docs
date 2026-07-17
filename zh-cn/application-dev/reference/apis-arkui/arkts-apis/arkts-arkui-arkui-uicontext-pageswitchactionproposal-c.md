# PageSwitchActionProposal

智慧手势翻页动作处理，默认方向为向前翻页，包括向右和向下。当通过[registerMonitor](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值[GestureHandlingResolution](arkts-arkui-arkui-uicontext-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的翻页操作。

**继承/实现关系：** PageSwitchActionProposal extends [TargetedGestureProposal](arkts-arkui-arkui-uicontext-targetedgestureproposal-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export class PageSwitchActionProposal extends TargetedGestureProposal--><!--Device-unnamed-export class PageSwitchActionProposal extends TargetedGestureProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(node: FrameNode, pageCount: number)
```

智慧手势翻页动作处理的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PageSwitchActionProposal-constructor(node: FrameNode, pageCount: int)--><!--Device-PageSwitchActionProposal-constructor(node: FrameNode, pageCount: int)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 响应翻页动作的目标节点。 |
| pageCount | number | 是 | 翻页数量。<br/>取值范围：[0, +∞)，小于0时按0处理。<br/>单位为页。 |

## pageCount

```TypeScript
pageCount: number
```

智慧手势翻页数量。

取值范围：[0, +∞)，小于0时按0处理。

单位为页。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PageSwitchActionProposal-pageCount: int--><!--Device-PageSwitchActionProposal-pageCount: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

