# ResolvedUIContext

ResolvedUIContext实例对象。

> **说明：**
> 
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。
> 
> - ResolvedUIContext继承自[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)，并新增strategy属性用于记录该UIContext实例的解析策略。

**继承/实现关系：** ResolvedUIContext extends [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## strategy

```TypeScript
strategy: ResolveStrategy
```

[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)的解析策略。

**类型：** [ResolveStrategy](arkts-arkui-arkui-uicontext-resolvestrategy-e.md)

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
